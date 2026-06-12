---
title: "Issues with internet on Hp laptop."
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by Krisverde on 2008-07-25
Alright so I just got the dual booting to work on my hp ze5470 laptop. Now I am having trouble getting the internet to work...I did have it working wired but now nothing is happening. I do have an integrated wireless card on the laptop and it is a broadcom 4306 card. I have tried searching how to get it working, but the articles I did come across have not helped. Sorry if this has been posted before. If someone could help me out, thanks!

---

### Post by Ayuthia on 2008-07-26
You can try starting with this:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
Option 2 has information on what you need to download to your computer if you don't have an internet connection.

If that doesn't work for you, you can try the NDISwrapper route:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Kevbert on 2008-07-28
Please see this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13").  I have a BCM4306 and this is how I got it working on Hardy and Intrepid.

---

### Post by Krisverde on 2008-07-28
Sweet guys, so I have started with the first link and I believe I messed up, I didn't read far enough and ended up clicking yes on the fetch/firmware,ima try and plug an ethernet in again and see if it works. If not what can I do? Oh and what can i do to get the networking to not be on manual config?

EDIT: Alright I got the hardwired connection working, so now onto getting this thing fixed.

EDIT2: So I got wireless working, then I rebooted my computer and now it will bring me into the login screen, I enter all the info to log in then it brings
this up first
[[IMG]http://img225.imageshack.us/img225/3142/hpim0505ti6.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img225.imageshack.us/img225/3142/hpim0505ti6.ecf243cdcc.jpg[/IMG]](http://g.imageshack.us/g.php?h=225&i=hpim0505ti6.jpg)then this pops up after waiting for a couple of minutes
[[IMG]http://img225.imageshack.us/img225/6836/hpim0507vg9.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img225.imageshack.us/img225/6836/hpim0507vg9.c6f78bd6a0.jpg[/IMG]](http://g.imageshack.us/g.php?h=225&i=hpim0507vg9.jpg)

But even after that everything works fine still so far.

---

### Post by Ayuthia on 2008-07-28
Well, that is a new one for me!  I don't think that this is related to the wireless setup unless something that you do with your themes or background that requires something from the internet/network.

Is there anything that is listed in dmesg that looks like an error?  If you are not sure, you can attach the dmesg results to your next post.

---

### Post by xnostradamusx on 2008-07-28
if you cant fix that just do a fresh install and do the first guides they already posted, i experienced that when i uninstalled my evolution program
it seems it grabbed also some important files which makes the linux work normal

maybe you uninstalled something critical

---

### Post by Krisverde on 2008-07-28
Yea I am not sure, I don't believe I saw anything that looks like an error but ill post up an attachment here so you can help me out if you would like.I know this error happened some time when I install ndiswrapper or something. Infact here is a link to the results. It is a .odt file  [http://rapidshare.com/files/133187562/Results.odt.html](http://rapidshare.com/files/133187562/Results.odt.html)

---

### Post by xnostradamusx on 2008-07-29
next tym it would be more easier if you use [www.imageshack.us](www.imageshack.us) to post your screenshots,

anyway i cant download your link rapidshare always say my ip is downloading something and cant download,

---

### Post by Ayuthia on 2008-07-29
> **Krisverde said:**
> Yea I am not sure, I don't believe I saw anything that looks like an error but ill post up an attachment here so you can help me out if you would like.I know this error happened some time when I install ndiswrapper or something. Infact here is a link to the results. It is a .odt file  [http://rapidshare.com/files/133187562/Results.odt.html](http://rapidshare.com/files/133187562/Results.odt.html)
It looks like you have a conflict with ndiswrapper and b43legacy.  Since they are both valid modules, they did not produce an error message.  We can try and see if we can use b43legacy first:
```
sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper
sudo depmod -ae
sudo modprobe b43legacy
sudo modprobe b44
sudo ifconfig wlan0 up
sudo ifconfig eth0 up
sudo iwlist scan
```
What this will do is remove all the modules that could be used for Broadcom.  Then we will load the b43legacy and b44 drivers.  I have added the b44 because I am not for sure what your wired card really is.  It shouldn't hurt anything though.

This will only work for this session.  Please let us know if you are able to see any wireless devices and if you can, see if you can connect.

---

### Post by Krisverde on 2008-07-29
Alright so after doing that I had no wireless connection, that last scan I did at the end showed my router being around, but when I looked through the manual network settings I no longer can find wireless connections. While I was typing in some of that stuff I kept getting that 
WARNING:/etc/modprobe.d/blacklist  ignoring bad line starting with 'mkd  and cle.

---

### Post by Ayuthia on 2008-07-29
> **Krisverde said:**
> Alright so after doing that I had no wireless connection, that last scan I did at the end showed my router being around, but when I looked through the manual network settings I no longer can find wireless connections. While I was typing in some of that stuff I kept getting that 
WARNING:/etc/modprobe.d/blacklist  ignoring bad line starting with 'mkd  and cle.
If the sudo iwlist scan does show your router and you don't have encryption set, please try:
```
sudo dhclient -r
sudo iwconfig wlan0 essid router-name
sudo dhclient wlan0
```

As for the WARNING message, that means that the file has some commands in there that it does not like.  It doesn't hurt anything right now, but it should be cleaned up.  You can go into the file and edit it by:
```
gksu gedit /etc/modprobe.d/blacklist
```
The file should only contain things that either start with # or blacklist.  If you are uncomfortable with removing lines in there, just have the beginning of the line have # as the first character.  That will comment out the line.

---

### Post by Krisverde on 2008-07-29
Well I don't think it finds it now, I got the error for wireless request "Set ESSID" So I am kinda lost now  Almost tempted to do a fresh install.

---

### Post by Krisverde on 2008-08-03
Bump any other suggestions on how to get rid of that error that pops up on startup? After about 5min? it's normal and everything. I imagine I will go through the first links again to get the wireless working.

---

### Post by Ayuthia on 2008-08-04
> **Krisverde said:**
> Bump any other suggestions on how to get rid of that error that pops up on startup? After about 5min? it's normal and everything. I imagine I will go through the first links again to get the wireless working.

Can you check /etc/network/interfaces and make sure that lo is configured:
```

auto lo
iface lo inet loopback

```
If you need to edit the file:
```

gksu gedit /etc/network/interfaces
```

That is what one of the bug reports in Launchpad said to try:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/227858](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/227858)

---

### Post by Krisverde on 2008-08-21
W00t! I got everything working good, and wireless is working great also. Thanks for all the help guys:biggrin:

---

