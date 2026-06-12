---
title: "a8v-e ethernet detection"
date: 2005-04-21
forum: Networking &amp; Wireless
---

### Post by bags on 2005-04-21
hy!
first of all, i do not speek english very well...

i have tried to install ubuntu linux but i have a problem: during the installation it does not detect my ethernet cart on the mobo asus a8v-e deluxe.

i have done some searches in google about the problem; someone suggested to type "modprobe -f sk98lin" in the shell, i have tried it without succes... 

can you help me please?

---

### Post by bags on 2005-04-22
up

---

### Post by ejohney on 2005-04-22
that's strange that it didn't autodetect it. but anyway, try typing "sudo modprobe sk98lin" that will run the modprobe command as root.  also, run "lsmod" and check to  see if the module is already loaded.

---

### Post by bags on 2005-04-23
[QUOTE=ejohney]that's strange that it didn't autodetect it. but anyway, try typing "sudo modprobe sk98lin" that will run the modprobe command as root.  also, run "lsmod" and check to  see if the module is already loaded.[/QUOTE]

thasnks! i have tried your commands and i loaded the module!!!

but there is another problem (not so easy ;) ). when X loads and the login appears linux crashes  ](*,) every time! i have tried to reinstall linux 4 times but each time it crashes at the login (the mouse stopps and i have to reboot)
what have i to do?

---

### Post by pirast on 2005-05-10
A question to the first problem (a friend has this motherboard):

I installed ubuntu for him, after that I ran sudo modprobe sk98lin, lsmod shows now s.t. about sk98lin.

But in the gnome network settings there isn't his network card listed.

How can I become the network card to be shown in the gnome network settings?

Thanks,
Martin

---

### Post by pirast on 2005-05-14
Sorry for pushing but it's really important for me/my friend..

Please help me  :neutral: 

Martin

---

