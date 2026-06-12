---
title: "Well...not much"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by lile001 on 2009-05-09
Well...not much is happening with this Ubuntu install.  I saw an Ubuntu logo, a progress bar, then a pretty looking pink screen that has no text on it and doesn't respond to the mouse.  I take it that's a fail.

I have a new Dell computer, downgraded to XP, dual monitors, with two hard drives arranged in a RAID array, the system is literally out of the box.

I've been following the Ubuntu installation guide, but I'm afraid I'm stuck.   Completely new to Linux.

-Lawrence

---

### Post by abn91c on 2009-05-09
remove one of the monitors during setup, see If that helps

---

### Post by lile001 on 2009-05-09
> **abn91c said:**
> remove one of the monitors during setup, see If that helps
Remove as vn unplug, or somethvng geekier?

---

### Post by lile001 on 2009-05-09
> **abn91c said:**
> remove one of the monitors during setup, see If that helps
Remove as in unplug, or something geekier?

---

### Post by Sef on 2009-05-09
1) Remove as in unplug.

2) Does the Live CD work?

3) Instead of running the live cd or installing, go down to 'Check Disk for Errors' (or something similar.)

---

### Post by lile001 on 2009-05-09
> **lile001 said:**
> Remove as in unplug, or something geekier?Unplugged a monitor cable and tried running Linux without changing the computer, seems to run.

---

### Post by lile001 on 2009-05-09
> **lile001 said:**
> Unplugged a monitor cable and tried running Linux without changing the computer, seems to run.

in other words Live CD runs OK.

---

### Post by abn91c on 2009-05-09
> **lile001 said:**
> Unplugged a monitor cable and tried running Linux without changing the computer, seems to run.
you will be able to install now, then configure ubuntu for dual monitors later

---

### Post by lile001 on 2009-05-09
> **lile001 said:**
> in other words Live CD runs OK.

Ran install from within Windows an with one monitor unplugged.

After lots of very hopeful activiy, it now boots into something called grub, which is very helpfully described as a BAsH-like utility.  Failing to make any sense out of that, I hit esc, which leads to a series of menu.lst files, none of which grub can find.  I think that must also mean a fail.

---

### Post by lile001 on 2009-05-09
Disk tests OK, also MD5checksum OK

---

### Post by lile001 on 2009-05-09
during a live CD session I was able to run a hardware test and install a driver for my video card however still won't boot from Linux... just goes to grub.  Not understanding what that is leaves me stuck again.

---

### Post by Didius Falco on 2009-05-10
When it is at the Grub menu, what , if any, errors are you getting?

---

