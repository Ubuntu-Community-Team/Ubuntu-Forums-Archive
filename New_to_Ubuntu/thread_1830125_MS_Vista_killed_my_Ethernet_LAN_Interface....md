---
title: "MS Vista killed my Ethernet LAN Interface..."
date: 2011-08-21
forum: New to Ubuntu
---

### Post by honeybear on 2011-08-21
Hi,

One buy a new PC. Do not start vista at all.
 I use gparted, resize MS Vista. 

Install my Ubuntu in the free space. No problem with LAN Ethernet cable. 
Ubuntu works great no issue. It can goes like that years...
Got X11 and reboot, thousands, a great machine


One day, I got a strange idea to anyhow give a try to MS vista. 
Ok, grub, arrow key down, select vista
well, after 10min, very disappointed. Vista, I dont like at all. MS is getting worse, for my impression. tahts personal

OK, go back to Linux. !! 
Man eth0 and no way to get Internet. 

ifconfig eth0 192.168.1.10 
gives:

```
SIOCSIFFLAGS: Resource temporarily unavailable
```

dhclient 
returns 
```
SIOCSIFFLAGS: Resource temporarily unavailable
```

I also tried to desactivate WIFI under MS Vista. It does no help

No way. And vista has Internet. Thank you Bill. 

I have a Lenovo IdeaCentre Q150 with  Intel Corporation - 82552 Ethernet

---

### Post by corncob on 2011-08-21
Did you try rebooting your modem and router?  I forget in which order they tell you to turn them back on but try both.

---

### Post by skompier on 2011-08-21
If I go from Linux to Windows, networking is fine. If I go back to Linux from Windows, Linux will not connect. Been that way for years. I have to reset my router BEFORE I boot into Linux. Try that.

---

### Post by MartyBuntu on 2011-08-21
Your ethernet controller is being put to "sleep" by Windows when it is shut down.

I had the same problem. There's a network setting in Windows, something like
"Do Not Put Controller To Sleep" or something like that...If I remember exactly which setting, I'll post it. Hopefully someone else knows what I'm talking about.

As a temporary fix, shutdown the computer and unplug it from the power source for a good 15 minutes. That will reset the LAN device.

---

### Post by Quackers on 2011-08-21
And do the same with the router too.

---

### Post by Jerry N on 2011-08-21
I have just the opposite problem on my primary computer - I normally run Windows 7 on it and if I run Linux and then reboot to Win 7, the ethernet adapter no longer works.  No problem in going from Win 7 to Linux.  The solution:  Turn the power to the computer completely off and then restart.  Depending on your computer, this could mean pulling the power plug.  

My primary computer has some sort power saving mode for the ethernet adapter and I suspect that it could be the root of the problem.  My other computers do not have this problem.

Jerry

---

### Post by honeybear on 2011-08-21
> **Jerry N said:**
> I have just the opposite problem on my primary computer - I normally run Windows 7 on it and if I run Linux and then reboot to Win 7, the ethernet adapter no longer works.  No problem in going from Win 7 to Linux.  The solution:  Turn the power to the computer completely off and then restart.  Depending on your computer, this could mean pulling the power plug.  

My primary computer has some sort power saving mode for the ethernet adapter and I suspect that it could be the root of the problem.  My other computers do not have this problem.

Jerry

I tried too modprobe e300 but nohting happened

It worked !!!
thank you very much Jerry !! you solved it.

I did : shutdown / halt under LINUX. waited

and removed the power cable of everything : TV + Lenovo PC.
wait 15 sec

Put power again (plug 110v electricity)
and then 
turn on TV + PC.

Ethernet is back. Even now posting from Ubuntu !! thank you !

---

### Post by skompier on 2011-08-21
Glad to hear that you have it working again. Please mark this post as solved.

---

### Post by honeybear on 2011-08-21
> **skompier said:**
> Glad to hear that you have it working again. Please mark this post as solved.

Thank you very much !

Although. this is solved, but I guess that modprobe e300 should have worked.
Maybe the driver could be improved for Linux

---

