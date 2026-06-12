---
title: "How do I convert back to Windows?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by bootDisk on 2008-12-22
After a couple of days of Ubuntu, I decided that it isn't right for me. I then tried to boot back to Windows XP, but it doesn't even give me an option. I popped in my Windows XP Pro disk and rebooted my laptop, pressed F10 and chose to boot from CD-ROM/DISK or whatever it was. It restarted and went back onto Ubuntu. I have no idea on what I did wrong. I just want my XP back.
:lolflag: <<sorry I like this smiley.
I am no computer pro so I didn't understand all this mumbo jumbo I just looked up. Can someone guide me step by step to getting XP back up and running? And no, I don't want to have Windows in Ubuntu at the same time.

---

### Post by Dj Melik on 2008-12-22
Pop up in your Ubuntu disk; delete your partition, reset up a NTFS partition + format it. Then stick your Windows disk and install it.

Sad to see you go :(. What didn't you like about Ubuntu?

---

### Post by Duck2006 on 2008-12-22
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by Ender41 on 2008-12-22
> **bootDisk said:**
> After a couple of days of Ubuntu, I decided that it isn't right for me. I then tried to boot back to Windows XP, but it doesn't even give me an option. I popped in my Windows XP Pro disk and rebooted my laptop, pressed F10 and chose to boot from CD-ROM/DISK or whatever it was. It restarted and went back onto Ubuntu. I have no idea on what I did wrong. I just want my XP back.
:lolflag: <<sorry I like this smiley.
I am no computer pro so I didn't understand all this mumbo jumbo I just looked up. Can someone guide me step by step to getting XP back up and running? And no, I don't want to have Windows in Ubuntu at the same time.

  First thing to do is to make sure booting from cd is enabled in the bios. Clean the xp cd it might be dirty/scratched. If that doesn't work then without a lot more information as to how you install ubuntu etc there isn't much more I can tell you.

Ender

---

### Post by bootDisk on 2008-12-22
I didn't like the procedures I had to go through in certain programs where as in Windows all I had to do is double click or drag and drop.

---

### Post by Cope57 on 2008-12-22
> **bootDisk said:**
> I didn't like the procedures I had to go through in certain programs where as in Windows all I had to do is double click or drag and drop.

So easy... A caveman can do it.

---

### Post by Duck2006 on 2008-12-22
> **Cope57 said:**
> So easy... A caveman can do it.

He may not have geico.

---

### Post by bootDisk on 2008-12-22
> **Cope57 said:**
> So easy... A caveman can do it.

Haha, hey just to let you guys know, I love the Ubuntu community and I have a feeling that I'll get it back up once I get a couple of things done with Windows.

Oh so i was looking through the tutorial and i was looking in my System -> Administration and I couldn't find GNOME Partition Editor, is there a way where I can get it in there?

---

### Post by Duck2006 on 2008-12-22
> **bootDisk said:**
> Haha, hey just to let you guys know, I love the Ubuntu community and I have a feeling that I'll get it back up once I get a couple of things done with Windows.

Some people install ubuntu and find that it's not for them, but a little way down the road they come back and give it a go again. see you when you come back.

---

### Post by kansasnoob on 2008-12-22
> **bootDisk said:**
> After a couple of days of Ubuntu, I decided that it isn't right for me. I then tried to boot back to Windows XP, but it doesn't even give me an option. I popped in my Windows XP Pro disk and rebooted my laptop, pressed F10 and chose to boot from CD-ROM/DISK or whatever it was. It restarted and went back onto Ubuntu. I have no idea on what I did wrong. I just want my XP back.
:lolflag: <<sorry I like this smiley.
I am no computer pro so I didn't understand all this mumbo jumbo I just looked up. Can someone guide me step by step to getting XP back up and running? And no, I don't want to have Windows in Ubuntu at the same time.

Well since you installed Ubuntu, which requires BIOS booting from CD first, my best guesss is that Win just doesn't like what it sees!

So, since you want to completely reinstall Win, first boot the Ubuntu disc you used to install Ubuntu. Choose to "Try Ubuntu without any change to your computer" and then go to System > Administration > Partition Editor. If any "locks" are displayed you may need to click on the SWAP partition and choose "swapoff'.

Then delete all partitions and choose apply. Wait until it's done. Reboot, remove the Ubuntu disc and replace it with your Windows disc. then install Windows.

---

### Post by ercferret18 on 2008-12-22
> **Duck2006 said:**
> Some people install ubuntu and find that it's not for them, but a little way down the road they come back and give it a go again. see you when you come back.

yeah, this is pretty much exactly what happened to me...

---

### Post by Locke_99GS on 2008-12-22
> **bootDisk said:**
> Haha, hey just to let you guys know, I love the Ubuntu community and I have a feeling that I'll get it back up once I get a couple of things done with Windows.

Oh so i was looking through the tutorial and i was looking in my System -> Administration and I couldn't find GNOME Partition Editor, is there a way where I can get it in there?

It is installed on the Ubuntu LiveCD, or you can get gparted from the repo's.

```

sudo apt-get update
sudo apt-get install gparted

```

It won't work on mounted partitions - it is easier to just use it from the LiveCD.

---

### Post by bootDisk on 2008-12-22
I can't find the Partition Editor in my Administration folder guys.

Ok, nevermind thanks Locke!

---

### Post by kansasnoob on 2008-12-22
> **Duck2006 said:**
> Some people install ubuntu and find that it's not for them, but a little way down the road they come back and give it a go again. see you when you come back.

Which is why I still dual boot .............. erm actually multi-boot:

>  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sda2            2678        9729    56645190    5  Extended
/dev/sda5            2678        5035    18940603+  83  Linux
/dev/sda6            5036        5169     1076323+  82  Linux swap / Solaris
/dev/sda7            5170        5934     6144831   83  Linux
/dev/sda8            5935        7434    12048718+  83  Linux
/dev/sda9            7435        8199     6144831   83  Linux
/dev/sda10           8200        9729    12289693+  83  Linux


---

### Post by kansasnoob on 2008-12-22
> **bootDisk said:**
> I can't find the Partition Editor in my Administration folder guys.

Ok, nevermind thanks Locke!

From the Live CD!

---

### Post by kansasnoob on 2008-12-22
As I said here:

> So, since you want to completely reinstall Win, first boot the Ubuntu disc you used to install Ubuntu. Choose to "Try Ubuntu without any change to your computer" and then go to System > Administration > Partition Editor. If any "locks" are displayed you may need to click on the SWAP partition and choose "swapoff'.

Then delete all partitions and choose apply. Wait until it's done. Reboot, remove the Ubuntu disc and replace it with your Windows disc. then install Windows.

You must use the Live CD. Otherwise it would be like sawing off the branch of the tree you're sitting on!

---

### Post by bootDisk on 2008-12-22
Whoa, well that was close, thanks everyone.

Ok i deleted the partitions from the Live CD , restarted with the Windows CD in and its saying:

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 22


and it's just staying like that.

---

### Post by decoherence on 2008-12-22
> **bootDisk said:**
> I popped in my Windows XP Pro disk and rebooted my laptop, pressed F10 and chose to boot from CD-ROM/DISK or whatever it was. It restarted and went back onto Ubuntu. I have no idea on what I did wrong. I just want my XP back.


That is the ONLY problem you have to fix. Why is your computer booting from the hard drive when you are instructing it to boot from the CD? 

Figure that out, and the Windows installer will be only too happy to blow away your Ubuntu partitions for you.

Deleting the partitions, as other posters have suggested, might make it so that when your computer tries to boot off the hard disk (after you've told it to boot form the CD) it won't be able to and then perhaps will fall back to the CD (even though you already told it to do that.)

I don't think you should have to do that.

Remember that, with Windows install media, you have to type a key when it prompts you otherwise it'll just boot off the hard drive. That's right -- the Windows install disc will cause your computer to boot from the hard drive even if you've told it to boot from the CD... IF you don't press some key at the magic moment (it'll prompt you.)

If you've already taken care of that then all I can suggest is double-check your BIOS settings.

---

### Post by bootDisk on 2008-12-22
Ok, its because I didn't save changes. Thank you so much, now I have to deal with my laptop's automatic ghostly shut down while its booting...


ok it started up alright until it said:
PXE-E53: No boot filename received.

then it loads grub again and gives me Error 22, maybe I mounted the ISO wrong.

---

### Post by PierreDeKat on 2008-12-22
[IMG]http://www.geocities.com/loek_bakker/images/msft.jpg[/IMG]
Step 1) Insert disk.
Step 2) Tell yourself how much better off you are, now that corporations rule the world.

---

### Post by 73ckn797 on 2008-12-22
> **bootDisk said:**
> Ok, its because I didn't save changes. Thank you so much, now I have to deal with my laptop's automatic ghostly shut down while its booting...


ok it started up alright until it said:
PXE-E53: No boot filename received.

then it loads grub again and gives me Error 22, maybe I mounted the ISO wrong.

So, I understand that you want to go back to Egypt ....err, Windows. Are you trying to reinstall XP?

Did you tell the Windows install to format and partition the entire drive? That should rewrite the boot once installation starts.

You could also boot into the Windows CD and go into recovery mode. At command line type *fixmbr* or it may have to be* fixboot*.

---

### Post by kansasnoob on 2008-12-22
> **PierreDeKat said:**
> [IMG]http://www.geocities.com/loek_bakker/images/msft.jpg[/IMG]
Step 1) Insert disk.
Step 2) Tell yourself how much better off you are, now that corporations rule the world.

