---
title: "Deleted Wlan0???"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by fin2010 on 2011-01-01
Been trying to install madwifi . 
I was following a guide - I entered this into the terminal "echo blacklist ath5k | sudo tee -a /etc/modprobe.d/blacklist.conf .
 Then after I had to enter "sudo ./scripts/madwifi-unload"but the terminal responded with "command not found"
So now my network connections have disappeard and I couldn't go on with the guide as that particular step woldnt work.
Now Wlan0 has disapeared when i look on ifconfig
Can someone please tell me how to fix this??
Much appreciated

---

### Post by Ocxic on 2011-01-01
edit "/etc/modprobe.d/blacklist.conf and remove the "blacklist ath5k" entry and reboot.

---

### Post by fin2010 on 2011-01-02
hey thanks a lot. Been using pc's all my life , now I'm on ubuntu im a complete noob

---

