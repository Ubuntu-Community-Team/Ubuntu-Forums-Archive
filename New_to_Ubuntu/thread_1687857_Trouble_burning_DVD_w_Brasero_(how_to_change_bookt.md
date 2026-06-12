---
title: "Trouble burning DVD w/ Brasero (how to change booktype?)"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by cero.kewl8080 on 2011-02-14
I've been trying to burn a backup copy of my Honda Navigation DVD Map Data Disc, just in case the original disc gets damaged (it cost me $200 for the 2010 version).

I created the .iso which worked fine and appeared to include all the data files upon inspection of the new disc's contents.  When I burned the .iso onto a DVD +R DL disc, I received an error from my car's NAV system (i.e. "error reading disc.  Wrong disc format.).  

I searched a few forums, and located some info on changing the book type (a 4-bit value which identifies the disc format; located at beginning of the disc) from the DVD+R to DVD-ROM.  Apparently this makes the standalone disc player (ie. in this case my Honda NAV DVD-ROM player)  believe that it's reading a correctly formated disc.  I'm using a Lite ON 24X DVD RW SATA which, I've been led to believe from a hardware review article, does support book type management.

In this Ubuntu forum, on a separate thread, I found the following command which the user claims to have successfully changed the book type of a DVD +R DL disc to DVD-ROM:

```
sudo dvd+rw-booktype -dvd-rom -unit+r /dev/dvd
```I received the following output 

```
 
:-[ LG_FCh failed with SK=5h/INVALID COMMAND OPERATION CODE]: No such device
big-geek@biggeek-System-Product-Name:~$ 

```I thought maybe I was referencing the wrong device name, so I checked system->administration->disk utility, which displayed, "device /dev/sr0" for this optical drive, so I changed the command to:

```

sudo dvd+rw-booktype -dvd-rom -unit+r /dev/sr0

```and received the same output:

```

:-[ LG_FCh failed with SK=5h/INVALID COMMAND OPERATION CODE]: No such device

```QUESTION:  how do I change the book type of this device?

---

### Post by mc4man on 2011-02-14
The man page for that does say this
"You can't expect this utility to work with all recorders."
So I'd think that is the case here

Also it's not too clear if it handles dvd-dl, ex. a successful command shows this
> sudo dvd+rw-booktype -dvd-rom -unit+r /dev/sr0
Unit was instructed to brand [COLOR="Blue"]DVD+R [/COLOR]media as DVD-ROM
That may not actually include  dl disks
(years ago it was quite useful to set dvd+r's to dvd-rom, many standalone players would not accept otherwise
Only certain dvd drives could be set, this also was a separate operation from having dvd-dl set to dvd-rom

Have no need here because I only use Imgburn running in wine, which almost always auto booktypes dual layer +r's as dvd-rom - see screen for last dl I burned
(again somewhat dependent of the model of the dvd drive, more recent dvd dl drives will accept dvd-rom booktyping for dl disks

---

### Post by cero.kewl8080 on 2011-02-14
I recently attempted to rip the .iso and burn the image on the DVD+R DL using DVD Decoder in my Windows 7 VM (VirtualBox), but DVD Decoder was unable to determine that my optical drive supported book-type management (i.e., the application reported the name of the writer as "VBOX writer").  When I tried to change the booktype of the disc/drive, I received an error message.

So I can expect different results with wine, I assume?

I suppose wine is similar to VirtualBox, but I've never used it before. 

Thank you for responding.  I'll try to install wine tomorrow or Wednesday and play around with it.  Will let you know my results....

:popcorn:

---

### Post by mc4man on 2011-02-14
> So I can expect different results with wine, I assume?
I wouldn't assume anything, may be drive model  dependent
(sudo lshw -C disk will show cd/dvd drive model

Most likely to be able to be set are the drives in the screenshot plus Optirac (note - many 'name' brand drives are made by either LG or Lite-on

> I suppose wine is similar to VirtualBox...
wine allows you to run .exe's in linux
Imgburn is quite easy to set up and use - the default setting's are good, though one change must/should be made to the I/O

If needed I'll give you some screens to help.

(if you have a matshita (panasonic) drive I'm not sure, have one here in my laptop but can't remember if it **auto** booktypes dl to dvd-rom, I do know it can't be set manually

---

### Post by cero.kewl8080 on 2011-02-15
> **mc4man said:**
> I wouldn't assume anything, may be drive model  dependent
(sudo lshw -C disk will show cd/dvd drive model

Most likely to be able to be set are the drives in the screenshot plus Optirac (note - many 'name' brand drives are made by either LG or Lite-on


wine allows you to run .exe's in linux
Imgburn is quite easy to set up and use - the default setting's are good, though one change must/should be made to the I/O

If needed I'll give you some screens to help.

(if you have a matshita (panasonic) drive I'm not sure, have one here in my laptop but can't remember if it **auto** booktypes dl to dvd-rom, I do know it can't be set manually

Here is the output from:

```


sudo lshw -C disk


```

```

*-cdrom
       description: DVD-RAM writer
       product: iHAS524   B
       vendor: ATAPI
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: AL24
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom


```

The output above says the vendor is "ATAPI."  I've never heard of this vendor before, and I was under the impression the manufacturer of this drive was Lite-ON.  The model number is accurate, and according to a hardware review article I found, it supports booktype management.

I'm really looking for a total Linux solution to this problem, but I will experiment with wine, and let you know the results.

):P

---

### Post by mc4man on 2011-02-15
> I'm really looking for a total Linux solution to this problem
Maybe ck. out k3b, it is  more advanced than brasero - your drive can certainly bitset to dvd-rom

---

### Post by cero.kewl8080 on 2011-02-15
I just installed wine, and the Imgburn.exe, but when I run Imgburn, it does not detect my DVD writer.

[IMG]https://docs.google.com/leaf?id=0B0HQHLzxy3W5Zjg3ZjMyODQtNmRjNy00M2UyLTlhMTQtZmQ5MGIwMDgyOGNl&sort=name&layout=list&num=50[/IMG]

---

### Post by cero.kewl8080 on 2011-02-15
Screen shot of imgburn attached.

---

### Post by mc4man on 2011-02-16
I did mention you needed to do something w/ Imgburn, didn't provide - you seemed inclined to ck. out yourself, ect...

Anyway  - 2 ways, either wine needs to be configured or you can have Imgburn access the drive directly. I prefer the later by far 
To do - 
open Imgburn, Tools > settings > I/O
Choose the top choice in the Interface box. (see screen
If any other ?'s about Imgburn just ask
(note in the settings > write that the auto change bookmark should be checked, (screen
 when in write mode look in bottom left corner, you can open the bookmark dialog to check (shown in previous post's  screenshot

Something to consider - 
The layer break is normally calculated and set when creating an iso.
If Imgburn complains with your existng .iso then you could try having it 'rip' your existing disk to .iso
As long as there is no protection it will be able to, you use the 'read' mode, available in the menu


Did you try k3b?

---

### Post by cero.kewl8080 on 2011-02-18
Hey, sorry it took so long to reply.  For some reason, I did not receive notification of your reply.....or I deleted the email by mistake (more likely lol).

No, I haven't tried k3b yet.  I'm attempting to burn the DVD-ROM now, as per your new instructions, with Imgburn. 

This should probably do the trick, and upon success, I will try to burn a seperate disk using k3b.

Will let you know my results either way.

Thanks for your help!!!!

Steve:guitar:

---

### Post by cero.kewl8080 on 2011-02-18
OK, so I burnt the .iso onto the DVD +R, but when I tried to run the disc in my Honda's NAV drive, I received the same error msg as before "wrong disc type."

How do I check to see if this burnt disc's booktype was indeed bitset to DVD-ROM?  Just want to confirm it was burnt correctly.  I changed the I/O setting as you instructed, and the write setting, but I did not shut down Imgburn after doing this, I just pressed "OK" and performed the write operation. After testing the disc in my car, I restarted Imgburn back up again and it displayed a msg stating the the configuration settings were updating.....so I'm thinking maybe the settings were not enabled before it was shutdown (possibly).  Thinking if I check the booktype now it might still read as DVD +R.

Thanks again for all your help!!!
:confused:

---

### Post by cero.kewl8080 on 2011-02-26
bump

---

