---
title: "What am I doing wrong?"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by Mike K on 2009-07-03
I have decided to start using Ubuntu(*) - convert from CentOS to Ubuntu on my Dell Laptop and get Ubuntu on my newly-acquired Acer Netbook. Here is what I did:

- went to [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook) where per instructions I created a bootable USB flash drive from an image ubuntu-9.04-netbook-remix-i386.img using
"dd if=/path/to/downloaded.img of=..." command

- The netbook proved defective (bad hard drive), but booted from USB successfully, presenting me with the menu:
> Try Ubuntu Netbook Remix without any change to your computer
Install Ubuntu Netbook Remix
Check disk for defects
Test Memory
Boot from first Hard DriveWhen I tried the first option, "Try Ubuntu Netbook Remix without any change to your computer" I got into a simple text shell:
> BusyBox v1.10.2 ... built-in shell (ash)
Enter 'help' for list of built-in commands.
(initramfs) I expected to get a graphical interface and such, not a limited ascii shell.

Just to make sure, I booted my Dell Laptop from the same USB and got the same shell. So it's not the smaller memory or broken HDD.
 I did not find any further instruction of how to launch graphical UI from the shell.

I am going to try LiveCD on my Laptop shortly but what am I doing wrong with the USB stick? From reading I was sure that one can get a fully-functioning system this way on any PC that can boot of a USB device, without installation, etc?... 

(*) curious that on Ubuntu forum the spellchecker would not recognise the word... :)

 Mike

---

### Post by Ocxic on 2009-07-03
double check the md5sum of the image, a corrupted download could cause that.

---

### Post by snakeman21 on 2009-07-03
I see this problem a lot with the Acer netbook.  I had the same problem with the same netbook, too.  The issue is that when installing Netbook Remix to the Acer Aspire One, you can NOT use the USB Startup Disk Creator.  For whatever reason, it doesn't work.  All you get when your done is a command line interface, as you've seen.  Instead, download USB Imagewriter and use that.  Trust me, it works.  

Edit:  and by the way, it's not the ubuntu forums that check your spelling, it's your web browser.  Ubuntu is not in the English language, so it will "red-line" it.

---

### Post by Mike K on 2009-07-03
The md5sum of the image was fine. Whether it got corrupted while transferring to USB...
I will try to create the second stick...

Heck... It seems to work... Strange - that it would boot me into some kind of a usable shell without any indication that it was not a normal operation...

Thanks. I will report further on my progress.
 Mike

---

### Post by snakeman21 on 2009-07-04
As I said, use USB Imagewriter.  This is the only way to install netbook remix from a USB to the acer aspire one.  If you'd like a tutorial, you can find one [HERE]("https://help.ubuntu.com/community/Installation/FromImgFiles#Ubuntu").  Scroll down about halfway to the section about installing from ubuntu.  You will see the Imagewriter logo.
I know this works, because I dealt with the same problem.  Good luck!

Edit:  After you do this, you can boot the usb stick normally.  Once again, I'm not sure why it does this, as you can use the USB startup disk creator for the Jaunty desktop release, but not for Netbook Remix.

---

