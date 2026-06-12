---
title: "Connecting two feisty conputers"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by aquavitae on 2007-05-20
I've got two computers with fairly new installs of feisty, but can't get an ethernet connection between them.  I've seen a few guides on the internet but they all start a stage beyond where I get stuck - I can't get the ip addresses sorted out.  I can't ping either computer from the other.  I also don't seem to be able to change the ip address using the system settings manager - when it restarts the network it changes the ip address back to what it was before.  If I try to change it using ifconfig I get this message

SIOCSIFADDR: Invalid argument
SIOCSIFBRDADDR: Cannot assign requested address
SIOCSIFNETMASK: Cannot assign requested address

Is there a quick, simple way to get a connection between the two computers?

---

### Post by Undertwotimes on 2007-05-20
Do you have the two computers connected to a hub or switch?  If not then you will need a crossover cable if you want to connect the two computers with just one cable.

Then just do a manual configuration, and give the two computers a non-routable ip, i.e. 10.x.x.x.  Make sure they are both on the same subnet, and you should have no problems, but I haven't tried this in a while.

---

### Post by merlinus on 2007-05-20
I am using a wired router, ssh and static IP addresses.  If you go to System/Administration/Network and click on your wired connection and then Properties, you can set up a static IP address.

This works perfectly for me, with no Internet access problems using DHCP.

One machine uses 192.168.100 and the other 192.168.101, with subnet mask of 255.255.255.0 and gateway address of 192.168.1.1.

hth....

-merlin

---

### Post by aquavitae on 2007-05-21
My computers are not connected using a router, its simply an ethernet cable connecting the two.  The kind of thing that in windows is plug-and-(probably restart-and-)play.  I personally can't stand windows, but I do think that its peer-to-peer networking is the one area that is much easier for people who don't have much knowledge of networking.

I spent about 3hrs messing around trying to set it up using the system settings gui provided with ubuntu, but I eventually gave up and dug out some out gentoo documentation I used when I was still running gentoo.  Then I had it set up in about 3 min.

For anyone who's interested, here's the gentoo wiki I used obviously making adjustments for ubuntu): [http://gentoo-wiki.com/HOWTO_Share_Directories_via_NFS]("http://gentoo-wiki.com/HOWTO_Share_Directories_via_NFS")

By the way, I strongly recommend the gentoo documentation for anyone using linux - I've found that they cover how to set up almost anything from scratch and are also very good for anyone who just wants to know a bit more about how linux works.

---

