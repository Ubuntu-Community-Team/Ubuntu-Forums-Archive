---
title: "problem with wireless and firestarter"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by themusicalduck on 2008-10-19
I'm trying to set up a filesharing/internet sharing network using my wireless card, that someone on a laptop can connect to. I've been through the configuration wizard on firestarter, but when I try to start the 'firewall' it comes up with:

Failed to star the firewall

The device wlan0 is not ready.

Please check your network device settings and make sure your internet connection is active.

Anyone know what might be happening?

---

### Post by themusicalduck on 2008-10-19
bump

---

### Post by forger on 2008-10-19
perhaps ufw (uncomplicated firewall) could be more useful?

install this package: [gufw]("apt://gufw")

> 
Description: graphical user interface for ufw
 gufw is an easy and intuitive way to manage your Linux firewall. It supports
 common tasks such as allowing or blocking pre-configured, common p2p, or
 individual port(s), and many others!
Homepage: [https://launchpad.net/gui-ufw](https://launchpad.net/gui-ufw)

---

### Post by themusicalduck on 2008-10-20
That looks like it might be useful, but it doesn't look like you can setup connection sharing with it which is what I need to use firestarter for.

---

### Post by forger on 2008-10-20
ah sorry

---

