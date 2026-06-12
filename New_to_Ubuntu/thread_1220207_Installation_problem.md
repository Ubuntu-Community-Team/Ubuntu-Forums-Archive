---
title: "Installation problem"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Evillian151 on 2009-07-22
Hi,
 
I am trying to install Ubuntu for the first time (9.04, 64-bit), so i am a newbie.
The problem is that when i select 'try ubuntu' or 'install ubuntu', the graphical interface does not start. I get the loading screen, and then after about 30/40 seconds the console starts without an error message. The installation does not start and i can type in the console but there's no GUI.
 
My video card: ATI Radeon 3870 X2

---

### Post by Durden on 2009-07-22
Sounds like it doesn't like your video card. What card do you have?

---

### Post by Evillian151 on 2009-07-22
> **Durden said:**
> Sounds like it doesn't like your video card. What card do you have?
 
The radeon 3870 X2, i have seen guys on forums having issues to get 3d acceleration going with this card, but the rest works they said.

---

### Post by Durden on 2009-07-22
Looks like the card only works with the proprietary drivers from ATI. From what I am reading it's the only card that doesn't work right off (crap luck here).

It's been a while since I did a fresh install. What are the boot options from the "try ubuntu" and "install ubuntu" screens again?

I'm curious also if this might be a 64 bit issue.

---

### Post by Durden on 2009-07-22
[http://ubuntuforums.org/showthread.php?t=499060&highlight=6715s](http://ubuntuforums.org/showthread.php?t=499060&highlight=6715s)

This may help. You can download the ati drivers and burn them to a CD with the Ubuntu install disk. I've never done this myself so you may wan to read through it.

Alternatively you could stick another video card in just to get it installed, then download the drivers, put the new ATI card in and do a manual install from safe mode.

---

### Post by Evillian151 on 2009-07-22
Ok thanks for the help, i will try!

---

### Post by Merk42 on 2009-07-22
Seems kind of odd it wouldn't even fall back onto some default graphics drivers. 

Are you sure you have a 64-bit processor?
If you are not sure, and have Windows currently installed you can use [this program](http://www.grc.com/securable.htm) to see if your processor supports 64-bit.

---

### Post by Durden on 2009-07-22
Well he gets the load screen and is dropped to a command line so it's booting 64 bit, just not initializing the graphics. If he was 32 bit the disk wouldn't even boot.

---

### Post by Evillian151 on 2009-07-22
Yeah i have a 64 proc and i have also been using XP 64 and Vista 64 in the past.
 
I just saw a post from guy who had no problems installing with this type graphics card. The card seems to be supported in ubuntu since 8.10 :(
 
The strange thing is that i don't get an error message of any kind. It just comes with the console.

---

### Post by Durden on 2009-07-22
The lack of an error message is making it difficult to help.

I suppose if you have the time you can try downloading both Xubuntu and Kubuntu and see if they will install. It's easy to switch between the Ubuntu's from synaptic once the system is installed, so the versin you install is rather irrelevent. I think we just gotta get you installed and running first.

---

### Post by JDShu on 2009-07-22
Have you tried booting it with acpi turned off? That sometimes helps.

---

### Post by Evillian151 on 2009-07-22
Yep and it didnt work. I will try 32 bits now (maybe 64 bit driver issue) and then try kubuntu. Hope it works :-(

---

### Post by okey666 on 2009-07-22
If you want to install, why not just use the alternate install disk. Then, once you are running, install drivers as need be.

---

### Post by Durden on 2009-07-22
I believe Okey is referring to the command-line install from the alternate disk. You could then install drivers and then do a "sudo apt-get install ubuntu-desktop" for the gui stuff.

However, I'm not certain this would help since the card is supposed to work regardless. Installing the drivers from the commandline probably wont solve the problem. Unless of course there is a problem with the installer itself.

---

### Post by okey666 on 2009-07-22
The alternate install disk is exactly the same as the live cd installer and installs exactly the same things. The only difference is that it uses a text based install enviroment, so is ideal for computers where the shipped drivers fail to function. Once installed, the user simply uses it like it had been installed using the live cd. 

The reason I suggest this is that It is a better alternative to using kubuntu live cd as the alternate will install gnome and allow the correct drivers to be installed via the command line. I presume you could install the drivers on the live cd, install ubuntu and then install the drivers again on the actual installation, but using the alternate seems like a better solution.

---

### Post by sackbj on 2009-07-26
The most recent release of the ATI Catylst drivers has release notes.  If you look through them - you will see that they explicitly state that the HD 3870 X2 is not supported.

I have not gotten mine to work no matter what I have done.

---

