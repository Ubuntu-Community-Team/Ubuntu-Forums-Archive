---
title: "Curious Realtek RTL8187B Problem"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by timothyparker@gmail.com on 2008-01-21
Hello,
If an effort to get this driver working on my Toshiba laptop, I have:
Installed the driver from here: [http://www.datanorth.net/%7Ecuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/%7Ecuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)
The above appeared to work successfully.

I then:
iwconfig wlan0 essid #name of essid#
iwconfig wlan0 enc #128 WEP key#

At this point, my (and several of my neighbors') network appears in the gnome network manager. However, none of them indicate any signal strength. ie None of the bars have any  orange color.

Any thoughts on where I am going wrong on this?

---

### Post by HandyAndyShortStack on 2008-02-25
That sounds about right.  No signal strength indication and no encryption.  I am keeping my fingers crossed for hardy on my [toshiba lappy]("http://ubuntuforums.org/showthread.php?t=622603").
:-?

Edit: 
Oh, you should probably also run 
sudo dhclient wlan0

---

