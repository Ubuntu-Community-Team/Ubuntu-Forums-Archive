---
title: "Bluetooth support in Edgy"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by jestersmurf on 2007-01-03
Hey all!

Ive been juggling around the bluetooth functions in Edgy for a cupple of days now, and just thought i would share my findings in one post!

My goals:

**Bluetooth connection to my Samsung mobile phone**
[LIST]
[*]Send and receive files directly from nautilus
[*]Manage contacts from evolution
[*]Syncronize my calender with evolution by using Multisync
[/LIST]

**Bluetooth connection to my Logitech headset**
[LIST]
[*]Use headset with Skype
[/LIST]

Now! I'm not a super admin in terms of linux. I use it only on my home network and desktop/laptop, and mostly do this for fun... But i've been Microsoft free for about 2 years now, and haven't worked in anything else then the Ubuntu/Debian envirement.

This is not gonna be a pureblood howto, just a sum up off my results in the bluetooth world :)  Still I'm gonna post some links for other good posts, and some quick fixes for some common problems when working with bluetooth...


My progress as of today (03JAN07)
**Bluetooth connection to my Samsung mobile phone :mrgreen: **
[LIST]
[*]Send and receive files directly from nautilus :mrgreen: 
[*]Manage contacts from evolution
[*]Synchronize my calender with evolution by using Multisync
[/LIST]

**Bluetooth connection to my Logitech headset**
[LIST]
[*]Use headset with Skype
[/LIST]

**So this is how I did it:**

_**Bluetooth connection to my Samsung mobile phone**_
I'm working with some noname USB bluetooth dongle, but Edgy found if off the box, so now problems here...

To get it all up and running I started by installing some bluetooth packages, heres a list that should get you up and running:
[LIST]
[*]bluetooth (wich should install a lot of other stuff)
[*]gnome-bluetooth
[*]bluez-utils
[*]nautilus-sendto
[*]obex-server
[*]phone-manager
[/LIST]

After having done this you should actually be able to recieve files from you phone off the box... All you have to do is launch a program called gnome-obex-server. You can either launch it from a terminal or by using the shortcut that should be created in your gnome-menu called "bluetooth filesharing" or something like that depending on your lingo...
Once this deamon is running you should be able to receive files from you phone! I found some of it in this thread:

[http://www.ubuntuforums.org/showthread.php?t=94713&highlight=gnome-bluetooth]("http://www.ubuntuforums.org/showthread.php?t=94713&highlight=gnome-bluetooth")

Now to be able to actually use the "sento" function in nautilus, we have to change the way Edgy handles your bluetooth pin codes... This is actually quite easy done!

[INDENT]1. As root open the file "/etc/bluetooth/hcid.conf"[/INDENT]
[INDENT]2. Change the security manager mode to auto[/INDENT]
[INDENT]3. At the bottom of the "HCId options" section insert the following:[/INDENT]
```
# PIN helper
pin_helper /usr/bin/bluepin;
```
[INDENT]4. Save and close the file[/INDENT]
[INDENT]5. Restart the bluetooth services with the following command[/INDENT]
```
sudo /etc/init.d/bluetooth restart
```
Theres a copy of my "hcid.conf" attached to the post...

Now you should be able to pare your phone with your computer! You can change the pin in the "hcid.conf" file to what ever you'd like...

I'll keep updating this post when I learn more! And I will! I seem to recall actually being able to browse my phone when running dapper, so I hope to able to do this again...

As this is my first real post in this forum please give me some comments...

Jester

---

### Post by elektronaut on 2007-01-06
I'm a bit puzzled that Bluetooth works so fine for you with Edgy. I didn't have any problems with bt on my old laptop running Breezy, but now the devices don't find each other. It's probably [this bug](https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718), there are also workarounds, presumably calling 'sudo hciconfig hci0 inqmode 0', as described in the bug comments, but this doesn't work for me all the time.

---

### Post by zerohalo on 2007-01-08
Thanks! Looking forward to hearing how you got your bluetooth headset to work.

---

### Post by thirstycat on 2007-01-15
> **jestersmurf said:**
> 

[INDENT]1. As root open the file "/etc/bluetooth/hcid.conf"[/INDENT]
[INDENT]2. Change the security manager mode to auto[/INDENT]
[INDENT]3. At the bottom of the "HCId options" section insert the following:[/INDENT]
```
# PIN helper
pin_helper /usr/bin/bluepin;
```


I'm a bit confused about the /usr/bin/bluepin part... I've installed all the same software as you (on Edgy; 64-bit- does that make a difference?), but have no "bluepin" file in /usr/bin or anywhere else.  I have /usr/bin/bluez-pin, but that's it.
What package provides this "bluepin" thing?

---

### Post by jestersmurf on 2007-01-15
Actually Ive just done a clean installation of Edgy on my new laptop! And I cant seem to find the file either.. But it seems to work fine with bluez-pin as well...

---

