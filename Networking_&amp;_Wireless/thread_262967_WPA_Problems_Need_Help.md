---
title: "WPA Problems Need Help"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by aglc2005 on 2006-09-22
Ok, I have found threads that say I am suppose to install Network Manager to use WPA-TKIP. I'm trying to get on my school's wireless and they require that form of security. My problem is that after installing Network Manager, it doesn't show up under Applications > Internet and I have no clue what the command for it is either to run it in terminal. Help?

---

### Post by spd106 on 2006-09-22
Network-Manager works through the nm-applet in the "system tray" You will need to comment out the device settings in the /etc/network/interfaces file. Then restart networking **sudo /etc/init.d/networking restart** or log out then log in again. If the nm-applet fails to start the try starting it from the terminal.

---

### Post by aglc2005 on 2006-09-22
Thanks much, I don't have my laptop with me for the weekend, but when I get back to school sunday I will try it and post my results

---

### Post by aglc2005 on 2006-09-24
OK, I did all of that, and still have an internet connection, but I still have no way to edit the settings for Network Manager, the icon that is suppose to show up under Applications > Internet is not there.

---

### Post by spd106 on 2006-09-24
Have a read through this page [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager).

---

