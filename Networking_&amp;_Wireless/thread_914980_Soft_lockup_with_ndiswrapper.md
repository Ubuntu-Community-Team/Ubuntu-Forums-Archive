---
title: "Soft lockup with ndiswrapper"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by bgugi on 2008-09-09
yet again i turn to this forum with a problem i cannot find the solution to, this time being networking. i looked around, but i couldn't find any threads in which this was resolved, or any recent threads to bump/add information

my (03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02); according to lspci) was working fine with the "restricted" driver, except for the fact i could not connect to ad-hoc networks (frantic google searching revealed that the 'restricted' driver does not yet support ad-hoc networking).

so i decided to use ndiswrapper, the install seemed to go fine, i used the drivers that were listed several times on the ndiswrapper list, and i didn't seem to receive any errors. it reported that the inf was installed fine, and that the hardware was present. however, it didn't create a network interface (now i'm down to eth0 and lo). 

then the system rape started. i couldn't boot (soft lockups at startup, immediately after something about hal), i couldn't shut down (soft lockups while trying to unbind ndiswrapper, or something to that extent. i booted with root shell, and used aptitude to remove ndiswrapper. the computer booted fine, albeit without any wifi, and shut down fine. reinstall ndiswrapper, rape again. uninstall, fine.

what's the deal? is there anything else you want me to do?

---

### Post by bgugi on 2008-09-10
bump for assistance?

---

### Post by bgugi on 2008-09-11
here's some bonus info, plus a shameless bump.

have tried both 1.53 made from source as well as whatever is in synaptic.
got "forcing parameter IBSSGMode from 0 to 2" when installing the inf file (don't know whether this was new or had always been there)
the depmod/modprobe commands don't say anything (are they supposed to?)
these seem to be in my log recently, don't know if related ( Sep 11 21:51:58 OPERATOR kernel: [  359.834137] atkbd.c: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
Sep 11 21:51:58 OPERATOR kernel: [  359.834143] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.)

can i at least get a 'that sucks, dude' from you guys? that way i know i'm not being totally ignored? ](*,)

---

### Post by Pixtu on 2008-09-12
I too have had this same problem.

I have got nowhere trying to connect with native Ubuntu drivers (left message on this forum 2 weeks ago which is currently unanswered).

So I tried using ndiswrapper. As with yourself, everything appeared to install correctly, but system hung on shutdown/restart and failed to start properly 'looping' around Soft Lockup.

---

### Post by bgugi on 2008-09-14
bump for confirmed problem, as stated: standard drivers work, no ad-hoc. 


this might just make me migrate back to windows... :-&

---

### Post by bgugi on 2008-09-22
one more bump

come on, somebody has to know this...

---

