---
title: "Wireless networks don't show up in gui"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by DeadlyMuffin on 2007-03-22
Hey folks, just upgraded from dapper to eft, and everything seems to work except for wireless. I'm using a Dell B130 laptop and the wireless card worked in the past using ndiswrapper.

Here's the problem: I can see networks using "iwlist scan" but in the gui, there are never any in the drop down menu. I'm usually a command line type person, but getting wireless working right from the command line always seemed like masochism. So wireless works, but the gui doesn't.

Any clue what I need to change to make the network gui work again?

Thank you much,

DM

---

### Post by dbott67 on 2007-03-22
Try installing network-manager-gnome:
```
sudo apt-get install network-manager-gnome
```

After installation, restart you computer.  A "Network Manager" icon should appear along the top that you can click on to configure:

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

Details are here:

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

-Dave

---

### Post by DeadlyMuffin on 2007-03-22
Found a bug report on it. 

[https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/59159](https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/59159)

<rant>
Apparently it's not important enough to fix in edgy. I guess having functional network managment by default is an every other release type thing. In the mean time, I'll give the other package a shot.
</rant>

Tried it, doesn't seem to like xfce, opens a whole bunch of instances. Wifi-radar works alright though, so I guess I'll stick with that. Thanks for the help.

---

### Post by woodrow4821 on 2007-03-25
Muffin!  

Thanks for pointing in toward the bug report.  I found my fix for network-manager there.    
When I went into /etc/network/interfaces and removed the references to my network name and the key.  Then I added the line "auto eth1" back in above the "iface eth1 inet dhcp" that was still there.

I found this solution proposed by manual (at 2006-10-17 14:11:48 UTC) from 
[https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/59159](https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/59159)

Thanks again!

---

