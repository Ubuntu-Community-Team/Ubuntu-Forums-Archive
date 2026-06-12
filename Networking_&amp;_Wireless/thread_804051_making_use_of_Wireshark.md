---
title: "making use of Wireshark"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by Sarah L on 2008-05-22
Hi,
Recently I've rediscovered Wireshark and found it to be a far more useful and well-designed utility than I had originally thought. I first stumbled upon it back when I was trying to set up my wireless card under Fedora 7, but doing that was such a pain in the rear that I had a general feeling of disgust for all of the software that I had tried in the process.

Now that (after a year!) I've switched back to Ubuntu and realized how much better the packages here are, I've given Wireshark a second chance. It works flawlessly here, and I've had such a great time opening it up and watching the packets fly by.

But I dislike having to open it up manually every time I want to sit back and watch the traffic, and having to use sudo is always a pain. Is there any way that I can have a utility that starts at login with whatever privileges it needs and runs in the background, logging all the packets, which I can then go to view by clicking an icon in the system tray?

knetworkmanager is fun and easy to use because it has a nice system tray icon that loads at startup and takes care of itself (aside: it took me months to get my wireless card and knetworkmanager configured correctly with Fedora, but everything worked out of the box with Ubuntu)... can Wireshark be as easy to use (or does another application exist that performs this sort of function)?

Thanks so much,
Sarah

---

### Post by Monicker on 2008-05-25
You could use the NOPASSWD option in /etc/sudoers and make an exception for Wireshark.

[https://help.ubuntu.com/community/Sudoers]("https://help.ubuntu.com/community/Sudoers")

One caveat - there is some security risk in doing this.  Wireshark's protocol dissectors can be prone to buffer overflows, which could allow a malicious crafted packet to do bad things using root privilges.  This is why you get a warning when you start Wireshark up as root.

---

