# PfSense
Nombre: Juan Felipe Criollo Valderrama
### Documentación

## creacion de redes NAT

1. vamos a herramientas y seleccionamos el menu, luego selecionamos (RED)
<img src="Paso_r1.png" alt="">

2. selecionamos RED NAT, luego le damos click derecho y selecionamos crear
<img src="Paso_r2.png" alt="">

<img src="Paso_r3.png" alt="">

3. cambiamos el nombre, desmaracmos el DHCP y ponemos una ip
<img src="redes2.png" alt="">

---
   
## Instalación y configuracion de maquinas 
###  PfSense

1. Crear la maquina de pfSense y colocamos la iso
<img src="maquina1.png" alt="">

2. Configuramos la memoria  y los procesadores
<img src="maquina2.png" alt="">

3. Configuramos el almacenamiento
<img src="maquina3.png" alt="">

4. Configuracion de la red
<img src="redes1.png" alt="">
<img src="redes3.png" alt="">

5. iniciamos la maquina y  selecionamos Install Install pfSense
<img src="Paso1.png" alt="">

6. le damos siguiente
<img src="Paso2.png" alt="">

7. le damos siguiente
<img src="Paso3.png" alt="">

8. le damos siguiente
<img src="Paso4.png" alt="">

9. le damos espacio y siguiente
<img src="Paso5.png" alt="">

10. le damos siguiente
<img src="Paso6.png" alt="">

11. esperamos y le damos Reboot
<img src="Paso7.png" alt="">
<img src="Paso8.png" alt="">

12. se quita el disco optico para que no se vuelva reniciar la instalacion
<img src="Paso9.png" alt="">

13. Seleccionamos 
* Enter an option: 2
* Enter the number of the interface you wich to configure: 2
<img src="Paso10.png" alt="">

14. Seleccionamos
* Configure Ipv4 address LAN interface via DHCP (y/n) n
* Enter the new LAN Ipv4 address. Press <ENTER> for none:
  > 192. 168.10.1
* Enter the new LAN IPv4 subnet bit count (1 to 32):
  > 24
<img src="Paso11.png" alt="">

15. Seleccionamos
* Configure Ipv6 addres Lan interface via DHCP6 (y/n) n
* DO you  want to... LAN? (y/n) y
* Enter the start address of the IPv4... range: 192.168.10.100
* Enter the end address of the Ipv4... range: 192.168.10.200
* Do you want to revert to HTTP as th webConfigurator protocol? (y/n) y
<img src="Paso12.png" alt="">

16. ingresamos esta URL en el navegador FireFOX del Equipo001
<img src="Paso13.png" alt="">

---

### Equipo001

1. exportamos la mquina
* la seleccionamos y le damos doble clik
* le damos en terminar
<img src="Eq0.png" alt="">
<img src="Eq1.png" alt="">

2. configuramos los adaptadores de RED
* en Adaptador 1: seleccionamos RED NAT 
* en Nombre: LAN
<img src="Eq2.png" alt="">

3. configuramos el SIstema
* Procesadores: 4
* Memoria base: 2048MB

---

### Web001

1. exportamos la mquina
* la seleccionamos y le damos doble clik
* le damos en terminar
<img src="W0.png" alt="">
<img src="W1.png" alt="">

2. configuramos los adaptadores de RED
* en Adaptador 1: seleccionamos RED NAT 
* en Nombre: DMZ
<img src="W2.png" alt="">

3. configuramos el SIstema
* Procesadores: 2
* Memoria base: 2048M

---

## web PfSense

1. En el navegador ponemos esta IP 192.168.10.1/
* en usuario (admin) y en password (pfsense)

2. Configuramos las interfaces
* seleccionamos interfaces, luego Asignnments
<img src="pa0.png" alt="">

3. Se añade una nueva Interfaz
* seleccionamos ADD
* Seleccionamos OPT1
<img src="pa1.png" alt="">

4. Configuramos la nueva interfaz
* marcamos en ENABLE ENABLE INTERFACE
* cambiamos la Descripcion (DMZ)
* Seleccionamos en IPv4 Configuration type   Static IPv4

<img src="pag2.png" alt="">

* Ponemos en IP Address (192.168.20.1) /24

<img src="pag3.png" alt="">

<img src="pag4.png" alt="">

<img src="pag5.png" alt="">

5. revisamos DHCP server / lAN
* seleccionamos Services / DHCP sever

<img src="pag6.png" alt="">

* revisamos que todos los campos

<img src="pag7.png" alt="">

<img src="pa8.png" alt="">

* Guardamos

<img src="pag9.png" alt="">

6. Configuramos DHCP Server / DMZ
*  Ponemos en Address Pool Range (192.168.20.100) (192...200)
<img src="pag10.png" alt="">

* Ponemos la ip En los DNS server (8.8.8.8, 8.8.4.4)
<img src="Pa11.png" alt="">

* Guardamos
<img src="pag12.png" alt="">

7. Configuración de la regla NAT y reglas del firewall
* Ve a Firewall > NAT > Port Forward y crea una regla
* configuramos para que redirija el tráfico entrante en la interfaz WAN, puerto 80, Protocol TPC, Address Family IPv4,hacia la IP interna del servidor web en el puerto 80.
<img src="fi1.png" alt="">

<img src="fi2.png" alt="">

<img src="fi2.png" alt="">

* Destination port range HTTP.
* Redirect target port HTTP 
* Description NAT_Redirgir Puerto 80 a Servidor Web en DMZ
<img src="fi3.png" alt="">
* Guardamos
<img src="fi4.png" alt="">


<img src="fi5.png" alt="">
