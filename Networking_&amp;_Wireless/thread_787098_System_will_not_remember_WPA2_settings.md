---
title: "System will not remember WPA2 settings"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by barkerkr on 2008-05-08
Ubuntu 8.04. In Network Settings I have Wlan0 set for Static IP.


Upon reboot the Network settings shows the Password Type as WPA Personal, despite the fact that I set it for WPA2 Personal. Once I change it back it will connect to the network but it changes back to WPA on the next reboot.

I don't have tis problem if I enable roaming mode, but then its using DHCP.

Any way to get ubuntu to remember the correct settings?

---

### Post by zyoung on 2008-05-21
I am seeing s similar issue. The wireless router I connect to uses WPA, so I set up the connection to use WPA personal in the network settings (this is the only choice that I could ever get to work). I fill in the router password and it works. However, when I reboot, the connection doesn't work. If I open Network settings again, it shows way too many dots for the password. When I retype it, it will connect again. The password is text, not hex, but it looks like a hex password is being put in there (since there are a lot more dots for the password), but I really have no idea.

Thanks for your help.

---

### Post by astralbat on 2008-05-24
I'm having exactly the same issue here with "Manual Configuration". When I reboot, I don't get a connection and I have to go in to network manager and change "WPA Personal" to "WPA2 Personal" and also the password looks too long so I have to retype that. Once I've done that, I can connect again until I next reboot. However, I've also noticed that going back in to network manager at any time inbetween will see things reverted. It's not remembering my settings at all!

This has now occurred on two separate systems using the same router for me and the system I'm using now is a completely fresh install of hardy with no prior network settings. Both systems are using the Intel 3945ABG chip.

Also, I have a particularly long SSID (21 characters). I wonder if that could have anything to do with it?

The only relevant bug I can find is [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155304](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155304). But it doesn't quite fit for me - plus using DHCP works fine and I don't have a problem.

---

### Post by test4444 on 2008-05-28
system will not remember WPA2 settings
Ubuntu 8.04. In Network Settings I have Wlan0 set for Static IP

same problem here

got fixed all hardy heron bugs now, only this is not working.

still get some errors when hibernating but not that often
(do restart hardy heron then and all working fine again but WPA2 password and settings are lost; just WEP selected, and long hidden password there)

Please help us !!!

---

### Post by mmxbass on 2008-06-05
I can also confirm this EXACT SAME THING happening every day when I boot up. Very annoying. I am considering changing back to openSUSE over this issue if it continues unresolved in the next few weeks.

Ubuntu needs to stop saying things "just work" when they clearly don't in many cases.

---

### Post by mmxbass on 2008-06-05
Lets all try something along the lines of this in our /etc/network/interfaces file and forget about Ubuntu's clearly broken network manager.

```

auto ra0
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up iwconfig ra0 essid ACCESS_POINT_NAME_HERE
pre-up iwpriv ra0 set AuthMode=WPA2PSK
pre-up iwpriv ra0 set WPAPSK='WPA2_PASSWORD_HERE'
pre-up iwpriv ra0 set EncrypType=AES

```

Replace ra0 with whatever your wifi adapter actually is.

---

### Post by primowalker on 2008-06-06
I tired editing /etc/networking/interfaces as you suggested and not only didn't it work when I rebooted, but I couldn't even get it to work by manually configuring the interface in Network Manager until set /etc/networking/interfaces back to the way it originally was.

---

### Post by astralbat on 2008-06-07
I have commented on a bug report [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/221485](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/221485), but nobody seems to be taking any notice.

