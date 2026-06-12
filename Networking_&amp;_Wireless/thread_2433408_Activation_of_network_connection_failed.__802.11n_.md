---
title: "Activation of network connection failed.  802.11n WLAN Adapter-  TECLAST  x2 PRO"
date: 2019-12-18
forum: Networking &amp; Wireless
---

### Post by alice1989 on 2019-12-18
I have installed Ubuntu 18.04 in one tablet  TECLAST  x2 PRO, everything works fine except the wireless . I can only see 1 network but there are many in my other  devices and every time I try to connect to this only network, it says Activation of Network connection Failed. I can connect from wired connection.

 I am sure pswd is right and Network is working.  I have updated :

```

sudo apt update
sudo apt dist-upgrade


```

I have tried reinstalling Network Manager. And I tried installing driver for adapter from this page [HTML]https://github.com/gnab/rtl8812au/blob/master/wlan0dhcp[/HTML] for the adapter i found i have:   [B]802.11n WLAN Adapter 
[/B]And nothing has worked.

This is the pastebin  of my wireless connection: [HTML]https://pastebin.com/DM6mbtVK[/HTML]. I am a little tired. I dont know what else to to, i would appreciate any advice.

Thanks.

Alice.

---

### Post by praseodym on 2019-12-19
You need this one
```

sudo apt-get install git build-essential
git clone https://github.com/lwfinger/rtl8723bu
cd rtl8723bu
make
sudo make install
sudo modprobe -v 8723bu
iwconfig
```

---

### Post by alice1989 on 2019-12-19
Thank you so much for writing everything so clear.  I followed your instructions and then reboot, but that did not work, then i took a look at the page of the source code yo gave me, and i found that  i had to blacklist the generic driver that i had installed before. I did that according to the instructions in sourcecode page, then reboot. I can see now all the networks and my tablet connects by default in one i had selected before. but if i disconnect and try to connect back, it does not work, saying as before activation of network connection failed.

---

### Post by praseodym on 2019-12-20
Does it reconnect after rebooting?

---

### Post by alice1989 on 2019-12-20
Yes, after rebooting it connects to the network i have selected as connect automatically and everything works fine, if i disconnect or try to connect to another network, i get the same activation of network connection failed. I have tried the instructions in this link... for updating the driver

[https://askubuntu.com/questions/1056910/wifi-is-not-working-on-ubuntu-18-04-lts-with-rtl8723bu](https://askubuntu.com/questions/1056910/wifi-is-not-working-on-ubuntu-18-04-lts-with-rtl8723bu)

 they did not help, but everything keeps working as before. May be  it is fine as it is... rebooting is not to much trouble. It is my wireless info now [https://pastebin.com/6LrSdKZZ ]("https://pastebin.com/6LrSdKZZ")

---

### Post by praseodym on 2019-12-20
What about just re-plugging if it disconnects?

---

