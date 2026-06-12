---
title: "Yet Another Wireless Problem (YAWP)"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by notthecheatr on 2007-08-28
I'm trying to connect to a WEP network on my laptop at the local library.  I can connect just fine in Windows, but in Ubuntu (Feisty Fawn) it seems to connect but the activity indicator is at 0% and I can't get anything in firefox.

Information according to Windows:

[Adapter info]
Broadcom 802.11g Network Adapter

[Network info]
SSID=LIBRARY
Authentication=Open
Data Encryption=WEP
Network key=8A57A4CF86


The key looks like hex to me, although I did try it as a passphrase (it's too long to be ASCII).  Nothing works.  In Windows I get "Signal Strength Excellent" and "54 Mbps" but in Ubuntu I can't get anything.  Any suggestions?

---

### Post by bmartin on 2007-08-30
**Please use a more descriptive title for your post. You're more likely to get help that way; people who know the answer are more likely to find your thread.**

If you haven't done so already, install [the drivers]("http://ubuntuforums.org/showthread.php?t=405990") for your Broadcom chipset. ndiswrapper comes highly recommended; the firmware does not.

If you have a hard time getting the default network manager to connect after successfully installing your WiFi drivers, I recommend installing WICD (you can install it using the same program as in the thread above).

---

### Post by kevdog on 2007-08-30
Your library use 64 bit WEP
Thats a 10 character HEX KEY - not ASCII -. That is the correct length of the key to comply with 64bit WEP standards.

As bmartin suggested I would install ndiswrapper if you do not have a functioning wireless connection.  Can your ubuntu machine connect with any unencrypted networks???  Just trying to see if we are working with a working network card / driver.

---

