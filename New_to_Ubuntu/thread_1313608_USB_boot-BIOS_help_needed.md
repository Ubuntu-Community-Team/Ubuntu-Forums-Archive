---
title: "USB boot-BIOS help needed"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by annie227 on 2009-11-03
Hi,I have a 2G and 16G flashsticks and I'd like to put Jaunty on one of them.
My major concern is my BIOS.I have these boot options:
CD-rom,HD,LS120,USB-FDD,USB-ZIP,floppy and USB-cdrom(?)not sure about that last one but anyway I don't know which one to use(if one is appropriate)so any info is gratefully received.
Also while you're at it the correct formatting of the usb stick,any hints or directions would be great.I tried it a while back and it failed but try,try again until I get it right.
Thankyou.;)PS-I currently have Karmic and xp duel boot though I still haven't bothered finishing putting all the programs on xp since installing on a new HD(I haven't needed to and I'm finding myself not wanting/needing to go there yet)

---

### Post by jimmy the saint on 2009-11-03
Install Unetbootin.  It is in the repos, so it should just be a matter of firing open the software Center and installing it from there.  easy.  

Now download the iso for the version you want to throw on it.  

Now plug in your usb drive, run unetbootin making sure to select the USB drive and the iso you just downloaded.

BAM!  you now have Ubuntu on a USB drive.  

As for your bios, I would guess USB-FDD would be the right choice.  If it isn't just keep trying others.  Worst case, it boots off the harddrive instead and you have to reboot a few times.

One final thing.  If you have access to a Jaunty installation, you can just use the USB creator under System>Administration.  Unetbootin has both a windows and a linux version.  If you are doing this from windows, the only difference is that you need to download Unetbootin from their website to install it.

Good Luck

---

