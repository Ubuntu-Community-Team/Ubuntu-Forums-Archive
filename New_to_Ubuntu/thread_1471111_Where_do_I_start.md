---
title: "Where do I start?"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by baldylocks on 2010-05-03
Hi all

I have a dead laptop (XP crashed)that I would like to convert and learn Ubuntu on. Please advise the best way to install - is it

1 Format hard drive
2 download Ubuntu onto desktop
3 copy across using pendrive/CD ?

What I don't know is how to get the laptop to load if I have wiped the hard drive, and will Ubuntu find the wireless router signal?

Thanks in anticipation....:confused:

---

### Post by LowSky on 2010-05-03
> **baldylocks said:**
> Hi all

I have a dead laptop (XP crashed)that I would like to convert and learn Ubuntu on. Please advise the best way to install - is it

1 Format hard drive
2 download Ubuntu onto desktop
3 copy across using pendrive/CD ?

What I don't know is how to get the laptop to load if I have wiped the hard drive, and will Ubuntu find the wireless router signal?

Thanks in anticipation....:confused:


Basically you have the right idea.

Ubuntu comes with a LiveCD mode, that you can use without using the hard drive if you like to try it without installing. And it will install to a wiped hard drive, as long as the hard drive is fine, and not the reason the computer went belly up with Windows.

As for the Wifi, well it gets better with ever new version of Ubuntu, I wont say yes it will work, but your chances are good. Its a good idea to have a Ethernet cable available just in case it does not, so you can can get the correct drivers if needed.

---

### Post by nothingspecial on 2010-05-03
If you don`t have a cd drive then number 3 is your best option - see [[COLOR="Magenta"]here[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick")

Ubuntu will format your hard drive for you when you install if you choose the "use entire disk" option when installing.

Most wireless cards should be detected and work straight away, some may need a little tinkering. As long as you have some way of accessing the internet, weather a wired connection or another machine - a quick question here or directed at Mrs google (or both) should have any wireless issues fixed in a jiffy.

---

### Post by Rex Bouwense on 2010-05-03
It is not as simple as copying.  When you download the ISO, the first thing that you must do is do an md5sum to insure that you got a good download.  See [https://help.ubuntu.com/community/HowToMD5SUM#Check%20the%20iso%20file](https://help.ubuntu.com/community/HowToMD5SUM#Check%20the%20iso%20file) and [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).  Then you have to make a bootable cd to transfer it to your laptop.  See [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation).  
It sounds complicated but it isn't.  Enjoy.

---

### Post by SweetShadow on 2010-05-03
All you have to do is download the ubuntu .iso (torrent method imho) and use Unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) to copy it on your usb flash drive.
Then plug it in the dead laptop, fire up, make sure it boots from the usb device you just inserted and clean install it/try it.Your choice.

---

### Post by TBABill on 2010-05-03
Just to tag onto the download iso, verify it with md5sum, write it to a blank CD or DVD (AS AN IMAGE!!!!), etc. Most importantly since you do not know if this machine will work well with Ubuntu or not, run the disk in Live mode, which means the machine will operate from the CD and install nothing. You do not have to get rid of Windows to try it out with the LiveCD. Then you can test out sound, wireless and whatever other configuration items are important to you before installing.
 
Always better safe than sorry, especially if you didn't make your Windows 7 recovery disks yet (unless, of course, yours came with them).

---

