---
title: "Retrieving data from formatted drives"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Shadows_In_The_Dark on 2009-10-15
Hello Everyone!

I have recently installed Ubuntu 9.04 and am completely new to Linux.
When I backed up my data from my OS drive I forgot to backup a folder containing rather important .txt files. I know that there are various ways of retrieving data from formatted drives under windows. I have been browsing the web for quite some time now in the hope to find a program that is able to do this on a Linux OS. However, I've had no luck so far.
I wondered if anyone here can recommend a program I can use and possibly explain how to use it. 

Any help is much appreciated.

Shadow

---

### Post by philinux on 2009-10-15
Do not use the drive. Use the livecd and from synaptic install testdisk.

Then use photorec to try to recover your data.

From the livecd then use a terminal to cd to partition where you can recover the data to. Do not use a partition that contains the data. Then use the command photorec.

---

### Post by lkraemer on 2009-10-15
Here is my suggestion.  Grab your camera, and take several pictures.
Then delete each photo.  Plug in your card reader, and then insert your
memory.  Use Synaptic Package Manager to install testdisk.  This will
also install Photorec.

Open a Terminal window and run photorec.  Try to recover your Photos....
This will allow you to TRY out the software BEFORE you start messing
with your hard drive.  You will need a Partition to write the data to,
and that DOES NOT mean the Partition that you are trying to recover.

I think you'll figure it out easy enough with a little playing.  It has
been a while since I played with it, but it didn't take but about two
tries and I knew what to do.


LK

---

### Post by aysiu on 2009-10-15
If you need (for Photorec) a step-by-step tutorial with screenshots, here is one:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

---

