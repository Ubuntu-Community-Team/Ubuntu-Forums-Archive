---
title: "Weird install trouble: Dual Boot 8.10 amd64 on IBM T400"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by rift321 on 2009-03-20
EDIT: I successfully uninstalled ubuntu, found the missing disc space (it wasn't missing, forgot about decimal->base 2 conversion factor...), and i guess I might as well post whether i get it installed in the end.

I just got a brand new T400 yesterday (I'm aware of all the other pages/posts regarding the T400 and amd64, but to my knowledge, my issue is unique).

Trying to install Ubuntu, I first just loaded the CD as it was booting, selected "install Ubuntu" and it never loaded any desktop environment, and just left me at the command line.  I figured it wasn't installed, restarted, tried the Live installer, finally got that to work, partitioned-off 15 gigs, and and installed it.  I then tried to select and boot into ubuntu, but it never enters into any graphical environment.  I'd like to start over from scratch w/ the Live installer, but getting the ubuntu partition back onto the windows partition seems to be a pain in the ***, involving rebuilding the mbr.  Could someone point me in the right direction?

I just want a nice dual-boot of vista (i have business 64bit edition) and Ubuntu 64.

*Edit: Here's a convo I had with someone, so I don't have to repeat it.

Patrick...	(2:08 PM) Have you tried different media?
Nicholas...	(2:08 PM) ?
Patrick...	(2:09 PM) Maybe its the iso?
Nicholas...	(2:11 PM) well, after the download, it was screwing up at 99% w/ the burned cd, so I downloaded a virtual CD prog, mounted it, and ran the live install without a hitch
Patrick...	(2:11 PM) My first step would be to DL the iso again
Nicholas...	(2:11 PM) ok
Patrick...	(2:12 PM) I have had problems like that
Nicholas...	(2:12 PM) so the disc image could be screwed up
Nicholas...	(2:12 PM) understandable
Patrick...	(2:12 PM) yep
Nicholas...	(2:13 PM) but then I still need to remove the existing ubuntu installation, rebuild the MBR, "expand" my existing C: partition, then run the install again?
Patrick...	(2:13 PM) oh and when you burn the disc make sure it is at a slow setting! 
Nicholas...	(2:13 PM) yea, but that's why I tried doing the virtual cd thing.
Nicholas...	(2:13 PM) essentially, i just need to start over.
Patrick...	(2:14 PM) You should be just able to install right over the existing half install
Nicholas...	(2:15 PM) see, there's the problem: if i boot from the cd, it goes to the command line, and if I use the install from windows, it asks me to partition-off yet another amount of space from my already reduced C:
Patrick...	(2:16 PM) Can you manually partition from windows?
Nicholas...	(2:16 PM) the disc manager doesn't even see the ubuntu partition
Nicholas...	(2:16 PM) crazy, right?
Patrick...	(2:16 PM) In windows? It won't see it. 
Nicholas...	(2:16 PM) yea
Nicholas...	(2:16 PM) nada
Patrick...	(2:17 PM) It should show up as healty but unknown
Nicholas...	(2:18 PM) zero.
Nicholas...	(2:18 PM) nonexistent.
Patrick...	(2:19 PM) Screwy

---

### Post by markbuntu on 2009-03-20
If the cd is giving you only command line then there is some issue with x starting. From the live cd when you get the menu screen choose F4 and select "safe graphics mode" or something like that. This should at least get you a gui.

---

### Post by rift321 on 2009-03-20
Yeah, I hear from the thinkWiki T400 page that I'll probably need to deal with a bunch of graphics BS due to my setup and the 64bit deelee.

Thank you, though. I've thus far re-downloaded the image to eliminate the infinitesimal possibility that there's something wrong with it.  I guess I'll re-burn that at an overly-slow speed, since I'm not entirely convinced that the Live install is dependable...  and I used easyBCD to fix the bootloader's list.

BTW... if anyone is thinking about purchasing an IBM comp, they throw all the Vista recovery stuff on a partition, which they later force you to burn to discs.  No, they don't supply you with the OEM discs or anything.  MAKE SURE YOU ORDER YOUR LAPTOP WITH A DVD BURNER.... i'm currently on CD #7.  And I don't want to hear about how dumb it was to try to save $30 in that department.

---

### Post by miegiel on 2009-03-20
For graphics issues during the install the "alternative CD" is a lifesaver :)
[http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)

---

