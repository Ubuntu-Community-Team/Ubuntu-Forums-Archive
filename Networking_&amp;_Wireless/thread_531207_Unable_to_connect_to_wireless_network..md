---
title: "Unable to connect to wireless network."
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by themetalpanda on 2007-08-21
Hey guys, like title says I'm having trouble connecting to my wireless in Ubuntu. After clicking the internet connections icon in the top right corner of the screen, the dropdown menu appears and my wireless network is listed, along with my neighbor's. When I click on my network, it attempts to connect, but after about a minute it stops and when I mouseover the icon it says something along the lines of "no network connected." I tried doing the same with my wired modem I use on my other PC and I get the same problem.

I'm a complete noob to linux, so bear with me...

Thanks in advance.

---

### Post by scrooge_74 on 2007-08-21
Did you set your network cards to roaming in the network manager? That seems to do the trick on some occasions.  Also in my caseI have to right click and unable the wireless, count to five (to avoid the system to freeze) and reenable it, then it just picks my wireless and works.

It could be something about your wireless card, with mine a broadcom it does this, with my wifes (which uses centrino) no problem

---

### Post by themetalpanda on 2007-08-21
> **scrooge_74 said:**
> Did you set your network cards to roaming in the network manager? That seems to do the trick on some occasions.  Also in my caseI have to right click and unable the wireless, count to five (to avoid the system to freeze) and reenable it, then it just picks my wireless and works.

It could be something about your wireless card, with mine a broadcom it does this, with my wifes (which uses centrino) no problem
I tried disabling and re enabling but that didn't work. And it's been in roaming mode. 

I also checked if my wireless adapter is problematic with linux systems and according to [this site]("http://linux-wless.passys.nl/index.php"), it's fine.

Thank you for the reply. :)

---

### Post by scrooge_74 on 2007-08-21
what wireless card you have? some are problematic than others..

also there is a file /etc/network/interfaces

it should only list the cards you have and it should have it to read like this in my case which I on a wireless network

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

In some cases after having things to roaming, the the interfaces file like this and a reboot then it works with no more problems. I did had a lot of similar problems in the past

---

### Post by themetalpanda on 2007-08-21
> **scrooge_74 said:**
> what wireless card you have? some are problematic than others..

also there is a file /etc/network/interfaces

it should only list the cards you have and it should have it to read like this in my case which I on a wireless network

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

In some cases after having things to roaming, the the interfaces file like this and a reboot then it works with no more problems. I did had a lot of similar problems in the past
I checked my /network/interfaces file like you said, and it looked similar to what you posted. However, instead of 2 blocks of test there were around 6.

---

### Post by Einheit on 2007-08-21
Seriously, just ditch network manager and install wicd. I was tearing my hair out trying to get my laptop to connect with hardware that was clearly compatible. Wicd worked on the first try.

---

### Post by themetalpanda on 2007-08-21
> **Einheit said:**
> Seriously, just ditch network manager and install wicd. I was tearing my hair out trying to get my laptop to connect with hardware that was clearly compatible. Wicd worked on the first try.
Thanks, I'll try that and post my results.

---

### Post by themetalpanda on 2007-08-21
Okay, I downloaded wicd to my flash drive and ran upstairs to install it. When I double clicked the .deb, it told me I needed to uninstall network manager. So I did that and restarted. The network manager icon doesn't appear in the toolbar and it isn't listed in add/remove programs so I'm assuming it uninstalled correctly. But when I try to install wicd it still tells me that installing it would conflict with network manager. :confused::confused::confused:

EDIT: Sorry, double post.

---

### Post by imdano on 2007-08-21
Open a terminal and run the command ```
sudo apt-get remove network-manager network-manager-gnome
``` I think using add/remove doesn't completely remove packages in some cases.  You should use Synaptic Package Manager instead (System->Administration->Synaptic Package Manager), or the terminal/apt-get.

---

### Post by themetalpanda on 2007-08-21
> **imdano said:**
> Open a terminal and run the command ```
sudo apt-get remove network-manager network-manager-gnome
``` I think using add/remove doesn't completely remove packages in some cases.  You should use Synaptic Package Manager instead (System->Administration->Synaptic Package Manager), or the terminal/apt-get.
I have network manager removed  and Wicd successfully installed but  I'm still unable to connect to any of the networks. 

I'm going to try to connect through my hard line again.

EDIT: Wired network has the same problem.

---

### Post by themetalpanda on 2007-08-22
Still not working :( Anyone else have any ideas?

---

