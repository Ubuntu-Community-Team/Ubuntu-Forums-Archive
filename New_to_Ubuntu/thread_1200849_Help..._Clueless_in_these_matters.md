---
title: "Help... Clueless in these matters"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by ~Soulman~ on 2009-06-30
Howdy all  ):P
 
Total newbie here , not a computer wiz by any stretch of the imagination  :redface:
 
K I got Studio installed... login went ok ... read the manual that was suggested... still a foriegn language... 
 
I's a musician not a typist ... kinda dyslexic when it comes to keyboards...
 
So now I have a screen with the $ thingme, which I understand represents my user home?  
 
From here I am lost .. 
 
I would like to get to the desktop to start checking out the recording program... but have no idea how .... :confused:
 
 
Would like to get :guitar:
 
Cheers peoples  \\:D/

---

### Post by The Cog on 2009-06-30
Is this right:?
You just installed Ubuntu studio. You log in at the username/password prompt and end up at a screen showing a ~$ prompt.

If so, is the screen you log into a brown graphical screen, or is it white text on a black background (like a DOS screen)? 

I suspect it is white-on-black, in which case I'm afraid your installation has problems starting the GUI. If I'm right, it would be helpful to know what the error messages say when you enter the command **startx** (and hit enter). This command tries to start the GUI, which should have started as the machine booted. Oh, and do you know what kind of video card you have?

---

### Post by ~Soulman~ on 2009-06-30
Yes, looks like Dos, white font, black BKG
 
Tried startx and says is currently not installed.. tried the commands recommended for installin it, and it is not found ... 
 
Onboard Realtek sound ... Is an HP sr5000 series dualcore I am tryin to run it on.
 
Ooops not the video card huh? LOL ummm is onboard too so unknown at this point ...

---

### Post by ~Soulman~ on 2009-06-30
Oh and I am using version 8, but have 9 on disc now and can't even find a way for it to boot from disc

---

### Post by ~Soulman~ on 2009-07-01
K can't even get it to change the bios over ... will be pullin out the HDD and putting it into my external case and reformat it there ... may try V9. whatever... if that doesn't work will start looking at other distros :confused:
 
Too bad too if it don't work .. that Studio looks decent

---

### Post by The Cog on 2009-07-01
If starts reports that something isn't installed, I wonder if you installed the server version instead of Ubuntu Studio. The server version doesn't have a GUI because it's meant to be sat in a rack without a screen anyway. The only other explanation I can think of is that maybe the CD didn't burn properly. 

If you are having trouble burning or booting CDs, that same problem will happen regardless which Linux distro you choose to try - they are all much the same in the way you install them. These two links should help:
[http://www.psychocats.net/ubuntu/burn](http://www.psychocats.net/ubuntu/burn)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

If you are planning to install to a new hard disk, don't try to format it first. Linux can't be installed to FAT or NTFS partitions, whcih are the only two types Windows can create. Leave the disk unpartitioned and then let the Linux installer create the partitions it wants to.

---

### Post by carml on 2009-07-01
Maybe you are missing the GUI,when you're arrive to that black screen,try to type```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```,after that command you have to insert your password,(if you don't see a letter when typing your password don't worry,it's a security feature),then to reboot type```
sudo shutdown now
```followed by your password if required.
I hope this can solve your problem.

---

### Post by ~Soulman~ on 2009-07-01
K gonna try this post for the 3rd time...
 
 
I used Imageburn for the bootdisk and it fired up fine ... I use verbatim MIT 16x single layer, on a Samsung 22x sata that has low burntime on it, so should be no issues with the burn or media quality... Data corruption would be another issue beyond my control.
 
I used this install 
[PC (Intel x86) alternate install DVD]("http://cdimage.ubuntu.com/ubuntustudio/releases/8.04.1/release/ubuntustudio-8.04.1-alternate-i386.iso") For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure 
From this page ... [http://cdimage.ubuntu.com/ubuntustudio/releases/8.04.1/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/8.04.1/release/)
 
Cannot update as there was no ISP detected durin setup....
 
Still no way to get into the bios to set it to DVDrom so I can run another distro and hopefully wipe this out of the HDD... tried this [http://en.wikipedia.org/wiki/Gpart](http://en.wikipedia.org/wiki/Gpart)
Am now getting grub loading, please wait... error 15 
 
Am gonna try setting the format to linux boot and see if it will at least become accessable on the HP ... right now am using my Dell and external sata enclosure to access the HDD with Gpart...

---