### Post by alanwalterthomas on 2009-05-10
I know grub as the little program that tells the computer which OS to boot. If you install from bare metal you'll hardly notice it. If you installed ubuntu on top of XP it should make it a boot option (at the bottom of the list). I think grub automatically picks the 1st one (ubuntu) after 10s if you don't change anything.
In grub you ought to see a list that looks something like this:
Ubuntu 9.04 (kernel version #'s here)
same as above but recovery mode
memtest (checks ram)
Other operating systems:
Win XP

Just use arrow keys to choose then press enter - worked for me.

But I never tried installing from within Windows. (wubi right?)
I pressed F12 after turning the computer on to choose to boot right from the CD & made a partition for ubuntu, then got rid of windows completely.

By the way, if you want to install ubuntu in RAID, I think you have to use the alternate install CD which isn't so user friendly. You'll probably want to open a separate thread for that if you don't find one that helps.

---

### Post by lile001 on 2009-05-10
> **Didius Falco said:**
> When it is at the Grub menu, what , if any, errors are you getting?

none that I can tell, just a grub prompt.

---

### Post by MaxVK on 2009-05-10
I'm not sure if this is relevant or not, or indeed how to fix it, but it might give others some ideas:

I get the same problem sometimes on a dual boot machine. If I boot into Ubuntu and do not mount the windows drive, the next time I try to boot into windows I see the grub menu, select the windows item and then get just a black screen with a prompt. Re-starting the computer again fixes this and I can then boot.

I'm guessing that its something to do with a drive not being mounted/un-mounted properly?

Unfortunately thats as far as I go, but maybe it will help someone come up with an idea.

regards

Max

---

### Post by mosaic2s on 2009-05-10
I have installed 9.04 from CD on a sony viao laptop - the person using it is amazed at the speed of booting and shutting down.

Did you try booting from CD instead of through windows?

---

### Post by 3rdalbum on 2009-05-10
What version are you using? You should be using 9.04.

---

### Post by Bölvaður on 2009-05-10
Lets begin with the basics.

Give us info :

What version of ubuntu did you install and how did you install it? (did you use wubi [inside windows] or live cd [normal]) Wubi doesnt give you grub but a simpler boot loader that kind of looks similar but still not.. make sure that you are indeed using grub.


What graphical card are you using? (if you are not 100% sure find the terminal under Applications &#8594; Accessories &#8594; Terminal and type "lspci | grep VGA")


Try fix :

If you get GRUB press E on ubuntu and add "xforcevesa" at the end of the boot command and press B to boot with this option. The change you made is not permanent and is 1 time only thing so no worry about screwing up.

alternativly you can type vga=791  (or any other number found in the table [here]("http://www.knoppix.net/forum/viewtopic.php?p=36777"))


If you managed to get graphic working by this you should log into ubuntu (perhaps with reduced resolution) and will be able to wait for the hardware to be detected and correct drivers found for you. Or you just go directly into System &#8594; Administration &#8594; Hardware Drivers and make a shiny green light next to the correct driver (you might need to guess if you dont want to google it... takes similar ammount of time).

If that worked you should be able to set up your monitors with nvidia-settings-manager or the one that comes with ati.. but that is a matter of another thread.

---

### Post by lile001 on 2009-05-10
[quote=Bölvaður;7250807]Lets begin with the basics.

Give us info :

What version of ubuntu did you install and how did you install it? (did you use wubi [inside windows] or live cd [normal]) Wubi doesnt give you grub but a simpler boot loader that kind of looks similar but still not.. make sure that you are indeed using grub.


What graphical card are you using? (if you are not 100% sure find the terminal under Applications &#8594; Accessories &#8594; Terminal and type "lspci | grep VGA")


I installed 9.04.  First, I tried it directly from the CD, which froze at the first splash screen.  Then I ran Live CD, which worked, but I didn't choose to install at that time.  Third, I tried to install from within Windows, which I think has now made a mess of things.  I'm tempted to pull out the Windows CD and wipe the computer clean - there are Ubuntu files and Windows files on the same partition, and Windows spends a lot of time complaining about "corrupt files" A.K.A. fiels that are valid under another operating system.  What a mess! 

If I told the install to use Safe Graphics Mode, i was able to get a little farther,and am stopped cold at hard drive partitioning.  You see, I have a RAID hard drive, and I don't know how to partition anything, let alone a RAID drive under an unfamiliar operating system.

I've been looking at this document [https://help.ubuntu.com/9.04/installation-guide/i386/non-debian-partitioning.html](https://help.ubuntu.com/9.04/installation-guide/i386/non-debian-partitioning.html) to try to figure out how to partition a RAID drive, thinking that I'm probably going in a completely wrong direction.  I thought RAID was for cockroaches.......

---

### Post by Bölvaður on 2009-05-10
Ah Wubi could be great for beginners if instructions are followed.... like defragging your hard disk which is the curse of the inferior.. things... lets not go into it as there is.. lets not go into it.
Lets just say that you got into trouble because you didnt defrag :)


I would assume you wouldn't get into any troubles if you'd first install windows, then ubuntu (with xforcevesa which brings the mighty "safe graphic mode") and install the propitiatory video drivers. And that's it.

Btw before installing windows put the live cd in and set up the partitions with gparted (gnome partition editor) and make 1 ntfs partition, 1 ext3 or ext4 and then a small (like 300 mb) swap partition.... this is a simple setup and in the future I'd advice to have a special data partition but as you are still probably going to give windows big space on the hard disk this might be the way to go for you... even though it is inferior to having a special data partition.

---

