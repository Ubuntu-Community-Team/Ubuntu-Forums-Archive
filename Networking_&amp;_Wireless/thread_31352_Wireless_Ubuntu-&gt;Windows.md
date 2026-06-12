---
title: "Wireless Ubuntu-&gt;Windows"
date: 2005-05-02
forum: Networking &amp; Wireless
---

### Post by nszeek on 2005-05-02
I am trying to configure a wireless connection from my notebook ( Linux ) to a server with windows XP.

I don't know what might me going wrong. Here's what i tryed:

Configure with graphical interface:
1st attempt:

Mode: Manual
IP: 192.168.0.43
Subnet Mask: 255.255.255.0
Gateway: 192.168.0.1
essid: "WiFi Barao"
Wep key: barao

2nd attempt:
Mode: DHCP Automatic
essid: "WiFi Barao"
Wep key: barao

3rd attempt:
using command 'iwconfig' i did the following:

iwconfig ath0 essid "WiFi Barao"
iwconfig ath0 freq 2.422G / iwconfig ath0 channel 11
iwconfig ath0 key off

*there might some more commands i don't recall right now

Basicly that was it. It didn't worked out.
Any hints ?

---

### Post by young on 2005-05-03
Hi there,

  Just checked out your post.

[QUOTE=nszeek]I am trying to configure a wireless connection from my notebook ( Linux ) to a server with windows XP.

I don't know what might me going wrong. Here's what i tryed:

Configure with graphical interface:
1st attempt:

Mode: Manual
IP: 192.168.0.43
Subnet Mask: 255.255.255.0
Gateway: 192.168.0.1
essid: "WiFi Barao"
Wep key: barao

2nd attempt:
Mode: DHCP Automatic
essid: "WiFi Barao"
Wep key: barao

3rd attempt:
using command 'iwconfig' i did the following:

iwconfig ath0 essid "WiFi Barao"
iwconfig ath0 freq 2.422G / iwconfig ath0 channel 11
iwconfig ath0 key off

*there might some more commands i don't recall right now

Basicly that was it. It didn't worked out.
Any hints ?[/QUOTE]

    I had a same issue couple of weeks ago, and have managed to solve the 
  problem.   Here's one thing you could try.  

    Assuming the wireless network is in eth0,

    type in
 
    ```
sudo iwlist eth0 scanning
```

    This provides you with current condition of your wireless network, including
    the essid, and whether your encryption key is turned on or off.  Thing is, your
   Ubuntu already recognizes the wireless signal, but there could be some 
   configuration procedure, which you might have to go through.  In my case,
    I had to switch my essid to the one 'iwlist' command provides, and also had to 
    turn the encryption key off (your wireless manufacturer should have some 
    instruction to that).  Anyhow, I think it is worth a try.  Good luck with it.


                                                                                                         Cheers,

                                                                                                                   Young

  *PS: One more thing....it is usually DHCP automatic

---

