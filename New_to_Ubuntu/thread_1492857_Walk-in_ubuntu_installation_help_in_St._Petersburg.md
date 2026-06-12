---
title: "Walk-in ubuntu installation help in St. Petersburg, Russia?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Rockcarver on 2010-05-25
My Karmic is crashing and I can't delete it and reinstall because I have a bunch of needed data stored under the home directory. I cannot move the data to a safe place because the file manager "Places" has stopped working. I tried to install PCMan File Manager from a flash, using sudo apt-get install in the terminal, but the error was "can't find package" even though I gave the path.

So I want to find somebody knowledgable in the St. Petersburg area who can help with this problem, and then with getting my Airplus MCD-650 to connect to Skylink so I can have internet on the dacha.

Failing all that, I will be forced to drop Ubuntu and go back to Windows, a bitter pill indeed.

---

### Post by philinux on 2010-05-25
For backing up you need the livecd and a usb stick.

---

### Post by Rockcarver on 2010-05-25
Ah, thanks, Phillinux, I will try that. I have the live 10.04 cd back at the ranch, I think. With me now is the 9.04 iso, but I can't get it to open in either Ubuntu or windows. I tried booting from cdrom in windows, in Ubuntu the terminal sees the CD but can't see the iso.

Any suggestions?

---

### Post by philinux on 2010-05-25
> **Rockcarver said:**
> Ah, thanks, Phillinux, I will try that. I have the live 10.04 cd back at the ranch, I think. With me now is the 9.04 iso, but I can't get it to open in either Ubuntu or windows. I tried booting from cdrom in windows, in Ubuntu the terminal sees the CD but can't see the iso.

Any suggestions?

You need to go into the bios and make sure the cdrom is the first boot device. Insert livecd reboot and at the menu choose Try Ubuntu. You'll get to the desktop after a couple of mins. You can then use it to backup stuff to a usb stick.

---

### Post by Rockcarver on 2010-05-25
Is live cd and ISO the same thing? because with the 9.04 ISO, I did the boot priority thing on the way in  to windows, but the cd was ignored, windows booted from the hdd.

---

### Post by philinux on 2010-05-25
> **Rockcarver said:**
> Is live cd and ISO the same thing? because with the 9.04 ISO, I did the boot priority thing on the way in  to windows, but the cd was ignored, windows booted from the hdd.

You would normally download an ISO file and burn it as a disc image. This creates the bootable live cd.

---

### Post by mastablasta on 2010-05-25
If you have the ISO file on CD you are doing it wrong.  Go to windows, move the ISO file to disk and then use a burner programe to burn the image to disk (don't burn the ISO file). The CD will be made of different files and folders. 
 
If the CD download was good and the burned image is also good (check md5sum) then it should work as a live CD (boot priority with CD)
 
Also before - did you install Linux from windows it using wubi?

---

### Post by Rockcarver on 2010-05-25
Hmm, OK, guys, I will try re-burning the disk, just listing the files that are under the ISO. 

Uh- (blush) what's a wubi? Can I look now and find out how I did it? I just had a disc that I  burned from a download, tried it first as a live disc, then installed it in parallel with Vista. Every time I boot I have to choose ubuntu or Vista, with vista as default.

I don't recall wubi or not.

---

### Post by philinux on 2010-05-25
> **Rockcarver said:**
> Hmm, OK, guys, I will try re-burning the disk, just listing the files that are under the ISO. 

Uh- (blush) what's a wubi? Can I look now and find out how I did it? I just had a disc that I  burned from a download, tried it first as a live disc, then installed it in parallel with Vista. Every time I boot I have to choose ubuntu or Vista, with vista as default.

I don't recall wubi or not.

As a disc **[COLOR="Red"]image[/COLOR]** not a data cd.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Rockcarver on 2010-05-25
Sorry, I don't understand that distinction. Obviously I am in the right forum.  Disc image or data cd: can I specify the right type in the average cd burning program? Apparently I did once, because I got a live 9.10 cd working.

---

### Post by DrMelon on 2010-05-25
Most CD Burning software will give you the option to burn from an ISO image.

---

### Post by Rockcarver on 2010-05-25
Thanks, everyone, I will go and try the suggestions you have offered, and will report back maybe in a day or so.

---

### Post by Rockcarver on 2010-05-31
Well,  with your help, I did get a live cd going for 9.04 as well as 9.10, But broadband is not enabled on either one, so I am still at an impasse.

---

