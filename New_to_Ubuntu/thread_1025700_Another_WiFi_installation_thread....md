---
title: "Another WiFi installation thread..."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by RAZRBAKK on 2008-12-30
Alright, I cant seem to figure out how to get my WiFi working. I've installed ndisgtk but I do not know what driver I need.

I am using an Atheros AR5007 802.11b/g WiFi Adapter.

Can anyone help? I have never used linux before...

---

### Post by anewguy on 2008-12-30
Follow this thread:

[http://blog.linuxoss.com/2008/05/ubuntu-804-enabling-atheros-ar5007-based-wireless/]("http://blog.linuxoss.com/2008/05/ubuntu-804-enabling-atheros-ar5007-based-wireless/")


If that doesn't work, then put ubuntu atheros ar5007 driver in a yahoo search and check the posts.

Dave :)

---

### Post by swamytk on 2008-12-30
What is your ubuntu version? The following link shows how to set right your WiFi adapter in Ubuntu 8.04. It may be applicable for 8.10 also. 

[http://ubuntuforums.org/showthread.php?t=789824](http://ubuntuforums.org/showthread.php?t=789824)

Cheers!

---

### Post by balloooza on 2008-12-30
this is an alternate way to install it, it should work in 8.10. it uses the latest madwifi drivers, witch are the linux drivers, I have had troubles in the past with ndiswrapper, spesificly with standby and hibernate. but the kernal drivers work allot beter

you might be ablr to get around this long guide by simply installing
```
sudo apt-get install linux-restricted-modules-generic
```
and then run
```
sudo modprobe -r ndiswrapper
```
then
```
sudo modprobe ath_pci
```
then reboot, but that is a guess, if you dont have the patience to try the script, definatly finish with what the others are suggesting. Hang in there, because there is a solution.

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

### Post by balloooza on 2008-12-30
Sory, i didn't read the last thread before my post, it looks like the method that anewguy submitted is the same thing. looks like it works :)

---

### Post by RAZRBAKK on 2008-12-30
None of these seem to work.

All for this reason: I do not have the option of System--->Administration--->Networking

As well as I do not have the option of disabling Atheros Hardware Access Layer (Hal)

I assume this is why, but I am  unsure...

---

### Post by lkraemer on 2008-12-30
Have a look at this thread.  It solved my problem on my
Compaq CQ50-139NR with Atheros Wifi card.

http://ubuntuforums.org/showthread.php?t=792158

lkraemer

---

