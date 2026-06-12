---
title: "Linksys WUSB54GC Freeze"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by kb00heda on 2007-03-12
Hi,

I recently bought the abovementioned WUSB-stick for my laptop (Acer Ferrari 3000). It was up and running after following this guide

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29#cooliris]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29#cooliris")

using Edgy. Also, it started out-of-the-box with Feisty Herd 5, so that is not my bother. (Well, of course I had to provide ESSID and WEP, and so on.)

However, after some use, with the laptop running for, say, an hour or so (take or give some), the connection drops. The LEDs on the stick go blank too. Now, if I try to restart the network using either

```
sudo /etc/init.d/network restart
```

or

```
sudo ifdown rausb0
sudo ifup rausb0
```

the computer freezes totally. The only remedy---seemingly---is a reboot.

I saw a post where users mentioned problems similar to mine, but I could not make out any solution from it. So, if anyone recognize this, and is able to provide some input, I would be grateful.

Best regards,
David

---

