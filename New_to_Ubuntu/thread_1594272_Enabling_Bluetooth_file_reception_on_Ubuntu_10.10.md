---
title: "Enabling Bluetooth file reception on Ubuntu 10.10"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by onizuka45 on 2010-10-12
Can anyone tell me how to enable bluetooth file reception on Ubuntu 10.10 since I cannot send a file to my comp. using bluetooth even though I make my comp. visible to other devices in Bluetooth Preferences. Tq.

---

### Post by theopulus on 2010-10-13
Same for me... it tells me I need the bluetooth sharing prefs but I can't find them...

---

### Post by Nightstrike2009 on 2010-10-13
Hope this helps,

Have you left-clicked on the bluetooth icon on top bar and selected "set up new device" and followed the wizard to pair your device first?

I just set to "visible" then and have no issues sending from to my phone/pc or pc/phone.

Hope thats all thats wrong :-)

---

### Post by theopulus on 2010-10-13
Yeah, have them paired, and I've managed to send files to the phone, but not to the PC... as I said, it seems it lacks of needed software (at least I cannot find it on *Accesories*)

---

### Post by Nightstrike2009 on 2010-10-13
I had this issue on a previous ubuntu, try accessing your pc's shared folder with your phone, rather than pc to phone transfer, that may work as a workaround.

Think it maybe down a bug in network-manager, or minor incompatibility with your hardware.

PS: Just re-read your post, I don't suffer that issue, don't know how to deal with that maybe use a different bluetooth manager think there one called "blueman" 

PPS: I am an Ubuntu 10.04TLTS user and don't have that problem, was just trying to help out, sorry I couldn't resolve it.

---

### Post by theopulus on 2010-10-13
> **Nightstrike2009 said:**
> I had this issue on a previous ubuntu, try accessing your pc's shared folder with your phone, rather than pc to phone transfer, that may work as a workaround.

Think it maybe down a bug in network-manager, or minor incompatibility with your hardware.

PS: Just re-read your post, I don't suffer that issue, don't know how to deal with that maybe use a different bluetooth manager think there one called "blueman" 

PPS: I am an Ubuntu 10.04TLTS user and don't have that problem, was just trying to help out, sorry I couldn't resolve it.

Ok, don't worry... Maybe a complete reinstallation do the job, but I'm a bit lazy about that ;-)

---

### Post by shadowpt on 2010-10-13
Bluetooth can't even find my cell phone :(

---

### Post by Melclic on 2010-10-14
This solved it for me. Go to Synaptic Package Manager, search and select to install for :

Apache2.2.bin
lib-apache2-mod-dnssd
gnome-user-share

I guess that there are some missing packages. 
You can then go and select from the preferences of the bluetooth icon "receive files"

(I also installed bluetooth manager, but I don't think that that was the problem)

Hope that helps

---

### Post by budi_indira on 2010-10-16
> **Melclic said:**
> This solved it for me. Go to Synaptic Package Manager, search and select to install for :

Apache2.2.bin
lib-apache2-mod-dnssd
gnome-user-share

I guess that there are some missing packages. 
You can then go and select from the preferences of the bluetooth icon "receive files"

(I also installed bluetooth manager, but I don't think that that was the problem)

Hope that helps

thx man :D
It works !

---

### Post by jimmyxu on 2010-10-18
:guitar:> **Melclic said:**
> This solved it for me. Go to Synaptic Package Manager, search and select to install for :

Apache2.2.bin
lib-apache2-mod-dnssd
gnome-user-share

I guess that there are some missing packages. 
You can then go and select from the preferences of the bluetooth icon "receive files"

(I also installed bluetooth manager, but I don't think that that was the problem)

Hope that helps


my 10.10 after install this packages it works.

Apache2.2.bin
gnome-user-share

thanks a lot.

---

### Post by anlag on 2010-10-26
Thanks Melclic, that worked great for me as well! Only needed two of the packages though:

> **Melclic said:**
> 
[B]Apache2.2.bin
[/B]lib-apache2-mod-dnssd
**gnome-user-share**

In fact the third one, lib-apache2-mod-dnssd, is not available in my (rather extensive) repositories. Since it wasn't needed though, who cares eh? :)

---

### Post by byronbgs on 2011-01-16
FYI: I had the same problem and I just installed gnome-user-share and went to System......"Personal File Sharing". Check off the appropriate boxes for Bluetooth to receive files.  :)

P.S. Apache2.2.bin is not installed on my system but I just found out it is required to share files over a network so I installed it.

---

### Post by myscam on 2011-01-22
Quote:
Originally Posted by Melclic View Post
This solved it for me. Go to Synaptic Package Manager, search and select to install for :

Apache2.2.bin
lib-apache2-mod-dnssd
gnome-user-share

I guess that there are some missing packages.
You can then go and select from the preferences of the bluetooth icon "receive files"

(I also installed bluetooth manager, but I don't think that that was the problem)

Hope that helps

my 10.10 after install this packages it works.

Apache2.2.bin
gnome-user-share

thanks a lot.

This worked for me too using a USB Bluetooth Dongle on 10.10.  Thanks for the help.  Please note : I had to do a restart after installing the packages, then only the bluetooth icon lit up in the system tray.

I love Ubuntu.  Respects and appreciation are due to Mr Mark Shuttleworth.

---

