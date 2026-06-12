---
title: "How to tell if 54Mb/s or 11Mb/s on wireless lan"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by DaleFarrell on 2007-11-15
1.How do tell if I have the rated 54Mb/s connectivity to the Linksys wireless gateway? Happily switched from XP on this Emachine laptop. I got the Broadcom to work, but I followed so many different methods I can't tell which worked! Widc isnetwork manager. Am using the restricted driver. Wireshark was way over my head. IPTRAF, not sure what it shows. Gnome System Monitor does not show anything. 

2. When I entered this topic I tried to use the similar topics help, but when I returned from reading the first the rest were gone. If I could get back to the list I probably could eliminate a lot of postshttp://ubuntuforums.org/images/smilies/icon_smile.gif

---

### Post by Griff on 2007-11-15
I know there's an easy way to check this.  I don't have my laptop booted up right now to confirm, but is there anything pertinent under:
```
sudo iwconfig
```

---

### Post by WakkiTabakki on 2007-11-15
Right-click this icon (nm-applet, the tray icon for you network manager) and choose "Connection information" from the menu... (see the attached image)

/N

---

### Post by DaleFarrell on 2007-11-15
<solved> Wicd, my nm, tells me I am connected at 56%, which is probably the signal strength. To get wireless working I used someones script that automatically installed Wicd. Is nm better? I do use WPA. I went out and bought the Ubuntu Linux Bible which is an awesome tome. It referenced the sudo iwconfig, which shows the data rate to the router. I did like having it displayed as TaskManager did in XP. The main thing is that if I have over 11Mb/s then I must have set up ndiswrapper and the driver correctly.

---

### Post by WakkiTabakki on 2007-11-16
> **DaleFarrell said:**
> Is nm better?
Don't really know. NetworkManager (and nm-applet) is the default wireless network thingy in Ubuntu (not sure about Kubuntu and the other flavours, though). It works for me with ipw3945 chip, and I use WPA as well...
The connection does drop from time to time, maybe once or twice a week and I need to restart the router to get it going again, so it may be a router thing...
I've read somewhere the wicd i supposed to be much better, but I haven't bothered to try...

BTW, have you got the tray icon? If not, check this out:
[http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)

/N

---

