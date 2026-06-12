---
title: "Cloned MAC Address problem"
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by emptycoder on 2013-10-05
Hiya, I'm having a problem with MAC spoofing thing, on network  connections, there's an option for MAC Spoofing called Cloned MAC  Address (See screenshot), simply typing random MAC address, but when I  do that the wireless won't connect until I remove it, does anyone have  any idea?

[IMG]http://i.stack.imgur.com/8bs0Q.png[/IMG]

Please note that  the screenshot is for Wired Connection while I'm using Wireless  Connection, but both have the same option for MAC spoofing.:razz: that screenshot was taken from AskUbuntu, here's the [Link]("http://askubuntu.com/questions/81648/how-do-i-change-spoof-my-mac-address-and-easily-switch-between-multiple-ones")

---

### Post by steeldriver on 2013-10-05
Well the simplest explanation would be that your wireless access point is configured to not accept the new 'device' - it's a feature called MAC filtering or MAC whitelisting and is often used to prevent random unauthorized wireless devices from trying to connect to your LAN

---

### Post by emptycoder on 2013-10-05
Wow, that makes sense, thanks for the info, but is there any way around I can spoof my MAC?

---

### Post by steeldriver on 2013-10-05
if that *is* the reason, then it's something you should be able to turn off at your router / access point

---

### Post by Wiking on 2013-10-05
Or you could use a designated spoofed MAC Address and add it to the MAC filtering of your router.

---

