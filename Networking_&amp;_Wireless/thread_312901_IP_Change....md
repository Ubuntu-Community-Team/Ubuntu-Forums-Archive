---
title: "IP Change..."
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by AL3X on 2006-12-05
Hi everyone :) I have one question: How can I change my IP ? 
I have ADSL with dynamic ip designed by DHCP. I made a program for windows that was able to do that, but I`m still just a noob in linux :( and i can´t make it...
In windows the program was in bat and I used the commands :
ipconfig /release
ipconfig /renew
...
Is there something similar to those in linux ?

Thanks a lot :)

Hola a todos :) Tengo una pregunta: Como puedo cambiar la IP ?
Tengo internet ADSL con cambio de IP dinamico, designado por DHCP. Hize un programa para windows que podia cambar la ip, pero en linux sigo siendo un novato y no se como hacerlo...
En windows use los siguientes comandos:
ipconfig /release
ipconfig /renew
...
Hay algo parecido en linux ?

Gracias :)

---

### Post by spd106 on 2006-12-05
Try 
sudo dhclient -r  
sudo dhclient

you can also specify the interface, check man dhclient for more options .

---

### Post by AL3X on 2006-12-12
Wont wokr.... 
Any other idea ?

tnx

---

### Post by earobinson on 2006-12-12
```
sudo ifdown eht0
sudo ifup eth0
``` that work? Or
```
sudo /etc/init.d/networking restart
``` ... nope that one wont work for me
```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
``` That one dont seem to work

---

