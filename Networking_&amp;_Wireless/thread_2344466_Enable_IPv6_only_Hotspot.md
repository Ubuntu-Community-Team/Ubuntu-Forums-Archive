---
title: "Enable IPv6 only Hotspot"
date: 2016-11-25
forum: Networking &amp; Wireless
---

### Post by cshipley2 on 2016-11-25
How do I set up an IPv6 only hotspot?  When creating a hotspot, the IPv6 tab is disabled. Is there a way to enable it?

I am doing this because as a mobile app developer I want to verify mobile apps work correctly under IPv6.

---

### Post by #&amp;thj^% on 2016-11-25
> **cshipley2 said:**
> How do I set up an IPv6 only hotspot?  When creating a hotspot, the IPv6 tab is disabled. Is there a way to enable it?

I am doing this because as a mobile app developer I want to verify mobile apps work correctly under IPv6.

Hello and Welcome!
Have a look here:[http://jochen.kirstaetter.name/blog/linux/configure-ipv6-on-ubuntu.html](http://jochen.kirstaetter.name/blog/linux/configure-ipv6-on-ubuntu.html)
And a more complicated to understand information found here:[https://www.jumpingbean.co.za/blogs/mark/set-up-ipv6-lan-with-linux](https://www.jumpingbean.co.za/blogs/mark/set-up-ipv6-lan-with-linux)
And when happy with your set-up...and if you are using a systemd OS IE: Ubuntu 15.10 and newer.
To Restart your network:
```
sudo systemctl restart networking
sudo systemctl restart network-manager 
```
If your using Ubuntu 14.04 use the following to restart Network:
```
sudo service networking restart
sudo service network-manager restart
```
Hope this is helpful.
Regards

---

