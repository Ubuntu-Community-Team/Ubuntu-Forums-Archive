---
title: "PS3 Wireless issue"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by roger_s on 2008-11-30
Hi all,

I am currently installing ubuntu 8.10 on my PS3. Tried yellowdog, didn like it.

PS3 is using fw 2.52
Router is using fw 1.007 wich is the latest version from linksys.

I have some issues with my wireless config. My PS3 is one of the 1st models (60GB) and my wireless router is a linksys WRT54GC, used to be a tornado 140.

In yellowdog my wifi was working, the led was blinking and I was able to surf the web. Now with intrepid installed I cannot establish a connection in any way. I am not using WEP or WPA, just MAC address control, even with MAC control of I do not get a connection. The LED doesn't even blink. 

Using iwconfig I see the networkcard is called wlan0, using the gelic driver.

I tried manual config:

sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 essid ps3wifi

ifdown tells me that wlan0 is not configured

dmesg is showing this continuously:  
gelic_eurus_sync_cmd_worker: cmd issue failed

I also have to mention that it did work wit my old tornado 140 router, but that is gone now.

Any help is appreciated.

---

### Post by roger_s on 2008-12-01
Anyone please?

---

### Post by roger_s on 2008-12-02
and up again.

---

### Post by roger_s on 2008-12-06
Ok I managed to get it working during installation. I had to enter essid and WEP key. It seems that it has downloaded a list of updates, shows this when logged on to Gnome. Bu I still cannot surf the web, download the updates or even ping. I also do not receive an IP address.

---

### Post by roger_s on 2008-12-07
bump

---

