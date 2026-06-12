---
title: "[SOLVED] 7.10 to windows xp with HP printer network problem"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by mike g on 2007-11-09
I think this may actually be a combination question.

I upgraded to 7.10 from Feisty using the upgrade in the update manager.  I am now unable to connect to a windows xp computer on a LAN.  I have tried all the suggestions I can find which include changing the recognition in SMB,  I have tried turning off the firestarter.  I have done away with the auto recognition and defined the printer location.  

I am to the point that I am truthfully not sure if I have a network recognition problem, a printer recognition problem or both.  I however find that I am able to view my shared folders on the XP machine so I assume at least part of my network may be working.

I am running a HP5610 series printer.  It appears as if the printer drivers are present.

---

### Post by mike g on 2007-11-09
Problem solved...purely by accident.

1.  Disable Firestarter.
2. Open System>Adminstration>Printing
3. Go to Windows system which has the printer.
4. Use what ever location you have listed for the printer --- in my case, mshome/mwgsr-1/printer3
5. Place that into the "Device URL:// space provided on the printer configuration page.
6. Place the printer designation, what ever you named it in Windows, into the Description box.

This worked for me and should work for you providing you enter the proper information.  

I hope it helps someone who is having a similar problem.

:popcorn::)

---

