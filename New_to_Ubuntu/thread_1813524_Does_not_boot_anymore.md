---
title: "Does not boot anymore"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by Alienspecimen on 2011-07-27
Youtube has been always hard on my slightly older Gateway laptop running either 10.04 or 10.10, I dont remember which.

Couple of days ago while on youtube it was freezing constantly and after I finished, upon powering down, the small window asking if I am want to quit showed up, but the buttons didnt show up.  I clicked on the space where normally "yes" would be and the computer powered down.

Next morning I tried to restart it, but it does not want to boot up, just a lot of letters and numbers on a black screen.  Only thing that makes sense is something in a sense:

mounting /dev on /root/ dev failed: no such file or directory

Here is what I did:

1.  Used the various versions of umount command, but without any success as it tells me that whatever I am trying to unmount is busy.

2.  Created an USB drive to boot from in an attempt to repair, but it does not work.  It comes up to the purple Ubuntu screen with the five dots that change from white to reddish underneath and just stays stuck there.  Needless to say, I can boot up Ubuntu from that USB drive on all my other computers...

I would appreciate if you provide suggestions how to proceed, because although the least powerful computer I own, it is the one I like and use the most.

Thanks in advance

Boris

P.S.  Ubuntu is the only OS installed...no double boot.

---

### Post by jtarin on 2011-07-27
You don't get a Grub screen at all? Won't boot from USB Live? Do you have a CD player? Can you get into the bios? See if it recognizes your drives, memory etc.

---

### Post by Alienspecimen on 2011-07-27
> **jtarin said:**
> You don't get a Grub screen at all? Won't boot from USB Live? Do you have a CD player? Can you get into the bios? See if it recognizes your drives, memory etc.

I dont know which screen is the Grub.  I can get passed bios (it recognizes the drives) and yes, it does not want to boot from USB live.  Here is what happens:

I get a menu asking me if I want to boot from this usb and also several other options including installing the OS on the HD etc.

After selecting either, it tries to boot up from the live USB, but it gets stuck on the purple screen with the five dots under the logo.

---

### Post by jtarin on 2011-07-28
All I can say to that is try to redo you USB creation and try again. Preparation of the USB is important and check the md5 checksum of the downloaded file to make sure you have the entire thing.

---

### Post by wildmanne39 on 2011-07-28
Hi, this link may help it sounds like you need to set a nomodeset option.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Alienspecimen on 2011-07-28
> **wildmanne39 said:**
> Hi, this link may help it sounds like you need to set a nomodeset option.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I saw what he did, but dont think am getting that far,  or at least my menus dont have the options he listed.  Here is what happens.

Upon boot up

1.  I choose F10 "Boot up Menu" option
2.  I then choose USB Hard Drive
3.  Then I come to lower resolution black screen with Ubuntu logo under which it says:  Installer Boot Menu. Here are the options:  Run Ubuntu from this USB, Install Ubuntu on a Hard Disk, Test memory, Boot from first Hard Disk, Advanced options (there is nothing there...) and help

Right at the bottom of the screen it says : PressENTER to boot or TAB  to edit a menu entry.

4. If I were to choose Run Ubuntu from this USB or Install Ubuntu on a Hard Disk, I get to the purple screen saying Ubuntu and having five dots underneath, whose colors alternate from white to reddish.  Funny thing I discovered is the following:   It is obviously stuck, but if I press ESC at that time it brings me to a black screen that shows this:

[  5.938502] xor: automatically using best checksumming function plll_see
[  5.956003]  plll_see 5478.000MB/sec
[  5.956006] xor: using function pll_see (5478.000MB/sec)
[  5.959473] device-mapper: dm-raid45; initialized v0.2594b
Begin: Loadding essential drivers... ...
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/ casper-premount ...
Done.
Done.
Killed
stdin: error 0
/init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr0: No medium found
unable to open '/dev/sda'

I can alternate from this to the purple screen by pressing ESC and every time I return to the black screen, additional set of the above will be displayed.

---

### Post by Alienspecimen on 2011-07-28
I was able to solve my problem.

It appears that I am running 10.04.  Upon creating a new Live USB using the 11.04 iso file, I was able to boot up and repair my older version.  

Thanks to all who responded

Boris

---

### Post by wildmanne39 on 2011-07-28
Hi, glad you got it fixed, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

