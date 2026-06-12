---
title: "File/printer sharing in Ubuntu"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by ojohnsen79 on 2007-11-30
Hi.

I have a Linux (Ubuntu 7.10) computer with a printer attached to it, and a Windows Vista laptop.  Both are connected to the internet through a D-Link DI-524 wireless router.  I want to use the Vista laptop to access both the files and the printer on the Linux computer, without having to type any username and password when printing or accessing the files.

Is there a way to do this, while, at the same time, making sure that my Linux machine isn't wide open for access from someone on the internet?

---

### Post by tjagoda on 2007-11-30
Does it have to be done through the internet?  Can both the boxes be connected to a local network, instead of connecting through the internet to each other?

---

### Post by ojohnsen79 on 2007-11-30
Sorry!  Slight misunderstanding here..  My bad.. :)

Two computers:
1 stationary computer with Ubuntu 7.10, connected to D-link router via TP cable
1 laptop computer with Windows Vista, connected to D-link router via WLAN

Router is then connected to the cable internet modem, which connects further onto the internet.

I want it so that the Vista laptop can access the shared printer and folders on the Linux computer without having to enter any usernames or passwords.  But while the Linux computer (Samba) is set up so that the printer and folders can be accessed from the Vista laptop, or any other computers on the LAN/WLAN for that matter, they should not be accessible from the internet.

In other words, I don't want to risk that some jerk-off on the other side of the continent enters my IP address into his web browser or whatever, and has full access to my shared printer and folders.

---

### Post by TheWizzard on 2007-11-30
you can set up a samba server.

---

### Post by lintoon on 2007-11-30
Your router uses NAT to convert between your external IP address and internal IP addresses so someone on the internet will not be able to see your files by simply typing your external IP address into a browser.  Your router also has a built in firewall to protect your internal network.  

As TheWizzard says check out Samba server.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Here's a video I found on Youtube.  It was created for Ubuntu 6.10 but should still give you some pointers:

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

The video is basically using the gui to configure Samba.

Personally I would follow the instructions for Samba rather than using a gui.  This way you will have a better understanding of your system.

There are lots of Samba guides on the net too.

---

