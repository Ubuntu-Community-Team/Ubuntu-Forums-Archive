---
title: "Bad Livesession USB Drive?"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Da_Gopherboy on 2010-01-25
Hello all, first time poster.

Bit of a background, I've been working on PCs for about 17 years now.  Grew up working on the DOS window, and Windows 3.11 Workgroup.  I took some classes years ago on the *nix OS environment but wasn't ready to make the switch.  But as time has past and I've become a full believer in the GNU project and want to be a part!

So as the title says I used a Jump Drive to get Ubuntu 9.10 live session working.  I've been using it for about a week and feel that I have enough of a grasp to not be counter productive in the basics (ie. being able to use openoffice to read/write documents).  So I decided it was time to make the switch, I took an older box (1.4ghz P4, 512RAM, 2x 45gig hard drives, 50x Cd-r-rw, Compaq Brand) and tried to install.  This is the part that begins to confuse me, I've been using this Live session jump drive without issue for a week now.  However when I go to install Ubuntu onto the box, I can format and partition the drives, but when it comes to installing the core packages it says they are corrupt.  It gives no description about how their corrupt, they just are.

Now, confused about this I downloaded the .iso file several times, and confirmed that it was a good download from Bit Torrent and by compairing the filesize to the one posted at ubuntu.com  In addition to that, months ago I ordered a livecd directly from Canonical, trying that I get the same corruption message.

So my question is (after telling my life's story) do the LiveCD sessions differ in some way from an actual install?  Could I have a bad .iso despite repeated downloads?  Is there a way to isolate the problem to figure if its perhaps hardware incompatibility or just the user?

Thanks,
G

---

### Post by phillw on 2010-01-25
> **Da_Gopherboy said:**
> Hello all, first time poster.

Bit of a background, I've been working on PCs for about 17 years now.  Grew up working on the DOS window, and Windows 3.11 Workgroup.  I took some classes years ago on the *nix OS environment but wasn't ready to make the switch.  But as time has past and I've become a full believer in the GNU project and want to be a part!

So as the title says I used a Jump Drive to get Ubuntu 9.10 live session working.  I've been using it for about a week and feel that I have enough of a grasp to not be counter productive in the basics (ie. being able to use openoffice to read/write documents).  So I decided it was time to make the switch, I took an older box (1.4ghz P4, 512RAM, 2x 45gig hard drives, 50x Cd-r-rw, Compaq Brand) and tried to install.  This is the part that begins to confuse me, I've been using this Live session jump drive without issue for a week now.  However when I go to install Ubuntu onto the box, I can format and partition the drives, but when it comes to installing the core packages it says they are corrupt.  It gives no description about how their corrupt, they just are.

Now, confused about this I downloaded the .iso file several times, and confirmed that it was a good download from Bit Torrent and by compairing the filesize to the one posted at ubuntu.com  In addition to that, months ago I ordered a livecd directly from Canonical, trying that I get the same corruption message.

So my question is (after telling my life's story) do the LiveCD sessions differ in some way from an actual install?  Could I have a bad .iso despite repeated downloads?  Is there a way to isolate the problem to figure if its perhaps hardware incompatibility or just the user?

Thanks,
G

Hi and welcome to the forums.

It is unlikely that the CD from Canonincal is faulty, however, you can test cd's using a better system than file-size. That is covered here --> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The LiveCD's should also have a menu option called 'test the CD' or words to that affect.

I'd suggest cleaning the cd-drive with one of those cleaning cd's - Data cd's (Specifically ISO's) are written to tight tolerance, and a bit of good old fashioned grime on the cd-lens can stop them in their tracks (excuse the pun).

Does the Canonical CD run happily in 'Try without altering my Computer' mode ?

Regards,

Phill.

---

### Post by Da_Gopherboy on 2010-01-25
> **phillw said:**
> 

Does the Canonical CD run happily in 'Try without altering my Computer' mode ?



Much thanks for the speedy response! The CD does run happily... for a time.  I can run it for a few hours and it seems to not like firefox after 3 or 4 hours, and I have to reboot.  That happens both on the machine I desire to install ubuntu on, and the laptop in which I have been using Ubuntu to become addicted.  The only thing I can think that could cause that on the CD is that perhaps the RAM become full as its not saving the history to the HD perhaps?  The lack of being able to use the persistent feature perhaps?  Don't know.. USB Jump Drive works great except for the actual install to the machine.

Thanks,
Gavin

---

### Post by phillw on 2010-01-25
Hi, I'm guessing you mean a usb memory-stick when you say usb jump-drive. If so, yes, they can become corrupted.

That wouldn't affect the LiveCD - Have you tried doing the installation off the LiveCD instead of a USB-stick ? And, have you ran the 'check CD for faults', or what ever the menu option is (!!) on the CD you're wanting to use for the install ?

Regards,

Phill.

---

### Post by Da_Gopherboy on 2010-01-25
> **phillw said:**
> Hi, I'm guessing you mean a usb memory-stick when you say usb jump-drive. 

Yeah I'm using one of those.  The Brand calls it a jump drive.


> **phillw said:**
> 
That wouldn't affect the LiveCD - Have you tried doing the installation off the LiveCD instead of a USB-stick ? And, have you ran the 'check CD for faults', or what ever the menu option is (!!) on the CD you're wanting to use for the install ?

I've checked the LiveCD twice, once it came back "corrupted", and the other time it didn't. I found that odd, however I had the same reasoning that you did, if they're going to ship this LiveCD they are much more qualified to know if its good or not.

I've tried installing from both the USB-stick and the LiveCD, both have corruption problem.  Perhaps hardware failure on the older machine?  That being said, why would the LiveCD and the USB-stick work for many hours on end? I don't have a newer machine to try the install on yet (still need business software from my windows based machines), so is there more diagnostics I could try?

Thanks,
Gavin

---

### Post by phillw on 2010-01-25
I would go back to cleaning the cd-drive with one of the lens-cleaner cd's.

As it works 'sometimes' it looks like a dirty lens.

The other option is to use the LiveCD in any computer that you get a couple of good 'check CD for defects' on (The works one is fine for this, we're **not** going to touch it !!, select the 'try without changing my computer' option, from there pop into System, Administration and re-master your USB stick. Once that is done, you should be able to both boot from & install using the usb-stick.

Regards,

Phill.

---

### Post by Da_Gopherboy on 2010-01-27
> **phillw said:**
> I would go back to cleaning the cd-drive with one of the lens-cleaner cd's.
 
As it works 'sometimes' it looks like a dirty lens.
 
The other option is to use the LiveCD in any computer that you get a couple of good 'check CD for defects' on (The works one is fine for this, we're **not** going to touch it !!, select the 'try without changing my computer' option, from there pop into System, Administration and re-master your USB stick. Once that is done, you should be able to both boot from & install using the usb-stick.
 
Regards,
 
Phill.
 
 
Thanks for all your help Phill!
 
I followed your advice and tried cleaning the CD-Drive, and tried checked for defects.  The scan didn't detect any defects, however now its not even booting to the Livesession Desktop.  I tried an alternative install with unsuccessful results.... I'm kind of at a loss, Ubuntu has been 100% great while using it on the USB drive.  But whenever I try to install it, I have a 100% failure rate.  Any sugjestions?  I've read the entire install manual from ubuntu.com and the different ways to install, but nothing is happening the way as described.
 
Thanks,
Gavin

---

