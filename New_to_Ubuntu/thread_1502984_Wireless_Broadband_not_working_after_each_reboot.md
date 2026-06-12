---
title: "Wireless Broadband not working after each reboot"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by Narpstar on 2010-06-06
Hi everyone!

My name is Ben and I just installed Ubuntu for the first time a couple of days ago, and I've been LOVING it. Huge thanks to all those who contribute to the project.

I'm only really experiencing one problem and that is that every time I reboot my PC, my wireless broadband connection stops functioning.

I've got a Hauwei e122 with Three, and when I first connected it to the computer, it automatically appeared in my network connections, and installation was straight forward and simple. I just followed the prompts through Network Manager. I was browsing with Firefox and everything. However, after I had shut down the computer and booted it back up again, the connection was no longer available. The device still appears in my Places folder, as both a CD Rom and an SD Card device, but it doesn't appear to recognise it as a modem anymore. 

In an attempt to fix it, I deleted the network connection and tried to set it up again through Network manager, but to no avail. Then, after several reboots, it suddenly recognised it again as a modem, and I was able to use it once again.

Unfortunately this problem keeps reoccurring and I have no idea what's causing it, or what's "fixing" it. Could someone please point me in the direction of a solution? I'm loving Ubuntu and I want it to replace my copy of Windows, but I can't do that until I sort this one out!

Cheers guys,
Ben

---

### Post by gandaran on 2010-06-06
try installing *usb-modeswitch* and *usb-modeswitch data* from synaptic or apt-get, maybe it can help.

---

### Post by Narpstar on 2010-06-06
Great thanks Gandaran :) I've just installed them... we'll see how we go!

---

### Post by Narpstar on 2010-06-06
:( No love!

I was using the internet in Ubuntu again, no problems! Then reboot> stops working. I click on the networking icon near the top right hand corner and the wireless broadband option no longer appears there, and I cannot connect.

I was browsing for some more info and came across this, which seems to relate to my problem: [http://swiss.ubuntuforums.org/showthread.php?t=1400240](http://swiss.ubuntuforums.org/showthread.php?t=1400240)

Only issue here is they are referring to a vodafone account, and mine is with 3. I don't know what settings to use!

Any tips?

---

### Post by 4Orbs on 2010-06-06
I can offer a suggestion, but I have no substantial evidence that it will fix your problem... except that it seemed to work for me last year when I was using a Cricket wireless usb modem. I came to the conclusion that the intermittent  problem was caused by the Ubuntu Update Manager (set to auto update) which was trying to connect to the network before the modem had a chance to finish it's connection process, thus killing the network connection in mid-connect. I turned off the auto-updating in the Update Manager settings and my modem began connecting more consistently and reliably. Sometimes it would connect quickly, other times it would take a while longer.

---

### Post by Narpstar on 2010-06-08
This appears to have fixed the problem! Thanks 4Orbs! And thanks heaps everyone :)

Cheers,
Ben

---