Very similar bug reports are [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/225599](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/225599), [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/214823](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/214823) and perhaps [https://bugs.launchpad.net/network-manager-applet/+bug/202605](https://bugs.launchpad.net/network-manager-applet/+bug/202605). There may be more password related bugs too.

My workaround hasn't involved editing /etc/network/interfaces. Instead, I've configured my router to reserve the IP for my network card's MAC address and then set up network manager in "Roaming Mode". This works pretty well for me as I don't have any problems after reboot and it automatically connects fine.

---

### Post by zyoung on 2008-06-09
I have laptop that exhibits this problem, but a desktop that doesn't. Both have hardy and use the same router. However, the laptop is upgraded from gutsy (where I first saw this issue), and the desktop is a fresh hardy install. Could there be a difference in what program is being used to manage the wifi settings? -Just a thought.

Anyway, I managed to get around this issue by allowing "roaming mode". This changed the gnome icon to display all the networks that it finds, and when I select my router, it will connect (after putting in the WPA password), and it remembers the password next time.

---

### Post by alan.shaw on 2008-06-10
Same problem Here ..
Ubuntu 8.04 does not remember WPA password
every time I reboot I have to put in the WEP key again.
BUG maybe ?

alan

---

### Post by Sxooter on 2008-07-01
I too am having this problem.

I have uninstalled Network Manager, which has never worked properly for me.
Since I need to be able to run multiple profiles based on where I'm going I use the simple manual network configuration tool under System -> Administration -> Network.

If I have the wifi interface turned OFF and go in and set the connection to WPA2 and set the password, hit OK, then click the box to bring up the wifi interface, it loses the config and won't connect.  

If I have the wifi interface box checked FIRST, then edit it and set it to WPA2 and the password, when I hit OK it works.

After that, if I open up the properties for my wifi, it will be set to WPA and have a different password.  

This is an inexcusable regression in behavior from 7.10 where this stuff just worked.

---

### Post by dardack on 2008-07-01
Same problem.  Sometimes the system reboots and works just fine (actually it's my wife's laptop and she called me 3 days at work complaining of this, but everytime I came home and rebooted it it worked fine for me, until today) and other times it doesn't.  I have manual enabled for WPA2 Personal but when it's not working and I go in and check the settings WPA Personal is being used not WPA2 and the password is too long.

---

### Post by Sxooter on 2008-07-03
OK, I installed wicd, and noticed that it didn't have separate WPA and WPA2 settings, just WPA1/2.  That got me to thinking that maybe they changed the way WPA/WPA2 work on 8.04.  So, I stopped Wicd and ran a little experiment.  In the network admin tool accessed from system->administration->network I set up my connection to use WPA, not WPA2, and entered my password.  I saved the profile for the network setup.

Now, when I select that profile, the interface comes up and work. I'm typing on the same machine right now.

So, I'm thinking that a change to combine WPA1/2 into one interface was just halfway done when ubuntu 8.04 came out.  Will experiment more, but give configuring the connection as WPA, not WPA2 a try and see if that helps

---

### Post by PeetOldBean on 2008-07-19
I'm having the same problems. Trying WPA rather than WPA2 didn't work for me. May have a go at some scripting I guess...

---

### Post by styrofoam cup on 2008-07-21
I was having the same problem where network manager forgets the setting and or key for my WPA2 network. Only if trying to use a static ip.
I installed wicd and its working great. very simple to install, and just tick a box to remember the default connection.

[http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

---

### Post by therage on 2008-08-26
Just wanted to say, I had the same problem, hardy, network manager losing WPA2 settings on reboots.  

installed wicd and it has been a success thus far.

sad that we had to work around the default install to use what should be the current standard in security.

---

### Post by bombcar on 2008-10-16
wicd fixed the problem for me. Network Manager is Notwork Manager.

---

### Post by louieb on 2008-10-16
> **zyoung said:**
> 
Anyway, I managed to get around this issue by allowing "roaming mode". This changed the gnome icon to display all the networks that it finds, and when I select my router, it will connect (after putting in the WPA password), and it remembers the password next time.

Your post is to old to have a thanks button or I would have pushed it. But that how I got it to remember my wpa password too.

---

### Post by mfm3 on 2008-10-21
> **styrofoam cup said:**
> I was having the same problem where network manager forgets the setting and or key for my WPA2 network. Only if trying to use a static ip.
I installed wicd and its working great. very simple to install, and just tick a box to remember the default connection.

[http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

Thanks. This worked for me. I had to download the deb manually and just double-click (oh-so-hard). I did need to remove network manager with synaptic before it would install.

---

### Post by Sxooter on 2009-05-20
This problem has now been fixed, but only for 8.10 and above.  See [bug #258404]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/258404").  Seems to me that it should also be applied to 8.04 since it is an LTS release, and this IS a bug.  We'll see.

---

