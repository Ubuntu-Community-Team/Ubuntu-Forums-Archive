---
title: "Quick Question"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by Jon11393 on 2008-05-29
Hello! I have a problem. 

I accidentally removed a wireless network selector icon from my panel (not very descriptive, I know). 

I don't know how to get it back, or how to connect to wireless networks without it! 

Please tell me how to reattach it to the panel. Thanks!

It's on hardy, if that matters.

---

### Post by Jon11393 on 2008-05-29
Bump :P

---

### Post by MeURi on 2008-05-29
Do you mean the nm-applet? If so, check under your session preferences that it is loaded whith Gnome (otherwise enter *nm-applet --sm-disable* as command and name it whatever you prefer)

nm-applet should be a part of package *network-manager-gnome*, if I'm correct

If you used other tools to connect to the wireless, maybe it's the same issue... or maybe not

---

### Post by Jon11393 on 2008-05-29
Yea. But when I typed

> 
nm-applet 


Nothing happens in the terminal.

---

### Post by Jon11393 on 2008-05-29
I basically just want to add the nm-applet back to the panel... 
or figure out how to connect to wireless networks without manually clicking on the drop-down from the icon.

---

### Post by MeURi on 2008-05-29
It loads into the notification area

It works for me either issuing *nm-applet* or *nm-applet --sm-disable* from the terminal

Under System>Preferences>Sessions I have this (see attachments)

If it doesn't work for you, try reconfiguring network-manager-gnome via *dpkg-reconfigure*

Hope this helps

EDIT:

For the manual connection to the wireless, I'm not the right one to ask :-P

EDIT 2:

I HAVE to go to sleep now, tomorrow I have to get up early and study study study

---

### Post by Jon11393 on 2008-05-29
Thanks! 

Hope you do well on your test. :)

---

### Post by MeURi on 2008-05-30
Actually, not a test :-P

I'm working on my thesis (second level degree at Politecnico of Milan)

And thanks for your "thanks" :-)

---

### Post by phos4us on 2008-05-30
> **Jon11393 said:**
> Yea. But when I typed



Nothing happens in the terminal.

Running 'nm-applet &' should run the network manager and return you to the prompt. If this does not happen make sure that you have a notification area on one of your panels. Perhaps you removed the notification area from your panel and not the applet itself.

HTH

Regards
Andrew

---

### Post by james_vanb on 2008-05-30
If the Network Manager has just been removed from the panel, try right clicking on the panel - look for the icon in the drop down menu - drag and drop it back onto the panel.  If you've accidentally uninstalled it, I think you can reinstall through Synaptic.

---

