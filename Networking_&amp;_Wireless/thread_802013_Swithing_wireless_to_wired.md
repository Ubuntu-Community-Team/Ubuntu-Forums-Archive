---
title: "Swithing wireless to wired"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by Znort_Ubern00b on 2008-05-21
Hey all,

My friend has just installed Hardy and has asked me a question to which I have no idea of the answer.

He has a wireless cable router that he uses when playing his Wii,the PC is connected to router, but reverts back to direct wire when just using PC as he finds the speed is halved when using wireless router even when Wii is off.

He tried this last night but had no connection when he plugged the cable directly into the LAN card.

Is there any way he can:
a) speed up router connection to go in line with wired connection thus negating the need to switch or
b) set it up so it recognises the variation of connections.


So to recap
Wii on: cable modem to router to PC(wired) and Wii (wireless), speed slow(even when Wii off)
Wii off: Cable modem to PC(wired), no connection (but when he had XP speed was faster).

Thanks in advance

---

### Post by Znort_Ubern00b on 2008-05-21
bump  :)

---

### Post by Znort_Ubern00b on 2008-05-22
bump...can anyone help me on this??? :confused:

---

### Post by Znort_Ubern00b on 2008-05-22
OK he solved it, all it took was a reboot. 

is there any way he can do this without rebooting the sytem??

---

### Post by Peter09 on 2008-05-22
Hardy should just switch between wireless and wired interfaces automatically.

Post the output of 

[HTML]ifconfig[/HTML]

here so that we can get more information.

PC

---

### Post by Znort_Ubern00b on 2008-05-22
ok will do.

Also would it work if he opened terminal and typed:

ifconfig eth0 down
then 
ifconfig eth0 up

would that refresh the IP?

---

