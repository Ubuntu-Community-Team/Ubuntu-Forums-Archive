---
title: "UTStarcom UM150AL can't get it to work"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by jack7h3r1pp3r on 2008-08-06
i can't seem to get this usb wireless modem to work in ubuntu and simply don't really know where to start.  i would really like to get this working as it is my only internet source but i can't use my ubuntu and be on the net at the same time so i can't make the full switch for windows to linux yet like i want to. i would really like to know if it is possible to get this working thx in advance for the help.

---

### Post by jack7h3r1pp3r on 2008-08-06
so it looks like no one has any ideas at the moment lol

---

### Post by jack7h3r1pp3r on 2008-08-07
looks like this isn't going to work? then

---

### Post by jack7h3r1pp3r on 2008-08-10
i'm thinking that if i can get this usb wireless internet device to be seen as a modem i think that i would be fine but i'm not sure as to how i can go about doing that. or how i would aproch such a task if anyone could just give me some tips to try out i would be glad to try out your ideas on how to get this to work.

---

### Post by Cresho on 2008-08-11
do you have a copy of all the windows drivers?  for UTStarcom UM150AL?

I can help.  when you do, extract each windows version drivers and make sure there is an inf.  When you do that, come back and we will talk again.  If not, then there are no drivers.  I tried looking for one but i can't seem to locate any.

---

### Post by jack7h3r1pp3r on 2008-08-11
ok so i have PTDMBus.sys modem.sys and oem21.inf should there be more or would these be it it think the rest are dll would i need those? i would think i would but i'm not sure.

---

### Post by jack7h3r1pp3r on 2008-08-11
ok so now i got the cd to work in wine but i can only install the software that it comes with and not the actual modem because it doesn't recognize the use as a modem. will i need the drivers to tell the system that it really is a modem?

---

### Post by Cresho on 2008-08-12
system administration->Software Sources
under ubuntu software, change download from to "main server"
if this is done, dont do this again.



applications->add remove
change drop down to all available applications
search for "windows wireless drivers" and install it.


after this is installed.  open the program "windows wireless drivers....crap I cant remember where it is.  it could be under administration or system.  if you find it, open it and then install new driver and try the drivers.  mainly work your way from xp drivers down to windows 98.  If xp works, leave it alone.  Make sure your hardware installed.

reboot.  open again  "windows wireless drivers" and look to see if it says something like....."hardware driver ready" or something in this manner.  I just finished installing a wifi on my nephews pc.

anyway, after you have this working (if it's working).  you cannot run it until you do this last step.  The drivers need to be working.

go to Administration->synaptic package manager and search for madwifi. Install madwifi-tools

Reboot.






you can now access wifi in the upper right hand corner of your network manager. right click disable or enable toggles, leftclick assign wifi.

Let me know if this works.

anyway, I just finished building my nephew (finaly converted to ubuntu) a pc and added wifi.  it took me 3 hours of reading around but most are outdated info.  If your interested in a 7 dollar wifi card from fry's electronics, this is the tutorial that i slapt together.

[http://ubuntuforums.org/showthread.php?p=5562566#post5562566](http://ubuntuforums.org/showthread.php?p=5562566#post5562566)

---

### Post by jack7h3r1pp3r on 2008-08-13
i tried all of the things that you suggested but it still doesn't work and it's not a wifi device. it actually dial in to a server and thats how i get connected. i can't get into other wifi networks with it. it think what i need to do is get it so it is recognized by ubuntu because when i am installing the software for it it get to a point for me to plug it in so it can configure it but it can't find it. like when you plug something in in windows it says that it's installing and ubuntu doesn't i need the software to see it then i think that i can get it to work.

---

### Post by Cresho on 2008-08-13
WOAH!  Dia-up?  So  embarrassed. :lolflag:

So if you need linux to see? what does your windows wireless drivers tell you?

---

