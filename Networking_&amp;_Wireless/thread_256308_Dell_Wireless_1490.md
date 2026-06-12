---
title: "Dell Wireless 1490"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by gauntalus on 2006-09-12
Hey Everyone,

I've been running gentoo for a while, and just made the switch to Ubuntu.  I just got a new laptop, and have spent a few weeks of frustration trying to get the wireless card, a Dell Wireless 1490, to work under gentoo.

I figured I'd give Ubuntu a try since it's a bit better at autodetecting hardware.

Ubuntu appears to have detected my wireless card correctly, if I go to System -> Administration -> Networking, it lists my wireless connection as eth1.  It says "The interface eth1 is not active, but when I click activate, though it changes the device's status to Active, I don't seem to be getting any wireless signal.  I tried running iwlist and I just get:
```

gauntalus@lotus ~ $ iwlist eth1 scanning
eth1      No scan results

```
iwconfig appears to be detecting my card correctly also, but I'm unable to connect to my wireless router:
```

gauntalus@lotus ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Enigma"  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```
Has anyone had any success getting a Dell Wireless 1490 card to work under Ubuntu?

Thanks,
-Mike

---

### Post by zerohalo on 2006-10-28
I can't remember the details offhand, but you may need to install a driver for the Broadcom chipset to get it working (bcmXXXX). You can probably find what you need by googling.

---

### Post by wool on 2006-12-07
[http://http://ubuntuforums.org/showthread.php?t=297092&highlight=inspiron+1501]("http://http://ubuntuforums.org/showthread.php?t=297092&highlight=inspiron+1501")
here is the link. He made it worked on a Inspiron 1505 and its dell wireless 1390. I just changed the downloaded windows driver for dell 1490 but it still doesnt work for me. Maybe i missed something or do some other configurations.

---

### Post by zekayi on 2006-12-08
I have the inspiron 1501 with broadcom 1490 and got it working with the HOWTO of paperdiesel [http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1501](http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1501)

It is written for the inspiron E1505 with 1390 card, but it worked perfectly for me. It was important to use the drivers mentioned in the HOWTO, which means I first tried it with the dell driver for 1490, but this failed. Thus I retried it with the driver mentioned in the HOWTO (for 1390) and got it working.

---

### Post by FrodoB on 2006-12-08
Also see this instruction for your chipset:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by Lexrst on 2006-12-08
> **FrodoB said:**
> Also see this instruction for your chipset:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

With help from paperdiesel's faq and the link from FrodoB, I was successfully able to get the wireless card in my (1st generation) Dell Inspiron XPS up and running and controlled by NetworkManager with WPA support.  No WiFi Radar required - everything is accessible from the NetworkManager tray icon.

Kudos to everyone for their help!!!

-Lexrst

---

