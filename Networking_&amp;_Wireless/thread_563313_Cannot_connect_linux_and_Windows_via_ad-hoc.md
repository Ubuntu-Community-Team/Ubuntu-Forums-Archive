---
title: "Cannot connect linux and Windows via ad-hoc"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by cs42na on 2007-09-29
I have 2 laptops, One has Windows xp operating system and the other one runs Ubuntu. The windows laptop is connected to the internet with a cable. Then I created an ad hoc connection so that it will share the internet via wireless to other laptops. The Linux laptop  can see the network created but cannot connect to it.

any suggestions??

---

### Post by cs42na on 2007-10-01
anyone? pls?

---

### Post by Lambert on 2007-10-01
have you read through this?

[https://help.ubuntu.com/community/WifiDocs/Adhoc?highlight=%28adhoc%29](https://help.ubuntu.com/community/WifiDocs/Adhoc?highlight=%28adhoc%29)

---

### Post by cs42na on 2007-10-07
yep but still cannot connect. I can see the network but Linux cannot communicate with it:(

---

### Post by Lambert on 2007-10-07
> **cs42na said:**
> yep but still cannot connect. I can see the network but Linux cannot communicate with it:(

Open a terminal and run these commands.

[COLOR=Red]wlan0[/COLOR] = device's interface (substitute with your device's interface name)
[COLOR=Blue]192.168.0.2[/COLOR] = static ip setting (change this to coincide with your network ip range and choose an ip not already in use)


```

sudo iwconfig [COLOR=Red]wlan0[/COLOR] mode Ad-Hoc essid ______ channel __

sudo ifconfig [COLOR=Red]wlan0[/COLOR] address [COLOR=Blue]192.168.0.2[/COLOR]

```

fill in the blanks with pertinent info based on your network.

test to see if you can exchange data.

---

