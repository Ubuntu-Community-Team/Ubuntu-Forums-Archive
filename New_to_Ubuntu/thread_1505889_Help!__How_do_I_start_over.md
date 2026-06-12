---
title: "Help!  How do I start over?"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by sks24 on 2010-06-09
This is my first time installing 10.04, and, I gottatelya, I'm a bit upset.  How on earth was I supposed to know that I had to hit the space key (upon the keyboard and man in a circle icon at the bottom of the screen) to call up the menu which had the option to "check disc integrity"?  Now I've got a partial installation, and I can't figure out how to do a disc check!  Since I don't want to complete the installation without performing this check, please help me with either starting the installation over, or, somehow, doing a disc check from the 10.04 desktop with the "Install Ubuntu 10.04 LTS" icon on the desktop.

I mean, really: what's the point of adding this "secret handshake" step? :mad:

Thanks in advance,
Scott

---

### Post by bodhi.zazen on 2010-06-09
Ouch !!!

Hats off to you on that, most people skip testing the install media.

I would tend to agree, the new boot menu may look better and cleaner, but the help and install/boot options should be easy to find.

I suggest you file a bug report on that.

In terms of your install , can you describe your problem and perhaps we can help.

---

### Post by sks24 on 2010-06-09
Thanks bodhi.zazen, for the kind and consoling words. . . 

At boot, I get a "Windows Boot Manager" which defaults to Windows (7, on a 64 bit Presario CQ61).  If I select Ubuntu, I get "Completing the Ubuntu Installation," then the optical drive doing its thing with the 10.04 installation CD for a couple of minutes, then the standard Ubuntu desktop with the "Install Ubuntu 10.04 LTS" icon on the top LHS under "Examples."  If I click on the install icon, it launches me on the standard stepwise installation (choose language and so forth).  I'm assuming there's no disc check in the sequence.  I just . . . (sniff, sniff) I just wanna do this right, you know?  :cry:

Again, thanks,
Scott

---

### Post by maestrobwh1 on 2010-06-09
I took too long writing my response and now I have more info.  I think you can reboot with the optical disk out at this point if this is the FIRST reboot after the installation (and it looks like it completed on the previous boot).

If on the reboot with the installation disk out, you don't get ubuntu, post back!

It is still recoverable most likely even if you don't get ubuntu to launch.

---

### Post by bodhi.zazen on 2010-06-09
If I am understanding you correctly, you are attempting a wubi install ?

[http://wubi-installer.org/](http://wubi-installer.org/)

Try booting to ubuntu without the ubuntu CD in the CD drive.

If that fails, I would boot to windows and check the md5sum of the iso first, and next on the CD.

Does the software you used to burn the CD confirm the burn is OK ?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, how did you make the CD ?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by maestrobwh1 on 2010-06-09
bodhi.zazen >> I'll let you handle this:-)  You seem a bit more on top of your game than me.  Good luck.

---

### Post by sks24 on 2010-06-09
I did the MD5 on the ISO b4 I burned using InfraRecorder; the ISO checked out.  I didn't confirm the burn with InfraRecorder.  Maybe I can still do that?  I don't know how to run checksums on CDs, which is why I always run the disc integrity utility.  

If I boot w/o the install cd and select Ubuntu in the "Windows Boot Manager," I'm prompted to insert the install CD.

I haven't run through the Gparted partition manager yet, and disc management in Windows 7 indicates three NTFS partitions ("System 199mb"; "C" 134gb; "Recovery" ("D")14 gb; and 1 FAT32 partition: HP_Tools ("E") 103 MB.

I'll look into doing a checksum on this CD . . .

---

### Post by sks24 on 2010-06-09
Oh: I'm not doing a wubi installation.  I would like Ubuntu to be on a dedicated partition . . . 17GB should be OK, no?  

I, uh, think I know why I don't know how to do an MD5sum on a cd . . . looks kind of involved.  But I'm headed back over there now to dive into it?  I don't have access to another 64 bit machine, btw.

---

### Post by bodhi.zazen on 2010-06-09
> **sks24 said:**
> I did the MD5 on the ISO b4 I burned using InfraRecorder; the ISO checked out.  I didn't confirm the burn with InfraRecorder.  Maybe I can still do that?  I don't know how to run checksums on CDs, which is why I always run the disc integrity utility.  

If I boot w/o the install cd and select Ubuntu in the "Windows Boot Manager," I'm prompted to insert the install CD.

I haven't run through the Gparted partition manager yet, and disc management in Windows 7 indicates three NTFS partitions ("System 199mb"; "C" 134gb; "Recovery" ("D")14 gb; and 1 FAT32 partition: HP_Tools ("E") 103 MB.

I'll look into doing a checksum on this CD . . .

So, for the others, you are attempting a wubi install.

It appears something went wrong.

I suggest you burn a new disk and check the integrity of the burn (I hope infrarecorder will do this ...).

Then remove & re-install wubi

Even better would be a standard install, but you may not wish to partition your HD or install GRUB.

---

### Post by bodhi.zazen on 2010-06-09
> **sks24 said:**
> Oh: I'm not doing a wubi installation.  I would like Ubuntu to be on a dedicated partition . . . 17GB should be OK, no?  

I, uh, think I know why I don't know how to do an MD5sum on a cd . . . looks kind of involved.  But I'm headed back over there now to dive into it?  I don't have access to another 64 bit machine, btw.

If you are running linux on another machine,

md5sum /dev/cdrom

17 Gb is sufficient space, I use 5-10 Gb for Linux installs, with a dedicated /data/partition. Resize your ntfs partition (from within windows), leave the space as free space.

Boot Ubuntu, start gparted and make an Extended partition. You need two partitions for ubuntu, / (root) and a swap partition (well you may not *need* swap ...).

---

### Post by sks24 on 2010-06-09
Ah! You're a lifesaver, bodhi.zazen.

I'm running 9.10 on a 32 bit machine, so I'll run the checksum on the CD over here.

And thanks for the architectural advice.  Once you're up and running with the swap . . . is there a way to "automatically" insure that all of one's files get saved in the swap partition?  
Is there a tutorial somewhere on this?  I've read about this setup you propose: if I understand it correctly, it allows one to periodically reinstall the OS without losing one's files.  I like the idea, but, operationally, I've never seen it in action.

Again, thanks so much for all your help.
Scott

---

### Post by bodhi.zazen on 2010-06-09
No, swap is used as temp storage on your hard drive if you run out of RAM. I think windows calls it paging ?

You can only hav e4 primary partitions, so you need an extended partition.

See if this post explains things a bit :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

### Post by sks24 on 2010-06-09
a google search on the result ( 9f2bd1e979b833f519121ef95fabf6ad ) yielded no result.  

I only see sums for ISOs [here]("https://help.ubuntu.com/community/UbuntuHashes").  Where does one check MD5 checksums from burned CDs?

But, no Google result has always meant a bad burn for me, so I'm just going to burn another cd.

---

### Post by bodhi.zazen on 2010-06-09
> **sks24 said:**
> a google search on the result ( 9f2bd1e979b833f519121ef95fabf6ad ) yielded no result.  

I only see sums for ISOs [here]("https://help.ubuntu.com/community/UbuntuHashes").  Where does one check MD5 checksums from burned CDs?

But, no Google result has always meant a bad burn for me, so I'm just going to burn another cd.

The md5sum from the CD should == the iso

If it is different = bad burn

/me looks at the md5checksum page - looks like you have yourself a bad burn =)

---

### Post by sks24 on 2010-06-09
Well, for being Mister Cautious, good for me, huh?

Thanks so much for all your help.

---

