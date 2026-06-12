---
title: "Solution for Intel 3945a/b/g wireless internet card not working in gutsy"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by ryan1519 on 2007-10-22
If you're having trouble using this card on your laptop after upgrading to gutsy then you're definetly going to want to use the "generic" kernel when you boot up, this should solve the driver issues with this card. (Also got my sound card working!) Just thought I'd share my solution since a lot of ppl seem to be having issues with this card. As far as I know there are no disadvantages to using the generic kernel but I could be wrong. This seems to be the simplest solution, plz post here if you have found this solution works for you to keep the thread bumped.

---

### Post by RyanGT on 2007-10-23
I can confirm that this works for me as well.  When I boot into the 386 kernel, the ipw3945 restricted module is listed as enabled but not in use.  When I boot into the generic kernel (after installing the generic restricted modules), the driver is Intel(R) PRO/Wireless 3945 Network Connection driver for Linux.  It is enabled and in use.  I am sending this reply using that driver.

This is a simple solution, but slightly unsatisfying.  Aren't there performance advantages of a non-generic kernel, such as the 386?

Ryan

---

### Post by natehall on 2007-12-30
> **RyanGT said:**
> 

This is a simple solution, but slightly unsatisfying.  Aren't there performance advantages of a non-generic kernel, such as the 386?

RyanTry this link
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

---

### Post by RyanGT on 2007-12-31
That link (linux.dell.com thread) caused me to loose all connectivity.

---

### Post by natehall on 2007-12-31
> **RyanGT said:**
> That link (linux.dell.com thread) caused me to loose all connectivity.
Sorry about that. You have to have the iwl3945 module already loaded . sudo modprobe iwl2945 should work.

---

### Post by natehall on 2007-12-31
> **natehall said:**
> Sorry about that. You have to have the iwl3945 module already loaded . sudo modprobe iwl2945 should work.
should be sudo modprobe iwl3945 . typo error

---

### Post by RyanGT on 2007-12-31
I appreciate your help.  modprobe iwl3945 doesn't show anything.  What is the easiest way to get it?  I search the forums and haven't stumble on a simple answer.

Thanks,

Ryan

---

### Post by RyanGT on 2007-12-31
I guess maybe it comes with gutsy by default according to this thread:
[http://ubuntuforums.org/showthread.php?t=636177&highlight=iwl3945+install](http://ubuntuforums.org/showthread.php?t=636177&highlight=iwl3945+install)

When I run these commands:

sudo modprobe -r ipw3945
sudo modprobe -r ieee80211
sudo modprobe -r ieee80211_crypt
sudo modprobe iwlwifi_mac80211
sudo modprobe iwl3945

lsmod | egrep 'iwl'

show iwl3945, iwlwifi_mac80211m and cfg80211

So, I guess I have it.  

This may actually work in my generic kernel.  But the iwl driver doesn't turn on my little wifi light, which was a good indicator of when things were not working with ipw.

When I try this same approach when booting into the 386 kernel, I get messages that iwl3945 and iwlwifi_mac80211 are not found.  How do I fix that?

Thanks,

Ryan

---

### Post by RyanGT on 2007-12-31
sudo apt-get install linux-ubuntu-modules-2.6.22-14-386 
fixes my problem with modules not being installed in my 386 kernel.

I have added ipw3945 to /etc/modprobe.d/blacklist

and added iwlwifif_mac80211 and iwl3945 to /etc/modules

and everything seems to be working in the 386 kernel (except my little wifi light).

Thanks,

Ryan

---

### Post by RyanGT on 2007-12-31
Actually, sudo apt-get install linux-ubuntu-modules-2.6.22-14-386  also seems to have fixed my problems with the ipw3945 driver and the 386 kernel, so that I can use either module.

Ryan

---

### Post by natehall on 2008-01-01
> **RyanGT said:**
> Actually, sudo apt-get install linux-ubuntu-modules-2.6.22-14-386  also seems to have fixed my problems with the ipw3945 driver and the 386 kernel, so that I can use either module.

Ryan
Glad I could at least steer you the right way.

---

