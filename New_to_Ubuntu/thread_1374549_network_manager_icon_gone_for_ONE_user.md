---
title: "network manager icon gone for ONE user"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Kilarin on 2010-01-06
running ubuntu 9.10 on a family laptop.  both my son and I have accounts with admin rights.  When we first set everything up, BOTH of us had the wireless icon on the panel and all was fine.  My son was playing with his panel one day, and somehow lost the wireless icon.  It's still there for MY account though.

For a while, my account could connect to the wireless just fine, but his couldn't.  On MY account I went into System/Preferences/Network Connections/Wireless, edited our connection, and clicked "Available to all users" and suddenly my son can connect to the web, even when I am not logged on.  Might have just been coincidence though, because he now shows two identical wireless connections in "Network Connections".

BUT, he's connected, but still no wireless icon, so no way to bring up the network manager window.

I've looked at this thread: [http://ubuntuforums.org/showthread.php?t=415835](http://ubuntuforums.org/showthread.php?t=415835)

And I've confirmed that Network Manager IS checked in the startup applications.

I've attempted to add "Notification Area" to his panel, double clicking "Notification Area" doesn't do anything.

I CAN run Network Manager from the terminal in his account using:
nm-applet --sm-disable

And it runs, and puts a wireless icon on his panel!!!!!

BUT, as soon as you close the terminal, or reboot, it goes away.

I'm missing something obvious here.  What do I need to do to get the network manager back onto his panel?

thanks!

---

### Post by tom.swartz07 on 2010-01-07
> **Kilarin said:**
> running ubuntu 9.10 on a family laptop.  both my son and I have accounts with admin rights.  When we first set everything up, BOTH of us had the wireless icon on the panel and all was fine.  My son was playing with his panel one day, and somehow lost the wireless icon.  It's still there for MY account though.

For a while, my account could connect to the wireless just fine, but his couldn't.  On MY account I went into System/Preferences/Network Connections/Wireless, edited our connection, and clicked "Available to all users" and suddenly my son can connect to the web, even when I am not logged on.  Might have just been coincidence though, because he now shows two identical wireless connections in "Network Connections".

BUT, he's connected, but still no wireless icon, so no way to bring up the network manager window.

I've looked at this thread: [http://ubuntuforums.org/showthread.php?t=415835](http://ubuntuforums.org/showthread.php?t=415835)

And I've confirmed that Network Manager IS checked in the startup applications.

I've attempted to add "Notification Area" to his panel, double clicking "Notification Area" doesn't do anything.

I CAN run Network Manager from the terminal in his account using:
nm-applet --sm-disable

And it runs, and puts a wireless icon on his panel!!!!!

BUT, as soon as you close the terminal, or reboot, it goes away.

I'm missing something obvious here.  What do I need to do to get the network manager back onto his panel?

thanks!

Im not exactly sure what the problem may be, but you could get the program to run from the terminal even after you close it by adding an & after it. So you would have ```
nm-applet --sm-disable &
```

Perhaps you could add the command to your startup applications?

If worse comes to worst, you could always wipe all of the panel settings and start anew
```
sudo rm -rf ~/.gconf/panel
``` and logout/login. This will remove any changes to the panel and you will end up with a 'fresh install' panel next log in.

---

### Post by Kilarin on 2010-01-10
[quote="tom.swartz07"]sudo rm -rf ~/.gconf/panel[/quote]
I had to modify this a bit to get the panel to go back to defaults.  Ended up using (from [<here>](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html))

gconftool – -recursive-unset /apps/panel 
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

Which DID get me a new default panel, but NO NETWORK ICON.  Insane, that should have worked!

[quote="tom.swartz07"]nm-applet --sm-disable &[/quote]
Oddly enough, even with the ampersand, when I close the terminal, the network icon goes away.  Very odd.  
I did try putting the command into a launcher.  That successfully puts the network icon on the panel, but, of course, you have to relaunch it every time.
The next step would be, as you said, to put it into the startup apps, it may come to that, but surely there is some way to just get the icon back normally!

Anyway, it still feels like I'm missing something basic that is wrong here, and fixing the problem backwards.  BUT, this fix DOES work, and thank you VERY much for helping to get there.

Any advice on whats actually wrong and how to fix it normally would still be appreciated.

---