I love that!

Just think Mojave project!

---

### Post by handydan918 on 2008-12-22
> **73ckn797 said:**
> So, I understand that you want to go back to Egypt ....err, Windows. 


Bwahahahah....



:grin::biggrin::-D;-)

---

### Post by akelsall on 2008-12-22
Face in the direction Washington (state), USA, get on your knees, and bow down to Bill Gates. Maybe he'll grant you permission to revert back to Windows.

---

### Post by 73ckn797 on 2008-12-22
> **akelsall said:**
> Face in the direction Washington (state), USA, get on your knees, and bow down to Bill Gates. Maybe he'll grant you permission to revert back to Windows.


It will actually be one his surrogates that has authority to grant permission and then they will want to authenticate that.

---

### Post by Bert1e on 2008-12-23
> **kansasnoob said:**
> Well since you installed Ubuntu, which requires BIOS booting from CD first, my best guesss is that Win just doesn't like what it sees!

So, since you want to completely reinstall Win, first boot the Ubuntu disc you used to install Ubuntu. Choose to "Try Ubuntu without any change to your computer" and then go to System > Administration > Partition Editor. If any "locks" are displayed you may need to click on the SWAP partition and choose "swapoff'.

Then delete all partitions and choose apply. Wait until it's done. Reboot, remove the Ubuntu disc and replace it with your Windows disc. then install Windows.

