---
title: "Problems making a static IP address"
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by geo488 on 2014-01-03
Hello, I have been trying to make a static IP address following [this]("http://draalin.com/setting-up-a-static-ip-address-in-ubuntu/") guide and I've run into a problem. My problem is that when I type "**sudo vi /etc/network/interfaces" **into the terminal, I get the following message:

auto loiface lo inet loopback

This is not helpful to me, as the guide I've been using as well as other guides instruct that you should edit the line that says "**iface eth0 inet dhcp" **and change the dhcp part to static. As I do not have this option available to me I am stuck as to what I should do. Any assistance would be greatly appreciated.

---

### Post by Iowan on 2014-01-03
You could manually enter (edit) that information into */etc/network/interfaces*, 
```
sudo nano /etc/network/interfaces
```
or you could use Network Manager to set a static IP address.

---

### Post by steeldriver on 2014-01-03
Regular desktop users should use the Network Manager GUI applet (Edit connections... then navigate to the IPv4 settings tab and set the method to 'Manual' and enter the details in the boxes provided)

---

