---
title: "Xubuntu 17.04 - no network connectivity -at all"
date: 2017-05-11
forum: Networking &amp; Wireless
---

### Post by PeterRJG on 2017-05-11
I downloaded Xubuntu 17.04 today via torrent and burned it to USB. The torrent and the burned distro both pass CRC. It loads fine both on my laptop and my gaming PC, but on neither computer will it connect to the internet, either via wireless, wired or tethering a phone via USB. All three methods work in Windows, so it's not the NICs or my phone or whatever. 

Sorry for the phone screenshots but I couldn't take real ones as I can't connect to anything! 
The wireless goes through about 10 seconds of thinking about it and bombs out with:
[ATTACH=CONFIG]275050[/ATTACH]

Yes, I call my wifi network badluckbrian - I'm a comedian like that.

var/log/syslog says:
[ATTACH=CONFIG]275051[/ATTACH]

Using a wired or a tethered connection, the connection works but it cannot contact the internet.
var/log/syslog says: 
[ATTACH=CONFIG]275052[/ATTACH]

I've followed some guidelines I found here --> [https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing/905019](https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing/905019) and here --> [https://superuser.com/questions/1153203/ubuntu-17-04-systemd-resolved-dns-lookups-randomly-fail/1200745#1200745](https://superuser.com/questions/1153203/ubuntu-17-04-systemd-resolved-dns-lookups-randomly-fail/1200745#1200745) but they do not work. Obviously I cannot follow that second link's advice and reboot as I'm using a live session and the settings won't stick.

Logically, I don't want to install a distro if it can't connect to the internet so does anyone know of a workaround to get connectivity? It's not a bad download or burn as I've ran a CRC and it checks out. So what is this? A buggy release? Wouldn't be the first time a Linux distro has been released with showstopping bugs on it I suppose. Shame, as I really want to give this Xubuntu version a go as reviews of it say it's very good. :(

So, any suggestions?

---

### Post by slickymaster on 2017-05-11
*Thread moved to **Networking & Wireless**.*

Screenshots replaced with attachments

---

### Post by wildmanne39 on 2017-05-11
I do not know what wifi card you have but this should get you going, do what is in the screenshots, then run the command.
That is the easy work around.
```
sudo systemctl restart NetworkManager.service
```
Once you are connected by ethernet please run the wireless script in my signature, if for some reason your ethernet does not come one you can use your cell phone if it has the capability to tether to your computer through an usb port.

---

