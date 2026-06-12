---
title: "Kubuntu 10.10 No Network Interfaces"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by dkc.com on 2010-10-30
Hi friends,

I had Ubuntu 10.04 LTS on my Dell Inspiron 1520 for about last 6 months and everything was running fine. When I tried to upgrade it to Ubuntu 10.10, the system got mad and it wasn't working at all.

So I did a fresh installation of Kubuntu 10.10 after formatting the hard drive from live USB. It said that installation was successful but it's not connecting to internet by either ethernet or wifi.

The system tray applet shows the message 'No Network Interfaces' and when I go to Settings>Network Connections, it won't offer me anything clickable except VPN.

Strange enough, ethernet was working at the time of installation from live USB.

Please help.

---

### Post by bioterror on 2010-10-30
> **dkc.com said:**
> Hi friends,

I had Ubuntu 10.04 LTS on my Dell Inspiron 1520 for about last 6 months and everything was running fine. When I tried to upgrade it to Ubuntu 10.10, the system got mad and it wasn't working at all.

So I did a fresh installation of Kubuntu 10.10 after formatting the hard drive from live USB. It said that installation was successful but it's not connecting to internet by either ethernet or wifi.

The system tray applet shows the message 'No Network Interfaces' and when I go to Settings>Network Connections, it won't offer me anything clickable except VPN.

Strange enough, ethernet was working at the time of installation from live USB.

Please help.

Networking is enabled? Right click on that same icon.
Nic's cant be broken becouse those was working okay when you installed it.

---

### Post by amateur_mav on 2010-10-30
I installed Ubuntu 10.10 on my Dell Inspiron and it worked so flawlessly that I installed it on my desktop too. But it doesn't work so good as a VirtualBox guest on an XP host. Anyway, check your BIOS settings and if NIC is properly Enabled then try using the Additional Drivers utility in the Admin menu.  You might want to try using the System Testing utility too.

---

### Post by Ganton on 2010-11-08
> when I go to Settings>Network Connections, it won't offer me anything clickable except VPN.
You could go to the command line and execute
```
ifconfig
```
and tell us the results.

---

### Post by shadrack111 on 2010-11-13
ive been using ubuntu 10.10 for a month or so and so i decided to dual boot kubuntu 10.10 but after installing kubuntu i can get on the internet with kubuntu. from what i can tell ubuntu is still working fine with the exeption that it wont find my internal mic so i can talk on skype or anything. any advice. im still new to linux.

---

### Post by Ganton on 2010-12-10
> **shadrack111 said:**
> ive been using ubuntu 10.10 for a month or so and so i decided to dual boot kubuntu 10.10 but after installing kubuntu i can get on the internet with kubuntu. from what i can tell ubuntu is still working fine with the exeption that it wont find my internal mic so i can talk on skype or anything. any advice. im still new to linux.

The problem that you show is different than the one in this thread. 

I suggest that you could go to [http://ubuntuforums.org/forumdisplay.php?f=334&daysprune=-1&order=asc&sort=postusername](http://ubuntuforums.org/forumdisplay.php?f=334&daysprune=-1&order=asc&sort=postusername) and click on "New thread" to start a new thread, so things don't mix.

---

