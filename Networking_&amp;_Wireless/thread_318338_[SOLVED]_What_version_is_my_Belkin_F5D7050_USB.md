---
title: "[SOLVED] What version is my Belkin F5D7050 USB?"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by werdna5225 on 2006-12-13
I keep reading where everyone had a version of their Belkin F5D7050 wireless network card, and I can't seem to find where it says what version I have.  I have searched the internet and can't seem to find anything there either.

---

### Post by FrodoB on 2006-12-13
You can tell by the USB ID that is put out by:

lsusb

Once you know which one you have you can get the drivers.

Here are two of them:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

Both of these work very well with WEP and they should work with WPA-PSK, but I have not done it yet.

---

### Post by werdna5225 on 2006-12-13
wow that was quick thank you

---

