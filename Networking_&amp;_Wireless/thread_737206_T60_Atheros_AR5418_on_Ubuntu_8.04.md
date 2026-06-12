---
title: "T60 Atheros AR5418 on Ubuntu 8.04"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by trent1980 on 2008-03-27
I'm pretty new to Ubuntu but this is my second day of unsuccessful attempts at getting wireless to work on my T60.

lspci: Network controller: Atheros Communications, Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)

It just appears as if I don't have a wireless card in my laptop at all. The network settings don't see anything wireless and neither does command line.

cat /etc/network/interfaces:
auto lo
iface lo inet loopback

ifconfig:
eth0
lo

I've attempted other's posts regarding installing madwifi ... everything installed great, but still not wireless.

If anyone can help me out with any suggestions or something I've overlooked, it would be greatly appreciated. Until then, I'm stuck with a wired connection.

---

### Post by jdriessen on 2008-03-27
I'm having the exact same problem (Macbook Hardy Herron Beta 1)

---

### Post by t4k1s on 2008-03-28
Same here with a MacBook (Core Duo2) and Ubuntu 8.04 beta.

---

### Post by trent1980 on 2008-03-29
i gave up for now ... I installed Windows XP and am running vmware server with Ubuntu 8.04 on it. It's the best I could do as a laptop is useless to me without wireless.

I bought another hard drive to try Ubuntu again without being laptop-less...

Did either of you try the the ath5k?
[http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)

---

### Post by trent1980 on 2008-03-30
I've been doing reading while I wait for my new hard drive to come in ...

Have either of you guys tried the SVN madwifi install?
[www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008) 

I saw it while reading here:
[http://madwifi.org/ticket/1781](http://madwifi.org/ticket/1781)


Looks like it's worth a shot ... Curious to see if it works on yours

---

### Post by trent1980 on 2008-03-31
just to give an update and wish for a little help...

I installed from the svn madwifi trunk from the link i posted above. The card seems to be working a little now. I can see wireless networks and even connect to them but I cannot get and IP address from them.

if i run "sudo dhclient ath0" ... it says no server found.

any ideas?

---

### Post by trent1980 on 2008-03-31
I used the gui ndisgtk to install the windows driver and it's working very good now. Although, from what I've read, it won't use n (only a/b/g).

Very happy now ... I hope you all get yours to work as well.


Driver Download:
[http://ubuntuforums.org/attachment.php?attachmentid=55734&d=1199824855](http://ubuntuforums.org/attachment.php?attachmentid=55734&d=1199824855)

Where I got the driver:
[http://ubuntuforums.org/showthread.php?t=651205](http://ubuntuforums.org/showthread.php?t=651205)


Ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by electedfreedumb on 2008-04-26
Excellent this worked for me! I never could get Gutsy going for this issue and have been using dreaded Visa for the last three months because of that. The link to the driver is exactly what I needed. 

This is the best driver I have a Toshiba Laptop P205D-S8804 and this driver worked perfect. 

It is the NET5416.inf the other I believe that people are having success with is NET5411.inf but that one would never work for me.

So for anyone struggling to get wireless going (keep in mind that my card would not even show up) all I did was follow these instructions
[http://ubuntuforums.org/showthread.php?t=739998](http://ubuntuforums.org/showthread.php?t=739998)

But instead of using the driver there This one above worked for me.

---

