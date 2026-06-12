---
title: "Upgrading to 9.10, clean install, save home folder."
date: 2009-10-14
forum: New to Ubuntu
---

### Post by servicetech on 2009-10-14
Currently have 9.04, want to upgrade to 9.10 when it comes out. It there an easy way to keep my home folder contents and install 9.10 on a different partition? I'm assuming I would need to create another partition to install 9.10 on (can I even do this w/o reformatting?).

---

### Post by bodhi.zazen on 2009-10-14
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by laidback on 2009-10-14
When I upgraded from 8.10 to 9.04 I stored a copy of ~/home/myname onto an external HD, did a fresh install of 9.04 and then copied what I wanted from the 8.10 ~/home/myname back again, overwriting the newly installed version. I then reinstalled any extra software via synaptic.

You can create ~/home/myname in a separate partition so that it doesn't get overwritten when you upgrade, I've never done this but it does seem logically to be the best route.

You can also simply upgrade from 8.10 to 9.04 and then to 9.10 via the provided upgrade software. Do a backup first though. I have yet to try this route.

---

### Post by donato roque on 2009-10-14
The general outline of what you are about to do is:
  1. Backup your /home/username folder.
  2. Create a new partition/s.  
  3. Install Ubuntu 9.10 on / directory and copy the /home/username folder back to its separate partition.
  4. Download additional software not included in the default package.

I strongly suggest you create a separate partition for your home directory.  This way the next upgrade you only have to replace system files.  For size I suggest allocating at least 5-6 GB depending on how much additional software you need.  For the swap partition a good rule is: swap file size=ram.  A regular desktop don't need that much.

After your installation, its always good to read on basic security stuff for[ Ubuntu here.]("http://ubuntuforums.org/showthread.php?t=510812")

The Ext4 file system is available for Karmic.  I am recommending it. I've been using ext4 since my upgrade to Jaunty and my experience has been positive all the way.  Since your making modifications in your hard drive and backing up, I think now is as good a time as any.

---

