---
title: "Can't keep internet connection"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by wrb1975 on 2006-11-01
I'm new to ubuntu and have just installed to a Dell Demension 4400 with an Intel Pro/100 nic.  Running from the CD (DVD) the ethernet /internet seemed to work fine, after I installed the OS the internet would not connect and the eth0 show to be working in all respects.  I found a few Google on IPV6 issues and after turning this off in the modprobe I was able to connect to the internet but, then just a quick I as disconnected.  I unpluged and re-pluged the network cable and lo and behold I was connected again but only for a short time.  I need help.:confused:

---

### Post by Paul41 on 2006-11-01
What is the output when you run **lspci | grep Eth** at the terminal?

---

### Post by wrb1975 on 2006-11-01
Tx for the reply, I was unable to use your command but did run 
**ip a | grep eth** and received verbage with the MAC address and the IP address that was asigned by DHCP.  All of which are correct and if I execute **ifconfig** I can see everything is as it should be.  I re-tested the unplug and re-plug the network cable thing and I have internet access for a couple of minutes and then it goes away.](*,)

---

### Post by Paul41 on 2006-11-01
See if doing this fixes your problem.

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)
Edit/Delete Message

---

### Post by wrb1975 on 2006-11-01
:) Great... I believe that this has done the trick.  I set up a ping to the ISP gateway and it never drop for the 500 cycles that I let it run.   Thanks Paul41 :)

---

