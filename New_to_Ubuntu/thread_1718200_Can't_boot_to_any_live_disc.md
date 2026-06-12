---
title: "Can't boot to any live disc"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by DGINSD on 2011-03-31
If I hit F12 on my bios screen and tell my computer to boot from  the CD/DVD drive it pauses and acts like its going to, then Grub will load and ask me to select an OS, I've tried with a few different live discs, I've checked to see if the drive is reading discs(it will play a DVD) but nothing seems to change the issue. What could be causing this?

---

### Post by wolfen69 on 2011-03-31
> **DGINSD said:**
> If I hit F12 on my bios screen and tell my computer to boot from  the CD/DVD drive it pauses and acts like its going to, then Grub will load and ask me to select an OS, I've tried with a few different live discs, I've checked to see if the drive is reading discs(it will play a DVD) but nothing seems to change the issue. What could be causing this?

Do you have 2 cd/dvd drives? If so, try the other drive.

---

### Post by DGINSD on 2011-03-31
negative one CD/DVD drive I have portable that plugs in through USB, but I don't think I can boot through that...Can I?

---

### Post by wolfen69 on 2011-03-31
> **DGINSD said:**
> negative one CD/DVD drive I have portable that plugs in through USB, but I don't think I can boot through that...Can I?

Plug in the external and see if the BIOS sees it. If so, you should be able to.

---

### Post by DGINSD on 2011-03-31
It appears to see the drive, same result though; a pause then on to GRUB.

---

### Post by wolfen69 on 2011-03-31
Go into the BIOS and make sure the cd drive is set to boot first.

---

### Post by DGINSD on 2011-03-31
> **wolfen69 said:**
> Go into the BIOS and make sure the cd drive is set to boot first.

The first and only thing I knew to try.

---

### Post by Clever_Username on 2011-03-31
Seems like if it's going to grub, then it's bypassing the cd as I've never heard of grub loading from a cd before.

---

### Post by DGINSD on 2011-03-31
> **Clever_Username said:**
> Seems like if it's going to grub, then it's bypassing the cd as I've never heard of grub loading from a cd before.

That was my assumption as well. I originally was trying to see if I had a defrag program on a bootable, that could completely defrag and compact my Windows partition, when I discovered the problem. Now I'm more concerned with upgrading upon new Ubuntu releases, this problem making that exceedingly difficult if not impossible without a complete hard drive, wipe, format, and Windows/Ubuntu reinstall. Good practice, but no fun what so ever.

---

### Post by DGINSD on 2011-04-02
I just though of something that was done to my machine that may of caused this problem, but I'm unsure and would appreciate some feedback. A couple of weeks ago I swapped the CD/DVD drive, the reason I didn't even consider it as a possible cause, is because I swapped it for the exact same model of drive, just one with a lot fewer miles on it. Are the drives in a computer recognized by some type of "electronic signature" and won't allow a boot from a drive thats been swapped without some type of confirmation or bios change?

This  is the only thing I can think of and with the lack of responses, I'm grasping at straws trying to figure this out. It kind of leaves me stuck if when i need to upgrade my Ubuntu or need to repair or reload my Windows XP.

---

### Post by gordintoronto on 2011-04-02
> **DGINSD said:**
> If I hit F12 on my bios screen and tell my computer to boot from  the CD/DVD drive ...

Could you be more specific, please? What computer or BIOS, what options did you use in the BIOS menus? Did you select "save" when you exited?

Swapping one drive for another should not cause your problem.

---

### Post by DGINSD on 2011-04-02
> **gordintoronto said:**
> Could you be more specific, please? What computer or BIOS, what options did you use in the BIOS menus? Did you select "save" when you exited?

Swapping one drive for another should not cause your problem.

My Computer is a Dell Inspiron 1150 which originally came with Windows XP and I've added Ubuntu 10.10 Maverick. I'm not super
knowledgeable with computers, but when I power up, my Dell Bios loads, while its loading at the bottom of my screen are 2 additional options given, F2 to enter set up, or F12 to enter boot menu. I hit F12 and my machine then says, "preparing one time boot menu", and gives me options for where to boot from, HDD, CD/DVD, Floppy Drive, On Board NIC. I select CD/DVD and it starts to act like its going to boot that way, but delays a short bit, then my Grub menu pops up giving me my various Ubuntu kernel options and my Windows XP.

Since I've noticed this I've gone into the set up and placed my CD/DVD Drive on the top of the list of Bootable devices, originally the order was Floppy HDD CD NIC so basically i switched CD and Floppy (seeing as I don't have a floppy thought this was best)

---

### Post by Hedgehog1 on 2011-04-02
On the swapped CD/DVD - if it is an IDE drive, please make sure the new one is set to 'Master' and not 'Slave'.  The setting is typically done with jumpers on the back of the drive.

***The Hedge***

:KS

---

### Post by DGINSD on 2011-04-03
> **Hedgehog1 said:**
> On the swapped CD/DVD - if it is an IDE drive, please make sure the new one is set to 'Master' and not 'Slave'.  The setting is typically done with jumpers on the back of the drive.

***The Hedge***

:KS

Even on a laptop CD drive? I looked and I didn't see anything like that. 

Just for S&G I put the old drive back in and followed the above procedure and sure enough good to go. So then I'm sayin' great I have to use this useless old worn out drive. So I thought I'd try and reload the BIOS drivers with the new drive back in and POW all was well. 

So it would appear that something in the Dell BIOS logs and registers all the devices or something but what ever it did it's back to working like normal. Ended up solving it my self but I appreciate the help guys.

---

