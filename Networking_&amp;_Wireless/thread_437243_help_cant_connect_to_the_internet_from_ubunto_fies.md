---
title: "help cant connect to the internet from ubunto fiesty"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by farside bunny on 2007-05-08
Hi all!!
very very new to linux just installed 7.04 and after reconfiguring my modem to router i still cant get internet access in ubuntu(just stole my lab partner's computer to post this) and for some reason all i can see in the connection menu is just a simple dial up and no broadband 
can any 1 help me ? i don't even know where to start !!!
:mad:

---

### Post by loserboy on 2007-05-08
is it a wireless or wired connection

---

### Post by farside bunny on 2007-05-08
wierd

---

### Post by farside bunny on 2007-05-08
ill rephrase my self ,for some reason i dont even see the fact that i have any router installed or any other indication of broadband connections

---

### Post by jerrylamos on 2007-05-08
What do you get when you do
Applications, Accessories, Terminal
ifconfig

Also, there should be a  little icon at the top right of the screen that looks like a monitor;if you put your cursor on it, what does it say?  If you click on it, what does it say?

Cheers, Jerry

---

### Post by farside bunny on 2007-05-08
it says no network connections ill post the output of ifconfig 2morow since i cant hog my friends computer for all the time 
thanks everyone !!:guitar:

---

### Post by loserboy on 2007-05-08
real friends let friends take home computers whenever they want... .jk

---

### Post by farside bunny on 2007-05-08
o.k what it gives me when i do ifconfig is :

```
linkancap:local loopback
inetadrr:127.0.0.1 mask 255.0.0.0
inet6 adrr: ::1/128 scope:host
up loopback running mtu:13 436 metric 1
rx packets:2 errors:0 dropped:0 overruns:0 frame:0
tx rx packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
rx bytes:100 (100.0b) tx bytes:100 (100.0b)

```
and when i put the curser on the network manger i get :"no  network connections"
so what to do now?

---

### Post by farside bunny on 2007-05-09
bump!
help i really need some sort of advice here:confused: :confused: :confused:

---

### Post by dodgePT on 2007-05-09
Well, i got a modem/router, and after ubuntu's installation i never had to configure anything, it just worked out of the box.

edit: was your network adapter detected and installed?

---

### Post by farside bunny on 2007-05-09
no i need to somehow install it i think since in the network manger i dont see it

---

### Post by farside bunny on 2007-05-09
FYI 
i have an "agere systems ET -131x PCI-E gigabit ethernet controller "

---

### Post by dodgePT on 2007-05-09
So i guess that's your problem right there, your network adapter not being detected. Unfortunetly i'm still a noob when it comes to hardware issues, maybe other user can help you.
Did you search the manufacturer's site for linux drivers?

---

### Post by farside bunny on 2007-05-10
bump!!
how do i install the ethernet card ? i am such a noob when it comes to this kind of things 
help someone!!:confused: :confused:

---

### Post by loserboy on 2007-05-10
do me a favor and go to a terminal and type

>  lspci

then show the output


Edit: also are you trying to connect to dialup or broadband, if broadband is it DSL or cable

---

### Post by farside bunny on 2007-05-10
> **loserboy said:**
> do me a favor and go to a terminal and type



then show the output


Edit: also are you trying to connect to dialup or broadband, if broadband is it DSL or cable


is there any way to some how copy the output i get in ubuntu to windows?
i have dual boot and each time i wana try something i have to boot again and go in to ubuntu since i only have workign internet in windows?
the output was way to long ot copy manully but when i played around a bit with the devcie manger thing it showed me that it can see the ethernet card but it does not recognize it/
also i am trying ot connect broadband in adsl 
again thanks for all the help!!

---

### Post by loserboy on 2007-05-10
i'm sure there is a way, but I can't think of it off hand, but I can help you narrow it down to something you can just write.

when you type "lspci" it shows you basically your connected devices and I wanted to make sure lspci saw your ethernet card, what you're looking for is something like

02:02.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
or
02:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

(that was just what mine says)

---

### Post by hessiess on 2007-05-10
this is what i do

use comand

copy to a word document

save as .doc to a memery stick.

reboot as windows ant you should be able to copy the word doc to the form.

it's a pain, i know!

---

