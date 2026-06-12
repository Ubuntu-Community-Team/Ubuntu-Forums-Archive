---
title: "&quot;Reboot into ...&quot; option"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Blutkoete on 2010-05-05
Hello!

I'm using both Windows 7 and Ubuntu 10.04 on my computer, with Ubuntu 10.04 as the default in the GRUB menu.

I was wondering whether it is possible or not to add a script/or an option somehow to my user menu in Ubuntu so that the computer reboots into Windows without me having to chose Windows in the GRUB menu. For clarification, like this maybe:

() Log on as another user
() Log off
() Restart
() Restart into Windows
() Turn off the computer

To put it simple, picking "Restart into Windows" should restart the computer and tell GRUB to start Windows automatically (but only that one time, use Ubuntu as default afterwards again).

That way I could just hit the "Restart into Windows" button, go to the kitchen, make some coffee and return to my computer with Windows already ready, skipping the waiting for the GRUB menu.

Is something like that possible?

Thank you very much!

---

### Post by mörgæs on 2010-05-05
Agree. You can vote for that idea here: 

[http://brainstorm.ubuntu.com/idea/18890/](http://brainstorm.ubuntu.com/idea/18890/)

---

### Post by Sealbhach on 2010-05-05
The quickest way to change to default OS is to install startupmanager, you can change the default OS to Windows, but you would need to change it back again once you go back into Ubuntu.

It updates the grub.cfg file, so it doesn't allow for a "one time only" change.

You can find startupmanager in Synaptic Package Manager.

.

---

### Post by Blutkoete on 2010-05-05
Great, thank you. I promoted the solution :).

And I'll have a look into the startup manager.

---

