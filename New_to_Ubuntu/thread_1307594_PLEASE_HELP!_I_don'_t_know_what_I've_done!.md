---
title: "PLEASE HELP! I don' t know what I've done!"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by adriang78 on 2009-10-31
OK, so I have an Acer Aspire One.
I was trying last week to update my java to version 6 but failed.
So this week instead I tried updating to version 9.10.
I read on a thread that to simply update I must first update the the old version.
When I tried installing all the updates my mouse and buttons have stopped working. The keyboard works but that's it. Also, next to the Internet signal,at the top of the screen to the left of it, it now says "No Indicators".
Half of my favourites have gone, other menus are half empty and when I scroll through the menus it takes forever and icons are overlapping each other.
 
I tried, after this, to install 9.10 from a USB and that doesn't work either.
 
Can someone offer me any advise please?
 
Thank you

---

### Post by humphreybc on 2009-10-31
Okay hang on, just to clarify I'll ask some questions.

> 
I read on a thread that to simply update I must first update the the old version.

What do you mean?

> 
When I tried installing all the updates my mouse and buttons have stopped working. The keyboard works but that's it. Also, next to the Internet signal,at the top of the screen to the left of it, it now says "No Indicators".

Was this straight after the upgrade, or was this after rebooting? Do you have automatic login? Have you got a USB mouse to try instead of the touchpad?

> 
I tried, after this, to install 9.10 from a USB and that doesn't work either.

Did you completely re-format your partition and install from clean? Did you choose any irregular options during install? Did you use the normal desktop installer, or the alternate CD, and 32 bit or 64 bit?

Also, is this Ubuntu, or Ubuntu Netbook Remix?

Thanks

---

### Post by adriang78 on 2009-10-31
Hi, thanks for the quick rsponse.
On the STICKY in the forums for udating it says: "
Be sure that you have all updates applied to Ubuntu 9.04 before you upgrade. 
THe mouse stopped working after a restart after updating the older version.
Unfortunatley I don't have a separate mouse to use.
Lastly, I formatted a USB, used unetbootin to create a bootable USB, put that in my netbook and restarted the machine. But it just brought me straight back to what I had before. So I guess I didn't partition the disc etc. I am using Netbook Remix.
Can't think of anything else to tell you.
Thanks, sorry for the bullit points, can't get them off!!

---

### Post by humphreybc on 2009-10-31
Ah okay I get what you mean regarding updating.

Put the pen drive in and restart the computer, when the BIOS shows up, change the boot order so that you boot off the USB drive first. 

Then choose to do a disk check (to make sure your installer isn't corrupted when you created the bootable USB) and then try re-installing UNR from scratch and see how you go.

It's pretty late over here so i'm off to bed, good luck! If you run into problems again, post in here, someone will be able to help you. I'm sure we can get it working, I've heard Ubuntu runs great on Acer Aspire Ones!

---

### Post by adriang78 on 2009-10-31
> **humphreybc said:**
> Ah okay I get what you mean regarding updating.
 
Put the pen drive in and restart the computer, when the BIOS shows up, change the boot order so that you boot off the USB drive first. 
 
Then choose to do a disk check (to make sure your installer isn't corrupted when you created the bootable USB) and then try re-installing UNR from scratch and see how you go.
 
It's pretty late over here so i'm off to bed, good luck! If you run into problems again, post in here, someone will be able to help you. I'm sure we can get it working, I've heard Ubuntu runs great on Acer Aspire Ones!
 
 
I'll give that a try.
Thanks very much for your help.
Much appreciated

---

### Post by 3rdalbum on 2009-10-31
You need to change the BIOS boot sequence setting so that your USB flash drive is booted from first. When you boot without a flash drive plugged in, the BIOS will go back to NOT looking for a flash drive to boot from; in other words, you need to change the setting every time you want to boot from flash drive.

Are you sure you didn't hit the keyboard combination to turn off the trackpad? It's the "Fn" key and the little icon of a finger in a square; it's on one of the F keys, probably F6.

---

### Post by adriang78 on 2009-10-31
> **3rdalbum said:**
> You need to change the BIOS boot sequence setting so that your USB flash drive is booted from first. When you boot without a flash drive plugged in, the BIOS will go back to NOT looking for a flash drive to boot from; in other words, you need to change the setting every time you want to boot from flash drive.
 
Are you sure you didn't hit the keyboard combination to turn off the trackpad? It's the "Fn" key and the little icon of a finger in a square; it's on one of the F keys, probably F6.
 
OK, just the pad working again, booted from the USB to install 9.10, and now I've got to stage FIVE (WHO ARE YOU?) and now it won't let me type anything or click on the boxes, but it will let me click back.
 
Starting to wish I hadn't bothered trying to upgrade:(

---

### Post by drseuk on 2009-10-31
Hi Adrian,

Apologies for the delay in replying - humphreybc asked me to help you about 30 minutes ago (as I've just installed Ubuntu on an Acer Aspire One for a friend with no problems) but I've currently got 'net connectivity problems :-(

This'll work:

1. Back up all your data somewhere safe.

2. If you have access to a machine with a CD drive, download and boot from a Live Ubuntu (not Netbook Remix) 9.10 CD.

3. Under System->Administration, launch the USB Startup Disk Creator.

4. Insert your (blank) USB stick which will usually appear as /dev/sdb - but you need to check this.

5. Use the USB Startup Disk Creator to copy an image from the .iso you've downloaded to the USB stick.

6. If / when if baulks, it means you need to wipe the stick first to get rid of the vfat filesystem on it (this is arguably a bug in the USB Startup Disk Creator).

7. Check (carefully!) whether the USB stick is on /dev/sdb (use mount and df)

8. Create the image

9. Put the stick in a USB socket on your Acer Aspire and power it up.

10. Press F12 and choose to boot from the USB stick. This will seamlessly boot Ubuntu 9.10 Live.

11. Double-click the Install and enjoy :-D

I'm around today so get back to me here if you need any further help.

---

### Post by drseuk on 2009-10-31
Hi again Adrian,

Experience says that you're better off doing a completely fresh install rather than trying to upgrade - this is generally true of all operating systems.

(Whilst the same is most definitely true of Ms Windows), I hate to say it but upgrading Ubuntu can still be a bit hit and miss - a single wrong click or two when you're asked whether you want the existing file or the package maintainer's version can make weird things happen.

Unless you know diff and friends and understand config files and the details of the packages being upgraded, a full fresh install followed by restoring your data is always a safer bet IMHO.

---

