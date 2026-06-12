---
title: "Network Ubuntu Laptop to Wired Desktop. Simple right?"
date: 2017-10-16
forum: Networking &amp; Wireless
---

### Post by sdsurfer on 2017-10-16
Fairly new to Ubuntu but can provide details and logs if required. I simply cannot get my wireless connected laptop to "see" the network share from my Ubuntu 17.04 desktop. 

Please presume I have spent at least six hours in Google searching for solutions, because I have.

Briefly,

SYMPTOMS: The wireless laptop can easily see and connect to my **Windows** network (when the desktop has Windows booted up, and the third Windows 8 desktop) but refuses to see/recognize the second desktop when it is booted in Ubuntu. When I open "Other Locations" on the laptop, I see "Windows Network" then "[Ubuntu desktop]"-> $print" and the third Windows computer shares. No shared directories from the Ubuntu desktop.

SHARED: 2.8 Ghz Pentium desktop, Ubuntu 17.04, sharing a directory in ~home. This is a dual boot machine with Windows 7 on one drive and Ubuntu 17.04 on the second.

REQUESTING: 3.8 ghz 8 core System76 Gazelle laptop, connecting to the network modem wireless.

THIRD MACHINE: A Windows 8 machine which has no context in the issue other than it is there and can see it in "Windows Network" and access all shared files.

MODEM: This is a Cox Communications modem, combination router and cable router. **All Internet connections, wired and wireless, are fine.**

What I've done (tons more, but as briefly as possible: ) From the Ubuntu 17.04 desktop, enabled a directory to be shared. Samba is installed on both computers. Aligns with the official Ubuntu guide and any of the gazillion instructions on the Internet. :-)

When I go to Other Locations on the laptop, I see the current computer of course and "Windows Network." This opens the shared directories of the third Windows-only computer fine, and if I boot the second dual boot shared computer into Windows, shows those shares just fine.

When the second computer is in Ubuntu, nada, zilch, nothing. Still only shows "Windows Network."

I know I am missing something basic. Any ideas?

---

### Post by Kirboosy on 2017-10-16
What happens if you try to manually connect to the server with the IP address? 

```
[COLOR=#333333][FONT=monospace]smb://<serverIP>/<ShareName>[/FONT][/COLOR]
```

---

### Post by sdsurfer on 2017-10-27
Sorry for the late reply Caboose885, and thank you, I'd given up on this thread and didn't have notifications on. To answer the question, nada, I could ping both computers, connect via command line, and have been through every how-to, setup document,  mailing list, and obscure note on the Internet to no avail. Purged Samba and reinstalled at least twice, painted myself into that dark corner where I can't recall what I tried and didn't try any more. But then . . . 

**TODAY IT IS SOLVED!** I hope this helps others with the same problem (there are tons of threads and  questions out there.) I have to give kudos to System76 support, since my Gazelle is still under warranty, in my  desperation I turned to them with a support ticket. At first one of the techs was like "this is really complicated, don't think we can help" but asked (okay, begged) he confer with other techs there, System76 is an awesome team.

It appears my GVFS package was broken, that is all! This is under Ubuntu 17.04, 

```
[LEFT][COLOR=#574F4A][FONT=&amp]sudo apt install --reinstall gvfs-backends[/FONT][/COLOR][/LEFT]

```[LEFT][COLOR=#574F4A][FONT=&amp]

[SIZE=2]Reboot.

[SIZE=4]***BAM!***[/SIZE]
[/SIZE]
[/FONT][/COLOR][/LEFT]
All shares restored across the board, everything is working. I can get back to actually doing some work now. :-)

---

### Post by sdsurfer on 2017-10-27
**POST NOTE:** in the original post I was able to see the "Windows Network" but in my efforts to fix it, that went away too. The previous reinstall fixed it ALL. :-)

---

