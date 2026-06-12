---
title: "ISA Network Card Intel Etherexpress Pro not working under Ubuntu"
date: 2005-07-30
forum: Networking &amp; Wireless
---

### Post by jeff2292000 on 2005-07-30
Dear Fellow Ubuntu Users,

I would like to know how I would go about setting up a older ISA style network card , a Intel etherexpress Pro. Unbuntu has not identified it , I assume older ISA cards are not well supported under Ubuntu. 
Is it possible to manually install it? If so, what is the procedure?

Regards,

Jeff.  
Perth,Western Australia

---

### Post by heimo on 2005-07-30
Probably e100 or eepro module should do it. You may need to enter parameters (for IRQ, I/O and stuff) by hand, but it may even work with plain and simple
 ```
sudo modprobe e100
sudo modprobe eepro

``` 
If either one of those doesn't give errors, it's probably successfull and you can verify this with ifconfig eth0, which should show you a new interface (eth0). You should add correct module to /etc/modules so it gets loaded automaticly during boot.

I'm not sure, but you may find isapnptools helpful.

---

### Post by jeff2292000 on 2005-07-30
Hmmm, 

sudo modprobe eepro

doesn't give error message, but then ifconfig -a doesn't list eth0 as present.

ifup eth0 does give a error message though.

Jeff

---

### Post by heimo on 2005-07-30
It's possible that you need to give some parameters for that module.

It's been a long time since I last configured any isa-card, but I faintly remember using isapnptools (package) and pnpdump to find more information.

Did loading of the module create eth0 directory under /sys/class/net ?

What does the error message with ifup eth0 say?

modinfo eepro tells you the possible parameters (irq, mem, io) and you can set those when issuing modprobe eepro, ie:
modprobe eepro irq=9

---

### Post by jeff2292000 on 2005-07-30
Well I have it working. 
My procedure was to:

1. Use Intel "Softset2" utility to set irq and io address on the card manully.         (in order to use softset2 you must use a DOS boot floppy BTW)
I set irq=5 and io=0x320
save settings and then a cold reboot

2. Next was to goto the BIOS, I disabled onboard sound( which I didn't really need) also disabled USB as well(which I don't need)

3. Reboot. startup Ubuntu Linux. Goto terminal
   issue command: sudo modprobe eepro io=0x320 irq=5

a check of ifconfig showed eth0 up and running. Problem solved.

In conclusion  I suspect the onboard sound irq was conflicting with the network card. Disabling this freed irq 5 for the netcard.

---

### Post by heimo on 2005-07-30
Great! Thanks for summarising the solution.

---

### Post by jackwhite on 2005-08-09
Hey, 

I think I might be having the same problem. Is ther any way to set the irq and io address in Ubuntu?

---

### Post by lakosked on 2006-08-03
I was excited to see this thread.  I had hopes that it would solve my issue... but alas it did not.  Its been a year since any input here so here it goes....

I too have an Intel Etherexpress Pro 10.  I configured the card in DOS, io=310  irq=11.   I have issued the command: sudo modprobe eepro io=0x310 irq=11

I then checked ifconfig -a  and eth0 did show up with the correct mac address.  But I could not get to the internet or ping anybody.  I then tried ifup eth0, but that gave me an error.  I am very familiar with PC's but not with the guts of Linux.  Am I forgetting to set some files here?  I checked the etc/modules file and tried adding the eth0 to it but that just made my mouse go haywire so I took it out. I just hate throwing away functional equipment. Any help in getting my old network card working is greatly appreciated.

---

### Post by lakosked on 2006-08-04
OK problem solved...  sort of.
By following the info above and the thread in "breezy>networking> eepro Network Adapter disappears after boot"  I have successfully connected to the internet.  But I have the same problem as the guy in the other thread. SO I will consider my case closed in this thread and continue my case in the other one.

---

