---
title: "BEGINNER:  NETGEAR wireless adapter working under Ubunu 8.04 x64"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by Sam324 on 2008-06-19
Hi.  I have a WPN311 wireless adapter on my PC.  It [worked before the update]("http://ubuntuforums.org/showthread.php?t=834226"), but is now not working.  Is there any driver (native) I can use for it, keeping in mind that I have no access to the internet on that computer?  Could I get step-by-step instructions for the process?  I have a copy of NDISWrapper on a flash drive, but I don't know how to install it.  Any help?

---

### Post by Sam324 on 2008-06-19
[EMAIL="sam@sam-ubuntu:~$"]sam@sam-ubuntu:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:4b:15:c7:0e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x2000 
eth1      Link encap:Ethernet  HWaddr 00:04:4b:15:c7:0c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 Base address:0x4000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86600 (84.5 KB)  TX bytes:86600 (84.5 KB)
[EMAIL="sam@sam-ubuntu:~$"]sam@sam-ubuntu:~$[/EMAIL]

---

### Post by Sam324 on 2008-06-19
I also found that the ndiswrapper is in .tar.gz format.  I don't think I have build-essentials installed, so I can't compile it.  How do I install the program?

---

### Post by Sam324 on 2008-06-19
*Bump?

---

### Post by ians1 on 2008-06-19
I too did the update thing having been trained by Gates's mob to do such things dutifully but now alas no network!

iwconfig is now saying (amongst other things) Access Point: Not-Associated whereas previously it said NETGEAR as thats the wireless routers name.

Any way to roll-back the updates?

ian

---

### Post by Sam324 on 2008-06-19
> **ians1 said:**
> I too did the update thing having been trained by Gates's mob to do such things dutifully but now alas no network!

iwconfig is now saying (amongst other things) Access Point: Not-Associated whereas previously it said NETGEAR as thats the wireless routers name.

Any way to roll-back the updates?

ian

A roll-back, exactly!  Just like System Restore on Win.  I miss SR...one thing where Windows is king.  Is there any similar program in Ubuntu?  Keep in mind I have already tried booting the old kernel in both normal and recovery modes.  If there's an installable rollback program, I'll need something I can save on a USB drive and run on Ubuntu.  For now I've been reduced to typing from the Wii browser.  Thank goodness for Wii!

---

### Post by Sam324 on 2008-06-19
Is it just me, or is this forum dead?  I got way more posts in the beginners' forum.  C'mon, isn't there some driver I can install?  Surely the devs wouldn't declare everyone who updated SOL and move on.

---

### Post by ians1 on 2008-06-19
What I did

I went into the gui (sorry if thats swearing on here) and opened Network

In there click Unlock and enter your password

The select Wireless Connection

Now change the security to WEP and click OK

Wait whilst the thing changes the settings 

Then go in again and change back to WPA (or whatever you had before)

Click OK and let it do the changes

Then I checked iwconfig and its all working now!

Seems the update does soemthing to the wireless security settings

ian

---

### Post by Sam324 on 2008-06-19
:(
I tried unlocking mine, but it had two Wired Connection options, a Point-To-Point option, but no Wireless option.

---

### Post by Sam324 on 2008-06-19
:confused:Bump.*

---

### Post by ians1 on 2008-06-19
sounds like you havent got the driver loaded, what does iwconfig say?

ian

---

### Post by Sam324 on 2008-06-20
TY, but I reinstalled and updated again.  It works fine now.

---

### Post by Sam324 on 2008-06-23
Ok, I was just installing new Nvidia drivers when it happened again.  Same symptoms as before.

---

