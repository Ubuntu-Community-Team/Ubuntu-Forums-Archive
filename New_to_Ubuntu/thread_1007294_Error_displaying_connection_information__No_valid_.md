---
title: "Error displaying connection information:  No valid active connections found!"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Najmudin on 2008-12-10
Hi
Yesterday I tried to use "xnetcardconfig" to setup my wired network yesterday, today when i turned on my computer i found the icon of network manager showing x like no connection , right click on the icon and select "connection information" an error message appeared saying:
Error displaying connection information:

No valid active connections found!
Right click on the icon again and select "Edit connections"
i found my connection "eth0" gone , nothing was there , the add button is activated.

Now i have no problem in my network, i tried browsing the net through Firefox and its OK ,torrent is working also, but i just want to fix the network manager problem to work like before.

I tried to reinstall the packages : network-manager-gnome and network-manager, then restart the system but without success.

Any help will be appreciated.

---

### Post by Titan8990 on 2008-12-10
Did you try specifying purge with the uninstall?


sudo apt-get remove --purge network-manager-gnome

---

### Post by Najmudin on 2008-12-10
> **Titan8990 said:**
> Did you try specifying purge with the uninstall?


sudo apt-get remove --purge network-manager-gnome

Thanks for your reply

That didn't work, i tried to remove it with that command and restarted the computer then install the package and restart again but didn't work.

---

### Post by Najmudin on 2008-12-10
I googled the error and found [[COLOR="RoyalBlue"]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/305606") , but it seems they didn't mention any solution for it.

---

### Post by Titan8990 on 2008-12-10
I suggest submitting your experience to that bug report. As a work-around you could try using the KDE network manager (even in gnome).

---

### Post by twistedneck on 2008-12-22
> **Titan8990 said:**
> I suggest submitting your experience to that bug report. As a work-around you could try using the KDE network manager (even in gnome).

I have the same problem after installing 8.10.  i got really mad reading that bug report - the arrogant problem solver person explained how it was some how 'supposed' to have that error. yea right.

---

### Post by Anubisxian on 2009-01-11
I had this same problem after I played around with my networking settings to get apt-cacher running (which I promptly scrapped).

I checked back on the other thread [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/305606"), and I followed the instructions below, rebooted, and I'm good now.

> If like me you *want* your connection to be managed by the network manager, you probably want to update your /etc/NetworkManager/nm-system-settings.conf with something like this :

[QUOTE][main]
plugins=keyfile

[ifupdown]
managed=true

You should of course save your former nm-system-settings.conf in case something goes wrong.[/QUOTE]

My [ifupdown] had been set to managed=false, since I tried to hardcode my IP rather than allow my router's DCHP to handle it. Props to Aurélien Couderc for this.

---

### Post by susenj on 2009-05-24
i also managed to fix this bug by using [this]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/305606")!
thanks:D:D

---

### Post by Steve H on 2009-06-23
> **Anubisxian said:**
> 
Quote:
[main]
plugins=keyfile

[ifupdown]
managed=true 

That has worked a treat and has saved me a right headache at work.

:D

---

### Post by progone on 2011-12-17
I believe in 11.10 this file is /etc/NetworkManager/NetworkManager.conf

---

### Post by wacheson on 2012-02-23
> **progone said:**
> I believe in 11.10 this file is /etc/NetworkManager/NetworkManager.conf

This thread was very helpful, thanks :). Im using a static IP. I dont know that if that makes a difference or not.
I had this same problem, but oddly enough, I could still remote into the box, I was just unable to get regular internet getting out of the box. So, I did the following:
sudo apt-get remove --purge network-manager-gnome
sudo apt-get install network-manager-gnome
{Didn't work}
sudo nano /etc/hosts
{adding the following line so I can reinstall:
91.189.92.177  us.archive.ubuntu.com
}
sudo /etc/init.d/networking restart
sudo apt-get install network-manager-gnome
sudo nano /etc/NetworkManager/NetworkManager.conf
{changed: 
manged=true
}

sudo /etc/init.d/networking restart
sudo reboot now

{and back to working}

---

