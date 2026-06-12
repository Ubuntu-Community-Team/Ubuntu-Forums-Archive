---
title: "which wifi  encryption to choose"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by Mujaheiden on 2007-04-11
hi

I'm setting up my home wlan and i want to have some light encryption on it, but one which is easy to maintain from Ubuntu. Which one to choose?

I don't want to have to do cumbersome terminal stuff like explained in [HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc.]("http://ubuntuforums.org/showthread.php?t=318539") and it should be portable, as in to bring the laptop to another place, and that it would be easy to connect to another (unsecured) network.

I have a [ sitecom 54 g router WL-160]("http://www.sitecom.com/product.php?productname=Wireless+Network+Broadband+Router+54g&productcode=WL-160&productid=519&subgroupid=2").

I tried the [ACL]("http://en.wikipedia.org/wiki/Access_control_list")option, only allowing certain Ethernet Addresses, but that's not really friendly to visiting laptops (and their owners), because first you have to figure out the EA address, enter it in the router console with another computer, and only then it works. Also, this variant doesn't offer any encryption.

So any other suggestions would be welcome.

---

### Post by reauthor on 2007-04-12
Install network-maneger-gnome and than setup encryption on your AP what ever you whish...Keep on mind;WEP & WPA is very easy to crack...

---

### Post by spd106 on 2007-04-12
I think the best choice for you will be WPA-PSK with TKIP aka WPA1. This is most likely the best compromise between security and backwards compatibility.

Install [Network Manager]("https://help.ubuntu.com/community/WifiDocs/NetworkManager") or wait a week and upgrade to Feisty.

---

