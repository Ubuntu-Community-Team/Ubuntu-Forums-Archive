---
title: "Not getting assigned an address on my ad-hoc wifi network."
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by Ubiquitousuk on 2008-02-18
Hello,

I've just installed Ubuntu 7.10 (Linux newbie) for the first time on my Dell XPS M1330 laptop. Thanks to a great tutorial on these forums, I have been able to install ndiswrapper and get my broadcom 43xx wireless working--well, kind of.

If I bring my laptop into my office, them I am able to connect to the office's wireless access point and surf the internet quite happily. However, at home I have a Vista desktop running internet connection sharing over an ad-hoc wireless nework that I am having less success with. My Ubuntu install can see the wi-fi network. When I attempt to connect, I am prompted for the WEP key and then everything appears to connect just fine. However, I am not able to access the network or the internet from the laptop, and when I right-click on network manager to view the connection details I get:

    IP Address: 0.0.0.0
    Subnet Mask: 0.0.0.0
    Broadcast: 0.0.0.0
    Gateway: 0.0.0.0
    Primary DNS: 0.0.0.0
    Secondary DNS: 0.0.0.0

So it looks as though my laptop isn't being assigned an address properly. I get exactly the same thing trying to connect to a friend's (unsecured) wireless ad-hoc network.

As I mentioned, the wi-fi works fine in the office, so I guess the ndiswrapper has worked. Also, my girlfriend is able to connect to and use the same Windows ad-hoc network using her install of ubuntu 7.10 on an Inspiron 1420--which suggests to me that I shouldn't need to reconfigure anything at the Windows end.

Any suggestions regarding what I might try to fix this would be much appreciated.

Many thanks.

---

### Post by Hightide on 2008-02-18
HI

can you post output from this command

```
sudo ifconfig
```

regards

:)

---

