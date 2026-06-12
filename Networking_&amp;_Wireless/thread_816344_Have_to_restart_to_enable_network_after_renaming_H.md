---
title: "Have to restart to enable network after renaming Host name"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by pterosky on 2008-06-02
I wanted to rename the Host name ("user name"-desktop) 
as you can see in [this thread]("http://ubuntuforums.org/showthread.php?t=813941").

If I right-click on the nm-applet icon and select Connection Information after a fresh restart, all the values are set to zeros, and I have to restart the my computer to get the network up and running. Sometimes going to Manual Configuration, disable roaming mode and choosing DHCP helps. I have ADSL internet.

I hope somebody has got a solution for this :)

---

### Post by bluefrog on 2008-06-02
sudo -i
nano /etc/hosts
127.0.0.1 localhost
192.168.1.2 desktop     ##change IP and machine name to your likings if using a fixed IP

OR
sudo -i
nano /etc/hosts
127.0.0.1 localhost desktop     ##change machine name to your likings

nano /hostname
desktop                 ## or desktop.example.com (the machine name must be the same as in /etc/host and adjust the TLD to your likings)

/etc/init.d/hostname.sh

your hostname should be set.

---

### Post by pterosky on 2008-06-27
Thanks for the suggestion, which I tried but didn't solve the problem.

Turns out after buying a new modem, returning it and much tweaking that the problem was with my ISP; The settings for my account in their system had atomagically been messed up around the time I was doing the changes. 

When they finally checked my settings in their system and made some changes I had connection again.
:guitar:

---

