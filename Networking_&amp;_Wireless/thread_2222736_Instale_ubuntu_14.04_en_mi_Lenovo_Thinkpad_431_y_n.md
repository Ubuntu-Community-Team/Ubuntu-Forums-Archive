---
title: "Instale ubuntu 14.04 en mi Lenovo Thinkpad 431 y no tengo WIFI"
date: 2014-05-07
forum: Networking &amp; Wireless
---

### Post by feo_war on 2014-05-07
Hola amigos, 

Hoy compre mi Lenovo Thinkpad e431 con FreeDOS, elimine FreeDOS e instale Ubuntu 14.04, toda la instalación resulto bien, la realice conectado al cable de red, pero posteriormente me di cuenta que no tenia redes wifi, he intentado de muchas maneras pero aun no logro activar el wifi, si tienen alguna ayuda por favor comentarla.

El modelo de mi tarjeta Wifi es [COLOR=#141823][FONT=Helvetica]Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

[/FONT][/COLOR][ATTACH=CONFIG]252967[/ATTACH]

---

### Post by vejuma71 on 2014-08-22
tube el mismo problema con una makina mas vieja. Ubuntu viene con una gran variedad de drivers y lo unico ke hay ke hacer es dejar ke la makina corra por algunos dias. Yo trate de arreglar el problema atravez de la terminal pero no pude hacer gran cosa, el problema aveces es solo un conflicto en la rutina de inicio pero se corrige con el uso. Se ke ya paso un buen desde ke pusiste esta post, talvez ya arreglaste tu problema, pero si no, dejame saber. [email]vejuma71@yahoo.com[/email]

---

### Post by chili555 on 2014-08-22
I hope you can understand or at least Google translate my answer.

The correct driver for this device can be installed with a working ethernet connection:```
sudo apt-get install bcmwl-kernel-source
```Be sure to check that the wireless switch or key combination; Fn+F2 or similar, is set to enable the wireless:```
rfkill list all
```

---

