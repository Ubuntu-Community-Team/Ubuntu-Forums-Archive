---
title: "Booting From Flash Drive Skips Unetbootin Menu"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by UnsafeData on 2010-07-02
I want to install Ubuntu from a flash drive due to a faulty optical drive. I used Unetbootin but when I try to boot from my USB drive, nothing happens.. it then continues to boot Windows from my HDD. 
The only way I could get a result is formatting it to NTFS and which then I only get "BOOTMGR IS MISSING"
What is wrong?

---

### Post by lkjoel on 2010-07-02
First of all, be sure your BIOS is up to date.
Then go to the BIOS and be sure that the USB drive boots before the hard disk.

---

### Post by UnsafeData on 2010-07-02
> **lkjoel said:**
> First of all, be sure your BIOS is up to date.
Then go to the BIOS and be sure that the USB drive boots before the hard disk.

It already boots before the hard disk. I've installed Windows 7 from this before

---

### Post by C.S.Cameron on 2010-07-03
Format flash to FAT32,
Check MD5SUM of the iso,
Try usb-creator or Universal USB Installer.

---

### Post by warfacegod on 2010-07-03
I'm almost positive that the drive needs to be FAT32. You should also check your BIOS, like previously suggested. Your BIOS may automatically remove USB's after the first start up if they aren't plugged. Mine does.

---

### Post by UnsafeData on 2010-07-03
> **warfacegod said:**
> I'm almost positive that the drive needs to be FAT32. You should also check your BIOS, like previously suggested. Your BIOS may automatically remove USB's after the first start up if they aren't plugged. Mine does.

I checked. It does detect it. 
Also I formatted it in FAT32

---

### Post by warfacegod on 2010-07-03
Does the BIOS still list it if it isn't plugged in? If not, your BIOS is doing the same thing mine does and you'll need to have it plugged in and set your BIOS to boot from it again.

---

### Post by lkjoel on 2010-07-03
What is your make/model?

Try seeing if there is an option such as:
> (F2) Boot selection pop-up

---

### Post by UnsafeData on 2010-07-03
> **lkjoel said:**
> What is your make/model?

Try seeing if there is an option such as:

That's what I do

---

### Post by UnsafeData on 2010-07-04
Bump

---

### Post by UnsafeData on 2010-07-04
[IMG]http://i49.tinypic.com/2mfzzp1.png[/IMG]

I think this is the problem. It stays like this for a while and then it finishes.

---

### Post by warfacegod on 2010-07-04
It's possible but unlikely. It stays that way for that length of time because it's extracting a 609 MB file. Which is the majority of the work that unetbootin does.

Are you sure you have all of the appropriate extraction tools? When I do an install of Ubuntu, I often forget the p7zip-full package that unetbootin needs. Perhaps something similar is happening here.

---

### Post by UnsafeData on 2010-07-04
> **warfacegod said:**
> It's possible but unlikely. It stays that way for that length of time because it's extracting a 609 MB file. Which is the majority of the work that unetbootin does.

Are you sure you have all of the appropriate extraction tools? When I do an install of Ubuntu, I often forget the p7zip-full package that unetbootin needs. Perhaps something similar is happening here.

Well that's what I figured.
Also I'm doing this from Windows. Could there be anything I'm missing

---

### Post by warfacegod on 2010-07-04
> **UnsafeData said:**
> Well that's what I figured.
Also I'm doing this from Windows. Could there be anything I'm missing

So I gathered from the window border in the screenshot;).

Something missing was what I was thinking. I only have experience with the Linux version but I can't imagine unetbootin opening without giving a warning about that. The Linux version does but will still try to make the LiveUSB without it. Check the unetbootin site to see what it recommends having for Windows, if anything.

---

### Post by lkjoel on 2010-07-04
> **UnsafeData said:**
> [IMG]http://i49.tinypic.com/2mfzzp1.png[/IMG]

I think this is the problem. It stays like this for a while and then it finishes.
I know that this is slightly off topic, but how do you even manage to get crunchbang work?
I tried it on my computer (actually the computer I am using currently, which is not my Ubuntu), but somehow it would not load up!

---

### Post by snowpine on 2010-07-05
Hi UnsafeData, you need to press a key (usually Esc or one of the Fn keys; it depends on the manufacturer) at boot time to enter the "boot device menu." You should then be able to select your USB drive. You also need to make sure your computer is capable of booting from USB (if it's new enough to run Windows 7 you're probably OK, but many older computers don't have this capapbility).

You should also probably test your USB on a 2nd computer to troubleshoot whether it is a faulty USB or whether the problem is with your computer. :)

---

