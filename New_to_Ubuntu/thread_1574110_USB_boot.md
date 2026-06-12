---
title: "USB boot??"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by Autodave on 2010-09-13
I downloaded the netbook edition and copied it onto my USB stick.  I have the option to boot to USB, but it won't boot to the stick.  What am I doing wrong?

---

### Post by daniell59 on 2010-09-13
Did you go into the BIOS and make it the first choice to boot off?

---

### Post by Autodave on 2010-09-13
> **daniell59 said:**
> Did you go into the BIOS and make it the first choice to boot off?

Yes.  But, it boots up to the old operating system.

---

### Post by amjjawad on 2010-09-13
> **Autodave said:**
> Yes.  But, it boots up to the old operating system.

There are two options you need to change:

1- First Boot Device = Should be [USB-HDD]

2- Hard Disk Boot Priority = Should be [USB-HDD0]

Just double check these two options :)

---

### Post by wilee-nilee on 2010-09-13
How did you load the thumb?

There is a f-key or esc or some key that will get you to a boot from menu outside of bios. Try getting there and seeing if when you choose the USB it boots. My f-key prompt is f12 this brings up a boot from menu. You just need to start hitting the key as soon as you hit power up until you see a prompt on the screen. Sometimes this option is turned off in the bios as well, so check for that if needed.

Personally I never muck around with the boot in bios as this key prompt will let you boot what you want. I would change the order if I needed a default, but just to boot a thumb or any individual media is pointless, to me, not necessarily a shared opinion with everybody.

---

### Post by Autodave on 2010-09-13
> **wilee-nilee said:**
> How did you load the thumb?

There is a f-key or esc or some key that will get you to a boot from menu outside of bios. Try getting there and seeing if when you choose the USB it boots. My f-key prompt is f12 this brings up a boot from menu. You just need to start hitting the key as soon as you hit start until you see a prompt on the screen.

Personally I never muck around with the boot in bios as this key prompt will let you boot what you want. I would change the order if I needed a default, but just to boot a thumb or any individual media is pointless, to me, not necessarily a shared opinion with everybody.

I plugged the thumb drive in and started machine.  Hitting the ESCAPE key allows me to chose the boot device. That did not work.  Went into the BIOS and set the thumb drive as first boot option.  That won't work either.

---

### Post by wilee-nilee on 2010-09-13
> **Autodave said:**
> I plugged the thumb drive in and started machine.  Hitting the ESCAPE key allows me to chose the boot device. That did not work.  Went into the BIOS and set the thumb drive as first boot option.  That won't work either.

So it would be helpful to know how you loaded the thumb and what your seeing as errors, when you try to boot.

There could be a number of scenarios here, a bad ISO MD5SUM,
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Just the thumb loader not working correctly. It may have just been a bad load to the thumb. A usb that has some firmware like a sandisk=U3. So the more you tell us will be helpful.

So generally when I use a thumb in this manner I format it with gparted, then install to it using either Unetbootin, or the native startup disk creator in Ubuntu.
You can format the thumb with a right click in Windows to fat and use Unetbootin to load it if you need to.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
This is in Linux already you just have to install it from the command line, synaptic, or the software center.

---

### Post by gerald3092 on 2010-09-13
> **Autodave said:**
> Yes.  But, it boots up to the old operating system.
Did you click Save Settings before exiting ?

---

### Post by gerald3092 on 2010-09-13
> **daniell59 said:**
> Did you go into the BIOS and make it the first choice to boot off?
...and did you leave the usb drive inserted to reboot ? Or did you taqke it out and then reboot ?

---

### Post by oldfred on 2010-09-13
When you said you copied the ISO to your flash drive, you did not just copy the ISO did you? You normally have to install it with unetbootin as wilee-nilee suggests.

Now I do copy but have grub2 installed and have modified my grub.cfg to directly loopmount an ISO, but that is not as common.

---

### Post by gerald3092 on 2010-09-13
> **Autodave said:**
> I downloaded the netbook edition and copied it onto my USB stick.  I have the option to boot to USB, but it won't boot to the stick.  What am I doing wrong?

:popcorn:
Not sure of your terminology and to clarify - the problem may be that you have a simple usb media card. You have to have the usb DRIVE - not a usb media storage card. This is probably your actual problem. 

I have just used this procedure, got a 4 gig usb drive ($20 US or less) to go the whole distance of wiping windows and installing Ubuntu Netbook - but of course you can use it as you wish as the "Live Distro" which allows testing Ubuntu out from the usb drive. (little usb stick that inserts in usb side port).

PS.... In BIOS setting up the usb drive as first boot priority and reboot - if you may do what I did, to install Ubuntu and wipe Windows altogether, the reboot may show the black screen with a list of failures. Oops... go back into BIOS now and set the normal drive as the first boot priority. Good to go. With the appropriate USB Drive (2 or 4 gigs) it is a piece of cake you will find.

---

