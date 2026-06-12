---
title: "Networking??? howto"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by sandclock on 2007-12-24
Hey
I am sorry if i am asking someting really dumb and stupid I am new to ubuntu I have been using winxp for several years i have small network of 6 pcs. one of then installed ubuntu but i dont have an idea how to setup network connections
facts
1. other pcs using windows xp
2. all pcs connected through wired network
3. Internet connection is directly connected to network switch
4. One pc is on Ubuntu / winxp dual boot
5. I can brows internet and local netwrok from windows on that dualboot pc
what i did
1. I configured wired network mannually from ubuntu providing exact IP subnet and defauly getway which i use for windows
2. tried browsing internet it didnt work
3. In Places--> Network it only shows windows network but when i enter that there is noting in it too
Thanks in advance
Regards
Nik
I love ubuntu

---

### Post by sandclock on 2007-12-24
update on this something i forgot 
i am using ubuntu 7.04
thanks
Nik

---

### Post by sandclock on 2007-12-24
anyone?

---

### Post by burbankmarc on 2007-12-24
> 
1. I configured wired network mannually from ubuntu providing exact IP subnet and defauly getway which i use for windows
2. tried browsing internet it didnt work


sounds like you forgot about the DNS. Check your DNS ip, and make sure your /etc/resolv.conf has that ip in it.

the following is an example:

```
nameserver *your.dns.ip.address*
```

---

### Post by sandclock on 2007-12-25
I have put dns and they are present in resolve.conf in the etc folder :(( 
do i have to install my realtek lan card?
thanks and regards
Nik
I love Ubuntu

---

### Post by xeth_delta on 2007-12-25
I am not sure I completely understand your problem, but isn't it possible to obtain the IPs via DHCP? Did you need to use a fixed IP?

---

### Post by jonandrews on 2007-12-25
I have put a step-by-step guide to networking Windows & Ubuntu pc's on a web site:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

I hope it's helpful to you.

---

### Post by sandclock on 2007-12-25
Hi
thanks for your step by step guide 
"D/clicking on it will take you to [the name of your windows network], in my case mshome

 

D/clicking on mshome will display all the Windows pc's currently on your network, and you can click on their icons to see their shared folders and files."

I can see Windows network but when i double click it i dont see anything where actually i should see my network "zenith' in my case. am i doing something wrong here?
Regards
nik

---

