---
title: "network manager on panel"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by jbdz5 on 2006-10-31
i accadentally removed my network manager from my panel, what can i do to get it back?  i dont know where the file is, but i set it all up according to this.. [http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom) thanks for your help.

---

### Post by Cynical on 2006-10-31
right click on the panel and choose add, then in the search box type network.

---

### Post by saxsux on 2006-10-31
Cynical - that's **Network Monitor**, he's talking about Network **Manager**.

To bring back the Network Manager tray icon, create a launcher (right click on the desktop > Create Launcher), and set the command to "nm-applet", without the quotes. Give it a name, click OK, and double click the icon your desktop.

You can also run the command "nm-applet" from a terminal, but it means that the icon will disappear when you close the terminal.

Hope this helps :-)

---

### Post by Cynical on 2006-11-03
Are you sure? I don't really see how he removed network manager without going into sessions and disabling it...

---

### Post by naxcz on 2006-11-03
I have same problem. I removed Network Manager (by Synaptics) and then install it again and now I can't see nm-applet. It running and also I found it in System/Sessions configuration, but on panel there is no more it's icon.

When I kill running nm-applet and run it by hand I get this errors:

```

(nm-applet:8683): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
...
nma_dbus_init() could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.20" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

```

If I add to /etc/dbus-1/system.d/NetworkManager.conf
```

--- NetworkManager.conf.bak     2006-11-03 22:14:24.633888702 +0100
+++ NetworkManager.conf 2006-11-03 22:16:26.676372966 +0100
@@ -13,6 +13,7 @@
                 <allow send_interface="org.freedesktop.NetworkManager"/>
         </policy>
         <policy at_console="true">
+                <allow own="org.freedesktop.NetworkManagerInfo"/>
                 <allow send_destination="org.freedesktop.NetworkManager"/>
                 <allow send_interface="org.freedesktop.NetworkManager"/>
         </policy>

```

It run from console, but applet still is not able to configure anything (it say there is no network interfaces which is not true). Can someone with working nm-applet attach working copy of configuration?

---

### Post by naxcz on 2006-11-04
I [found]("http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-45c7dcb29a13372e1da1221b5ed499d981ea7ec6") why I can't see any networks in applet.

---

### Post by dr_d12 on 2007-01-26
I just did the same thing as jdzb5 - Network Manager is configured and running, but I removed the icon from my panel and need to put it back. In my startup sessions I have "nm-applet --sm-disable" but from terminal "nm-applet" doesn't do anything.
Thanks for your help,
Dave

The following didn't work for me (launcher or terminal):

> **saxsux said:**
> 

To bring back the Network Manager tray icon, create a launcher (right click on the desktop > Create Launcher), and set the command to "nm-applet", without the quotes. Give it a name, click OK, and double click the icon your desktop.

You can also run the command "nm-applet" from a terminal, but it means that the icon will disappear when you close the terminal.

Hope this helps :-)

---

### Post by dr_d12 on 2007-01-26
Simple solution (for my problem and I beleive for the original post):
Right click on the panel, select "+add to panel", and under "utilities" select and add "Notification area".

---

### Post by lazychris2000 on 2007-02-17
I am having the same problem.  when i open a terminal and run 'sudo nm-applet &', it works, but when I run it as my normal user, I get:
> 
** (nm-applet:4995): WARNING **: <WARNING>      nma_dbus_init(): nma_bus_init() could not acquire its service. dbus_bus_acquire_service() says: 'Connection ":1.14" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

It's really annoying that I have to manually run the program when I log in.  Also, I don't know if it's related or not, but it doesn't use the gnome-keyring to store WEP keys.  I have to manually enter it each time I log in.

gnome nm-applet 0.6.3 (installed using apt-get)
gnome 2.16.1
Ubuntu Edgy
see signature for specs (this is on the latitude)

any help would be greatly appreciated!

---

### Post by lazychris2000 on 2007-02-17
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)
I just found that link and it fixed all my network-manager problems.  hope that helps you guys!

---

### Post by |Porsche on 2007-07-19
To add the icon back to the panel just right click on the panel>add to panel>Notification Area>Add

Hope it helps.

---

