---
title: "Internet problems"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by adamleslie15@hotmail.com on 2009-03-16
Hey everyone, it's me for the second time. Now that I know my computer is fine the way it is. I would like to connect to the internet. Now, I read the "ubuntu pocket guide" for the "getting online" section. I am stuck at a certain point.

I am running Ubuntu 8.04. I have a wired internet situation on my "crappy computer" (specs listed below, its just a computetr I can play with untill I learn enough to try it on a good computer haha). So I went to the part of the guide where it tells me how to connect in this edition with a wired connection. It says to: > System &#61537;
Administration &#61537; Network. In the program window that appears, click
the UNLOCK button and enter your password when prompted. Select the
Wired Connection entry and click the PROPERTIES button.

Now my problem here is that when I go to said "network" there is no "wired connection entry" in the list. Only "point to point connection"


Please help, Thanks,

Adam Leslie

---

### Post by adamleslie15@hotmail.com on 2009-03-16
anything ?

---

### Post by Dynaflow on 2009-03-16
Are you plugging in an ethernet cable, or are you trying to do dial-up?  If the former, it should automatically configure and connect once plugged in.

---

### Post by adamleslie15@hotmail.com on 2009-03-16
Yes I'm plugged in using ethernet. And I also thought the same thing, but it just doesn't work. Could the computer itself be to old?

Thanks
Adam Leslie

---

### Post by Dynaflow on 2009-03-16
Y'know, since this is your messing-around machine and you're on 8.04, try doing a fresh install of 8.10 and see if your problem clears up.  You might kill two birds with one stone. 

I would also take a look inside the machine (if it's a desktop tower) to make sure the NIC card is pushed securely into its slot, assuming it's not built directly into the motherboard.

---

### Post by plucky on 2009-03-16
From a terminal ```
lspci
lshw -C network
ifconfig
``` and post to forum.

---

### Post by adamleslie15@hotmail.com on 2009-03-16
```
adam@adam-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 1b)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 0e)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 0e)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 20)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 21)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
adam@adam-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
adam@adam-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38000 (37.1 KB)  TX bytes:38000 (37.1 KB)
```


theres what i get when i do what you told me too.

and I will try Ubuntu 8.10 soon. As soon as I can get my hands on another CD-R.

Thanks guys for your help!

Adam Leslie

---

### Post by plucky on 2009-03-17
Your Network Controller card is not being seen by the system.This is why you cannot connect to the internet.Make sure it is plugged in securely and check the leds on the card are working.It could be the card is broken.

Until you can see it using **lspci**,then you have no chance of connecting to the internet.

Good luck

---

### Post by adamleslie15@hotmail.com on 2009-03-17
how will i know if it is being seen by the computer or not?

---

### Post by Dynaflow on 2009-03-17
It'll show up in ```
lspci
```

---

### Post by adamleslie15@hotmail.com on 2009-03-17
o ok thanks for your help! much appreciated

---

### Post by adamleslie15@hotmail.com on 2009-03-18
Hey everyone,

Just wanted to say thanks for all the help! I got it to work!!!!

Thanks again,

Adam Leslie

---

### Post by plucky on 2009-03-19
[CENTER]What was wrong? 
How did you get it to work?
Help others with the solution?

[/CENTER]

---

### Post by adamleslie15@hotmail.com on 2009-03-19
I could not get the computer to even realize that it had a network card installed. 

I installed a different network card in the computer and rebooted. The computer from then on was connected to the internet.

Thanks,

---

