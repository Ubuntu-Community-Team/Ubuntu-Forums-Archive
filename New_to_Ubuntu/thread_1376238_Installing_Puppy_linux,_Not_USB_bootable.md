---
title: "Installing Puppy linux, Not USB bootable"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by ovid9 on 2010-01-08
Ok, so I'm attempting to help a friend frugal install puppy on an ancient laptop.  How ancient?  I dunno, but the BIOS doesn't support booting from the USB port.  Oh, and it has no CD drive.

So, to clarify, booting from CD or USB is out as the CD has to use the USB port.  

It has Win98 on it, and she's attempting to follow [these vague and fairly technical]("http://puppylinux.org/main/index.php?file=Frugal%20Install%20to%20Hard%20Disk.txt") (for us noobs) to follow.

She's done up to the point of running grubinstall.exe but all she gets is a window flashing quickly saying a failure of some sort occured.

Is there a way to create a Linux partition, copy the stuff there and make it boot from that partition?  Any ideas?

---

### Post by Darce on 2010-01-08
Hi ovid,

Can you not boot from the CD because its not an option in the bios ?

I recently installed Puppy on a 10 year old lappy using a combo of CD and USB thumbdrive.

What are the boot options in your bios ?

---

### Post by ovid9 on 2010-01-08
Right, the BIOS is too old to boot from a USB port.  And since both the thumb drive and external CD drive use the USB port, booting from them is out.  Copying files is still possible while windows is running.

I know attempting to upgrade the BIOS is a possibility, but  we're kind of hoping to avoid that.

Apparently options are hard drive or floppy drive.  (Not physically looking at the machine....)

Its an old Dell Latitude CSx H with 128meg ram and a 6 gig HD.  Currently almost totally used by Win98 bloat.

---

### Post by Sef on 2010-01-09
Check out [Ubuntu Installation]("https://help.ubuntu.com/community/Installation") from the Community Docs.   There is section on minimal installing.

---

### Post by Roger Allott on 2010-01-09
I had an almost identical puzzle with an old Toshiba laptop, which had an internal CD drive that was fugged and BIOS that wouldn't boot from USB. I wanted to put Xubuntu onto it. Here's what I'd recommend for you based on how I did it.

Almost certainly, your HDD is PATA (a.k.a. IDE or ATA). Buy yourself an HDD caddy for PATA, which should cost no more than a tenner. Remove the Dell's HDD and put it in the caddy.

(As an option, your friend might want to take this opportunity to purchase a larger HDD to use instead of the 6Gb one. This will give her the peace of mind of always being able to go back to Win98 unaltered if she doesn't like Puppy.)

Find a more modern PC that can boot from internal CD. Remove its HDD (very important!) and ensure that CD is the first location searched in the BIOS.

Connect the caddy HDD to the USB port of the modern machine.

Insert the Puppy CD into the modern machine.

Boot up the modern machine. The Puppy install CD should now install Puppy to just the caddy HDD.

Once installed, remove the HDD from the caddy and put it back into the Dell machine. Boot the Dell machine and enjoy Puppy.

Put the modern machine's HDD back and you'll see that it'll load up as before - no issues.

---

### Post by Darce on 2010-01-09
Sounds like you need to fire up your floppy.

Grab the file wakepup2 file attached. Unzip and run. It will create a boot disk which will allow you to run puppy from cd/usbflash

Once you've got puppy running from that, you can then do an install back to your hard drive.

Check instructions here

[html]http://www.murga-linux.com/puppy/viewtopic.php?t=7979[/html]Cheers,

Tim

---

### Post by ovid9 on 2010-01-09
Sef:  Thanks for that link.  Lots of handy resources there.   It always seems to be the answer to my question is there somewhere, just being able to find it in the wonderful mass of data.
 
Roger: That was my suggestion as well, and that might still be how this gets accomplished. However, the only other computer in her house is her good laptop, so she didn't want to dissect it as well.  If it comes down to this being the way to go her parents have a desktop she could do it with easily.   However....
 
Darce: We'll give that a shot. That sounds like exactly what we need to do this. Thanks.
 
Hopefully she has a floppy disk lying about somewhere...
 
This is just a fun project for her that I'm sort of helping on since I was the one who told her about linux in general. Of course I'm 900 miles away and not overly knowledgeable myself, so you all are a great and wonderful resource! 
 
I'll let you know how it all ends up.

---

### Post by ovid9 on 2010-01-09
Thanks to you all.  

Darce, we went with your method first and she got it to work first try.  Now her next question is what to do with the computer...but it was as much the journey as the result.  

Thanks again!

---

