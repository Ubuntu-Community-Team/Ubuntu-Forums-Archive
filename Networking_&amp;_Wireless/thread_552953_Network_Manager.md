---
title: "Network Manager"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by coolth3 on 2007-09-17
I somehow deleted the Network Manager applet from my panel. Now , I can't seem to find the applet anywhere (Well, anywhere in the GUI). Network Manager is running and connecting to my wireless router at home as usual, except that I can't see the applet telling me the signal strength and other networks available, etc (whenever it connects to my router a notification appears telling me it has done so). I really like the Network Manager applet, it comes in handy since I take my computer to school and it makes it easy to switch on and off of different wireless networks that are available. How do I get the applet back? I already tried uninstalling the Network Manager and installing it again through the Update Manager and I even "completely" removed the Network Manager using the Synaptec Package Manager and installed the application again. Any help will be appreciated.

---

### Post by z0mbie on 2007-09-17
Make sure in System > Preferences > Sessions, **Network Manager** is checked. Then logout and login.

Also if you reinstall something you're old config files stays. To remove everything including config files use **sudo aptitude purge remove packagename**

---

### Post by spd106 on 2007-09-17
Make sure that you have a notification area on the panel, it looks like two vertical columns of six dots. You can add it by right-clicking, then Add to panel... select notification area in the box that appears and click Add.

---

### Post by unisol on 2007-09-17
after you reinstall nm, if it doesn't show up, try this:

System > Preferences > Sessions

Under Startup Programs, check for Network Manager. If it's there, make sure it's checked off. If it's not there, you may need to re-add the entry:

1) Click New
2) Make name "Network Manager"
3) Make command "nm-applet --sm-disable"
4) Click OK
5) Hit Ctrl + Alt + Bksp to restart GNOME

---

### Post by coolth3 on 2007-09-17
thanks! This worked out perfectly.

---

### Post by shimumu on 2007-10-03
I have a different problem with Network Manager. I think it is the applet I used to use to connect to the Internet before I reinstalled, but it looks and acts differently now.

It used to look like a series of gradually ascending bars, indicating signal strenth. Now it looks like two monitors, one in front of the other. If I moused over it before, it gave the name of the wireless network I was connected to, and the strenth. When I mouse over it now it says "Manual Network Connection" And when I clicked it before, it gave me list of wireless networks it saw, also indicating if they were open or locked. If I click on it now, it give me a menu of one choice, Manual configuration, which takes me to the Network Settings control panal.

Is there a way I can get Network Manager to look and act like I've described? Or, am I thinking of a different applet?

---

