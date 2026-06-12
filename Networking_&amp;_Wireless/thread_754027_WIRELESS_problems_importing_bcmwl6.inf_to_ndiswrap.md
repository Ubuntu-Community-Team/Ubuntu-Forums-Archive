---
title: "WIRELESS problems: importing bcmwl6.inf to ndiswrapper,"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by oarion7 on 2008-04-13
Hello all

Any help would me much appreciated!! I am dual booting Vista and Ubuntu 7.10, with difficulties getting the Wireless Card to function in the latter. Tried the default options for the Broadcom driver, these did not work. So I went with ndisgtk and ndiswrapper, and copied over the corresponding drivers straight out of my drivers folder on Windows Vista and onto my Ubuntu desktop. These are the files "bcmwl6.sys" and "bcmwl6.inf." I did System--Administration--Windows Wireless Drivers and clicked to add driver, and selected the "bcmwl6.inf."

As you can see in the screen shot, it has accepted the driver and says "Hardware Present: Yes" - However, I do not have the option in my Network Settings for "Wireless connection", ALSO if I go into "Devices/Network Tools" and I go to "Network device" I only have the options "(lo)" and "(eth0)", I have no option to configure a wlan0, for example.

Screenie: [http://tinypic.com/view.php?pic=2yzj621&s=3](http://tinypic.com/view.php?pic=2yzj621&s=3)

Please help!! Been trying to get this to work for a couple months. :)
-rts


p.s. f.y.i:

If I type:

lspci | grep Broadcom\ Corporation

I get:

10:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

---

### Post by oarion7 on 2008-04-13
also i have blacklisted bcm43xx

---

### Post by oarion7 on 2008-05-14
In case anyone stumbles upon this thread by searching for the model I included in the first post, I solved this via method 2a on this page: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Note to other newbies, I don't believe extracting bcmwl6 from vista installation works, bcmwl5 should be used instead.

---

