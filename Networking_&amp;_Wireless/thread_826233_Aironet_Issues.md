---
title: "Aironet Issues"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by Aestivalis on 2008-06-11
I've been having problems with my Cisco Aironet 340 since upgrading from 7.10 to 8.04.  I've got an old Compaq Armada M700, which worked fine with Ubuntu 7.10 (but not Xubuntu for some reason).  When I upgraded to 8.04, I lost my wireless, except if I booted back to the old kernel.  So with every kernel release, it's been Russian Roulette.  Right now, it only works if I boot to 2.6.24-16, and if I boot to -17 or -18, I lose wireless.

Does anyone else have this problem, and should I be checking to see if the modules are loading correctly?  How?

---

### Post by chili555 on 2008-06-11
Please check here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398) Especially see this:> I fixed it this way, which should still work even if the kernel gets updated (I think). Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

This fixed wireless on my Cisco Aironet 350 and eliminated the hang during boot.

---

### Post by dfnkt on 2008-09-04
> **chili555 said:**
> Please check here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398) Especially see this: 
Quote:
I fixed it this way, which should still work even if the kernel gets updated (I think). Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

This fixed wireless on my Cisco Aironet 350 and eliminated the hang during boot.

This fixed 3 of my issues. #1 it fixed my wireless issue, no matter what I did FN+F5 (enable/disable wireless) i could not get it to turn the card on and iwconfig recognized no wireless interfaces. 

#2 this fixed my sound and finally #3 this fixed my hang on boot (took about 6 minutes to boot up).

Going well now, sound, wireless, and quick boots! Thanks a lot.

---

### Post by seren6ipity on 2008-11-06
:grin: worked for me too! yippie!

---

### Post by newyorkpaulie on 2009-11-20
When I boot I get a very long delay at the "padlock" line and would like to use the above fix, and incidentally get my internal wifi recognized too. I brought up the blacklist file and after adding the lines I am not able to save it. With my current OS, a test version of the new PhoenixOS, I am unable to logon as root, but I can get into the system using the console. Can this be done via this way? Any suggestions?

---

### Post by chili555 on 2009-11-20
> after adding the lines I am not able to save it.I am not familiar with PheonixOS. In Ubuntu, you would do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Substitute nano, kate or vim if you don't have gedit. Add the lines, save and close.

---

### Post by newyorkpaulie on 2009-11-20
> **dfnkt said:**
> This fixed 3 of my issues. #1 it fixed my wireless issue, no matter what I did FN+F5 (enable/disable wireless) i could not get it to turn the card on and iwconfig recognized no wireless interfaces. 

#2 this fixed my sound and finally #3 this fixed my hang on boot (took about 6 minutes to boot up).

Going well now, sound, wireless, and quick boots! Thanks a lot.This is the BEST! My bootup was amazingly fast, my wireless is up and running for the first time and my sound issue is gone. Thanks for this fabulous tip!!!!!

---

