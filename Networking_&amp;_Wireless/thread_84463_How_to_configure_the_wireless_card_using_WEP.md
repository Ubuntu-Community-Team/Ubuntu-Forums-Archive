---
title: "How to configure the wireless card using WEP"
date: 2005-10-31
forum: Networking &amp; Wireless
---

### Post by jallajalla on 2005-10-31
I use Ubuntu 5.10. I have a broadcom wireless adaptor and I have installed it using ndiswrapper. I have now problems configuring the card.

In network settings I have eth0 and wlan0. If I choose properties for wlan0 I get a list of all networks (including mine) under ESSID. I choose mine and I enter the WEP key. I choose DHCP connection and click OK. The interface wlan0 is then activated (takes some time).

Under Default gateway device I choose wlan0 but I have no success (it will still not work).

If I go to connection poroperties by clicking on the network icon on the toolbar, I can only choose between eth0 and lo. Guess the wlan0 should show up here..

One immediate question is the WEP key. I have tried different settings on my router, using 64 bit, 128 bit, hex, ASCII, etc. I've read that you should insert dash (-) between every four characters when entering hex.. I've tried both with and without.  The transmission key number is set to 1 on my router. MAC-address filtering etc is disabled so that shouldn't be a problem.

Any idea of what I might do wrong?

---

### Post by spd106 on 2005-10-31
I think you are right to suspect something is wrong with the wep key. You should not need to enter any dashes. If you ok with the console try editing the network settings file **sudo gedit /etc/network/interfaces**.

There should be a stanza like this:

```
iface wlan0 inet dhcp
wireless-essid "your_essid"
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx

auto wlan0
```
Just fill in your details, I would stick with the WEP entered in hex. Then save and close. You should be able to **sudo ifup wlan0**.
If this doesn't work then try disabling WEP for a short while to test it out. 

Perhaps not the easiest wifi card to set up, but it should work ok. My old belkin card has the same Broadcom chip. 

Good luck

---

### Post by jallajalla on 2005-11-01
Thanks for your help, but unfortunately it still doesn't work. I have made sure that the ESSID and WEP-key is correctly entered in the interfaces file as you wrote above. Have also tried disabling the WEP key, and hence left the WEP-key field empty (in the interfaces file the line with the wireless-key is completely deleted).

Writing:
> sudo ifup wlan0
ifup: interface wlan0 already configured

I do see a list of all neighbouring networks (including mine) so the wireless adaptor must work to some extent. Still, when I choose network connection (clicking on the icon on the toolbar) I can only choose between eth0 and lo. There is no wlan0 in the list. Frustrating.

---

### Post by spd106 on 2005-11-04
How about trying a different driver? Have a look at the hardware [list]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") on the ndiswrapper website or perhaps in the ubuntu [wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")

---

### Post by Fermanagh on 2005-11-04
I am having a problem entering the WEP Key because the field limit on the number of characters that can be entered into the field is 1 character shorter than the number of characters in my WEP Generated Key on my wireless G network. The last character of my WEP key is ignored so when I then try to connect to the internet, the connection fails.

---

### Post by Craigyoo on 2005-11-16
After seeing this post (WEP Key field limit) I thought perhaps that was my problem as well. So I changed the key to 64 on the Router (linksys) and entered the result in Network Setting > Properties and the card (also linksys) recognized the router. Connection made. Happy day.

But long term and security-wise, is there a better method. Does anyone know if this field limit issue has a workaround (assuming it is valid), I mean, should I go into terminal and set up the connection with full 128 WEP Key as opposed to through Interface Properties with the shortened key? Please be gentle, command lines are still greek to me but I am learning.

---

