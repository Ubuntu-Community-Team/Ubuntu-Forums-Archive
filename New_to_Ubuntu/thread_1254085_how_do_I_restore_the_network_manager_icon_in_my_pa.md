---
title: "how do I restore the network manager icon in my panel bar (without internet)?"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by ChubbySauce on 2009-08-30
I found this question on the forums but I couldnt reply to it for some reason.
 
 
anywho this much I know I need to redownload network-manager-gnome and network-manager.
 
but I only have wifi is there a way I can connecct to a wireless network without the network manager so I can redownload it?
 
also I dont have an ethernet cord to put into my laptop :c

---

### Post by tgeer43 on 2009-08-30
The first thing that I would try is to mark them for reinstallation in Synaptic Package Manager. There may be an archived copy of them in /var/cache/apt/archives in which case they won't have to be re-downloaded.

tgeer

---

### Post by lswb on 2009-08-30
First, did you actually uninstall Network Manager and nm-applet, or is it possible you just deleted the notification area from the panel? If the notification area is missing, right-click on the panel, select "add to panel" and the select Notifcation Area from the dialog list. You may need to log out and back in to the desktop to see any changes.

If you actually did uninstall NM, for most typical wireless nets you can connect by opening a terminal and issuing these commands. Supposing your wireless interface is eth1, essid of you network is mynetwork, and you are using a wep or wpa key of abcd1234 (if using an ascii string for a key, enter the key as s:my-ascii-string)

sudo ifconfig eth1 up
sudo iwconfig eth1 essid "mynetwork" key abcd1234 
sudo dhclient eth1

---

### Post by lswb on 2009-08-31
Forgot to mention, you can also reinstall from the live cd by opening synaptic, from menu select Settings/Repositories/ubuntu software, and check the box for the cd rom. Insert the cd, close the dialog, click reload, and install Network Manager and nm-applet.

---

### Post by ChubbySauce on 2009-09-01
you have just confirmed my suspicions about you.........................YOU ARE AWESOME!

thanks that worked :3 the first one that is

---

### Post by thelastquincy on 2010-11-29
Jesus H Christ. Thank you so much man. This was KILLING me. I had too many icons on the top bar and my dumbass decided to remove that one, and it ****ed up my wireless to no end and it was notification area. Who would have thought. Thanks a bunch man.

---

