---
title: "Accidental deletion of system tray"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by BelgianKiwi on 2010-12-22
Hi Guys
 
I accidentally deleted the system tray and do not know how to get it back. How can I add it back to the desktop? 
 
I have tried a terminal command already posted for a missing System tray but the reply is telling me that I need to be a root user for the command.
 
Is there a way to change the location of the system tray as well as adding or removing it? I would like it on the bottom or the side rather than the top.
 
Please let me know.
 
Thanks

---

### Post by pastalavista on 2010-12-22
The 'Notification Area' panel app is what you're missing. System Tray is a Windows term. Right click on the panel (task bar in Windows) where you want to put it and click 'Add to panel' and select 'Notification Area'

---

### Post by BelgianKiwi on 2010-12-22
Hi there - sorry to be a bit dense, but my desktop only shows program icons and no other details. I can get the panel on right click (Which is a similar to the "Start" option in Windows) - so do I need to look in a particular option for the notification Area like system or something like that?

---

### Post by tajiknomi on 2010-12-22
> **BelgianKiwi said:**
> Hi there - sorry to be a bit dense, but my desktop only shows program icons and no other details. I can get the panel on right click (Which is a similar to the "Start" option in Windows) - so do I need to look in a particular option for the notification Area like system or something like that?

[SIZE=2]As mentioned by [/SIZE][pastalavista]("http://ubuntuforums.org/member.php?u=521710").. [SIZE=2]You just have to add the "**Notification Area**" by simply right-Clicking the panel and choose option "**Add-to-panel**", then you will be given a set of Applet..select "Notification-Area applet"[/SIZE] [SIZE=2]Or Drag it to your Desire Place in panel...[/SIZE]

---

### Post by john77eipe on 2010-12-22
I had the same problem. I figured out that this could be solved as said above. But certain applications like the volume control, once removed cannot be found anywhere to add it back on the panel. 

The sound application in System->Preferences will suffice but it's not the same as the other one.

---

### Post by Verbeck on 2010-12-22
> **john77eipe said:**
> I had the same problem. I figured out that this could be solved as said above. But certain applications like the volume control, once removed cannot be found anywhere to add it back on the panel. 

The sound application in System->Preferences will suffice but it's not the same as the other one.
volume control is part of the 'Indicator Applet'

edit: didn't notice the 'xubuntu' prefix..

---

### Post by Sir Jasper on 2010-12-22
Hi,

The advice given above is incorrect.

You should

Press and hold down the Alt key and then press the F2 function key
Release both keys then type (or copy and paste):
xfce4-panel
Press Enter and hey presto.

My regards

Now you have your tray back you can search "how to reposition it".

---

### Post by pastalavista on 2010-12-22
Yes, my bad. I didn't even notice the Xubuntu tag in the header. Sir Jasper is on the money.

---

### Post by john77eipe on 2010-12-22
> **Verbeck said:**
> volume control is part of the 'Indicator Applet'

edit: didn't notice the 'xubuntu' prefix..

Not sure if I should start a new thread as I'm using Ubuntu. 

But where do we find this 'indicator applet.'??

---

### Post by gandaran on 2010-12-22
> **john77eipe said:**
> Not sure if I should start a new thread as I'm using Ubuntu. 

But where do we find this 'indicator applet.'??
for ubuntu, right click the panel » add to panel » indicator applet

---

### Post by spillage2 on 2010-12-22
Once your sorted see thread below. I have posted code for a .sh file to save your setting once done and restore if needed in the future.

[http://ubuntuforums.org/showthread.php?t=1595798](http://ubuntuforums.org/showthread.php?t=1595798)

---

### Post by john77eipe on 2010-12-22
thanks gandaran.

---

### Post by BelgianKiwi on 2010-12-22
All sorted thanks guys - Sir Jasper - You Rock!!

---

