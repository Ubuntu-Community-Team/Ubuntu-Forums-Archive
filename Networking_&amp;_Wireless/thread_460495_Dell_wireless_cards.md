---
title: "Dell wireless cards"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by cbranha1 on 2007-05-31
I have a Dell Wireless 1390 WLAN Mini-PCI card manufactured by Broadcom. I just can't seem to get the card to work or find any linux drivers for it out there. My wired connect works fine. Maybe someone here will be able to help me.

If a driver is found, how do I go about installing it here? I'm pretty new to the command line stuff, although I have a few basics down.

Thanks!
cbranha1

---

### Post by cbranha1 on 2007-05-31
BUMP

Come on, can't anyone help me here?

---

### Post by macron1 on 2007-06-01
i think you just need to do a bit of searching in the forum for this partiular problem. have you tried ndiswrapper or   bcm43xx-fwcutter? check these tutorials out: [http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")
[http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174")

---

### Post by macron1 on 2007-06-01
o and since you say you are new to this command line stuff id reccommend the bcm43xx-fwcutter before the other one as its a bit more straight forward

---

### Post by bradrover on 2007-06-02
this did not work at all on my D620. I've only been using ubuntu one day but this is something I can not figure out.

---

### Post by macron1 on 2007-06-03
what diddnt work? you would need to try one or the other id imagine, ive read elsewhere on these forums here that the ndiswrapper especially can become unusable if its not absolutely implemented as per the tutorial. just keep trying, it often doesnt work the first time either. Persevere man!

---

### Post by AndrewB on 2007-06-03
How 'bout more info??

Which Ubuntu version are you running?

---

### Post by eiskalt on 2007-06-03
The search box in the upper right is super new ultra fantastic tool, you should learn to use.  While i'm here, I have a dell e1705 with the dell wireless card running edgy.  Follow this tutorial exactly.

[http://ubuntuforums.org/showthread.php?t=297092&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=297092&highlight=ndiswrapper)

---

### Post by uman2008 on 2007-06-03
> **cbranha1 said:**
> I have a Dell Wireless 1390 WLAN Mini-PCI card manufactured by Broadcom. I just can't seem to get the card to work or find any linux drivers for it out there. My wired connect works fine. Maybe someone here will be able to help me.

If a driver is found, how do I go about installing it here? I'm pretty new to the command line stuff, although I have a few basics down.

Thanks!
cbranha1

Try this method: [http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated](http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated)

---

### Post by eightdollarbeer on 2007-06-20
apt-get install bcm43xx-fwcutter will work fr you.then use knetwork manager or whatever program for flavor.

---

