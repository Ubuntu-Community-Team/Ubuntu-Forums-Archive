---
title: "WPA for Ubuntu"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by marcos.placona on 2006-12-07
Hi I'm a newbie in the *.nix life and just installed Ubuntu Kernel Version **2.6.15-27-386**.

I've installed it on my notebook dual-booting with XP pro and I can only see WEP encryption when configuring wireless.

For XP, I have configured with WPA-PSK and wlan works flawlessly.

How do I WPA-PSK encryption to work with Ubuntu ? I'm using  intel centrino

Doing some tests I noticed that if I change my router's configuration to WEP, the wireless connection works stright away, but stops working on Windows.

I was reading on the help about how to configure WPA, but did get much success on the instalations.

Is it possible for someone here to describe how to do it step by step? I'm sure it shouldn't be too difficult, but it just doesn't work. I've got wpa_supplicant installed already, but still couldn't get anywhere.

Thanks a lot,

Marcos Placona

---

### Post by FrodoB on 2006-12-07
Have you looked at this?

[http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

---

### Post by jml on 2006-12-07
I feel your pain.  It took me quite some time to get WPA working in Ubuntu.  Ubuntu does not support WPA out of the box, only WEP.  What you have to do is download and install two applications.  network-manager, and network-manager-gnome.  That will add WPA support to Ubuntu.

---

### Post by victorbrca on 2006-12-07
I'm a fresh big time noob as well.

  I tried installing network-manager and network-manager-gnome and for some reason my network-manager-gnome would not start or show

  I was able to install WPA using the link that "FrodoB" provided thou.

  Take a look at the link below. It may clear some stuff for you.

[http://www.lowfatlinux.com/](http://www.lowfatlinux.com/)


Vic.

---

### Post by FrodoB on 2006-12-07
Now I guess I will have to do it if the link worked for you. :)

---

### Post by lcohen999 on 2006-12-07
> **jml said:**
> I feel your pain.  It took me quite some time to get WPA working in Ubuntu.  Ubuntu does not support WPA out of the box, only WEP.  What you have to do is download and install two applications.  network-manager, and network-manager-gnome.  That will add WPA support to Ubuntu.

Speaking of which.

I have both network-manager and network-manager-gnome, but when I execute it, nothing happens...any thoughs?

---

### Post by victorbrca on 2006-12-08
> **lcohen999 said:**
> Speaking of which.

I have both network-manager and network-manager-gnome, but when I execute it, nothing happens...any thoughs?


Good question... Is this screen only available for 6.10???

_[http://www.debianadmin.com/images/wpa/2.png](http://www.debianadmin.com/images/wpa/2.png)_ 



Vic.

---

### Post by marcos.placona on 2006-12-08
> **FrodoB said:**
> Have you looked at this?

[http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

Amazing, I used the newest one (from the same) which is in [http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136) and it worked straight away. I spent hours last night trying that and with this tutorial it only took me 10 min.

Thank you very much, you guys are such a :KS

---

### Post by lcohen999 on 2006-12-08
> **marcos.placona said:**
> Amazing, I used the newest one (from the same) which is in [http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136) and it worked straight away. I spent hours last night trying that and with this tutorial it only took me 10 min.

Thank you very much, you guys are such a :KS


I figured out my question...

I got wpa_supplicant to work...finally

there are no gui wpa_supplicant additions where I an manage multiple networks, are there?

---

