---
title: "There's no 'infrastructure mode' in wireless connection adding tab."
date: 2016-06-29
forum: Networking &amp; Wireless
---

### Post by josephinehopemarch on 2016-06-29
Hi.
I installed Ubuntu 16.04 on my computer few days ago and I'm completely new to Linux and I don't know much about computer itself.
I tried to connect to campus wifi, following the manual that school posted on homepage.
School homepage provides .crt file for certification and all but I can't even get to that stage.

The manual says I should add the wifi via Network Connection and choose **'infrastructure mode'** in Mode tab. 
But there's no such mode at all, which is the problem here. There are only three choices; client, hotspot and ad hoc.

While googling, I read in old threads that in order to find out whether my card supports infrastructure mode, I must use the command
"sudo iwconfig wlan0 mode master"
and according to the answers to those questions, it seems that there's no way of my laptop connecting to this wifi following the school's instruction.
Network Controller of my laptop is Intel Wireless 3160, by the way.
I tried downloading a firmware and iwlwifi driver things(?) and every possible methods I could think of, but it's no use.
Is buying other adapters is the only solution?


Thanks,
Jo

---

### Post by howefield on 2016-06-29
Welcome to the forums.

Thread moved to the "*Networking & Wireless*" forum for a better it.

---

### Post by jeremy31 on 2016-06-29
Use client mode and select WPA/WPA2 Enterprise for encryption and then you can find where to load your certificate

You shouldn't need any firmware or anything else for your wifi card if it can detect networks.  If it can't detect networks, see the wireless script link in my signature and post your results

---

### Post by josephinehopemarch on 2016-06-30
Thank you.
It worked with client mode!

---

### Post by wmstrome on 2016-07-19
> **jeremy31 said:**
> Use client mode and select WPA/WPA2 Enterprise for encryption and then you can find where to load your certificate

You shouldn't need any firmware or anything else for your wifi card if it can detect networks.  If it can't detect networks, see the wireless script link in my signature and post your results

I cannot connect using client mode (the network is found without any problem). The ISP provider says I MUST use Infrastructure. Ubuntu 15.04 Live CD allows me to connect, as it DOES have the Infrastructure (which is the default). However, my installed 16.04 system will not work, nor will the Live CD Ubuntu 16.04. 

Fortunately, I can connect to almost every place I have been and there is no problem at my home, but I would like to know how to get the Infrastructure mode in 16.04 (and for future releases).

---

### Post by him610 on 2016-07-20
Actually, it is probably already set to Infrastructure. To check or set it...

Click on network icon (Up/down arrows) in upper right status bar, from dropdown list click Edit Connections, 
In Network Connections window, highlight the correct *routername*, click Edit...
In window, Editing *routername*, tab Wi-Fi, Mode: [Infrastructure | Ad Hoc]  (you have a choice)

Note: Guidance is based on Ubuntu LTS 14.04, don't think LTS 16.04 would be much different.

---

### Post by zvezda2 on 2016-08-01
> **wmstrome said:**
> I cannot connect using client mode (the network is found without any problem). The ISP provider says I MUST use Infrastructure. Ubuntu 15.04 Live CD allows me to connect, as it DOES have the Infrastructure (which is the default). However, my installed 16.04 system will not work, nor will the Live CD Ubuntu 16.04. 

Fortunately, I can connect to almost every place I have been and there is no problem at my home, but I would like to know how to get the Infrastructure mode in 16.04 (and for future releases).


I have occured the same problem. In order to connect the wi-fi at my university all of the settings must be as following:

wireless 
connection name:yildiz-net
ssid:yildiz-net
**_mode:infrastructure_**

security:dinamic wep 802.1x
authentication: protected eap(peap)
anonymouse identity: xxxxxx
peap version:automatic
inner authentication:mschapv2
username: xxxxxx
password: xxxxxx 

I was able to connect when i was using Ubuntu 14.04 but after i begin using 16.04 it occurred to me that there is no infrastructure option. There is only Client, Hotspot and ad-hoc options. In ceteris paribus using "mode: client" won't help. Changing dinamic wep 802.1x to WPA&WPA2 Enterprise also won't do any good.

---

