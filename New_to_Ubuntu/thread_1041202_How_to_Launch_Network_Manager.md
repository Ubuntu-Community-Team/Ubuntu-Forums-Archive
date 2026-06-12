---
title: "How to Launch Network Manager"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by kelmark2180 on 2009-01-16
I cannot find a way to launch network manager. I can see this Ubuntu machine from Windoze but I have no idea how to exec NM on this side to see the Windows network. I saw on another thread to R/click and add a program launcher. No idea what the needed config params are though. 

Poking around, I see that NM has been auto started. I just don't know a method to exec it. I have no idea why the install did not automatically give me an icon since I have not done anything to (Ubuntu 8.10 new install) except install Mythbuntu. Is there a way to get back to just Ubuntu, all I have after install is Mythbuntu. I'm lost and would appreciate any guidance.

Thanks; Don

---

### Post by zvacet on 2009-01-16
> I can see this Ubuntu machine from Windoze

Does this mean that you are trying to start nm-applet from Windows?If so I don't think it will work.You have to be in Ubuntu to start it and set up your network.Sorry if I misunderstand you.

---

### Post by kelmark2180 on 2009-01-16
> **zvacet said:**
> Does this mean that you are trying to start nm-applet from Windows?If so I don't think it will work.You have to be in Ubuntu to start it and set up your network.Sorry if I misunderstand you.
Thanks, but that was just a comment that I can see Ubuntu from windows but not vice versa.

---

### Post by Nepherte on 2009-01-16
The network applet can be launched with:
```
nm-applet
```

A terminal will spit out errors if there are any.

---

### Post by kelmark2180 on 2009-01-16
I keyed into a terminal window and just had warning
** (nm-applet:7478): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

I did same before in program launcher, maybe thats why the warning, Still nothing really launched so I could see any network or other computers. There are now two other windows machines connected besides this Ubuntu.

---

### Post by Nepherte on 2009-01-16
nm-applet appears to be already running. To be sure you can verify it with:
```
pidod nm-applet
```
If a number shows up, it's running.

Did you add the notification area to the gnome panel?

---

### Post by kelmark2180 on 2009-01-16
I guess I'm lost.
dwb@dwb-desktop-U:~$ pidod nm-applet
bash: pidod: command not found

"Did you add the notification area to the gnome panel?" I added a program launcher but I don't think it's set up correctly. all I see is an icon that says it has not been configured on the mouse over.

---

### Post by Nepherte on 2009-01-16
Oops, it should be
```
pidof nm-applet
```

To add the notification area to the gnome panel, right click on the panel and choose "add applet". Look for notification area.

---

### Post by kelmark2180 on 2009-01-16
dwb@dwb-desktop-U:~$ pidof nm-applet
5798
I managed to add icons of what's running, just (browser,email,term window) is running.
My R/click panel options are add, do that and it lists only additional items to panel are: ((No notification area choice)?)
launcher
action btns
clock
icon box
pager
separator
show desktop
system tray
task list
trash
volume
window list 
xfce menu

---

### Post by kelmark2180 on 2009-01-16
I'm dense, it may already be there since I get email and software updates. Duh

---

### Post by 11lettenJ on 2009-01-18
Thanks alot, I accidentally deleted this from my panel as I installed a vista style panel. I kept looking around for in my commands for anything with wireless or networks in it and got nowhere. I had no clue it was under notifications, thanks

---

