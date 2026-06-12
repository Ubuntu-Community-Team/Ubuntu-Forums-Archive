---
title: "Cannot connect to WPA2 wifi network"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2008-06-27
I have been trying to research if the problem I am having is based on any known issue, but have not found anything so far, hence I am posting this here.

Our institute has a WPA2 encrypted wifi network which I can connect to without problems from OSX Leopard. But when I switch to Ubuntu on the same machine (a macbook) I cannot connect to the WPA2 network. Network manager tries to connect and then gives up.

The network admin said it should work.

Has anyone experienced something similar? Does network manager not like WPA2? Is there a special way to connect to WPA2 networks in Ubuntu?

Thanks in advance.

---

### Post by jay019 on 2008-06-27
Install WICD. Makes WPA2 connection simple.

---

### Post by PartisanEntity on 2008-06-27
Thanks for the tip, does WICD remove network manager ?

---

### Post by jay019 on 2008-06-27
No, network manager is still on my laptop, it just never gets used now.
I havent bothered trying to remove it as I'm not sure what depends on it.

WICD also handles wired networks which is cool, no more using multiple apps for similar tasks.

Also found a cool tip on the wicd site ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) that I wasnt aware of. It has a handy tray app.
I am using the version from the Ubuntu repos, but you can add the wicd repo and get the latest version.

> 
In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".


---

### Post by ninjapenguin on 2008-06-27
> **PartisanEntity said:**
> Thanks for the tip, does WICD remove network manager ?

When I installed WICD it forced me to remove network manager . . .

---

### Post by PartisanEntity on 2008-06-27
> **ninjapenguin said:**
> When I installed WICD it forced me to remove network manager . . .

My brother reported the same thing happening, which is why I am a little reluctant to install WICD. Any other experiences ?

---

### Post by ninjapenguin on 2008-06-27
> **PartisanEntity said:**
> My brother reported the same thing happening, which is why I am a little reluctant to install WICD. Any other experiences ?

Also, I tried using WICD to get my encrypted wifi on my iMac to work, and so far no luck, but this weekend I am going to try to use multiple drivers.

---

### Post by jay019 on 2008-06-27
> **PartisanEntity said:**
> My brother reported the same thing happening, which is why I am a little reluctant to install WICD. Any other experiences ?

Would it really matter? With WICD you dont need network manager. It can be set up to automatically connect to a network so roaming is seamless and requires no intervention once you make WICD aware of the details of the networks the first time. But hey its up to you. There are ways to use network manager to connect to WPA2 but they are mostly convoluted workarounds for an app that is so far behind its not worth having.

---

### Post by jay019 on 2008-06-27
> **ninjapenguin said:**
> When I installed WICD it forced me to remove network manager . . .

Just had a look and yeah, Network Manager is no longer installed. But seriously, if NM cant manage WPA2 then whats the point of having it installed? What's so special about it?

---

### Post by PartisanEntity on 2008-06-29
Well what I am interested to know at this point, is whether NM is the reason I cannot connect to WPA2? Is this a known issue with NM, or does it have something to do with the wifi network setup at the institute?

As I said, I tried researching whether NM has issues with WPA2, but have not found anything yet.

---

### Post by jay019 on 2008-06-30
> **PartisanEntity said:**
> Well what I am interested to know at this point, is whether NM is the reason I cannot connect to WPA2? Is this a known issue with NM, or does it have something to do with the wifi network setup at the institute?

As I said, I tried researching whether NM has issues with WPA2, but have not found anything yet.

I guess its not so much that it has issues with it as much as it is not easy to use. With wicd you plug in the details and hit connect. You are online quicker than firefox can load up. With network manager from what i remeber you had to edit config files and roaming was a nightmare. Maybe things have changed? I am still using 7.04 but most people I know with ubuntu swear by wicd for being so easy to use.

As for nm, here are some links that may or may not help...
[http://ubuntuforums.org/archive/index.php/t-442897.html](http://ubuntuforums.org/archive/index.php/t-442897.html)
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Let us know how you get on.

---

### Post by PartisanEntity on 2008-06-30
Things have definately changed from when you used NM last, it too is just a matter of entering data in to the window.

---

