---
title: "Karmic Koala login loop"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by electric_mayhem on 2010-02-09
*Hello everyone,*
  
  *I am fairly new to Linux and I am stuck in a GUI login loop in Karmic Koala.  I enter my user ID / password and the Ubuntu loading screen appears for a second then switches back to the login prompt.  Note that I am able to get into recovery mode and then to the root command prompt.  FYI - I ran repair packages and I know that my hard disk is not full.*
  
  *I found a few threads and attempted to change my monitor resolution in the xorg.conf file without success.  I will post the xorg.conf file contents later if needed.*
  
  *Also note that I am unable to boot from any known good live CD after the login loop occurred.  From what I remember I receive a boot system error message insert a system disk during live CD boot.*
  
  *System hardware:*
  *karmic koala live CD*
  *AMD*Athlon *64 X2 with an ASUS motherboard*
  *Two eSATA hard disks *
  
  *My server (older HP Pavilion) is running Karmic without issues so I think that this is a hardware problem on the AMD PC.*
  
  *Thanks for any help you can provide.*

---

### Post by phidia on 2010-02-09
Hi-welcome :) If you have the gui login then it would seem that x is working so although you might want to fine tune it x doesn't seem to be the issue. I would login through recovery mode again and type > startx see if you get your desktop or note any error messages and copy paste them here.
Are you using the correct password to login?

If you are for some reason having xorg issues then [this community doc]("https://help.ubuntu.com/community/Video") may prove helpful.

---

### Post by electric_mayhem on 2010-02-09
Thanks for the tip.  I forgot to mention that I tried startx from the recovery console and it just hung.  I did not receive any error messages and the only way out of the console (that I knew of) was to reboot.

---

### Post by bumanie on 2010-02-09
Have not tried it, but have been told that the key combination of alt+sysreq/printscreen+k will get around the looping problem (same thing is happening on my lucid installation, but I haven't been near the computer to try the above combination yet).

---

### Post by rajeev1204 on 2010-02-09
This is a bug.I had to create a new user to log in.

---

### Post by electric_mayhem on 2010-02-09
Thanks for all the suggestions but I am still unable to log in using the methods in previous replies.

---

### Post by pantsman523 on 2010-02-11
I noticed this too.

After the same download multiple times i was frustrated.

I checked the disk for errors from the live cd menu.  1 file found.

So I ran an md5sum on the .iso.  Guess what?  It seems that the one I downloaded directly from the get Ubuntu page didnt match.  I downloaded one from a mirror (the MIT media lab) and the md5 matches this time.

Trying now.

---

### Post by electric_mayhem on 2010-02-14
> **pantsman523 said:**
> I noticed this too.

After the same download multiple times i was frustrated.

I checked the disk for errors from the live cd menu.  1 file found.

So I ran an md5sum on the .iso.  Guess what?  It seems that the one I downloaded directly from the get Ubuntu page didnt match.  I downloaded one from a mirror (the MIT media lab) and the md5 matches this time.

Trying now.

 I downloaded multiple ISOs and I am unable to boot from the live CD on this machine.  They work fine on my Intel boxes but not the AMD.  Did you have any luck?

---

