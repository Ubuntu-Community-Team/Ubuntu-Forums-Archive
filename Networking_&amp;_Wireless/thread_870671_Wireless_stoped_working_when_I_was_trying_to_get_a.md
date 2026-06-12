---
title: "Wireless stoped working when I was trying to get ati card working properly"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by AdamKinmont on 2008-07-26
Hey, I've got a Acer Aspire 5100 wlmi version.  When I first installed ubuntu the wireless was working properly.  I recently upgraded to Hardy and the first thing that went wrong was that it would wouldn't start unless I used the .14 kernel instead of the .16 If I tried to boot with the .16 it would put a bunch of blue lines down my screen.  Thats just a side problem though.  I was trying to get my ati card working a x1100 express. I'm not sure what gave me the the idea that it wasn't working I think that it was the fact that it always was in the restricted drivers tab and the check wasn't checked like it was on my wireless.  First I believe I checked the box and then went in the package manager and typed in ati and downloaded anything that seemed like drivers for ati cards.  When I started the next time the screen went white and I had to ctrl+alt+backspace and start in gnome fail safe mode.  From then on out I followed this guide [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers) I got to this point sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

Finally, reboot the computer and type

fglrxinfo

but when I rebooted my wireless was no longer working and my graphics card nor my wireless was in the Hardware drivers section.  It really confused me.  Anyone know whats up?  Also I'm running the 64bit version of Hardy almost forgot that and I was running the 64bit version of gutsy before this also so yeah.

---

### Post by terry slaughter on 2008-07-26
I've had trouble with my ACER 5102wlmi which should share your set up.
 (AMD TL50, Atheros WIFI and ATI xpress 1100).I went the 32 bit route,so things will be different.Change the posting from here to Multimedia there is a sticky for ATI driver installation> IT WORKS WELL. First, set up your ATI drivers using your choice of set-up instruction. (I use Envy:IT'S NOT FOR EVERYONE).The WIFI will again be visible under Hardware Drivers.Make sure the two boxes are checked: ATHEROS HAL and ATHEROS Wireless.After you reboot you should be off and running.If you see that the Hardware Drivers are both checked and you still cannot connect then the problem maybe with Networkmanager.Have no fear,just follow the sticky on the thread "Connecting without network manager" .I hope this has helped, it is not a HowTo more like a Been-There-Done-That.:)

---

### Post by AdamKinmont on 2008-07-26
Thanks a bunch for the reply, since you have a similar setup it sounds like I'll try envy first and if that doesn't work out I'll go with the other route.  Also I've got the exact same card so it seems like envy should work

---

### Post by terry slaughter on 2008-07-26
I hope it works! You may still have problems with your WIFI,it seems there is a bug or two with this latest update.DO NOT FEAR UBUNTU Forums has the 
answers:guitar:

---

### Post by AdamKinmont on 2008-07-27
Ok so heres the deal, I tried starting in .16 recovery mode and then resumed normal boot at the next menu and it started.  When I typed in my information it even didn't show that white screen just went right to gnome I didn't even have to go to failsafe mode like I did in .14 and my wireless was working.  I couldn't even believe it lol.  Yeah now I'm just trying to figure out why it gives me vertical blue bars when I don't start .16 in recovery mode.

---

