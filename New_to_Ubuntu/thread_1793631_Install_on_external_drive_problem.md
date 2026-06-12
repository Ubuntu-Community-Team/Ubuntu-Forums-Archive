---
title: "Install on external drive problem"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by catagious on 2011-06-29
I downloaded 11.04 NN i386 to install on an external drive.  I removed the internal drive, ran the disk, installed, then restarted.  All I got was a screen with a little cursor blinking in the top left of my screen.  Nothing else.  I re-installed 3 times and same results.  I can use the disk with no problems.

Asus U50F
4 GB ram
Intel i3 dual-core 2.13 Ghz
Intel HD graphics chip

---

### Post by Ozymandias_117 on 2011-06-29
One thing to check is that your computer is set to boot from USB.

---

### Post by catagious on 2011-06-29
> **Ozymandias_117 said:**
> One thing to check is that your computer is set to boot from USB.

Already did that.  Set to boot from CD then USB followed by internal.

---

### Post by jtarin on 2011-06-29
Can you boot from the CD and select Try get to the Ubuntu desktop and run Gparted and take a screen shot or download and run the **bootinfo script** in my signature so we can see what is what with your drives and where Grub is.

---

### Post by catagious on 2011-06-29
> **jtarin said:**
> Can you boot from the CD and select Try get to the Ubuntu desktop and run Gparted and take a screen shot or download and run the bootinfo script in my signature so we can see what is what with your drives and where Grub is.
OK, label me an idiot, but how do I do a screen shot?   And how do I get into a command prompt?
When looking at the disk, I saw nothing about GRUB.
Remember, I'm a newbie......

---

### Post by jtarin on 2011-06-29
> **catagious said:**
> OK, label me an idiot, but how do I do a screen shot?   And how do I get into a command prompt?
When looking at the disk, I saw nothing about GRUB.
Remember, I'm a newbie......Both can be found in the menu...command prompt would be "terminal". I think screenshot can be done via "print screen" key and a screenshot dialog will appear or it can be found in the menu.

---

### Post by catagious on 2011-06-29
The Print Screen doesn't work with Linux.  Maybe an Asus laptop thing.  I did find out that GRUB wasn't installed on any drive.  Apparently wasn't on the CD either.  I'm going to try a few ideas.  If they don't work, I'll scrap Ubuntu and use something else.

---

### Post by jtarin on 2011-06-29
> **catagious said:**
> The Print Screen doesn't work with Linux.  Maybe an Asus laptop thing.  I did find out that GRUB wasn't installed on any drive.  Apparently wasn't on the CD either.  I'm going to try a few ideas.  If they don't work, I'll scrap Ubuntu and use something else.How did you find out Grub wasn't installed? You can install Grub by using the Live CD.

---

### Post by James! on 2011-06-29
Forgive me if I don't understand all of what the problem is (this is my first ever post on Ubuntu Forums). I am still a bit of Newbie as well, having only gone to Ubuntu a few months ago...

I had a similar problem installing a boot disk, and I had to run the ISO through the startup disk creator, and I had no problems afterwards... and since you stated that you BIOS was set to boot correctly, I think what I did may also be a possible solution for you.

---

### Post by catagious on 2011-06-29
> **jtarin said:**
> How did you find out Grub wasn't installed? You can install Grub by using the Live CD.
Followed the Help advise and ran a search.  Said no GRUB found but to type a command and it would install.  Still nothing.
I ran the same disk on a 4 year old HP laptop and installed with no problems.

---

### Post by catagious on 2011-06-29
> **James! said:**
> Forgive me if I don't understand all of what the problem is (this is my first ever post on Ubuntu Forums). I am still a bit of Newbie as well, having only gone to Ubuntu a few months ago...

I had a similar problem installing a boot disk, and I had to run the ISO through the startup disk creator, and I had no problems afterwards... and since you stated that you BIOS was set to boot correctly, I think what I did may also be a possible solution for you.
Love to hear it!  I just want to be able to run Ubuntu on other computers without messing up other hard drives.

---

### Post by amjjawad on 2011-06-30
Usually, or at least this is how I do it, GRUB2 should be installed in the MBR of the External HDD "specially" if the whole idea/point of installing Ubuntu on an External Media is NOT to mess around with the internal HDD.

As long as GRUB2 is installed in the MBR of the External HDD, your internal HDD is untouched, period.

How will this work?
As long as your External HDD is plugged in, BIOS set to boot from External HDD first then the internal HDD, GRUB Menu will show up and you can select whether to boot into Ubuntu or your previous installed OS on your machine.

Once you unplug your external HDD, everything will be back to normal and if you have Windows installed on your machine, GRUB2 Menu won't show up at all.

Now, either it's something wrong you have done through the installation process or it's your Graphics Card.

I would suggest to try one more time but be more careful with the steps.

[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
It's how to install Ubuntu on USB Drive but you can follow the same procedure. Just ignore the part that talks about Wubi.

---

