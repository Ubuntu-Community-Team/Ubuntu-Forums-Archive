---
title: "bluetooth tray icon not visible"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by agibby5 on 2008-06-19
for some reason, my 7.10 system doesn't have the bluetooth icon in the tray.  It never shows up.  My settings in Bluetooth Preferences indicate that it should always be shown.  I even tried changing this option to see if it would ever show up.  Still not visible in the tray area.

Any ideas?

---

### Post by azior on 2008-06-20
I have the same, but I know why.

My Toshiba laptop has turns the power to bluetooth on using software in Vista. Ubuntu clearly lacks that.

There is a way however to enable bluetooth in Ubuntu. Boot to Vista. Restart (don't shutdown) and reboot into Ubuntu. Bluetooth is still powered, so it works in Ubuntu!

I hope this helps a bit. Otherwise could you tell what kind of desktop/laptop you've got?

---

### Post by agibby5 on 2008-06-20
I have a Dell XPS M1330. My bluetooth works fine. I just want the tray icon so I can get the functionality that comes along with it.  No matter what I do, that icon is still missing.

---

### Post by agibby5 on 2008-06-23
Is this in the right place?  Has anyone else experienced this?

---

### Post by Schendje on 2008-08-17
I had the same problem, but I found out I had deleted the Bluetooth Applet from Sessions, so it wouldn't start when I logged in.

If you guys have the same problem, simply add the command "bluetooth-applet" to your Sessions, log out and log in again.

Without the bluetooth-applet, no little windows will pop up asking for a password or things like that. I couldn't connect to my phone because of this. But all is fine now. :)

---

### Post by dedyisn on 2008-11-11
Thank you for the tips
its same with me
I delete this in session 

How About the network applet ?
cause i'm losing it too

Thanks for your reply

---

### Post by mr.interested on 2010-10-26
It's an old thread, but the problem is still in Ubuntu 10.10. When I go to Preferences --> Bluetooth, the option "Show Bluetooth icon" is ticked. The only way to show the icon is to untick the option, restart OS, and then tick the option again. The icon is then visible, but then again in disappear after some unspecified time.

---

### Post by code_linux on 2011-01-04
I have the same problem, the bluetooth icon would randomly disappear after resuming from standby! However the bluetooth works as normal and my BT keyboard connects as usual but no BT icon. 
Finally I found that the process "bluetooth-applet" was not running. Press Alt+F2 to get the "Run Application" window and type in the command "bluetooth-applet" and run. The BT icon is back with all its neat features and I don't have to restart the machine! :) Hope this helps.

---

### Post by pkkid on 2011-07-27
> **code_linux said:**
> Finally I found that the process "bluetooth-applet" was not running. Press Alt+F2 to get the "Run Application" window and type in the command "bluetooth-applet" and run.

Thanks, this was exactly my problem.  I also have some annoying issues with audio quality dropping (cutting in and out) until I tinker with settings a bunch each time this happens.

---

### Post by bwanamarko on 2013-01-09
In 12.10 (Quantal Quetzal) my bluetooth indicator is also disappearing intermittently. It is always on when I boot up, but at some point disappears. There is no switch System Settings to make it always appear, nor is there any bluetooth-applet that comes up in the unity dash. However, `ps -e | grep blue` shows that bluetooth-applet is indeed running, and bluetooth is functional - ie I can use bluetooth - even when the indicator disappears. One trick that worked to get the indicator back, and the nice context menu that comes with it is to use the keyboard switch to cycle all radios, which unfortunately also turns of the wifi, but when I cycle the radios back on, the bluetooth indicator reappears.

---

### Post by Elfy on 2013-01-09
This is a 4 year old thread, if you need help I suggest you start a new thread. Closed.

---

