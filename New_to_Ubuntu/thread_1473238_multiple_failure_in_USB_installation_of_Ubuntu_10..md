---
title: "multiple failure in USB installation of Ubuntu 10.04. give up?"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by hanzj on 2010-05-05
When I run USB Startup Disk Creator, I get at the end this message:
> Installation is complete.  You may now run Ubuntu on other computers by booting them with this drive inserted.
So I restart the computer and boot off the USB drive. But 


And I've tried the following:


[LIST]
[*][ubuntu-10.04-alternate-amd64.iso.torrent]("http://releases.ubuntu.com/10.04/ubuntu-10.04-alternate-amd64.iso.torrent")
[*][ubuntu-10.04-alternate-i386.iso.torrent]("http://releases.ubuntu.com/10.04/ubuntu-10.04-alternate-i386.iso.torrent")
[*][ubuntu-10.04-desktop-amd64.iso.torrent]("http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent")
[*][ubuntu-10.04-desktop-i386.iso.torrent]("http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.iso.torrent")
[/LIST]
For the amd64, the install stops at 74%.
For desktop i386, install stopped at 79% the first time. On my second attempt, I stepped away from the computer, only to return to the 10.04 purple "light" background with nothing else.

The only one i haven't tried installing is alternate 386. And I'm just about to do that now.

If that fails, how can I figure out what the source of this problem is?
I'm guessing it could be:
the USB drive
or
the iso copy.

Could it be something else?
How could I figure the source?




May 14 UPDATE: I did give up, and went with the waste-a-CD route.

---

### Post by hanzj on 2010-05-05
I've just tried USB-installing with the alternate i386 iso. but the crazy thing is that it's asking for the CD in the CD-rom drive. It shouldn't be doing that. It should look for things on the USB.

Aaagh!!! 8-(

---

### Post by k3lt01 on 2010-05-05
I find USB stick installations are so much easier than CD installations but, and it's a big but, I have never used USB StartUp Disk Creator yet. I have read to many bad reports on it and you have just written another.

[This is what I do]("http://ubuntuforums.org/showthread.php?t=1288604"). Be sure to use the NO lua support option.

Let us know how you go.

---

### Post by hanzj on 2010-05-05
[k3lt01]("http://ubuntuforums.org/member.php?u=397303"),
thanks. will try your method.

---

### Post by hanzj on 2010-05-07
[k3lt01]("http://ubuntuforums.org/member.php?u=397303"),
I tried the "HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2" as you suggested. 

The md5sum is correct.

I put the 64-amd-desktop iso onto the USB. I rebooted the computer, booted from the usb, saw the ubuntu 10.04 logo, attempted to install ubuntu 10.04 and got a black screen with an error message. I don't remember everything that was on the screen but I think it started with the word "Busybox ...". 

What's going on?

---

### Post by k3lt01 on 2010-05-08
You may need to make some command line adjustments so your vido card wotks with Plymouth. What type of card do you have?

---

### Post by hanzj on 2010-05-10
k3lt01,
> lspci | grep VGA
05:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)]


---

### Post by k3lt01 on 2010-05-10
Do a search for Plymouth and ATI that will tell you what you need to do to get it working past Plymouth. I know some of the Intel cards, like mine, need i915.modeset=1 put in the Grub file so it would work.

---

### Post by -humanaut- on 2010-05-10
Try booting with the kernel mode option " nomodeset " & " noapic " that will basically throw it into safe mode.

---

### Post by narendraD on 2010-05-10
> **hanzj said:**
> When I run USB Startup Disk Creator, I get at the end this message:



So I restart the computer and boot off the USB drive. But 


And I've tried the following:


[LIST]
[*][ubuntu-10.04-alternate-amd64.iso.torrent]("http://releases.ubuntu.com/10.04/ubuntu-10.04-alternate-amd64.iso.torrent")
[*][ubuntu-10.04-alternate-i386.iso.torrent]("http://releases.ubuntu.com/10.04/ubuntu-10.04-alternate-i386.iso.torrent")
[*][ubuntu-10.04-desktop-amd64.iso.torrent]("http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent")
[*][ubuntu-10.04-desktop-i386.iso.torrent]("http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.iso.torrent")
[/LIST]
For the amd64, the install stops at 74%.
For desktop i386, install stopped at 79% the first time. On my second attempt, I stepped away from the computer, only to return to the 10.04 purple "light" background with nothing else.

The only one i haven't tried installing is alternate 386. And I'm just about to do that now.

If that fails, how can I figure out what the source of this problem is?
I'm guessing it could be:
the USB drive
or
the iso copy.

Could it be something else?
How could I figure the source?


