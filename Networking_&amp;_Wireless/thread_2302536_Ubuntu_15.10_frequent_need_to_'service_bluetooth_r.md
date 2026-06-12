---
title: "Ubuntu 15.10: frequent need to 'service bluetooth restart'"
date: 2015-11-11
forum: Networking &amp; Wireless
---

### Post by aridus on 2015-11-11
Using Ubuntu 15.10 on a Dell xps 13 the bluetooth connection to my mouse and keyboard fails every 20-30 minutes. I can reconnect with 'service bluetooth restart' in a terminal but it is a continual headache that breaks my work flow.

If anybody has any suggestions about how this matter can be rectified, I would love to hear them.

With thanks.

---

### Post by doc_ccb on 2015-11-13
Same situation here, Ubuntu 15.10 on a Dell Vostro 5560 laptop. Cursor would stop responding to mouse at random intervals, although B/T mouse remains connected. 

Doing a "sudo service bluetooth restart" would sometimes bring back control of the cursor. If this doesn't work anymore, I follow suggestions from here: [http://ubuntuforums.org/showthread.php?t=2142366](http://ubuntuforums.org/showthread.php?t=2142366) (comment #7 - reset B/T, reset usb port, reset usb hub).

Also installed Blueman-manager 2.0, didn't change anything.

---

