---
title: "install of jaunty seems to have just installed memtest"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by susanw on 2009-07-11
Hello,

I have been dual booting xp and hardy but decided to upgrade to jaunty. My cd drive doesn't work very well to boot from so I copied the cd image of jaunty livecd onto a new partition which I then installed from. Unfortunately after install I have now got a grub menu with just "Ubuntu 9.04, memtest86+" (and XP) in and apparently no way to get to jaunty or "installer" the link I made before to get to the livecd on the other partition.

Perhaps there is some clever way to load jaunty that I am not seeing? Perhaps I chose the wrong settings ext3/4/other?? thus jaunty didn't fully load? or perhaps my livecd image was broken (checksum was correct though). Perhaps I could reach something from windows or command line?

I am flummoxed at what to do now though... and which option in the livecd to choose differently if I did manage to get back there.

Any ideas gratefully received, thank you.

---

### Post by earthpigg on 2009-07-11
is your computer capable of booting from a USB drive?

you could always try system -> administration -> USB startup disk creator

---

### Post by susanw on 2009-07-11
> **earthpigg said:**
> is your computer capable of booting from a USB drive?

you could always try system -> administration -> USB startup disk creator

I'd forgotten about that method. Worth a try, pretty sure my computer complains about it though which I've wondered if is to do with the size of the memory stick, never found any advice on possible sizes a computer will boot off?

cheers

---

### Post by susanw on 2009-07-11
And I have Jaunty, even internet and a method of livecd I thought didn't work for me, thank you!!!

---

### Post by LewRockwell on 2009-07-11
if your machine is capable of booting from USB then you will have that selection available in your BIOS settings(usually F2 at start-up)

alternatively, you can manually select your desired boot device by depressing "F12" approximately twice per second during start-up which will bring you to the appropriate screen for that selection

.

---

### Post by LewRockwell on 2009-07-11
It would be interesting to see what a Supergrubdisk would report

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

