---
title: "iwconfig doesn't save after reboot"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by thoffland on 2007-05-30
I got my wireless working using "iwconfig" in a terminal, however, when I reboot I have to do it over again. I think the trick is "sudo iwconfig wlan0 ap any" but I'm setting the essid as well then doing a "sudo dhclient3 wlan0" to get an IP address. 

Is there a way to save those configurations that way when I reboot I don't have to do it again? I've just done a fresh install and have only rebooted once after an update, but I thought I'd ask just in case.

---

### Post by RomeReactor on 2007-05-30
Hi. If using iwconfig doesn't seem to change settings, you can manually set them opening the terminal (Applications-->Accessories-->Terminal) and entering
```
gksudo gedit /etc/network/interfaces
```
That will bring up the text editor with the network settings configuration file. Look for **wlan0** and modify the entry:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid YOUR_ESSID
```
Not the preferred way to go, but useful nonetheless. As for using "sudo dhclient3 wlan0", you can make a launcher for that: From the terminal:
```
gedit .wireless
```
note that the file we're opening does not exist yet on your home folder, and is hidden; copy and paste the following into the file:
```
#!/bin/bash
sudo dhclient3 wlan0
```
save it and close gedit. You need to make that file executable:
```
sudo chmod +x .wireless
```
Now right click on your desktop and select "Create Launcher...", and fill it out with this:
```
Type: Application
Name: Start Wireless (or whatever you choose)
Command: gksudo /home/YOUR_USER_NAME/.wireless
```
Put an icon on it if you like (I use this one: /usr/share/pixmaps/tsclient.png), and you can drag it onto your top panel, so you only click it instead of entering "sudo dhclient3 wlan0" into the terminal. Hope this helps.

---

### Post by thoffland on 2007-05-30
Thank you!!! 

That totally did the trick, I actually named it .dhclient3 so I'd remember what it was for :roll: and it worked like a charm. I also added it to the startup program in sessions. 

Also, since you showed me where everything was, I took the liberty of adding "ap any" to my /etc/network/interfaces as well, and all is good. :p

Thanks again, I really appreciate the help!

---

