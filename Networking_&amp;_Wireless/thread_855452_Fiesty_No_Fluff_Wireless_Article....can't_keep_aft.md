---
title: "Fiesty No Fluff Wireless Article....can't keep after reboot"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by ericnord on 2008-07-10
Hey everyone,

I'm setting up my wireless on a fresh install and went through the excellent 'how to' [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

Everything works, but I can't get it to work after a reboot without opening terminal and typing in:
sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb

The 'how to' has the following to use for it to work after reboot:
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 

and I typed it all in as one command in terminal and got the echo back, but it didn't persist after reboot. 

Any ideas?

---

### Post by chili555 on 2008-07-10
Let's take a look at:```
cat /etc/modprobe.d/ndiswrapper
```Let's see how much of the command got properly written to file.

---

### Post by ericnord on 2008-07-11
I think I got it working now. I removed one of the rmmods since I don't have b44 and I think I deleted the closing ' with it.

---

