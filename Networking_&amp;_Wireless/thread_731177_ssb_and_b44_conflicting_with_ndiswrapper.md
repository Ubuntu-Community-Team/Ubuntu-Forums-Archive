---
title: "ssb and b44 conflicting with ndiswrapper"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by kevin_j_morse on 2008-03-21
Hi I'm having some problems getting ndiswrapper to properly load at startup.

I'm pretty new to the whole linux thing but I know exactly how to reproduce the problem so hopefully you guys can help me out.

Basically at boot ndiswrapper will load (I think) but it won't work correctly because the ssb module is interfering with how it loads. Because of this I can't even see any wireless networks when the computer first starts up until I do the following.

```
sudo modprobe -r b44
sudo modprobe -r ssb (can't be shut down until b44 is shut down)
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44 (or ssb if I only care about enabling wireless)
```

When I do a ndiswrapper -l it displayes the following:
```
bcmwl5 : driver installed
device (14E4:4328) present (alternate driver: ssb)
```

Originally I thought that the ssb driver was preventing the ndiswrapper from working however I have confirmed now that after I shut them all down no networking will work until I start restart ssb.

The reason I start up the b44 module is because it is responsible for wired networking and also happens to use the ssb module. The wireless will still work if I only start up ssb but I won't be able to use wired networking until b44 gets restarted.

Now after I've run those 5 commands everything works great. It automatically connects to my home WPA network and if I plug in an ethernet cable it will drop the wireless and switch back to wired connection. If the wired is unplugged it will go back to wireless. Basically it works flawlessly... However I would like to have this work right away without having to run any commands so any help would be appreciated.

---

### Post by kevin_j_morse on 2008-03-23
No one has any help at all... I figured Ubuntu would be a good distro to try because  I heard the community was very user friendly and helpful:confused:

---

### Post by kevdog on 2008-03-23
echo 'blacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist

---

### Post by kevin_j_morse on 2008-03-24
No that didn't work. ssb gets loaded anyways when b44 gets started so maybe I could blacklist them both but then I would need to reload them because I need sbb in order for the wireless to be able to connect to a network.

---

### Post by tayroni on 2008-04-23
I make ndiswrapper works with a broadcom wireless board with a following procedure on a clean install of hardy

First, install the packages ndisgtk and ndiswrapper-utils-1.9

Second, install driver from broadcom using

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

you should see a message that says driver present, hardware detected

Third, blacklist free drivers. Add these lines on /etc/modprobe.d/blacklist

blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist b44

THE RELEVANT PART: Install aliases on /etc/modprobe.d

sudo ndiswrapper -ma

AGAIN, It's "-ma", NOT "-m". Finally add ndiswrapper to /etc/modules and reboot

Please, test and if success, post here!

---

### Post by jeffktay on 2008-05-04
This link solved my problem:
[http://gf4e.wordpress.com/2008/04/28/ndiswrapper-and-ssb-conflict/](http://gf4e.wordpress.com/2008/04/28/ndiswrapper-and-ssb-conflict/)

Seems that ssb gets loaded by the kernel even if you put it on the blacklist.

Editing etc/rc.local to add the following lines worked for me:
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb

(to edit rclocal type gksudo gedit /etc/rc.local in a terminal window)

---

