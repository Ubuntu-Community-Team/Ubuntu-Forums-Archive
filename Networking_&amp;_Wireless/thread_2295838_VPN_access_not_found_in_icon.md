---
title: "VPN access not found in icon"
date: 2015-09-21
forum: Networking &amp; Wireless
---

### Post by dkolars on 2015-09-21
Just upgraded my desktop from 12.04 to 14.04...  I have a VPN and a wired Ethernet connection...  I upgraded my laptop a few months ago, and it retained the icon in the panel that will let me select between the Ethernet and VPN connection...  but, when I upgraded the desktop, there was no networking icon installed in the panel... and, I can find the "Network Connections" button that will show me the 2 available connections, but there is no way to switch between them?  The laptop has a nice pop-up menu with options for listing the Ethernet network, Wi-Fi networks, Cable WiFi, Connect to Hidden Wi-Fi Network, Create New Wi-Fi Network, VPN Connections, Enable Networking, Enable Wi-Fi, etc. etc.

I can find no menu item to add to the Panel that will give me the option to switch connections as existed in 12.04.  Any clues?  TIA  DK

---

### Post by Toz on 2015-09-22
Try running:
```
nm-applet
```
...in a terminal window to see if it brings back the panel icon.

---

### Post by dkolars on 2015-09-22
Nope... when I run that in Terminal, cursor goes to 2nd line, nothing happens... Ctrl-C yields:  
> dk@Desktop:~$ nm-applet^Cnm-applet-Message: PID 0 (we are 10789) sent signal 2, shutting down...


Looking at the executables in my /usr/bin/ dir I have:  nm, nm-applet, nmcli, nm-connection-editor, nm-online, nm-tool...   The nm-connection-editor is the one that brings up the display of available networks.  The others do nothing when selected.  Still no menu box that would let me switch my connection.

As an aside, I'm also finding a few other programs that I've used for several releases of Ubuntu or Xubuntu that now don't work in 14.04...  grrr...  Wish upgrades didn't require hours of time to "make it right" again...

---

### Post by Toz on 2015-09-22
Do you have the **Indicator Plugin** added to the panel?

---

### Post by dkolars on 2015-09-22
Ah, that is problem... I just added it, but now have 31 up-down arrow indicators for Networking, one for sound, one for system logout/etc.  Also have the time, but I already had that as Date & Time???  Panel now has expanded to cover part of other panel...  I only really need 1 Network indicator :-)  Can see no way to edit in the Indicators pop-up menu...  Is there a file to edit somewhere?  TIA

---

### Post by dkolars on 2015-09-22
OK, marking this as "Solved"... did a bunch of reading on-line...  ended up shutting down the system, re-starting, and I now have one Networking indicator, along with Temp, Sun/Moon, Power Management, Sound, Time.  Still can find to way to re-arrange, format, or eliminate any of them, however.

---

### Post by Toz on 2015-09-22
> **dkolars said:**
> Still can find to way to re-arrange, format, or eliminate any of them, however.
Right click on the Panel and select Panel > Panel Preferences, and go to the items tab. There you can sort the order and edit the properties of the individual plugins.

---

### Post by dkolars on 2015-09-23
[ATTACH=CONFIG]264608[/ATTACH]No, that doesn't work... The Indicator Plugin doesn't appear to allow any fiddling with its contents...  Nothing I do with the boxes seems to have any effect.  So, I have the Time shown in the Plugin, but I have the DateTime shown as well in a Launcher... would like to eliminate the Time from the Indicator Plugin...  No bigee, but surely would think that it would be more customizable than it is.

---

### Post by Toz on 2015-09-23
Click on the "hidden" box next to the DateTime component. You need to restart the panel for it to take effect:
```
xfce4-panel -r
```

---

### Post by dkolars on 2015-09-23
OK, that ~finally~ worked... what a hassle...  1st, I could not check any boxes, so had to remove and reinstall... then could check the Hidden box for DateTime, but ended up with two sound icons.  Hid that and got "Indicator Hidden" message in its place + a sound icon???  Ran the [COLOR=#000000][FONT=Ubuntu Mono]xfce4-panel -r[/FONT][/COLOR] command several times, and it finally put it right.  Thank you!!

---

