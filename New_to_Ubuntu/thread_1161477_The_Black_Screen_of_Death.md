---
title: "The Black Screen of Death"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by lile001 on 2009-05-16
Well, I'm looking at the Black Screen of Death after trying to install Ubuntu 9.04 for the umpteenth time.    Here's the story:

I have zero experience with Ubuntu  (OK, I have several evenings experience which all end in the Black Screen of Death after trying to install it... that's about it)  

The Black Screen of Death seems to see the mouse, as a cursor moves around, that's pretty much it, nothing else ont he screen, punching keys or clicking around randomly doesn't elicit any life. And it resembles Darth Vader in it's blackness... 

Assume that I am making the most simple, bonehead error you can think of, you'll probably be correct!  Earlier, I posted a thread that went on and on about arcane options, when the problem was I needed to try install under *safe graphics mode*, a super-basic option under install.  Let's look for that kinda stuff. 

I have a dual monitor, (unplugging the cable on one of them also helps) and a RAID1 hard drive.  It is done through the BIOS, and if you ask me if it is "fake RAID" or "not fake RAID" I can't tell you.  I can tell you that Ubuntu installer isn't talking nice to it.   

I've tried to partition this thing several ways, usually trying to leave Windows XP alone in a 10GB partition by itself.  Most recently I just let Ubuntu blow away Windows XP and use "the entire disk".  So much for Microsoft.  This resulted in a freeze right after the RAID1 Bios screen saying 
"Couldn't open drive multi(0)disk(0)rdisk(0)partition(2) NTLDR: Couldn't open drive multi(0)disk(0)rdisk(0)partition(2)"    This seems to be a showstopper, looks like I've wrecked this computer completely.  

Well, that's more informative than the Black Screen of Death at least. 

Now, during install, and partitioning, Ubuntu does not recognize that the two hard drives are one, it treats them as two.  There's no place to tell it that there is anything special.

Ubuntu also doesn't give any options for setting up the monitors.  Safe Graphics mode is fine for setup, apparently doesn't work thereafter.   This probably is the source of the Black Screen of Death.  

 

:popcorn: Here's some popcorn, let's watch the Black Screen of Death and see if we like the Special Effects or the acting..........the suspense is killing me...

---

### Post by rustutzman on 2009-05-16
Does the Live CD boot to a GUI? 

Russ

---

### Post by anewguy on 2009-05-16
The BSOD as you call it, as long as the mouse or SOMETHING is there, usually indicates that the video needs a driver.  Just boot up, then at the BSOD hold down ctrl alt and press F1.  This will open a command line session.  Log in with your usual userid and password.  Then at the prompt do the following:

lspci <press enter>

Post the output of that back here so we can see what video adapter you have.

Dave :)

---

### Post by lovinglinux on 2009-05-16
I think you are confusing a stalled installation screen with [Black Screen Of Death](http://en.wikipedia.org/wiki/Screens_of_death#Linux_Black_Screen_of_Death). BSOD usually involves a [kernel panic](http://en.wikipedia.org/wiki/Kernel_panic), due to a fatal error and it shows a lot of stuff on the screen like [this](http://en.wikipedia.org/wiki/File:Ubuntu-linux-kernel-panic-by-jpangamarca.JPG). In this situation, you can't even use the mouse, just like when you have a Blue Screen Of Death on Windows.

---

### Post by anewguy on 2009-05-16
> **lovinglinux said:**
> I think you are confusing a stalled installation screen with [Black Screen Of Death](http://en.wikipedia.org/wiki/Screens_of_death#Linux_Black_Screen_of_Death). BSOD usually involves a [kernel panic](http://en.wikipedia.org/wiki/Kernel_panic), due to a fatal error and it shows a lot of stuff on the screen like [this](http://en.wikipedia.org/wiki/File:Ubuntu-linux-kernel-panic-by-jpangamarca.JPG). In this situation, you can't even use the mouse, just like when you have a Blue Screen Of Death on Windows.

Exactly why I asked the op to login via a terminal and list the pci devices so we can see his video card to get a driver for him.  I just used BSOD as that seemed to be his reference point.

Dave :)

---

### Post by lile001 on 2009-05-16
> **rustutzman said:**
> Does the Live CD boot to a GUI? 

Russ

Yes, the live CD will boot and run.  Once I install Ubuntu the fun starts [sarcasm]

---

### Post by lovinglinux on 2009-05-16
> **anewguy said:**
> Exactly why I asked the op to login via a terminal and list the pci devices so we can see his video card to get a driver for him.  I just used BSOD as that seemed to be his reference point.

Dave :)

Yep, I understood why you used "The BSOD as you call it". I just wanted to clarify the situation, since he used the term BSOD a lot on this thread.

---

### Post by Nasaki on 2009-05-16
I have run into the "black screen of death" problem on several occasions. The first time happened to be during my installation of Ubuntu on my workstation. Which happens to have dual GPUs. After the install, I had to open a TTY (ctrl-alt-F1) and edit the Xorg file with:

```
sudo nano -w /etc/X11/xorg.conf
```
and added the PCI busid of my graphics card by inserting
```
Busid "PCI:02:00:00"
```
Under the "Device Section". If you don't know the busid of your graphics card run: ```
lspci | grep -i vga
```

I also encountered this problem when doing an install an a dual-headed system, which may be closer to you setup. I refered to: [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

Hope it helps,

Nasaki

---

### Post by HereInOz on 2009-05-16
Just for fun, take out one of the drives in the RAID, plug the other drive into a non-RAID port on the motherboard, and see if you can get an install that way.

If you can, it means that Ubuntu is not working well with the RAID chip on the motherboard.  There are ways to set up a software RAID, and this is often a good way to go if there is "no-talkies" between Ubuntu and the RAID controller.

---

### Post by Game Over on 2009-05-16
I just got past this exact same thing on my HP Pavilion dv6000. I just downloaded Ubuntu 8.10 Intrepid and made a CD with my old man's Macbook. Popped that bad boy in a booted her up, installed, partitioned the whole hard disk (didn't want/need XP -- seems to run smoother that way). 

I know we're using different hardware, but see if a stable version helps. It helped me!

---

