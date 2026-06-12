---
title: "Now you see it, now you don't"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by twygly on 2007-06-04
Have an Ubuntu machine with a Samba share all set up and working perfectly being access by both Windows and Xubuntu desktops - until today!

What's changed? Some security updates from last week required that the machine with the Samba share be rebooted - since the reboot that computer can't be accessed by \\computer_name\share

What does work? It can be accessed by \\ip_address\share (from Windows - Xubuntu I have no idea)

Any ideas?

---

### Post by swoll1980 on 2007-06-04
Maybe the update reset your firewall settings did you check?

---

### Post by twygly on 2007-06-05
Spot on... the reboot turned the firewall on and I don't think it was running previously.

Guess I need to work out how to configure the firewall and turn it back on.

Thanks for the pointer.

---

