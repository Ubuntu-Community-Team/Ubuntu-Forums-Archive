---
title: "Windows 7"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by brandoncolorado on 2009-03-30
Hi,

I have seen a few other threads, but I haven't seen one posted since beta came out.  I have Windows 7 installed on my new PC and i would like to dual  boot Ubuntu.  Can I just install Ubuntu without harming my Windows 7 install?

Thanks

---

### Post by dmaxel on 2009-03-30
I'm not sure, as I've heard of people having booting problems. However, it may or may not apply here.

---

### Post by damis648 on 2009-03-30
Sure. Just partition and install like you would if any other windows version was installed.:popcorn:

---

### Post by aeiah on 2009-03-30
id imagine that it would be the same as it is with vista. your only danger is wiping the master boot record with grub and grub not being able to boot windows 7. it'd be easy to repair with the windows 7 dvd if this happened id have thought.

perhaps have a look here: [http://ubuntuforums.org/showthread.php?t=1036632](http://ubuntuforums.org/showthread.php?t=1036632)

and at all the other windows 7 related threads

---

### Post by jakupl on 2009-03-30
> **brandoncolorado said:**
> Hi,

I have seen a few other threads, but I haven't seen one posted since beta came out.  I have Windows 7 installed on my new PC and i would like to dual  boot Ubuntu.  Can I just install Ubuntu without harming my Windows 7 install?

Thanks

Well if you have the recovery cd for windows 7, then it would not hurt to try.. ? I'm not windows savvy, so I don't really know.
If you can resize the windows partition without making windows too angry, it should not be a problem.

---

### Post by wsonar on 2009-03-30
Is windows 7 shipping with new pc's now? I thought it was still beta

---

### Post by dmaxel on 2009-03-30
> **wsonar said:**
> Is windows 7 shipping with new pc's now? I thought it was still beta
I believe it still is in beta, although they are preparing for Release Candidates...

---

### Post by tad1073 on 2009-03-30
I f you have more than 4 partitions already, you will need to create a logical partition.

---

### Post by brandoncolorado on 2009-03-30
> **wsonar said:**
> Is windows 7 shipping with new pc's now? I thought it was still beta

Built my PC and installed Windows 7 because it was free (need windows for games and blackberry).

Thanks for the responses guys!  I'll give it a go and let everyone know what happened.

---

### Post by linlux on 2009-04-12
It was a bit aggravating but I was able to dual boot Intrepid and Win7. I installed Windows first, and then Ubuntu. After that, Windows wouldn't load because it didn't like the MBR...I forgot the exact error. So I had to restore Windows from CD (it was quick though). Then GRUB started giving me Error 17. Then I had to restore GRUB by booting from the Ubuntu CD and referring to the threads here. After that, GRUB recognized the Win7 partition as 'Windows Vista/Longhorn' and both OS's lived happily ever after.

---

### Post by ubudog on 2009-04-12
> **damis648 said:**
> Sure. Just partition and install like you would if any other windows version was installed.:popcorn:

Yeah that's what I'd do.

---

### Post by JoshuaRL on 2009-04-12
> **linlux said:**
> It was a bit aggravating but I was able to dual boot Intrepid and Win7. I installed Windows first, and then Ubuntu. After that, Windows wouldn't load because it didn't like the MBR...I forgot the exact error. So I had to restore Windows from CD (it was quick though). Then GRUB started giving me Error 17. Then I had to restore GRUB by booting from the Ubuntu CD and referring to the threads here. After that, GRUB recognized the Win7 partition as 'Windows Vista/Longhorn' and both OS's lived happily ever after.

I didn't have a problem.  I created a partition and formatted in NTFS with Parted Magic first, then installed Windows 7 there.  After that, I installed Ubuntu alongside and haven't had any issues whatsoever.  I even changed some partitions and reinstalled with Ubuntu server.  GRUB and Windows 7 were still fine.  I'd say at this stage, give it a go and just keep the usual Windows dual-boot precautions and you should have a good chance.

---

