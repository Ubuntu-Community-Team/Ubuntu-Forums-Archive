---
title: "Tarjeta wifi rtl8812au no funciona en ubuntu (solucionado)"
date: 2019-04-12
forum: Networking &amp; Wireless
---

### Post by zoyo101 on 2019-04-12
Buenas a todos y gracias de antemano, soy nuevo en el foro aunque me he servido de el en numerosas cuestiones. Entrando en materia, el tema es que he estado utilizando mi tarjeta wifi usb con chipset rtl8812au con normalidad hasta ahora en ubuntu 18.04 instalando los controladores a traves de git. El problema me ha surgido despues de un formateo forzoso que realize ayer, desde entonces he instalado diferentes controladores pero ninguno de ellos ha funcionado correctamente, me reconoce la antena, pero la misma parece que estuviera sorda, no detecta ninguna red.

Tambien he probado con los controladores de los repositorios oficiales de ubuntu.... :(

Si algun alma caritativa me ayudara estaria agradecido y me ahorraria el comprar otra antena, gracias de antemano.



Finalmente he conseguido solucionarlo yo mismo, por si a alguien pudiera servirle explico como:

 Primero desmonte y eliminé los modulos relacionados al chipset en cuestion (8812au)

despues instale los controladores tal y como se describe aqui [https://ubuntuforums.org/showthread.php?t=2409357](https://ubuntuforums.org/showthread.php?t=2409357) ( me guié por estos ya que fue el post que encontre con la fecha mas reciente y por ende tambien supuse que la version de los drivers estaria mas actualizada )

Aun no funcionaba por lo que probé a desconectar el adaptador y a volver a conectarlo y se hizo la magia. Gracias igualmente:P.

---

### Post by chili555 on 2019-04-12
Google translation:

> Good to all and thanks in advance, i am new to the forum although i have used it in numerous issues. Going into matter, the issue is that i have been using my wifi card usb with rtl8812au chipset with normal until now in ubuntu 18.04 installing the drivers through git. The problem has arisen after a forced formatting that i made yesterday, since then i have installed different drivers but none of them has worked correctly, the antenna recognizes me, but it seems to be deaf, it does not detect any network.

I have also tried with the drivers of the ubuntu official repositories ....

If any kind soul would help me i would be grateful and it would save me buying another antenna, thanks in advance.

Finally i have managed to solve it myself, in case anyone could help explain how:

First remove and remove the modules related to the chipset in question (8812au)

then install the drivers as described here [https://ubuntuforums.org/showthread.php?t=2409357](https://ubuntuforums.org/showthread.php?t=2409357) (i was guided by these as it was the post that i found the most recent date and therefore also assumed that the version of the drivers would be more updated)

it still did not work so i tried to unplug the adapter and reconnect it and the magic was done. Thanks also.

---

### Post by zoyo101 on 2019-04-13
Ok thanks and sorry

---

