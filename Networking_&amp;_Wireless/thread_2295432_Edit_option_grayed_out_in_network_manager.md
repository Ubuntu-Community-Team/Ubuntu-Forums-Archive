---
title: "Edit option grayed out in network manager"
date: 2015-09-18
forum: Networking &amp; Wireless
---

### Post by Halbarad on 2015-09-18
Hi, Lubuntu 14.04 here. If I right click the icon of network manager, the only available option is "Connection information", the other three (Enable Networking, Enable Wi-Fi and Edit Connections) are grayed out. I cannot remember when this began, I just know that they were active and responsive some months ago. Both the wireless and the ethernet work flawlessly, though.
I tried to reboot and to restart nm,
> sudo service network-manager restart
I also checked /etc/NetworkManager/NetworkManager.conf, but it regularly reads "managed=true".
I can still edit my connections by running nm-connection-editor from the terminal.
Another thing is, if I right click anyone of the two little icons with two screens in them (I don't know what they are called) a little menu appears with options to "Repair" and "Disable". However, if I choose "disable" nothing happens. When I right click the nm icon, "Enable Networking" and "Enable Wi-Fi" are still grayed and checked by default.
I have a feeling that the connections are being managed automatically but they are substantially out of my control. Or this might be the first symptom of a problem.
I have browsed a bit and I have seen that lots of people have similar problems but not precisely the same; at any rate the solutions suggested to them haven't worked for me.

---

### Post by praseodym on 2015-09-19
Start the GUI from terminal via
```

gksudo nm-connection-editor
```

---

