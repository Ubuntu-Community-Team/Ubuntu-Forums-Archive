---
title: "Switch to Ububtu without CD?"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by anlasbry on 2009-10-17
Hi everyone, I was wondering if someone may be able to help me. I installed Kubuntu 6.06 a few days ago because I found the Live CD I ordered and I had completely forgotten about. I have a ThinkPad laptop and I installed Kubuntu, even though I really wanted Ubuntu but I couldn't find the CD for that. Then I found the Ubuntu CD and wanted to install it, but I tried booting up from it and it didn't work. I tried pressing F12 to open up the BIOS to no avail (it only worked the first time when I got rid of Windows). Then I looked online and I found someone who said I should try:

```
sudo apt-get install ubuntu-desktop
```in order to switch from KDE to Gnome, but I got an error message saying that the package ubuntu-desktop could not be found.

I tried using Adept because it's the package manager and I thought it could help. I typed ubuntu-desktop into the search field and it only found the 
kubuntu-desktop package, so I tried installing the ubuntu-desktop package, but I made a mistake there. I went to manage (I think that's what the option was called) and typed in the URL for the package in the Ubuntu website (I really wasn't sure what I was doing) and now I get an error message anytime I try to open Adept or 
Add/Remove Programs saying:

> The APT database could not be opened! This may be caused by incorrect APT configuration...Then, I checked the Ubuntu website and tried downloading the package and seeing what I could do from there, but when I downloaded the package and tried to open it by right-clicking it and clicking Install Package, it opened up a window where I typed my password and I got an error message, but now I'm getting another error message that says:

> dpkg: status database area is locked by another processThen I thought abut deleting the drive and installing Ubuntu over it. I went to System Settings and then to Disk & Filesystems, but since I didn't know what I was doing I messed it up and can no longer open my CD drive.

I would like to know, can I fix this mess? Does the Ubuntu installer come in a format that doesn't require booting from anything else?

---

### Post by Ingvar G. on 2009-10-17
try this one: [http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

But, before doing something READ it carefully.

Good luck!

---

### Post by cabrey on 2009-10-17
You might want to consider downloading a newer version of Ubuntu, either the current LTS (8.04) or the soon-to-be released 9.10. You can even request a CD at [ShipIt]("http://shipit.ubuntu.com"). Then you can switch between kubuntu-desktop, ubuntu-desktop, xubuntu-desktop.

---

### Post by Jason Cook on 2009-10-17
You could wait until October 29 and download the 9.10 version. You can also put it on you flash drive using these [[https://help.ubuntu.com/community/Installation/FromUSBStick]](https://help.ubuntu.com/community/Installation/FromUSBStick]) instructions.

---

### Post by anlasbry on 2009-10-17
Thanks everyone, but I have a couple of problems. I tried the link to the code where I could remove Kubuntu, but I got an error message saying that the list of sources cannot be read; I'm guessing it relates to how I accidentally broke my Adept Package manager. A newer CD wouldn't work because my CD drive doesn't open anymore. Whenever I try to remove the CD I have in there it says:

> unmount: only root can unmount /dev/hda from /media/cdrom0 

And I wouldn't know how to boot from a USB drive because I can't access my BIOS menu anymore. I used to be able to press F12 at startup, but that does nothing anymore.

Currently, I have the Ubuntu 6.06 live CD in my CD drive. Is there any other way I can make my laptop boot from it again?

---

### Post by cabrey on 2009-10-17
You mean you can't physically open your drive anymore? If you get a paper clip and unbend it, stick it in the small hole that should be on the front of the drive somewhere, that'll pop it open.

---

### Post by anlasbry on 2009-10-17
The CD that's currently in there won't eject. I'll try logging out and trying to open it up before I log back in, but since it's a laptop I don't know if the trick with the paperclip would work (I won't rule it out though).

I was thinking of taking it to the laptop repair shop on campus, but the university's rules say we're not allowed to mess with the laptops they gave us.

---

### Post by Merk42 on 2009-10-17
Wait, did you actually install 6.06 to the hard drive, or are you merely booting the LiveCD version? It sounds like the latter.

---

### Post by anlasbry on 2009-10-17
I installed Kubuntu, but I want to use Ubuntu. I want to install is, especially now that 
I accidentally did something to prevent me from using packages.

---

### Post by Merk42 on 2009-10-17
I understand your problem and the packages is probably because 6.06 is no longer supported.
I'm just curious why you can't even eject your disc.

---

### Post by Devon64327 on 2009-10-17
Hmmm... Im no expert but Im 83% sure the disk drives for laptops are SPRING loaded therefore your OS couldnt prevent it from opening... Have you tried booting from WUBI through Wine(I have no idea what Im talking about) or a flash drive?


!!!!!!!!!! I just spent 5 minutes typing out a rather long forum signature... and its gone :(

---

### Post by anthos_hero on 2009-10-17
You could try making a bootable flash drive using Unetbootin.  It's really easy.

---

### Post by Devon64327 on 2009-10-17
> **anthos_hero said:**
> You could try making a bootable flash drive using Unetbootin.  It's really easy.
   :( I said that....

---

### Post by anlasbry on 2009-10-17
Actually, I wouldn't be able to use WUBI or Wine because, while the laptop did come with Windows XP, I got a pretty nasty virus and decided to just wipe the hard drive clean when installing Kubuntu. I think the CD drive fiasco is from when I messed with the system. I'll give the flash drive idea a shot, but how big does the drive have to be? I have a 128 MB drive, but I think I'll borrow my friend's 2 GB.

---

### Post by themusicalduck on 2009-10-17
Even if you make a bootable usb, if you can't change the boot order or get to a boot menu in your bios, then you probably won't be able to use it.

Also ```
unmount: only root can unmount /dev/hda from /media/cdrom0
```

Makes it look like you were using the live CD, since its saying that the first hard disk is mounted on the CD rom. (I'm only guessing here, someone might know better)

Or perhaps if it isn't, using the command ```
sudo umount /dev/hda
``` might let you eject it?

---

### Post by Jason Cook on 2009-10-17
> **Devon64327 said:**
> [quote=anthos_hero;8121938]You could try making a bootable flash drive using Unetbootin.  It's really easy.:( I said that....[/quote]
I sort of suggested that too! [[http://ubuntuforums.org/showpost.php?p=8121305&postcount=4]](http://ubuntuforums.org/showpost.php?p=8121305&postcount=4])

---

### Post by anlasbry on 2009-10-17
Thanks, but

```
sudo: unmount: command not found
```

---

### Post by Merk42 on 2009-10-17
> **anlasbry said:**
> Thanks, but

```
sudo: unmount: command not found
```

umount, not unmount

---

### Post by anlasbry on 2009-10-17
Thanks. I was able to eject the CD by restarting the computer and pressing the eject button before Kubuntu loaded.

---

### Post by anlasbry on 2009-10-21
Thanks. Problem solved, kind of. I was able to get a new hard drive for my laptop and I used Wubi to install Ubuntu 9.04. This time, I read all of the instructions instead of merely trying to experiment without knowing what I was doing. I used Wubi because I still need Windows to log on to the university's Wi-Fi; the laptops they gave us log on using a password they programmed into it, and they won't tell us what it is. At least I can log on at home.

Again, thank you all for your help. If this were a Mac or Windows problem, they would have charged me a lot of money and they would not have been as helpful. That's one of the many reasons I like Ubuntu. This time I'll do some reasearch into what I'm doing and I'll be more careful. Hopefully, somewhere along the line if someone needs advice with Ubuntu I'll be able to help them out.

---

