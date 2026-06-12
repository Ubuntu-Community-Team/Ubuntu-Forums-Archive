---
title: "switching my brother - no internet"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by DFreeze on 2007-06-01
I’ve tried to fix the extremely slow and crappy-driver plagued el-cheapo system (Celeron 2.8, 512 MB RAM) by giving him Ubuntu. Yes, that may turn out to be a challenge, but since he’s the not demanding type (“where’s the internet, does it have MSN, can I still read my mail”) I thought I’d give it a go.

Using the LiveCD, we quickly discovered that everything worked out of the box. Even his Logitech webcam! Applying the network settings from is ISP (cablemodem) we browsed the internet in no time.

However, after install, the network settings that worked before, didn’t anymore. I applied the exact same IP, gateway, DNS, Host and domain settings, checked them again and again, but to no avail. 
Changing the hostname prompted me to re-login. That did it for the liveCD, but not for the installed OS. 

What’s going on here? I thought an internet-grown OS would at least do that part right. I had my doubts about the webcam, but never the internet. 

Is is possible the firewall settings are stricter once installed? Or are there other differences between liveCD and installation that explain why it’s not working? Please help me figure this out. 

…It ‘d be a shame to reinstall Windows after the evangelism I bored him with yesterday … ;-)

---

### Post by Genecks on 2007-06-01
> **DFreeze said:**
> Or are there other differences between liveCD and installation that explain why it&#8217;s not working?

I've been using a philosophical logic to understand Linux this whole week, and I figure this is what's going on. So, compare and contrast to find what's wrong.

---

### Post by DFreeze on 2007-06-01
> **Genecks said:**
> So, compare and contrast to find what's wrong.

I'd love to do a philosophical version of bitwise comparison, but I guess I'm not that skilled  ;-)

In order to find the differences, one must be able to interpret them as such. I **see **no difference between Ubuntu on the LiveCD and harddisk, but I'm sure there are many. 

I did check whether the ethernet adapter (onboard) was still detected, and it showed up as eth0. Also, when placing the system-monitor applet in the taskbar, I could see the network having some kind of activity. But then again, these windows auto-scale, so the little spikes I see might just as well be nothing. On mouseover, it said "Network 0%" mostly. but I saw some spikes, so it's not flatlining all the way.

Anyway, if someone could get me started on how to find the solution to this problem, please speak up!

---

### Post by Rui Pais on 2007-06-01
hi,
essentially net configuration it's on file /etc/network/interfaces. 
you can boot from the liveCD, get a connection and after that copy that file to a pen or mount your already installed system and copy it to your /home there. 

Then you can reboot normally and do the "philosophical bitwise comparison" :)

Another advised thing is get a list of loaded modules (drivers):
```
lsmod > lsmod_liveCD.text
```
and save that too to compare with lsmod of the running installed version. 
I heard that sometimes detection programs on livecd work better then ones installed or a config file may be missing that prevents some fundamental module isn't loading...

good luck.

---

### Post by DFreeze on 2007-06-01
He, I'm typing this from his PC. I tried to get networking back up with the LiveCD. Nothing... So I went to the folder of /etc/network, like you said. Checked out interfaces, and saw nothing out of the ordinary.
But in that folder I saw the scripts for bringing interfaces up and down, and I remembered all my trouble with wireless. So I just typed in 'sudo ifup eth0', and off I went... Never thought that the wired ethernet interface wouldn't be up allready.

Will it stick? Or should I add some startup command so eth0 will come up upon boot automatically. Giving my brother linux is one thing, making him type CLI commands from day one is maybe a bit too much to start with ;-)

Anyway, thanks for helping me out on this. If anyone could chime in on the eth0 up on boot, I'd be very grateful.

---

### Post by Rui Pais on 2007-06-01
> **DFreeze said:**
> He, I'm typing this from his PC. I tried to get networking back up with the LiveCD. Nothing... So I went to the folder of /etc/network, like you said. Checked out interfaces, and saw nothing out of the ordinary.
But in that folder I saw the scripts for bringing interfaces up and down, and I remembered all my trouble with wireless. So I just typed in 'sudo ifup eth0', and off I went... Never thought that the wired ethernet interface wouldn't be up allready.

Will it stick? Or should I add some startup command so eth0 will come up upon boot automatically. Giving my brother linux is one thing, making him type CLI commands from day one is maybe a bit too much to start with ;-)

Anyway, thanks for helping me out on this. If anyone could chime in on the eth0 up on boot, I'd be very grateful.
glad you managed to get connection :)

this "non start automatically at boot" it's becoming epidemic... check some suggestions (mine and others) on [this thread]("http://ubuntuforums.org/showthread.php?p=2757887").  
Post any doubts here to not hijacking the other thread ;)

good luck.

edit: 
in case you don't know you can add a line:
```
ifup eth0
```
to the file /etc/rc.local before exit 0
to run that command every time it boots.

---

