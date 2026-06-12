---
title: "Ubuntu on Dell 2400 Need help"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by jason65483 on 2010-01-07
I also have a Dell dimention 2400 I installed Ubuntu after my xp os crashed for the 100th time. I found Ubuntu online. Well I didn't have any blank disks to copy the *.iso image too.
so I went back online and found a .iso Buster called (ISOBuster) to change the Image to useable software that could be ran from my hard drive. The good news is that I had no problem installing ubuntu and running it Bad news is I can not muti task very well Meaning I can't do more then one thing at a time without my system freezing up on me. Also most of the time it takes about 10-20 sec after I click on a app before it starts to load or before it pops up on the screen. now I am very new to linux I mean like only 3 days new so I know really nothing about it at all. I need Help big time. Is there anything I can do as far as apps, software, ect. to speed up ubuntu and keep it from freezing up all the time. Now I have found on some forums talking about tweaks that can be done to open up a bottle neck so ubuntu uses more ram then disk space. the thing is I have no idea on how to do that. something about sudo (what the heck is sudo? where do I find it in my system? and then when i do fine it How do I use it?) I know what everyone is saying buy more Ram will I'm broke and don't have the money for more ram. Or money for a book telling me how to program linux for dummies. Can anyone help me?  P.S. I really hate windows. do not want to go back.

---

### Post by Temposs on 2010-01-07
What are the specs of your current machine?

Which programs are you trying to use?

What kinds of tasks do you like to do with your computer?

---

### Post by melrokz on 2010-01-07
Just curious, How did u install Ubuntu using isobuster???

---

### Post by Temposs on 2010-01-07
Oh, what did you do with that ISO buster program? Did you just have it put Ubuntu on your hard drive in a bootable fashion?

Did you go through the Ubuntu install process, or are you just running the "Try Ubuntu without any change to your computer"?

---

### Post by Temposs on 2010-01-07
Also, did you know that you can install Ubuntu very easily with a usb flash drive instead of a CD? As long as you have a flash drive that is at least 1GB, you can do it. From Ubuntu, you can go to System->Administration->USB Startup Disk Creator.

---

### Post by jason65483 on 2010-01-07
the isobuster   I have two hard drives c: e: I installed isobuster in windows on C:\ click and dragged the *.iso file image to the program. then told Isobuster to convert the iso image to useable files that can be ran from my Hard disk. Saved the new files on e:\   Then while still in windows I opened my e:\ drive and click on the install file told it to install ubuntu on e:\   ran install until it was time to reboot. I rebooted the computer then I had 2 options pop up  Asking me what to run  (windows xp) or (ubuntu) I ran uduntu and finshed with the install

---

### Post by Temposs on 2010-01-07
Ohhhhh Wubi. Always with the Wubi. Every time people have weird install or universal problems with Ubuntu, Wubi seems to be the culprit...oy

Do you still have the e:\ with the iso files on it in tact?

EDIT: And is your e: actually a different hard drive?

---

### Post by Temposs on 2010-01-07
The problem with installing Ubuntu from within Windows is that it's not actually a standard Ubuntu install. It stores Ubuntu in a single file in Windows and sets up your computer so you can boot to Ubuntu or Windows.

If you want to do a proper install without a CD, you should use a flash drive. Do you have one?

---

### Post by jason65483 on 2010-01-07
before I installed ubuntu I copyed the files to my 2gb removable flash drive. yes I do have 2 hard drives  one 80gb and one 40gb windows is on the 40gb C:\ and ubuntu is on the 80gb e:\    as far as the files still being on e:\ I do Not know for sure I really don't think so becouse in the install it said something about removing Casper

---

### Post by Temposs on 2010-01-07
Can you use your 2gb flash drive to make a new Ubuntu installer?

From within Ubuntu, download the standard Ubuntu 9.10 iso file, if you're not already able to access it.
(EDIT: If you use the torrent, it'll download a lot faster :-) [http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt) )

Go to System->Administration->USB Startup Disk Creator

Click "Other" under CD Drive/Image and select the iso file.

Select your USB drive as the device, and then click "Make Startup Disk".

When you've done that, you need to restart the computer, if you don't have the USB disk set to boot first, go into your BIOS and change the boot order so that the USB drive will boot first.

Then you can do a regular Ubuntu install.

---

### Post by jason65483 on 2010-01-07
?

---

### Post by jason65483 on 2010-01-07
do i need to format E:\ again or un-install ubuntu 1st

---

### Post by Temposs on 2010-01-07
It depends. Do you want to keep Windows installed?

---

### Post by Sylslay on 2010-01-24
Try Ubuntu 8.04 , and instruction from step by step

[http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-tutorial/](http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-tutorial/)

or burn iso cd with [http://www.freeisoburner.com/](http://www.freeisoburner.com/)
Acually Ubuntu is only Os with I can run on my laptop,

other are very difficult to boot,
I fanud that works from live CD

Knoppix until ver 4, none above

gentoo 2008, not 2009

Debian 5,

Fastest system to use were Slax , whan whole loaded to RAM memory,
and ubuntu 9.04 is rocket with UXA intel grapic driver, xorg-edgers,,

most problem are couse by xorg , when its start.

---

