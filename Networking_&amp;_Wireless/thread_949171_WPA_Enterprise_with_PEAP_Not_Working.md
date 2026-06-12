---
title: "WPA Enterprise with PEAP Not Working"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by nebcanuck on 2008-10-15
Hey there!

So my university campus uses a wireless network with WPA Enterprise encoding, using PEAP security. in 8.04 I managed to connect just fine to the network, with Ubuntu doing most of the detection work, and myself mostly filling in fields (username, password, etc.). However, since I upgraded to the beta version of 8.10, that seems to have ceased. Now, my computer recognizes the encoding required, but while connecting it hangs and eventually asks me to re-insert the information.

Not quite sure what's up. If this is a known bug in 8.10 at this point, that's cool, and sorry for asking. But I'm hoping someone's come up with an easy fix, so that I can get back to connecting at school and don't have to revert to 8.04 in the interim -- something which is a bit more of a pain than it sounds like, since I'm running an Eee PC.

Thanks in advance!

-Ben

---

### Post by Nudgesome on 2008-10-16
I had a similar problem just now when i upgraded, the way i sorted it out was under the PEAP version dropdown box i chose Version 0 and it all started working correctly from then on. Hope that it works for you aswell

---

### Post by nebcanuck on 2008-10-16
I'm afraid not. I've fiddled with pretty much every option available, including the one you recommend. Oddly, there was one time that I managed to connect when I switched back from type 0 to type 1. But since, though the settings didn't change, it has been unable to connect regardless of the type of PEAP I'm using.

The only thing I haven't been able to fiddle with is the CA Certificate. Is that necessary to connect to a protected network? In the instructions for connection provided by my school, they show that a Windows Vista computer will have to accept *their* Certificate. But Ubuntu doesn't give any such recognition. I'm not sure if that's a necessary component to connecting, or if that field is more for my protection.

---

### Post by Spartan22x on 2008-10-27
I'm having this problem as well. Does anyone have any info on this?

Nevermind, just got a chance to try version 0. Worked right away, athough I'm wondering about the CA certificate as well.

---

### Post by wch on 2008-10-27
I seem to be having a similar problem, with my new Dell Inspiron Mini 9 with a Broadcom 4312. I'm using the 8.10 release candidate on it (I've never tried 8.04).

What happens for me is that it keeps trying to connect and it keeps asking me for network authentication -- WPA Enterprise, PEAP, username, password, and all that. I tried switching from PEAP version 1 to version 0, but then my computer simply freezes somewhere in the connection/authentication process and I need to reboot. 

I haven't played with the server CA certificate but I'll try that next...

Update: I tried the server certificates. I still can't connect, but there is one small change: the computer doesn't freeze anymore with PEAP Version 0.

---

### Post by DemaSRV on 2008-10-27
I'm currently having the exact same problem described above. I have no problem connecting to my own broadcasted WPA-Personal connection in my dorm, however whenever I try to connect to Purdue's wireless, it is completely hit or miss.  Sometimes switching to version 1 or 0 works, but sometimes I cannot connect at all although once I attempt to connect to the hidden network, my wireless card sees it.

the network is as follows
PAL2.0
WPA-Enterprise
PEAP, MSCHAPv2

then I use my username and password to connect.

Again prior to the 8.10 upgrade, I was able to connect however I had to reenter all of the settings on each connect after deleting the previous settings.  Now I cannot connect at all.

---

### Post by Arrdee on 2008-10-31
I'm having the same problem -- my university uses a secure and an unsecured network, and I can only connect to the unsecured one now. I've used Version 0 for the PEAP, but it only stays connected for a few minutes, disconnects, and then reconnects me to the other one. Any ideas?

---

### Post by TheSe7enthProphet on 2008-10-31
The following is from a VERY disgruntled point of view:



This is the most frustrating thing I've gone through. Not only am I not able to connect to my school's WPA-Enterprise connection, but attempting to do so actually cause Ubuntu to CRASH. Freeze, stall, and unrecoverable. Everything worked fine under Hardy. Honestly, why the hell mess with what works? 

AGH. I understand that what was changed probably had nothing to do with whatever is causing the problem. 

On top of that, it has decided that I don't have permission to mount my Windows partition, so I've lost access to all of my music. GREAT.

---

### Post by Kretien on 2008-11-02
I am also having the same problem.  I have a broadcom 4321ag card running Intrepid and can see all the networks in the area.  When I try to connect to the WPA network here on campus, using PEAP, Version 1, MSCHAPv2, and a CA cert Thawte_Premium_Server_CA, the network manager thinks for a little while then says Authentication Required.  I have a friend on an intel wireless card who needed to change the PEAP version to 0 in order to connect, but when I try to, Ubuntu locks up and I am forced to do a hard reboot, not fun.  Has anyone an idea or seen a solution to this problem?

Thanks,
Nate

---

### Post by mattgaunt on 2008-11-03
Plus one for this problem, I am currently using the restricted drivers for broadcom wireless in my MacBook 1.4 running 8.10.

I got this working in 8.04 by not installing the restricted drivers. I can't do this though since my wireless didn't work out of the box until i installed the restricted drivers. This is what's leading me to think it is something to do with the broadcom drivers.

My computer will either try and connect then fail OR will start connecting and then just freeze my computer :-(

---

### Post by Surfrock66 on 2008-11-03
Having similar problems, used to connect via WPA with Hardy, now can't connect at all in Intrepid.  If it helps, here's the configuration guides for my school, I've tried everything and it simply doesn't work.

[http://its.uncg.edu/Projects/Wireless_Refresh/Configure/](http://its.uncg.edu/Projects/Wireless_Refresh/Configure/)

---

### Post by jakegub on 2008-11-13
Add one more to this problem.  
Dell m1330 using BCM 4328

I tried the driver that ubuntu installs with and I also used a driver from dell using ndiswrapper.  

both drivers caused the computer to freeze during the connection with my school's WPA/WPA2 connection.

---

### Post by mk4umha on 2008-11-14
+1 Same issue here. Sometimes it will connect after 4-5 tries, then it will disconnect after 10mins, sometimes 2 hours then I have to go through that trouble again to get it to connect.

---

### Post by jcollins on 2008-12-02
bump

I have the same issue here. It appears there is a different method of connecting. You now need to connect using a certificate file, whereas before you had to connect with just a user name and password.

I work at itap (the Purdue IT department) and see this problem a lot. It is not a driver issue. I have seen Broadcom and Intel having these problems. Sometimes you can connect but it never stays connected.

---

