---
title: "wireless SSID issue"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by Yelldon on 2008-05-05
Hello everyone.  This is my first post.  Before I begin, I want to add that I've been running Ubuntu 8.04 now for a few days, and this is the first Ubuntu install I've ever done, so I'm a slight noob with this Linux distro

I have a wireless network with a hidden SSID (For various reasons other than security), setup with WPA.  The Gnome network manager connected fine to my network, the issue was that it would not auto connect, and I had to enter the SSID and WPA password every time I shut the machine down, rebooted, or suspended/hibernated.  This was a slight annoyance, but it worked...

So now I have installed WICD, which works great as well, except it does the same thing; will not auto connect to the network.  I've checked the "remember connection" check box, as well and saved the WPA password in the connection info settings.  So when I reboot, or whatever, I have to pull WICD back up, enter in the SSID, then click connect for it to connect (This time though at least I don't have to type the WPA password).

So my question is, is there a way around this, to make it always remember the SSID?  Could I write a script to make WICD add the SSID name and connect at boot?

Any help would be greatly appreciated.  Thank you all for your time.

---

### Post by Yelldon on 2008-05-05
Any help would be greatly appreciated.

Thank you!

---

### Post by evil316 on 2008-05-05
Search the forums but from what I have seen no one seems able to get it to connect automaticly unless it's not hidden.

---

### Post by Yelldon on 2008-05-05
That's what I was afraid of... and thank you for the reply :)

Has anyone had any luck though, with the wpa_supplicant.conf, and passing it to wicd to pull the SSID?  Or even using it with Network-Manager to always pull a hidden SSID by chance?

---

