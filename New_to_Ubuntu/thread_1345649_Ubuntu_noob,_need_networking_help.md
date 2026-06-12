---
title: "Ubuntu noob, need networking help"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by fitties on 2009-12-04
Ubuntu 9.10, Fresh install, no problems

the problem is that my wireless home network is on there but its greyed out.  I am able to connect to others that the aircard is picking up, but they are not mine.  any help would be greatly appreciated.  :)

History:

I have the Cisco Aironet 350 aircard on my hp/compaq nc6000.  i had some network issues before where i wasnt able to see any networks at all.  after some research i found that if i blacklisted some "modules?" it would fix the problem.  It seems to have corrected that problem as i am now able to view available networks.

---

### Post by fitties on 2009-12-04
*bump*

---

### Post by bkratz on 2009-12-04
> **fitties said:**
> Ubuntu 9.10, Fresh install, no problems

the problem is that my wireless home network is on there but its greyed out.  I am able to connect to others that the aircard is picking up, but they are not mine.  any help would be greatly appreciated.  :)

History:

I have the Cisco Aironet 350 aircard on my hp/compaq nc6000.  i had some network issues before where i wasnt able to see any networks at all.  after some research i found that if i blacklisted some "modules?" it would fix the problem.  It seems to have corrected that problem as i am now able to view available networks.




Maybe this one would be of some help

[http://ubuntuforums.org/showthread.php?t=917267&highlight=Aironet+350](http://ubuntuforums.org/showthread.php?t=917267&highlight=Aironet+350)


Good Luck

---

### Post by fitties on 2009-12-04
haha, thats funny.  thats the documentation i found that helped me with the ubuntu recognizing my aircard.

thats all fixed and i see wireless networks so i know its seeing my aircard.  i can see and connect to my neighbors wireless...shhhhh...but mine is greyed out.

im connected to it with my windows laptop so i know that everything is working, just ubuntu has it greyed out for some reason.

---

### Post by fitties on 2009-12-04
*bump*

---

### Post by fitties on 2009-12-06
Your help is greatly appreciated.  Any ideas?

---

### Post by Iowan on 2009-12-06
Is your wireless open or protected? (I presume your neighbor's is open).

---

### Post by The Cog on 2009-12-07
I have an advent 4211 which is a Wind clone. I find that Fn-F11 cycles through 4 states: Bluetooth, Wifi, both, neither. It does this in Ubuntu (9.04 and 9.10) and even in the Grub boot menu, although strangely not in the select boot device menu if you hit F11 right at the start.

So if yours doesn't do this even in the grub menu, I do wonder if there is a problem with your machine.

---

### Post by rustybronco on 2009-12-07
what kind of encryption does your network use?

IIRC the Cisco Aironet 350, is at the moment, only capable of wep encryption.

I have both the NC6000 and Aironet 350. maybe I'll give it a go later on tonight.

---

### Post by fitties on 2009-12-12
My home network is on WPA2 Personal...

Is there any way around on the wpa2 security?

---

### Post by fitties on 2009-12-14
*bump*

---

### Post by rustybronco on 2009-12-15
[http://www.cisco.com/en/US/tech/tk722/tk809/technologies_configuration_example09186a008054339e.shtml](http://www.cisco.com/en/US/tech/tk722/tk809/technologies_configuration_example09186a008054339e.shtml)
> Note: Cisco Aironet 350 series products do not support WPA 2 because their radios lack AES support.

looks like you might be able to use LEAP-TKIP?
[http://ubuntuforums.org/showpost.php?p=1176169&postcount=1](http://ubuntuforums.org/showpost.php?p=1176169&postcount=1)

or, I can see if I have a spare internal wireless card that works with wpa2 if you would like (no charge)...

***note*** is your internal wireless card missing, or just not working properly?

---

