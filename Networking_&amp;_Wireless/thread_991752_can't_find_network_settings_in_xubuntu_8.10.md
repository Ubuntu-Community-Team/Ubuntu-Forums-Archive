---
title: "can't find network settings in xubuntu 8.10?"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by tontikki on 2008-11-24
In documentation (file:///usr/share/xubuntu-docs/internet.html#connect-to-internet) it says 

1. Open Applications &#8594; System &#8594; Network.

2. Go to the Connections tab and click the connection you wish to use to select it.

3. Press Properties to change any settings.

etc, but there is no option 'Network' when i open Applications &#8594; System? Neither there is a 'Manual configuration' option when you click on the actual icon of the connection in the task bar, which did exist on xubuntu hardy but disappeared in 8.10. 

:confused:

---

### Post by sennett on 2008-11-24
Same here.  Most odd.  I installed using wubi and had trouble so I chose another option at the install time (was it acpi disabled?  I forget), if this helps.

---

### Post by jstevans on 2008-11-25
Same here, no "Networks" under "Places."

In my case the Windows machines on my home network can "see" the Xubuntu machine and files within a folder I shared using "Applications > System > Shared Folders."  

However, the Xubuntu machine cannot see the Windows machines at all.  It can ping them just fine, but the Xubuntu machine provides no indication at all that it even knows there is a network or workgroup or that there are other machines out there on it.

A mystery indeed.

---

### Post by skompier on 2008-11-25
Right-click on the Network icon on the top bar. There should be an "edit connection" option.

---

### Post by tontikki on 2008-11-28
> **skompier said:**
> Right-click on the Network icon on the top bar. There should be an "edit connection" option.

is 'edit connections' option the same as 'manual configuration' in xubuntu hardy? 


still, why there is no option 'network' in Applications &#8594; System &#8594;, if documentation clearly says its supposed to be there?


.

---

### Post by tontikki on 2008-11-29
bump

---

### Post by J172 on 2008-11-29
In 8.10 there is a new Network Manager
System->Preferences->Network Configuration. But that is Ubuntu. It should be in Xubuntu too.

If you need to do workgroups check this thread
[http://ubuntuforums.org/showthread.php?t=980567](http://ubuntuforums.org/showthread.php?t=980567)
(specifically, this post [http://ubuntuforums.org/showpost.php?p=6276939&postcount=6](http://ubuntuforums.org/showpost.php?p=6276939&postcount=6))

---

### Post by tontikki on 2008-11-29
> **J172 said:**
> In 8.10 there is a new Network Manager
System->Preferences->Network Configuration. But that is Ubuntu. It should be in Xubuntu too.

heh i know that it *should be*, the whole problem that it is *not*:lolflag:

according to Xubuntu documentation Network Manager is to be found in Applications->System->Network. but on my machine (and it seems on some other people's too) its not there! hence the question, why..:-k

---

### Post by J172 on 2008-11-29
OHHH sorry!! Uhm..... go to terminal
nm-applet (might need sudo nm-applet)

---

### Post by 714snoopy on 2008-12-01
I have recently installed Xubuntu 8.10 twice now on two different computers and also do not see the "Network" icon that *should* be in *Applications-->System* as the docs say. In fact, I couldn't find it anywhere in the menu system. This was very frustrating for me when I was trying to setup my wireless connections. You can, however, right-click the network icon in the top-right panel area and select "Edit Connections..." as was mentioned.

BUT! I found this *replacement* network manager to be very helpful and easier to use than Xubuntu's (and Ubuntu's) default network manager: **wicd**

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It installs an icon in *Applications-->Network* and will *replace* the gnome network config tool that comes installed by default.

I have some other gripes about 8.10, like my Webcam and Sound no longer working ... but that's for another thread. Anyone else have problems like this from 8.04 to 8.10?

---

### Post by Rhemat on 2009-05-09
I installed Xubuntu 8.10 a couple of weeks ago, and the network icon was in the task bar, but I noticed it was missing yesterday.

Also, mm-applet didn't exist, and it isn't in the repositories as well.

I'll try wicd later.

---

### Post by Rhemat on 2009-05-09
Okay, I found it, and hopefully this works for everyone else too.  I right clicked on the top panel (menu bar I guess), and selected +Add New Item.  I then scrolled down and selected System Tray.  I now see Update notifications, Networking Options, Battery (I use a laptop), and Amarok (for my iPod).

I hope this helps.

---

### Post by Rhemat on 2009-05-10
Okay, I apparently spoke too soon.  Ever since I restarted, I have been getting the error message "System tray is already running" and then the system tray gets hidden (network manager, new updates, etc.).  I remember I had to add xfce Panel to the auto started apps a few days ago, because one day I booted up and it was not there.  However, I removed that from the auto-started apps, and it is still giving me the same error (but I still have the panel).  Right now, what is in my auto started apps:

Network Manager
Check for Hardware Drivers
Battery
Update Notifier
Print Queue

I'm going to uncheck those, restart, and see what happens.

==================
I still got the same error, plus I had to use nm-applet in terminal to connect to the network.  Unfortunately, Googling the problem doesn't find any related errors.  I tried redoing what I did last night [right click the top panel > +Add New Item > System Tray] but it then tells me that "There is already a system tray running on this screen."  I'm guessing it is there, it is just that once I click "Ok" on that error message, it is hidden.  I can see the bubble message that each program outputs, but I can't click on them to change them or anything else.  What can I do?

Thanks in advance.

---

