---
title: "Skype microphone sound too soft"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by qvyang on 2009-02-14
I'm having trouble setting up the microphone in Skype.
The sound is too soft for anyone to hear.
The microphone works perfectly fine if I switch to Windows.
Anyone know how to set this up properly? Thanks!

---

### Post by treesurf on 2009-02-15
Have you tried adjusting the microphone input level?  Double click on the volume applet in you taskbar.  Under the recording tab you can adjust the microphone levels.  If you don't see this tab click on Edit>Preferences and click all the little boxes to make all the options appear.

---

### Post by qvyang on 2009-02-21
they are all set to the max already, but still...

---

### Post by markbuntu on 2009-02-21
You need to set the capture level for the mic, that is what skype uses. If you have a mic boost switch you need to enable it.

---

### Post by Miljet on 2009-02-21
Click on the Skype main menu in the bottom left of the Skype window, select options, then sound devices. Try selecting different options until the sound works. I had to select "Intel hd0", but yours may very well require some other setting.

---

### Post by orinoco_w on 2011-04-25
> **Miljet said:**
> Click on the Skype main menu in the bottom left of the Skype window, select options, then sound devices. Try selecting different options until the sound works. I had to select "Intel hd0", but yours may very well require some other setting.

I had the soft microphone problem. I managed to fix mine by clicking the volume icon in the task bar, then choosing Sound Preferences, then finding that my settings were on Microphone 1 - I put it to Microphone 2 and voila! it worked.

Hope yours is an easy fix like that!
:D

---

### Post by rosencrantz on 2011-04-25
I seem to say this a lot, but try pavucontrol :-) Also, in Skype Options -> Sound Devices, try whether it makes a difference if you allow Skype to adjust mixer levels.

---

