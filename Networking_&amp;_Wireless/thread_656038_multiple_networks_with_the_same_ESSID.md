---
title: "multiple networks with the same ESSID"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by glopv2 on 2008-01-02
I seem to have two wireless networks in the area with the same ESSID: both are called "NETGEAR". However, one of them is encrypted and one is not. nm-applet shows only one "NETGEAR" and shows it as encrypted. On another laptop sitting right next to mine, "NETGEAR" shows up as unencrypted. I did "iwlist" and there are two entries called "NETGEAR", one with key=on and one with key=off. How can I connect to the unencrypted network? I tried "sudo iwconfig ap <cut&pasted address 03:303:40:ab: whatever here>" When I typed that, there was no output, but still I was not connected.

What can I do to convince the computer to connect to the unencrypted network? I hate the fact that windows is doing this automatically but linux is not...

Please advise!

Thanks

---

### Post by ubutufan on 2008-01-02
Try the following excellent guide posted by Kevdog

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by glopv2 on 2008-01-02
Well I followed the guide exactly, but I am still not getting a "lease" from "dhclient ath0".

It worked earlier in the day for a few minutes, but now it refuses to work again. 

I am following the instructions on the link for "unencrypted wireless". I am typing this on the windows computer sitting right next to mine which somehow is able to avoid the passworded one and connect to the unencrypted one (with the same ESSID). is there anything else I can do?

I tried "sudo iwconfig ath0 ap 00:14:aC:103:whatver" to get it to focus on the "NETGEAR" that I want, but that seemed to have no affect.

Thanks in advance!

---

### Post by ubutufan on 2008-01-03
Good you had it working even temporarily.
Now try the following in /etc/network/interfaces file

auto lo
iface lo inet loopback

make sure only these two lines are present. If not comment everything else out. Save and reboot

---

### Post by glopv2 on 2008-01-03
Sorry, but do you think you could explain a bit what that does? I'm trying to learn/understand what I'm doing so I can improve on linux.
This is what my /etc/network/interfaces file looks like:
```

auto lo
iface lo inet loopback


#iface eth0 inet dhcp
#
#auto eth1
#iface eth1 inet dhcp
#
#auto eth2
#iface eth2 inet dhcp
#
#auto wlan0
#iface wlan0 inet dhcp
#
#
#auto eth0

```

What were those other lines doing?



btw,
I find that now, when I boot up, nm-applet always finds the wireless with the password, and I click "cancel". Then, when I type,
```

$ sudo iwconfig ath0 essid NETGEAR
$ sudo dhclient ath0

```
the computer connects successfully to the unencrypted wireless (also called "NETGEAR).

---

### Post by ubutufan on 2008-01-04
Hi glopv2
If I understand correctly you now have your system working with wireless.

Now some hints on the /etc/network/interfaces file. When installing ubuntu, this file only contains the first two lines. It has no reference on connection attempts to any wired/wireless network by any user. Once you installed ubuntu, then an attempt to connect to a network, will be logged in this file. And this is where problems start. The recorded logs will interfere with connection attempts to other networks and you can't really connect to any other network than those recorded in the interfaces file.
I have come across many users dealing with same situation. That is why, I "virginize" the file by using the first two lines. All the rest that are now commented out are not read by the system.
I hope that helps

I have had a number of malfunctions (in one of my systems), whilst using the Network Manager. I replaced it with Wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) and it works flawlessly. This piece of soft will allow you to connect to all sorts of networks (wired/wireless) using any kind of encryption (WEP, WPA, WPA2). If you decide to install it, NOTE THAT IT WILL AUTOMATICALLY UNINSTALL the Network Manager and take over.

---

