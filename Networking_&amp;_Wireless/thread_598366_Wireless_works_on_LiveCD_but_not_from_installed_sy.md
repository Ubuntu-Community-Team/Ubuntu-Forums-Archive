---
title: "Wireless works on LiveCD but not from installed system"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by Meej on 2007-10-31
Hi all,

I'm using Kubuntu Gutsy to breath life into an old PC and I'm having issues with my wireless internet (surprise surprise)
I use a Belkin USB 54g adapter (F5D7050B - think it's got a Ralink RT2500 chipset but I'm not sure).
This works fine out of the box when using the LiveCD which I was delighted with because this is the first time I haven't had to mess about with ndiswrapper to get wireless to work.
BUT... once I've installed the system on my hard drive and rebooted, the wireless has disappeared. It can't detect any networks and it's shown as being disabled (and refuses to enable) in the network settings.
The USB devices list in KInfoCenter show it as being detected so it's plugged in alright I'm just getting no response from it (and the activity light is always out).

I'm confused! How come it works one minute and not the next?! The only thing I can think of is that when installing, some update was downloaded that messed it up (because it worked during the installation).

This is the specs of the PC it's running on:
Athlon XP 1900+
ECS K7S5A Pro motherboard
768MB PC2100
30GB hdd
GeForce 4 MX440 8x 64MB

---

### Post by GozzoMan on 2007-10-31
Hi,
   I had the same problem with Tribe 5 and a very similar one with the final release, using your same Belkin USB dongle.

I have frankly no idea where the point is (I may just suppose it's some sort of bug), but, if you had the network connected before installing, I *might* have a workaround (it worked for me):

- boot the live cd, and be sure NOT to connect to the wifi network
- install (just at the end of installation, it would lament that it can't reach the repositories, that's fine)
- reboot
- connect the wifi! This time it should work!
- open synaptic (well, its Kubuntu equivalent... is Adept the name?), you will find all repositories has been disabled, enable them all.


Hope this works for you too, good luck!


PS: Despite the WiFi is now working, I'm still experiencing the problem I described in this thread: [http://ubuntuforums.org/showthread.php?t=596326](http://ubuntuforums.org/showthread.php?t=596326)

---

### Post by Meej on 2007-11-01
Thankyou for the reply! It works now! I'm using it now!

But now I'm afraid that it will go again if I download and updates. Do you think there's a way to find out which update it was that caused this so I can avoid it?

Thanks again!

---

### Post by GozzoMan on 2007-11-01
> **Meej said:**
> Thankyou for the reply! It works now! I'm using it now!


Nice! You're very welcome ;)

> 
But now I'm afraid that it will go again if I download and updates. Do you think there's a way to find out which update it was that caused this so I can avoid it?

I'm sorry I really have no idea. I've briefly tried to trace the problem to a specific package, but with no luck... :( Anyhow, I have regularly updated my system until now, and it's still working (albeit with the aforementioned problem at boot; could you please have a look to [http://ubuntuforums.org/showthread.php?t=596326](http://ubuntuforums.org/showthread.php?t=596326) and check if you have the same situation also in that regard? I'm trying to understand if the two things are related, thank you)

---

