---
title: "Wireless Connection Drops Out After Sitting for Awhile"
date: 2016-10-09
forum: Networking &amp; Wireless
---

### Post by jeffhoogland on 2016-10-09
I am using nm-applet from the package network-manager-gnome in a window manager. I connect to my desired network just fine, but after the system is connected for several hours it simply stops sending / receiving network activity. The connection is still active according to the applet in my system tray, but I have to manually disconnect and reconnect the network before I am able to get a connection.

The system in question never had connectivity issues under Ubuntu 14.04 base with the same setup. This behavior started after I moved it to 16.04 with a clean install.

Open to suggestions / debugging idea.

Thanks!

---

### Post by Hadaka on 2016-10-09
Hi, this should help, provides an answer to  generate a "keep alive" command
[http://askubuntu.com/questions/653096/how-to-keep-alive-a-wifi-connection-on-a-laptop](http://askubuntu.com/questions/653096/how-to-keep-alive-a-wifi-connection-on-a-laptop)
also a command given to monitor the keep alive in that link
```
ps [COLOR=#ff0000]-[/COLOR]aux | grep cron
```
Does not work for me with the  "minus"  ps -aux , instead..
```
ps aux | grep cron
```
seems to work fine, I do not have 16.04 so your mileage may vary
more and up to date additional information.
[http://manpages.ubuntu.com/manpages/trusty/man8/keepalived.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/keepalived.8.html) <-needs to be loaded..link on the page
[https://raymii.org/s/tutorials/Keepalived-Simple-IP-failover-on-Ubuntu.html](https://raymii.org/s/tutorials/Keepalived-Simple-IP-failover-on-Ubuntu.html) <-Tutorial
thanks

---

### Post by jeffhoogland on 2016-10-09
Command doesn't seem to do anything. Still losing connection after awhile. That link and the link within it reference creating a cron job. Maybe I will take a crack at that. If anyone has suggestions still open to them.

---

