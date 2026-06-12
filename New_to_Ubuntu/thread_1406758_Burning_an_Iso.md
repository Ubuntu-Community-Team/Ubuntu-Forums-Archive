---
title: "Burning an Iso"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by daniell59 on 2010-02-14
I want to put Ubuntu 9.10 on a flash drive. I already downloaded it. I have no idea how to burn an ISO in Ubuntu 9.10. My ultimate goal is to install Ubuntu on to my laptop that does not have an optical drive.

Any assistance will be appreciated.

---

### Post by phillw on 2010-02-14
Hi, 
Follow the steps here -->  [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

if you then use the CD to boot into "Try without altering my computer" mode, Simply select System --> Administration --> Startup Disk Creator.

As a quick note, do not allocate all the free disk to persistance - leave a a little unused on your usb drive. For whatever reason, the seem to get 'upset' if you allocate it all (I'm guessing it's for any updates to the Kernel that would need extra room).

Regards,

Phill.

---

### Post by kio_http on 2010-02-14
Under windows you can use a program called cdburnerXP and under OS X you can use built in Apple Disk Utility.

Note: It would be much faster to install from a pen drvie or SD card. To achieve this use a program called Unetbootin. It will make a the removable disk bootable with the Ubuntu installer.

Note: In Windows 7 and Windows vista you can boot an iso from Hard disk by adding an entry using a program called Easy BCD (2.0 beta version 1.0 doesn't have that feature)

---

### Post by bumanie on 2010-02-14
With whatever burning software you use, you need to choose the option to burn "as an image" - do not choose a data cd. Once you boot from the live cd, you should be able to go System --> Administration--> USB Start up Disk creator and have ubuntu put on the flash drive for you.

---

### Post by phillw on 2010-02-14
I think that [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)  about covers every eventuality on burning :p

Phill.

---

### Post by phillw on 2010-02-14
> **bumanie said:**
>  System --> Administration--> USB Start up Disk creator 

I'll have to remember it is slightly differently named in 9.10 -- oops !!!

Regards,

Phill.

---

### Post by lyall on 2010-02-14
have you tried ***USB Startup Disk Creator*** ?

check System > Administrator > USB Startup Disk Creator

if it is not there go to Synaptic Package Manaager and look for 
usb-creator-common and usb-creator-gtk and install them

also see the doc at for more info
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick") 

and for USB Installation Media see
[https://help.ubuntu.com/community/USB%20Installation%20Media]("https://help.ubuntu.com/community/USB%20Installation%20Media")

I have used to to make a bootable USB for Ubuntu, works great

good luck and have fun learning

---

### Post by daniell59 on 2010-02-14
Thanks to all for you informative replies.
I burned an ISO on a CD. I booted off it and it worked. Is this a problem?
It took a really long time for it to boot up from the CD.

---

