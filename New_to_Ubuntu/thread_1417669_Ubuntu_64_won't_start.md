---
title: "Ubuntu 64 won't start"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Daisho on 2010-02-27
Hello everyone,

I just upgraded from 9.10 32-bit to 9.10 64-bit Ubuntu and now I can't get the OS to start properly. I make it through dual boot and the loading screen (brown background, horizontal loading bar) but when it is done loading it just stops on the beige background and the bars/menus never appear. I can see the mouse and it does a bit of loading but nothing more happens.
I have tried reinstalling and checked the disc for errors, but I can't get it to work.

Can anyone help me?

/Daisho

---

### Post by howefield on 2010-02-27
How did you install 64 bit, did you wipe out your 32 install completely and clean install your new system as would normally be the case for moving to 64 bit ?

---

### Post by corncob on 2010-02-27
Hmmm.  It told me right off that it was the wrong operating system when I tried to install 64-bit into an older computer that wasn't 64-bit capable.  Are you dual booting it with 32-bit Ubuntu?

---

### Post by Daisho on 2010-02-27
I installed it on the same partition as the 32-bit was using before. I installed it as a new OS by choosing that partition as root and formatting it. I don't know if it matters, but the partition was ext3 before and I made it into ext4 (when I tried reinstalling I went back to ext3 but it made no difference in the behavior).

Edit: I'm dual booting it with Windows XP and have four partitions: Windows XP, Ubuntu root, Ubuntu home and a partition for various movies/mp3s and other files.

---

### Post by corncob on 2010-02-27
Are these all primary partitions? (System > Administration > gparted)  I've been told that you can only have a maximum of four primary partitions on a hard drive.  Otherwise, funny things happen.

---

### Post by Daisho on 2010-02-28
I can't figure out where to find that information in gpart, but as far as I remember only the ubuntu root partition and maybe one more are primary partitions. I don't think that's the problem. I went back to 32-bit and it works just fine. It's the 64-bit that messes things up...

---

### Post by corncob on 2010-02-28
> **Daisho said:**
> I can't figure out where to find that information in gpart, but as far as I remember only the ubuntu root partition and maybe one more are primary partitions. I don't think that's the problem. I went back to 32-bit and it works just fine. It's the 64-bit that messes things up...

I thought it showed up somewhere.  Maybe somebody else could jump in here.  Is your computer capable of 64 bits?  Did you check your installation disk for errors?  Download it again and make another installation disk?  It seems I've had your problem but it was with an older computer that I figured wasn't up to running Ubuntu and went on to install Puppy Linux instead.

---

### Post by Daisho on 2010-02-28
I'm pretty sure it can handle the 64-bit system. It might be the disc but wouldn't it have shown when I scanned it for errors? And the same problem appears when I update Ubuntu 8.10 (that's the 32-bit version I have on CD) to 9.04.

I'm starting to suspect that the problem lies with the graphics. Sometimes when I start Ubuntu I can see "shadows" of the top and bottom bars and a box (probably a window) on the desktop. It occured to me that I had the same problem when activating loose bindings in Compiz before I installed the graphics driver (my card is a AMD HD4850 Sapphire),
the screen went white apart from the mouse but the desktop was still there and I could sometimes restart the computer if I managed to click the right spots.
I can't do it now, though. Is it possible that it can be solved by installing the graphics driver? I'll try it and get back to you on that.

---

### Post by Daisho on 2010-02-28
Well, my suspicions were correct. It was the graphics driver.
I simply selected Recovery mode in grub, opened the terminal and issued the command
[FONT=Fixedsys]
$ sudo apt-get install xorg-driver-fglrx[/FONT]

I happened to see that the fglrx module was missing.
Problem solved, thanks for your help, guys  \\:D/

---

