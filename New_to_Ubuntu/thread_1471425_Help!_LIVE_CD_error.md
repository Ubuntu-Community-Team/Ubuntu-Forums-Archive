---
title: "Help! LIVE CD error"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by frillybob on 2010-05-03
So whenever I try the live cd I get a bunch of loading then it freezes. It says random stuff with this always on the outside []! I have spent almost 20 hours on it. I'm on windows 7 laptop. I need you to guide me through step by step I've tried live cd and flashdrive. I do see the start up of the purple thing then it goes into that strange mode! HELP!!!!!
P.S. I want to dual boot!

---

### Post by yozgoesdigital on 2010-05-03
Without more information about you system it is unlikely people can provide you with a proper answer. So what can you tell about your brand of laptop, brand video-card etc?
Is there always the same text when it hangs?

---

### Post by spiky001 on 2010-05-03
did you do a md5sum check on the downloaded iso then when you burned it check again, also did you burn it at slowest speed?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by spydeyrch on 2010-05-03
I usually will ask for the basic info of your system:

CPU
RAM
GPU
HDD
ODD
Brand Name
Model

Info like that is always a huge help to start a resolution to an issue. Let us know and we will see what we can do.

-Spydey :P

---

### Post by frillybob on 2010-05-03
CPU- AMD-Athlon(tm) II Dual-Core M300 2.00 Ghz
RAM- 3 gig
GPU????
HDD- 300 gig
ODD?????
Brand Name- Toshiba Satilite
Model- L505D-S5983

---

### Post by KirbySmith on 2010-05-03
While waiting for more specific help, you might try starting the live cd, and at the menu screen click F4 to get to another set of menus that includes safe video mode.  Highlight that, click return, and then back at the main menu run the live cd.

kirby

---

### Post by alexanda on 2010-05-03
> **spiky001 said:**
> did you do a md5sum check on the downloaded iso then when you burned it check again, also did you burn it at slowest speed?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Spiky's questions deserve to be asked again.

Also, have you tried using the Live-CD on another computer to see if it boots up okay?

---

### Post by frillybob on 2010-05-03
Ok, I tried it on another pc this one windows xp with 512 ram cmpared to my 3 gig and it works! WHat do I do now? I used the toshiba image burner which didn't give an option to burn  speed at but apperently there is nothing wrong with the disk. I also  checked it with that thing and no error

---

### Post by spydeyrch on 2010-05-03
> **frillybob said:**
> Ok, I tried it on another pc this one windows xp with 512 ram cmpared to my 3 gig and it works! WHat do I do now? I used the toshiba image burner which didn't give an option to burn  speed at but apperently there is nothing wrong with the disk. I also  checked it with that thing and no error

When you say you "checked it with that thing", what do you mean exactly? Did you check the MD5 SUM, the burn speed, or safe mode?

Can you at least bet to the options menu off of the live cd? What I mean by that is, when you insert your cd and boot from it, can you get to the menu that gives you a few options such as: Try this cd out without .......; install this cd .......; check cd for errors .........; run memory test .........; etc. Does that make sense? If you can get to that menu, try to run the "check this cd for errors" and see if it come sup with anything.

Your GPU would be your graphics processing unit, or in other words, your video card.
Your ODD would be your Optical Disk Drive, or in other words, your cd/dvd drive.

:D

Also, how old is your computer, do you have access to a working computer with internet connection, and do you have a usb flash drive with at least 2GB of space on it? I am just thinking of alternative methods here. :KS

-Spydey :popcorn:

---

### Post by colinwhipple on 2010-05-03
1.  Use a boot option of acpi=off.
2.  Look in this message thread for help:

[http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d](http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d)

Colin

---

### Post by frillybob on 2010-05-03
I have a 2gig flash drive, made it bootable and got the same thing. I checked it with md5sum. I have a cd/dvd read/write.ATI Radeon™ 4100 Graphics with dynamically allocated shared
graphics memory And I use to be able to get to the start Ubuntu without starting but when I would click on anything it would do what it is doing to me now! Bought in December 2009! Here is the technical specs [http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_L505D-S5983.pdf](http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_L505D-S5983.pdf)

---

### Post by spydeyrch on 2010-05-04
Ok, so I am assuming that you still have windows 7 on it. I am going to have you try a few different things so that we can try to get an idea of what is going on. Some of it might seem repetative or you might have already tried it but it will be slightly different, so please just bare with me and have a little patience. :) 

We need to use that usb flash drive because buring a cd will just take too long and it is a waste of a perfectly good cd. I want you to use either UNetBootin or the Universal USB Installer from pendrives, google it if you need to find it.

I would like you to download Knoppix,. making sure it is the x32 version (i386), and using unetbootin or the universal usb installer, "burn" the knoppix.iso to the usb flash dride (ufd). Try to boot off of it two different ways: (the reason I want you to try this is because there was a machine that I had that would not boot off of a live cd nor a usb if it contained ubuntu. But it did boot off of knoppix and a few other linux distros. I just need to see if this is the case with yours too.)

1.) change the boot sequence in your BIOS to boot from first removable storage devices (might just be called USB, mine says removable storage devices), second optical drive, third hard drive. save your changes and shut down the machine. insert that usb stick in to an available usb slot, make sure there are no other usb connections being used. start the computer. it should boot from the ufd. once you see the usb's menu come up, you should select default and hit enter then let knoppix load. if it boots into your hard drive and therefore windows, restart your computer and try option 2.

2.) in your bios change your boot order to go first optical drive, second hard drive, third removable storage drive. save your changes and shut down the machine. insert the usb, turn on the machine and press the boot selector key. On my machine it is F8, on some machines it is F12, yours may be different. Typically during post it shows a few options such as: press DEL to enter bios, press F8 to enter boot choice menu, press ALT+F2 to flash bios, etc. etc. So look for yours during POST and press it. Select the usb storage device. once the usb's menu comes up, select default and hit enter. you should get into knoppix that way.

If none of those options work for you, go into your bios and look at how your drives are being seen as. What I mean by that is, because your HDD is a SATA drive, your bios can use it in either IDE mode or AHCI mode. I know that for me, when trying to boot off of a live CD or usb, if I have to have my HDD in one mode or the other (I don't remember which) because if I don't, it just spits out lines of code during the boot of the live cd/usb and they are usually surrounded with the [brackets], like you mentioned before. So that may be the issue. Look at it. The only thing is, that if they are currently in IDE mode, and you switch it to AHCI mode, then your windows system wont boot because the AHCI mode drivers weren't installed during installation of your windows system. Does that make sense? It can be a big hassle! The only way that I was able to get around it without having to switch modes was to not use the live cd but just do an install. For some reason that worked for me, if I didn't want to change my HDD modes via the BIOS.

Hopefully all that makes sense. If it doesn't, please let me know and I will see if I can clear it up a little. Good luck and report back with any results.

-Spydey :D

---

### Post by frillybob on 2010-05-05
Ok, thanks a lot........ I'll try that AFTER I GET WINDOWS Working it had nothing to do with Ubuntu it just crashed after update. The thing is when I restore and rewrite all partitions it goes back to the old software so I have to update it. It's worked fine before I wonder why now.... I'm thinking of just keeping a back-up of win 7 and going all linux! What do you thinkl!

---

