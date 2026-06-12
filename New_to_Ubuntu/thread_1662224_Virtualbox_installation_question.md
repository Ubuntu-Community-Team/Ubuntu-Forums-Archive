---
title: "Virtualbox installation question"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by taber59602 on 2011-01-07
On my new 64-bit hp pavilion dv6 I have shrunk the sda2 windows7 partition and installed kubuntu 10.04 LTS on sda5-6-7 in a dual boot configuration. I'd like to install Virtualbox, however I have no windows7 installation disk per se with this computer. I only have the recovery disks I created. 

The installation instructions I've read call for either an xp installation disk or an iso image. With what I have, can I still install Virtualbox to run an occasional windows application under kubuntu?

---

### Post by foxmulder881 on 2011-01-07
You can still install VirtualBox, yes. But to run and install ANY operating system in VB, you must have the full install disc or ISO of that particular OS.

Hope this helps.

---

### Post by James_Lochhead on 2011-01-07
You probably can't do an install directly. However, there has been talk for a while about virtualizing from an existing partition or a copy of an existing partition. I have never tried it personally.

Check out: [http://ubuntuforums.org/showthread.php?t=481523](http://ubuntuforums.org/showthread.php?t=481523)

---

### Post by wep940 on 2011-01-07
Yes, it's possible to run an existing installation as a vm, but believe me, you don't want to.  Back a few years ago I wanted to do the same thing, figuring why install something I already have?  I was advised strongly against it by some very knowledgeable people here, but went against their advise.  Everything was in the help in those days, under the vboxmanage section.  Sure, I got it to work.  But, it virtualized all the devices, so it wanted to re-register Windows.  Then I had this great idea about just booting Windows stand alone again from the same installation.  Let's just say you can't imagine the mess.  It forced a complete reinstall.
 
So my advice, which I was to niave to follow from someone else, is to don't do it.  Create a seperate installation inside a VM.

---

### Post by taber59602 on 2011-01-08
Thanks to all of you for your honest advice. It's what I was afraid I would hear, but there's always a chance you know...

Being of sound mind, I will proceed with abundant caution. Thanks again.

---

