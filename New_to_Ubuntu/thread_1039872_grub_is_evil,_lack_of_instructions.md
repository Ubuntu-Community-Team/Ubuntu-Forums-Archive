---
title: "grub is evil, lack of instructions"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by downinit_xyz on 2009-01-15
I downloaded the disk for unbuntu, burned it and ran it in my computer (XP).  The disk image seems to be ok, the file size is correct, and it gives me 3 options for how to install.  After following the option to help me reboot, since my computer would not boot off the disk otherwise, as soon as I reboot and select 'unbuntu' from the list ,it automatically pulls up a 'grub>' prompt. 

I have searched for hours on just what exactly I am supposed to enter for this prompt but everything I have tried does nothing,  I have tried all sorts of combos from the options that come up for 'tab' and 'help', and none of them will do anything.  From everything I have read, there is no mention of this step on the install instructions, so is there a problem with my disk, or is this just some obvious oversight that no one bothered to mention how to get past.  

Please tell me that either I should never see this screen at this point (my disk if faulty) or tell me what I am supposed to type for the 'grub>' prompt.  I am on the verge of throwing this computer down the trash chute along with any desire I ever had to try using Linux.  
Thank you

---

### Post by Ocxic on 2009-01-15
No, you should never see that screen, try re-burning the disk at a lower speed and re-installing.

---

### Post by albinootje on 2009-01-15
> **downinit_xyz said:**
>  After following the option to help me reboot, since my computer would not boot off the disk otherwise, as soon as I reboot and select 'unbuntu' from the list ,it automatically pulls up a 'grub>' prompt. 


Did you set up the BIOS of your machine to boot from cdrom ?
Or did you press F12 or F8 to get a menu to let you boot from cdrom ?
Please try that first.

And which cdrom image did you download and what program did you use to burn it ?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

For the installation cdroms it's indeed important to burn them at lower burn speed, and to verify the correct download.
Check the md5sum, and/or check the cdrom with the verify option if the Ubuntu cdrom offers that option.

---

### Post by hyper_ch on 2009-01-15
I fail to understand what happens, what works and what you did...

---

### Post by igknighted on 2009-01-15
Is this something you see after install?  Or when you try to boot the liveCD?

That grub prompt should only be seen if grub is installed but not configured.  Since the liveCD is preconfigured to boot itself, if it is on the CD then you should burn a new disk, it is bad.  If you see it on an installed system, chances are something went wrong during install (either a bad disk, or something really weird and fluky).

---

### Post by downinit_xyz on 2009-01-15
The 'grub' prompt appears as soon as I select 'ubuntu' from the boot list on start-up.  

Should I burn the file I downloaded exactly as it was received? Since the file came as a rar file (or at least it is automatically opened in winrar), I assumed I had to extract it first before burning, since that is what I usually have had to do with rar files in the past.  The burn mentioned above was with the files after being extracted.  I really wish the instructions would be a little more specific, it seems like they just glaze over some of the minor details since the people who wrote this have probably done dozens of installs already.

Thanks for any assistance. I have been using much more intuitive OS's (usually Apple since I can't stand windows) since the mid 80's, and if DOS was still the only option, I would have never touched a computer at all, much like most other non-programming people in the world.  I was hoping that the newer version of Linux would be at least a little user friendly, but so far, I am finding that not to be that case.  I dont mind a little effort and a few command prompts, but I am not about to learn a new language just so I can check my email.  I've always had more than enough common sense to find my way through any apple or windows 98 and newer program or OS, but I am not a computer programmer, nor do I intend to become one.

---

### Post by albinootje on 2009-01-15
> **downinit_xyz said:**
>  What file exactly do I need to burn as an image?  I read that I need to burn the iso file as an image, but I cannot find an iso file what will allow me to select it to be burnt as an image. 

Try this one :
[http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.iso](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.iso)

