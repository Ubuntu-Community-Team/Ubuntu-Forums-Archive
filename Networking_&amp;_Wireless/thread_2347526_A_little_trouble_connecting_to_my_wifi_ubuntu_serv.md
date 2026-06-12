---
title: "A little trouble connecting to my wifi ubuntu server. 16.0.4.1"
date: 2016-12-26
forum: Networking &amp; Wireless
---

### Post by garrett13 on 2016-12-26
k so what I'm having to do is turn it on (ifup wlp4s9) then I run down this list 

[http://askubuntu.com/questions/294257/connect-to-wifi-network-through-ubuntu-terminal](http://askubuntu.com/questions/294257/connect-to-wifi-network-through-ubuntu-terminal)    

but I'm getting stuck on number 3,  I keep getting (error for wireless request "Set ESSID" (8b1a) SET failed on device wlp4s9 ; operation not permitted.)

---

### Post by howefield on 2016-12-26
Moved to the "*Networking & Wireless*" forum.

---

### Post by praseodym on 2016-12-26
You need to run it as root:

```
sudo su
iwconfig wlan0 essid name key password 
exit
```

or using "sudo"

```
sudo iwconfig wlan0 essid name key password 
```

---

### Post by garrett13 on 2016-12-26
Ok so I get (Error for wireless request "Set Encode" (8B2A) : Invalid argument.)  
what I;m reading on here [http://superuser.com/questions/42460/can-you-explain-how-to-understand-what-the-iwconfig-command-displays-in-ubuntu](http://superuser.com/questions/42460/can-you-explain-how-to-understand-what-the-iwconfig-command-displays-in-ubuntu)   I need to change the password to something longer or type of securty (wpa2) I'm using wont work?

---

### Post by praseodym on 2016-12-26
WPA2 needs a PW with at least 8 characters. So, change it in your router interface, check the manual for that

---

### Post by SeijiSensei on 2016-12-26
Does your computer not have an Ethernet port?  In general, servers should be hard-wired rather than use wifi.

---

### Post by garrett13 on 2016-12-26
I am trying to get it setup on the ethernet port, but that's not working also.

---

### Post by chili555 on 2016-12-27
Did you read this in the link you gave?> The command iwconfig wlan0 essid name key password only works with access points that use WEP as encryption. If the access point uses WPA/WPA2, you'll have to use another method to connect, found here:Is your network protected with a $2 rusty lock called WEP???

I didn't think so.

This chap proposes a better method in my opinion: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

---

### Post by SeijiSensei on 2016-12-28
> **garrett13 said:**
> I am trying to get it setup on the ethernet port, but that's not working also.

Have you read this: [https://help.ubuntu.com/lts/serverguide/network-configuration.html#static-ip-addressing](https://help.ubuntu.com/lts/serverguide/network-configuration.html#static-ip-addressing)

What precisely do you mean by "that's not working also?"

---

