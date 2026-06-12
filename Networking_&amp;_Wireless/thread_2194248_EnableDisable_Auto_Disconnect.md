---
title: "Enable/Disable Auto Disconnect"
date: 2013-12-17
forum: Networking &amp; Wireless
---

### Post by kingcobraa on 2013-12-17
Hi,

You know that small indicator applet on the system tray of Ubuntu?

This allows us to edit the connections, make new connections, connect to the internet etc.

It looks like 1 arrow pointing upwards and the other arrow pointing downwards.

I would like to know how to make this possible and my query is below.

IF my internet connection is idle for xyz seconds, minutes or hours then networking is to be disabled by an automatic un-checking of the "enable networking option" in the drop down menu. When I need to reconnect to the internet then I would need to manually click the enable networking option.

I know this is possible but don't know how to get it done. Can someone show the commands?

---

### Post by varunendra on 2013-12-20
The icon you mentioned is called "nm-applet" (can be killed from "System-Monitor" and restarted from either terminal or "Alt-F2" > "nm-applet"), and ticking/un-ticking the "Enable Networking" option edits a file "/var/lib/NetworkManager/NetworkManager.state" to enable/disable networking support by Network Manager (the program whose "nm-applet" is just a frontend).

If you wish to automate detection of a connection state, and/or enable/disable a particular connection, you should look at the man page of "nmcli" command.

Although you can also write a script to manually the file that is edited by putting/removing tickmark from the "Enable Networking" option, using nmcli command would be better for most cases.

---

### Post by kingcobraa on 2013-12-20
yes. that is all fine. but what i want to do is have it disconnect automatically if connection is idle for a prespecified amount of time then reconnect when i open my browser and go to my homepage

---

### Post by varunendra on 2013-12-20
For that you'll have to permanently keep running a script in background that checks the traffic stats after every desired amount of time, and if it seems idle (no significant change in the stats), disconnects the connection.

Then you can edit your browser's .desktop file to change the actual command that runs when you click its icon. You can change it in such a way that it activates the connection first (or runs a script that does it properly), THEN opens the browser.

The catch in this plan is that usually a connection is almost never 100% idle. So you need to decide the limit of the traffic below which you can safely consider it "idle". Also, the plan about editing the .desktop file will only work when the icon of the desired browser is clicked. Only that clicking action would automatically activate the connection again.

If you think this makes sense, please study the "nmcli" command and let me know what you come up with. I am interested in helping, but only if you seem to be doing some homework yourself. I can help with the automation part, but you'll have do some experiments yourself to make sure the commands can do what you want them to do.

---

### Post by steeldriver on 2013-12-20
You could probably use the DBUS monitor and/or notify capabilities - either through the command-line dbus-monitor interface (ugly! painful!) or through the python or Qt APIs

[http://stackoverflow.com/questions/11544836/monitoring-dbus-messages-by-python](http://stackoverflow.com/questions/11544836/monitoring-dbus-messages-by-python)

[http://askubuntu.com/questions/38733/how-to-read-dbus-monitor-output](http://askubuntu.com/questions/38733/how-to-read-dbus-monitor-output)

[http://dbus.freedesktop.org/doc/dbus-monitor.1.html](http://dbus.freedesktop.org/doc/dbus-monitor.1.html)

Hope this gets you started - good luck!

---