Hi Kansasnoob, This one worked for me. However having reloaded windows me I cannot reset screen resolution. Could I have wiped motherboard drivers? Bert1e

---

### Post by bootDisk on 2008-12-23
Well Windows wouldn't even reformat pass 20% without having to automatically shut down on me. It looks like I'm stuck with Ubuntu :]

---

### Post by Nico-dk on 2008-12-23
If windows has started formatting, then that means the XP cd can "see" your harddrive, but if it fails at 20% you might have a hardware problem.
Try again, and select quick/fast when formatting.

Did you remember to delete all partions (L, I think), so you ended up with one big unformatted harddrive?
Does it fail at 20% again?
Can you install Ubuntu again?

If yes, then follow the previous advice of booting from the Live CD, and formatting your harddrive to ntfs.

If all else fails, you could always try the [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) although I wouldn't recommend that for a newbie.

---

### Post by richg on 2008-12-23
People with very limited knowledge should never try to install Linux on a Windows XP or what ever OS. Use a hard drive rack and put each hard drive into a drawer that installs into the rack. Locks the drive rack with a key. One hard drive, one OS. Been doing that for nearly five years. Never, ever any issues.
I use to have a Windows PC with a drive rack. One drive for Windows OS. Two drives, each with their own Linux OS. No heartburn. No frustration. That PC is gone now.
Remember, those who say it easy, have Linux experience and would like you to experience the same frustrations as they did.
I do not have much Linux experience but my PCs are always working. I do not like spending a lot of time in the forums trying to get a PC to operate. I can use my PCs as they were intended to be used.

[IMG]http://i98.photobucket.com/albums/l267/richg1998/Misc/Harddriverack.jpg[/IMG]
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=529421&CatId=285](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=529421&CatId=285)


Rich

---

### Post by anewguy on 2008-12-23
The 2nd reply in this thread pointed you to the post you should have followed.  It allows you to be sure your Windows will boot okay first, then lets you remove Linux.  It's safe and it's easy.  For future reference, please read it (ignoring the idea that I originally wrote it ;)  )

For others reading this thread - check the link.  It's an easy process and if followed correctly there is no need for a grub disk, you won't get a grub error when you remove Linux, etc..


dave :)

---

### Post by balaknair on 2008-12-23
@anewguy

Yep, I just finished reading it. Great howto. Bookmarked it for future reference.
I just wish I'd known about it earlier(no, I'm not switching back to Windows, but it would have let me help some people who did; at least I know where to send them).

---

