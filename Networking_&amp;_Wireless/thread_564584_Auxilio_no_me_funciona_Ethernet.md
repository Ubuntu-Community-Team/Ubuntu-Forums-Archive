---
title: "Auxilio no me funciona Ethernet"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by armilso on 2007-10-01
Auxilio, instale  ubuntu 7.04  y  al tratar de configurar la conexion a Internet a través de ethernet, no me aparece el icono  de tarjeta, unicamente me aparece el modem.
Revie el archivo /etc/network/interfaces y alli aparece claramente definido eth0,eth1,etc...
ag
uien me puede por favor indicar como soluciono este inconveniente..
cabe aclarar que si monto el live cd de kubuntu, me reconoce  la conexion...
:confused:

---

### Post by bull8042 on 2007-10-01
Quero alludarte, pero ya no peudo explicar en expanol. Disculpa.
Pero, si preguntas en esta forum: [http://www.ubuntu-es.org/index.php?q=forum](http://www.ubuntu-es.org/index.php?q=forum)
yo se que hay algien alli quien puede alluda.
Bull

---

### Post by noob12 on 2007-10-01
[I missed bull8042's response.  This may or may not be helpful.]

This forum is in English, so I'm not sure how much of a response you'll get in Spanish.  I hope you can understand the following. Even my menu directions here are in English.  

First boot from the hard disk.  Run a terminal (Applications | Accessories | Terminal).  Run the following commands which will save output to files in /tmp .

```

lspci -vvnn >/tmp/lspci.txt

sudo lshw -C network >/tmp/lshw.txt

dmesg >/tmp/dmesg.txt

```

Boot the Live CD  (where you say you have connectivity). 

Mount the hard disk volume by going to Places | Computer .  Find the correct volume. Right-click and select Mount Volume .   In my English system, this mounts the volume as **/media/disk**.  In the directions below, you may need to replace **/media/disk** with what you see.

Run a terminal (Applications | Accessories | Terminal).  Post the output of the following commands

```

lspci -nn

sudo lshw -C network

ifconfig -a

dmesg


cat /media/disk/lspci.txt

cat /media/disk/lshw.txt

cat /media/disk/dmesg.txt

```

---

