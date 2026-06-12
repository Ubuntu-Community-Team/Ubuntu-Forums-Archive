---
title: "UNetBootin infinite loop"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by sirgerbil on 2011-06-19
Hi again.

so courtesy of this forum, i managed to get the windows ISO file and I managed to put it on a USB with UNetBootin. However (and apparently, this is a common problem) when I select boot from USB device in the startup menu, and UnetBootin gives me a screen, it has a countdown saying "Automatic Boot in x seconds".... it counts down from 10 to 0, and restarts from 10 when it gets to 0. There is also a menu saying "select boot option," With default as the only option. However, when I press enter, the "automatic boot" loop just starts from 10 again. In fact, when I press ANY key, the loop restarts from 10.

I'm almost there... how do I fix this?

---

### Post by Rubi1200 on 2011-06-19
Hi and welcome to the forums :-)

Check the integrity of the image:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, check that BIOS is enabled to allow booting from the USB as first priority.

Try a different USB port and/or USB stick.

Hope this helps.

---

### Post by sirgerbil on 2011-06-19
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Check the integrity of the image:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, check that BIOS is enabled to allow booting from the USB as first priority.

Try a different USB port and/or USB stick.

Hope this helps.
I gave this a shot. Unfortunately I'm still getting the infinite countdown from 10. 
Are there any other programs that can write a Live USB that I can get on Ubuntu? Maybe I'll give those a try instead.

---

### Post by Rubi1200 on 2011-06-20
Haven't done it this way, but this site also has tutorials for USB installs.
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by sirgerbil on 2011-06-20
> **Rubi1200 said:**
> Haven't done it this way, but this site also has tutorials for USB installs.
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
I'm trying to boot Windows 7 From Ubuntu.

Don't think I made it clear in the original Post, so I don't blame you.

---

### Post by RenThaL on 2011-11-19
Did you get any solution? 
I get this: "You need to use NTFS, and not FAT32, for windows 7 to work through Unetbootin."

but unetbootin won't recognise my device ntfs formated
Thanks

---

### Post by beew on 2011-11-19
Who told you that Unetbootin works with Winodws ISO?

From their website
> UNetbootin allows you to create bootable Live USB drives for** Ubuntu, Fedora, and other Linux distributions** without burning a CD.
As far as I know there is only one guy who cliamed to be able to use unetbootin to make a W7 live usb that works on his blog(all other "turorials" were written by guys citing him without actually doing that themselves) The first comment on the guy's blog post  was "What are you smoking man??!"


**Edited:** Also where did you get the idea that it is even possible to run Windows 7 on a usb? MS provides an iso, from what I understand, it is for people to upgrade from Vista on netbooks that don't have a CD drive. The live usb can only be created with MS's tool and it has to be installed on the Vista machine to be upgraded, the usb thus created would only work on that machine, and only for installing/upgrading; and you are supposed to make only one such usb.

---