Have you tries Unetbootin?
I have found it more reliable than Startup Disk.

---

### Post by hanzj on 2010-05-10
[-humanaut-]("http://ubuntuforums.org/member.php?u=1049264"),
one can install while booting in safe mode?

---

### Post by hanzj on 2010-05-10
yes, i've tried unetbootin. 

i used unetbootin and rebooted my comp and booted off the usb drive but, after seeing the new ubuntu 10.04 logo and the horizontal line of dots, i get an error message saying something like "unknown user id". [URL="http://ubuntuforums.org/showpost.php?p=9236445&postcount=16"]( http://ubuntuforums.org/showpost.php?p=9236445&postcount=16 )
[/URL]

---

### Post by darkstaar on 2010-05-10
I had a problem similar to yours recently. Not with Ubuntu but with other distros, specifically Fedora and openSuse. Burning the same images to DVD's solved the immediate problem and indicated that the ISO images I was using were sound.

Reformatting the flash drives to FAT16 (from FAT32) _seemed_ to solve the problem. I say "seemed" because I can't prove that FAT32 was the issue, but if you're using a flash drive that is not formatted to FAT16, it might be worth trying.

---

### Post by hanzj on 2010-05-10
thanks, darkstaar. i haven't had much problems when using disc media (CD or DVD), and I do have some optical discs. I'm just trying to keep them unused. 8-)

Will try the FAT16 format.

---

### Post by k3lt01 on 2010-05-11
I formatted my flash drives to ext4 and haven't had an issue with it.

---

### Post by lavinog on 2010-05-11
Just curious, have you tried the check disk for defects option in the boot menu?

Flash drives are not perfect.  One of my flash drives is bad.  I can read all of the files that existed a couple of months ago just fine.  I can write to it and not get any write errors, but if I wait a couple of minutes and try and read the file I just wrote, I get a corrupted file.

The "check disk for errors" (I think that was the wording) option checks the integrity of all of the installation files.

---

### Post by hanzj on 2010-05-11
lavinog,
yes, I have tried the "check disk for defects" option, but it doesn't check the USB flash drive. Rather, it checks the cd/dvd drive, which is empty.

---

### Post by hanzj on 2010-05-13
I gave up and wasted a 700 mb CD-R disc for this task.

---

### Post by lavinog on 2010-05-14
> **hanzj said:**
> lavinog,
yes, I have tried the "check disk for defects" option, but it doesn't check the USB flash drive. Rather, it checks the cd/dvd drive, which is empty.
EDIT (misread previous posts):  What version USB startup disk creator did you use (what version ubuntu was it on)?

I have yet to try it with 10.04, but I haven't had this problem with 9.10's startup disk creator.

---

### Post by hanzj on 2010-05-14
I was having problems with the 9.10 version of USB startup disk creator, so I downloaded and installed the relevant packages from 10.04.

---

### Post by k3lt01 on 2010-05-14
You never told us, that I have seen anyway, if you tried the links that OldFred and myself gave you. If you did what happened, obviously it didn't work but why? If you didn't, why didn't you give it a go?

---

### Post by hanzj on 2010-05-14
Yes, I did try the link that OldFred gave in [http://ubuntuforums.org/showpost.php?p=9286143&postcount=33](http://ubuntuforums.org/showpost.php?p=9286143&postcount=33)

The one on " MultiBoot USB with Grub2 (boot directly from iso files)"

It didn't work. I checked the iso md5hash (no problem), followed instructions of howto on how to put onto usb drive. restarted the computer, booted off usb drive, saw new ubuntu 10.04 logo, chose "install ubuntu", but got a black screen with some text. I Dont' remember the text.

I spent 5 hours or more trying to make the USB option work. But burning on CD-R was just a 10 minute job.

---

### Post by spamless on 2010-06-11
I am having essentially exactly the same problem as the OP.

I used the Startup-Disk Creator and tried the Lucid i386 Netbook ISO and the full one.  Both stopped installing at exactly 79%.

Will review some of the suggestions, in particular the one about alternate video modes.  It is not yet clear to me how I run those commands while I'm using the USB stick.

---

### Post by spamless on 2010-06-11
> **-humanaut- said:**
> Try booting with the kernel mode option " nomodeset " & " noapic " that will basically throw it into safe mode.

Okay, I'm trying this now.  It took me a few minutes to figure out to hit the Esc key on booting with the USB stick in order to get to a menu where I could select these options.  It took me even more minutes to figure out to hit the Esc key again to get out of the submenu after having selected the items. &#9786;

I will wait a few minutes and see what happens before I post this. . . .

Wow.  It made it past 79%.  I'm impressed.  Thanks!  Maybe you could explain what those modes do more specifically.

---

