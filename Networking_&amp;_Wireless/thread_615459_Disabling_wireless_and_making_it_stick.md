---
title: "Disabling wireless and making it stick"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by reghuram on 2007-11-17
Hi,

I just strated running Gutsy and am now facing the this problem. I did not have this problem with 7.04. And previous versions of Ubuntu.

I'm trying to disable my wireless from activating upon reboot. I disabled wireless networking on the main Gnome UI by right clicking on the wireless icon and unchecking enable wireless. But when I reboot the s****d thing comes back on again. 

I uncheck the "enable wireless setting" again and try to use the wired connection it keeps giving me the "failed to find server" message. It seems to try to use the wireless settings and if its disabled just gives up on networking.

Also how do I disable the wireless networking rather that putting it on "roaming mode". Permanently. Do I have to add "sudo ifconfig eth* down" in a boot up script some where so that Gutsy stops trying to enable my wireless on boot up. The problem is in my country its illegal to wirelessly hook onto someone elses network without their permission. And right now it seems that Gutsy is trying to log onto any open wireless network it can find.

I can't give snap shots of what is happening as I'm using a Windows machine which currently can connect to the internet and does not pose a legal problem for me.
:(

---

### Post by 5-HT on 2007-11-17
Do you have a need for networkmanager at all then if you don't want wireless? Easiest way would be to simply remove nm-applet from your session or remove networkmanager entirely. Apart from that you can always blacklist/delete your wireless module.
cheers

---

### Post by kevdog on 2007-11-17
According to the wiki: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

You can do this:
Disabling NetworkManager

According to [WWW] this bug here's how to disable Network Manager without uninstalling it:

Stop network manager

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Create two files with only the word 'exit' in them. These files are:

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

---

### Post by reghuram on 2007-11-18
Thanks guys will try it out.

But what happens when I do want to use wireless? 

Previously in Drapper I could uncheck enable wireless and the system would be that way even after reboot. Why was it suddenly changed to be always on and you had to keep unchecking it.

---

