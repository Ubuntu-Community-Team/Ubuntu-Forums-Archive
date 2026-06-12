---
title: "Cannot connect to internet"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by maxedoubt on 2010-06-18
Upgraded to 10 last night and all was well. Set my computer to hibernate and this morning I cannot connect to the internet. No connection shows up in network connections. I know my modem is ok because im connected to it now on my other computer. PLease help.:confused:

---

### Post by Chesamo on 2010-06-18
Did you try shutting the computer off and turning it back on? It could be that your network hardware didn't reactivate coming back up out of hibernation.

---

### Post by Saint_ on 2010-06-18
> **Chesamo said:**
> Did you try shutting the computer off and turning it back on? It could be that your network hardware didn't reactivate coming back up out of hibernation.
+1

Aye, I've heard a lot of people having trouble with this in 10.04. Just reboot your computer and hopefully it works, let us know.

---

### Post by maxedoubt on 2010-06-18
Yes, I have rebooted my computer a few times as well as my modem. It's strange that it worked fine last night after the upgrade. Is there a way to see if the hardware is working ? THe lights on the ethernet port are lit and my modems ethernet light is on light it sees a connection. Is there a way to roll back to the previous version of  ubuntu which was working?

---

### Post by Saint_ on 2010-06-18
> **maxedoubt said:**
> Yes, I have rebooted my computer a few times as well as my modem. It's strange that it worked fine last night after the upgrade. Is there a way to see if the hardware is working ? THe lights on the ethernet port are lit and my modems ethernet light is on light it sees a connection.

So neither your ethernet or your wireless is working? In your terminal type ```
ifconfig
``` and paste the results here

---

### Post by maxedoubt on 2010-06-18
No connection at all. Cannot paste bc I'm on a different computer. This is what I get-
 
lo        Link encap:Local Loopback
           inet addr:127.0.0.1 Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING MTU:16436 Metric:1
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes240 (240.0 B)  TX bytes: 240 (240.0 B)
 
Should it show my eth0 also?  Thanks for all the help. This is driving me crazy.

---

### Post by Saint_ on 2010-06-18
Yes it most definitely should show the eth0. Uh try ```
ifconfig eth0 up
``` This really isn't my area of uh, expertise, so bear with me until someone who knows more about this comes along

---

### Post by maxedoubt on 2010-06-18
I really appreciate the help. I can do most anything in Windows but when my harddrive crashed I switched to Ubuntu. I've been able to figure out most problems I have run across but this has got me stumped.
 
When I try that I get this:
SIOCSIFFLAGS: Permission denied

---

### Post by Saint_ on 2010-06-18
Yeah no problem man and sorry about that, just throw a sudo in front of it so: ```
sudo ifconfig eth0 up
```

---

### Post by CharlesA on 2010-06-18
Do you happen to have any hardware drivers avalible (not that you can download them without internet access)?

Try booting off a livecd and see if the network interface shows up.

---

### Post by maxedoubt on 2010-06-18
Eth0 came up now, ifconfig now shows:
 
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:4b:4c:56
            inet6 addr: fe80::20e:a6ff:fe4b:4c56/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
            Rx packets:4 errors:0 dropped:0 overruns:0 frame:0
            Tx packets:6 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:240 (249.0 B)   TX bytes:468 (468.0 B)
            Interrupt:23 BASE address:0x4000
 
lo         
 
all info for lo is the same as before, just don't feel like typing it again.

---

### Post by maxedoubt on 2010-06-18
If I boot from disk (9.10)I get internet acces back. I may just end up reinstalling 9.10 from disk If I can't get this fixed. The only reason I updated to 10.04 was beacause I couldn't get screen resolution above 800x600 in 9.10 but at least I had a connection.

---

### Post by CharlesA on 2010-06-19
Sounds like a video driver problem with 9.10. Does the livecd of 10.04 have network access?

---

