---
title: "forgot wireless password and it doesn't exist on my command line list"
date: 2019-07-17
forum: Networking &amp; Wireless
---

### Post by billie mulcahy on 2019-07-17
I've forgotten my wifi password and I'm using a computer with a wired connection. ls from the command line only lists the wired connection, although my previous laptop used the wifi connection. The list of available wireless connections does show it however. I guess I could just add a new connection and delete the current one, but I don't know the ssid or the key. I don't have my kde wallet password and my /etc file seems to be corrupted. I will greatly appreciate any help!

---

### Post by crip720 on 2019-07-17
Your wireless password should be on your router.  If you are connected by wire, just log into your router.  It should be also in your network manager, click edit and the wifi connection.

---

### Post by kurt18947 on 2019-07-21
> **crip720 said:**
> Your wireless password should be on your router.  If you are connected by wire, just log into your router.  It should be also in your network manager, click edit and the wifi connection.

I never thought about looking in network-manager for a wifi password, I'll have to remember that. An easy way to edit and remove network connections is with this command:  nm-connection-editor.

---

