---
title: "network manager is not running in my ubuntu"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by squishy003 on 2010-08-29
hi,

if anyone could help me, it would be great.  I just did a dual boot on my mac book with ubuntu and mac os x.  i had previously did an installation on my windows7 and I loved it.  so my mac was next.  But for some reason, network manager is not working!  I get the message, "networkmanager is not running".  Even though wireless connection works when I switch to mac.  It doesn't even detect a connection.

I've been googling for a long time and no avail.  If anyone can please help me, it would be appreciated.  I am a new ubuntu user and I don't know how to fix it.

Again, thank you for your help. :D

---

### Post by blazemore on 2010-08-29
The easiest way to fix this problem is to open a terminal (Applications -> Accessories -> Terminal)

Type the following commands, pressing Enter after each one.
If it asks for your password, type it in and press Enter again. You won't see any kind of visual feedback when doing this.

```
service NetworkManager start
chkconfig --level 345 NetworkManager on
```

---

### Post by squishy003 on 2010-08-29
thanks for the reply.  But when i typed in 'service NetworkManager start', it says NetworkManager is an unrecognized service.

And the second command, says that chkconfig is not installed.  And after I tried to install it,  it says that chkconfig is not a candidate for installation.

is there anything else that I can do?

---

### Post by zeroseven0183 on 2010-08-29
Based on your another post, you accidentally removed network-manager.
You can reinstall it by downloading the package
[http://ubuntuforums.org/showthread.php?t=1563970](http://ubuntuforums.org/showthread.php?t=1563970)

---

### Post by dineshs on 2010-08-30
I think this is the command
sudo service network-manager start

---

### Post by Iowan on 2010-08-30
Just a hint... :)
From Code of Conduct:> Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.

---

### Post by kaqfa on 2011-03-25
Hi All. I'm a newbie and also have same problem.
I've done lots of googling and tried proposed solution, but non of them are success.

```
sudo service NetworkManager start
```

return says NetworkManager is an unrecognized service
Try to remove connman which is actually not installed. Then reinstall the network-manager and network-manager-gnome also don't work.

I wonder is it possible if the network manager is conflict with another program.
I install some programs like Oracle-XE, PostgreSQL, VirtualBox, and yeah library for 32bit.

I think network-manager is only GUI interface of network, can we connect to LAN, WLan, and Broadband modem by using shell command without using network-manager?

Thank you for helping me

---

### Post by uberphokis on 2011-06-10
Same problem with a twist, ok maybe a totally different issue but feel this is the best place to post.

Issue: When trying to run airmon-ng I get the classic message about killing processes. I stopped the avahi-daemon service then went to stop the NetworkManager as I do everytime, only this time I get 
[COLOR="DarkOrange"]ubuntu@ubuntu:~$ service networkmanager stop
networkmanager: unrecognized service[/COLOR] 

I reinstalled with
[COLOR="DarkOrange"]sudo aptitude reinstall network-manager network-manager-gnome[/COLOR]

I tried again and got the same "networkmanager: unrecongnize service" error

when I run airmon-ng  it gives me
[COLOR="DarkOrange"]ubuntu@ubuntu:~$ sudo airmon-ng start wlan0


Found 3 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID	Name
6914	NetworkManager
7107	wpa_supplicant
7121	dhclient
Process with PID 7121 (dhclient) is running on interface wlan0


Interface	Chipset		Driver

wlan0		Broadcom	b43 - [phy0]
				(monitor mode enabled on mon3)
mon0		Broadcom	b43 - [phy0]
mon1		Broadcom	b43 - [phy0]
mon2		Broadcom	b43 - [phy0]

ubuntu@ubuntu:~$ sudo service Networkmanager stop
Networkmanager: unrecognized service
[/COLOR]
I'm using my wireless connection to type this so it is working, but I can't kill it. I will try any suggestions, thanks.

---

### Post by ADani on 2011-09-17
Hi I have the same problem and I can't  connect to the Internet. I'm  on kubuntu 10.04.
When i tried reinstalling network manager from terminal using the cd it says network manager is already the newest version. "service Network kManager start" returned: unrecognized service.
mi connection icon on the system tray shows: "Network Management disabled"
I tried adding my wired connection manually in the Network Connections on the System Settings menu but nothing happens.
Any ideas?
Thanks

SOLVED FOR ME: Using "sudo dhclient eth0" got me connected again and editing NetworkingEnabled=true in /var/lib/NetworkManager/NetworkManager.state solved the "Network Management disabled" part.
[https://bugs.launchpad.net/ubuntu/+bug/555571](https://bugs.launchpad.net/ubuntu/+bug/555571)

---

