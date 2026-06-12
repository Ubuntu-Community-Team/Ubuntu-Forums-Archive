---
title: "broadcom 4315 hp dv2000 dv6000 easy way to make it work on ubuntu 8.04"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by gwolf on 2008-05-11
hi i do this on my hp pavilion dv2845se and i believe it works for all hp laptops whit broadcom 4315, in windows vista i use the driver bcmwl6 buuuut it doesnt work whit ubuntu, you need the bcmw15 and works great same as windows
1.-open a terminal and write:
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
2.- then write:
sudo apt-get install ndiswrapper-common ndisgtk
3.- download and extract [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe) (i try with hp drivers but i had no luck so download this)
4.- then go to system-> administration->windows wireless drivers-> install new driver, then go to the folder where you extract the R174291.exe file and then to de driver_us folder and select bcmwl5.inf and thats all, sorry for the bad english is not my lenguage, now i write it on spanish (my lenguage yeey)

yo hize esto en mi pavilion dv2845se y estoy casi seguro que para cualquier laptop hp con tarjeta broadcom 4315 funciona, para ver que tipo de tarjeta tienes ve al administrador de dispositivos en windows click derecho a tu tareta inalambrica y depsues en propiedades y en mmm no recuerdo donde pero creo es la ultima pestana revisa todas las porpiedades y por ay vas a ver que se repite mucho algo como 43xx y esa es la que tienes en mi caso salia 4315, bueno ahora como se instala en ubuntu
1.- en una terminal teclea esto:
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
2.- despues esto:
sudo apt-get install ndiswrapper-common ndisgtk
3. descargas y extraes [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe) (puedes hacerlo con winrar desde windows o con unzip desde ubuntu)
4.- vas a sistema-> administracion->windows wireless drivers->instalar nuevo controlador, y seleccionas el archivo bcmwl5.inf que esta en la carpeta DRIVER_US que a su vez estaba en el archivo que descargamos y listo, yo no necesite reiniciar, enseguida se puso azul la luz de mi tarjeta

---

### Post by Ivy_ on 2008-09-25
Gracias por escribir esta explicacion!  La voy a tratar ahorita.

---