That's the 8.04.1 LTS Desktop installation cdrom image.
Burn it at a low burning speed.

---

### Post by kansasnoob on 2009-01-15
It sounds to me like the disc was not burned as a .iso image!

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by alzie on 2009-01-15
I'm a bit confused, did you select the install while you were in Windows (this would be a Wubi install) or did you partition your hard drive and do a full install?

When you end up at the "grub prompt" do you notice anything called "busybox" pop up?

I may not be able to help you directly but maybe we can find the issue and someone familiar with the problem.

---

### Post by estyles on 2009-01-15
When you get into the grub menu, it should give you an option to "edit" the command - I believe you press 'e'.  Highlight Ubuntu, press the button to edit, and tell us what you see.

---

### Post by Gias Kay on 2009-01-15
> **downinit_xyz said:**
> The 'grub' prompt appears as soon as I select 'ubuntu' from the boot list on start-up.  

Should I burn the file I downloaded exactly as it was received? Since the file came as a rar file (or at least it is automatically opened in winrar), I assumed I had to extract it first before burning, since that is what I usually have had to do with rar files in the past.  The burn mentioned above was with the files after being extracted.  I really wish the instructions would be a little more specific, it seems like they just glaze over some of the minor details since the people who wrote this have probably done dozens of installs already.

Thanks for any assistance. I have been using much more intuitive OS's (usually Apple since I can't stand windows) since the mid 80's, and if DOS was still the only option, I would have never touched a computer at all, much like most other non-programming people in the world.  I was hoping that the newer version of Linux would be at least a little user friendly, but so far, I am finding that not to be that case.  I dont mind a little effort and a few command prompts, but I am not about to learn a new language just so I can check my email.  I've always had more than enough common sense to find my way through any apple or windows 98 and newer program or OS, but I am not a computer programmer, nor do I intend to become one.

Something is wrong with the file you downloaded - it should come as a .iso file not a .rar file. Download Ubuntu from the [official site]("http://www.ubuntu.com/getubuntu/download") please and you will get a file with a name like ubuntu-8.10-desktop-i386.*iso*. After the download is initiated, the *exact same* page has instructions on how to burn an iso image. It reads:

[LIST]Learn how to create a CD from your newly downloaded file: [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")[/LIST]

Basically you just burn the whole, single .iso file - no extraction whatsoever - onto a CD, using the "burn from an iso image" option in your CD authoring software. You can refer to the link for more detail.

Ubuntu is a very intuitive OS environment and the documentation is reachable in the place it's needed, the problem as I have heard it described is really not a Ubuntu issue. Hope you can try out the actual Ubuntu first before judging, it won't disappoint you.

---

### Post by kwacka on 2009-01-15
You have probably (correctly) downloaded an .iso (cd image) file, winrar has basic capabilities to handle .iso files. Sadly Windows assumes that it knows best and has told winrar to open it up.

If you have something like Nero, burn the cd image to a cd [http://www.wizardskeep.org/mainhall/tutor/neroiso.html](http://www.wizardskeep.org/mainhall/tutor/neroiso.html)
tells you how, then boot from the CD.

---

### Post by albinootje on 2009-01-15
> **kwacka said:**
> You have probably (correctly) downloaded an .iso (cd image) file, winrar has basic capabilities to handle .iso files. Sadly Windows assumes that it knows best and has told winrar to open it up.

If you have something like Nero, burn the cd image to a cd [http://www.wizardskeep.org/mainhall/tutor/neroiso.html](http://www.wizardskeep.org/mainhall/tutor/neroiso.html)
tells you how, then boot from the CD.

The OP wrote that the free and open source InfraRecorder was already used following this howto : [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Thanks for explaining about the rar problem in MS-Windows, I've read about that before, but since I'm not a Windows user I decided to not talk about things that I don't know enough about.

For the OP it makes sense to check the md5sum of the cdrom image after downloading. 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
--> section "MD5SUM on Windows".

---

