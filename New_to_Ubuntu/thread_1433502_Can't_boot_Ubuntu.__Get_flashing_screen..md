---
title: "Can't boot Ubuntu.  Get flashing screen."
date: 2010-03-19
forum: New to Ubuntu
---

### Post by Tallwes on 2010-03-19
[FONT=Arial, sans-serif]This is my very first time trying to install Ubuntu.[/FONT]
 

 [FONT=Arial, sans-serif]I am using an Asus  EEE PC 900XP with 1 GB ram, a 16 GB solid state drive (which has windows XP installed on it) instead of a hard drive and a 900 MHz Celeron M processor.  I am using the EEE PC for both installing Ubuntu and running Ubuntu from the USB pendrive.  I am using an 8 GB pendrive for the Ubuntu installation.[/FONT]
 

 [FONT=Arial, sans-serif]Using the Windows OS to do the following procedures.  I downloaded the Ubuntu Netbook Remix ISO.  I saved the ISO file to an external USB hard drive.  Then using Virtual Clone Drive, I ran USB creator to install Ubuntu on the USB pendrive from the external USB hard drive.[/FONT]
 

 [FONT=Arial, sans-serif]I then tried to boot the Ubuntu installation by turning on or rebooting the EEE PC, pressing F2 to enter the BIOS, pressing ESC to exit the BIOS, pressing RETURN to select the OK button in the BIOS exit dialog box, tapping ESC to bring up the boot selection menu and selecting the pendrive.[/FONT]
 

 [FONT=Arial, sans-serif]Ubuntu boots up into the initial boot-up/Start-up menu.  When I make the selection to boot up Ubuntu I get a white Ubuntu symbol for a while then I end up at a black screen with the text:[/FONT]
 

 [FONT=Arial, sans-serif]Starting early crypto disks...[/FONT]
 [FONT=Arial, sans-serif]Starting remaining crypto disks...[/FONT]
 [FONT=Arial, sans-serif]Starting init crypto disks...[/FONT]
 [FONT=Arial, sans-serif]Starting kernel Oops catching service kerneloops[/FONT]
 [FONT=Arial, sans-serif]Speech-dispatcher configured for user sessions[/FONT]
 [FONT=Arial, sans-serif]Starting Common Unix Printing System: cupsd[/FONT]
 [FONT=Arial, sans-serif]PulseAudio configured for per-user sessions[/FONT]
 [FONT=Arial, sans-serif]Checking battery state...[/FONT]
 [FONT=Arial, sans-serif]...done.[/FONT]
 

 [FONT=Arial, sans-serif]Flashing in the upper left hand corner of the screen.  Nothing else happens.[/FONT]
 

 [FONT=Arial, sans-serif]When I make the selection to install Ubuntu from the [FONT=Arial, sans-serif]initial boot-up/Start-up menu. [/FONT] I get a white Ubuntu symbol for a while then I get the following text:[/FONT]
 

 [FONT=Arial, sans-serif][  ###.######] SQUASHFS error: Unable to read page, block XXXXXXXX size cbd7[/FONT]
 [FONT=Arial, sans-serif][  ###.######] SQUASHFS error: Unable to read data cache entry [XXXXXXXX][/FONT]
 [FONT=Arial, sans-serif][  ###.######] SQUASHFS error: squashfs _read_data failed to read XXXXXXXXXX[/FONT]
 

 [FONT=Arial, sans-serif]#s are varying numerical digits.  Xs are varying combination of alphabetical characters and numerical digits.  That is both flashing and is repeatedly scrolling up the screen.  Nothing else happens.[/FONT]
 

 [FONT=Arial, sans-serif]As suggested for flashing screens, I read about in other forum posts, I tried to unplug all my other USB drives and devices(except for the pendrive I got Ubuntu on) but it still will not boot up.  I tried to delete xorg.con but I cannot find that file on my pendrive.  The other posts concerning flashing screens made mention of a login screen.  I see no prompt for logging in, I don't think I am making it that far.[/FONT]
 

 [FONT=Arial, sans-serif]What's wrong and what do I do to fix it?:confused:[/FONT]
 

 [FONT=Arial, sans-serif]Tallwes[/FONT]

---

### Post by Psumi on 2010-03-19
Did you install ubuntu with the "decrypt my home" or whatever?

I suggest re-installing without if you did, encryption makes your computer almost 3 times as slow.

---

### Post by Tallwes on 2010-03-19
I don't think so.  I did not select anything that said "decrypt my home".  Is that option in the create USB program?

---

### Post by Psumi on 2010-03-19
> **Tallwes said:**
> I don't think so.  I did not select anything that said "decrypt my home".  Is that option in the create USB program?

it's part of the installer, so if you created a USB Stick with Ubuntu USB Creator, then it would be in with the installer portion, not the live session.

---

### Post by Tallwes on 2010-03-20
If the "installer portion" you are referring to is the second selection down from the top of the menu I get when I boot from the USB stick, then I definitely did not select "decrypt my home", because that is one of the two menu selections that doesn't work.  The other selection on that menu that doesn't work is the first selection at the top to try out Ubuntu.

---

### Post by Tallwes on 2010-04-07
It seems that everybody has drawn a blank on this one.

Where else can I go to get help?  I'll like to get my Ubuntu installation working.

Tallwes :confused:

---

### Post by Psumi on 2010-04-07
> **Tallwes said:**
> It seems that everybody has drawn a blank on this one.

Where else can I go to get help?  I'll like to get my Ubuntu installation working.

Tallwes :confused:

IRC Channel is worse, too many people talking at once. You can try linuxquestions.org

But, this is the best place to get help on ubuntu, even if you have to bump your thread for weeks.

(Oh and, no one likes to help much during the month or three before a new release, because they will just wait to see what happens when you install the new release before helping, see if a new release helps your problem.)

---

### Post by uRock on 2010-04-07
> **Tallwes said:**
> [FONT=Arial, sans-serif]This is my very first time trying to install Ubuntu.[/FONT]
 

 [FONT=Arial, sans-serif]I am using an Asus  EEE PC 900XP with 1 GB ram, a 16 GB solid state drive (which has windows XP installed on it) instead of a hard drive and a 900 MHz Celeron M processor.  I am using the EEE PC for both installing Ubuntu and running Ubuntu from the USB pendrive.  I am using an 8 GB pendrive for the Ubuntu installation.[/FONT]
 

 [FONT=Arial, sans-serif]Using the Windows OS to do the following procedures.  I downloaded the Ubuntu Netbook Remix ISO.  I saved the ISO file to an external USB hard drive.  Then using Virtual Clone Drive, I ran USB creator to install Ubuntu on the USB pendrive from the external USB hard drive.[/FONT]
 

 [FONT=Arial, sans-serif]I then tried to boot the Ubuntu installation by turning on or rebooting the EEE PC, pressing F2 to enter the BIOS, pressing ESC to exit the BIOS, pressing RETURN to select the OK button in the BIOS exit dialog box, tapping ESC to bring up the boot selection menu and selecting the pendrive.[/FONT]
 

 [FONT=Arial, sans-serif]Ubuntu boots up into the initial boot-up/Start-up menu.  When I make the selection to boot up Ubuntu I get a white Ubuntu symbol for a while then I end up at a black screen with the text:[/FONT]
 

 [FONT=Arial, sans-serif]Starting early crypto disks...[/FONT]
 [FONT=Arial, sans-serif]Starting remaining crypto disks...[/FONT]
 [FONT=Arial, sans-serif]Starting init crypto disks...[/FONT]
 [FONT=Arial, sans-serif]Starting kernel Oops catching service kerneloops[/FONT]
 [FONT=Arial, sans-serif]Speech-dispatcher configured for user sessions[/FONT]
 [FONT=Arial, sans-serif]Starting Common Unix Printing System: cupsd[/FONT]
 [FONT=Arial, sans-serif]PulseAudio configured for per-user sessions[/FONT]
 [FONT=Arial, sans-serif]Checking battery state...[/FONT]
 [FONT=Arial, sans-serif]...done.[/FONT]
 

 [FONT=Arial, sans-serif]Flashing in the upper left hand corner of the screen.  Nothing else happens.[/FONT]
 

 [FONT=Arial, sans-serif]When I make the selection to install Ubuntu from the [FONT=Arial, sans-serif]initial boot-up/Start-up menu. [/FONT] I get a white Ubuntu symbol for a while then I get the following text:[/FONT]
 

 [FONT=Arial, sans-serif][  ###.######] SQUASHFS error: Unable to read page, block XXXXXXXX size cbd7[/FONT]
 [FONT=Arial, sans-serif][  ###.######] SQUASHFS error: Unable to read data cache entry [XXXXXXXX][/FONT]
 [FONT=Arial, sans-serif][  ###.######] SQUASHFS error: squashfs _read_data failed to read XXXXXXXXXX[/FONT]
 

 [FONT=Arial, sans-serif]#s are varying numerical digits.  Xs are varying combination of alphabetical characters and numerical digits.  That is both flashing and is repeatedly scrolling up the screen.  Nothing else happens.[/FONT]
 

 [FONT=Arial, sans-serif]As suggested for flashing screens, I read about in other forum posts, I tried to unplug all my other USB drives and devices(except for the pendrive I got Ubuntu on) but it still will not boot up.  I tried to delete xorg.con but I cannot find that file on my pendrive.  The other posts concerning flashing screens made mention of a login screen.  I see no prompt for logging in, I don't think I am making it that far.[/FONT]
 

 [FONT=Arial, sans-serif]What's wrong and what do I do to fix it?:confused:[/FONT]
 

 [FONT=Arial, sans-serif]Tallwes[/FONT]

Looks like you installed it with encryption and the encryption broke or you told it to decrypt your home  when it isn't encrypted.

My suggestion is to reinstall, it only takes about 20 minutes with your processor speed.

Let us know how it goes.

Best wishes,
Ronnie

---

