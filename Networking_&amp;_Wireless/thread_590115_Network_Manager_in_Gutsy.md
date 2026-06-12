---
title: "Network Manager in Gutsy???"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by petzworld999 on 2007-10-24
I have tried to get the network manager applet many ways in gutsy. I have tried using the terminal, the Add/Remove programs box, and downloaded files from the project website, but the applet will not start. Any idea why I am having this problem?

---

### Post by dca on 2007-10-24
By default after install the 'nm-applet' is already added to the tray right next to the speaker icon if that's what you're referring to...  To verify that loading on start-up, you can click on System -> Preferences -> Sessions...  Network Manager should have a check mark next to it...  If you're using wireless w/ network manager and you click on the two monitor looking dealies in the tray and don't see any wireless access points it could be an issue with the driver.

---

### Post by petzworld999 on 2007-10-24
I've dicked around with it in "Sessions" and it still won't appear in the panel. It is running, just not looking like it is.

---

### Post by petzworld999 on 2007-10-24
Is Network Manager the same thing as Network Monitor?

---

### Post by Arthur Archnix on 2007-11-21
You need nm-applet started on login, you can confirm this in your sessions startup. You also need Notification Area in your panel, right-click add to panel.
Add this command: nm-applet --sm-disable

---

