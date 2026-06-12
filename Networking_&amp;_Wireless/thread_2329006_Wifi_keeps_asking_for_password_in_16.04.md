---
title: "Wifi keeps asking for password in 16.04"
date: 2016-06-27
forum: Networking &amp; Wireless
---

### Post by jdkcarlson on 2016-06-27
I have an Acer Aspire series laptop running 16.04 and had troubles getting the wireless working generally, now solved (one can find my previous problems here: ubuntuforums.org/showthread.php?t=2328020). At most routers, my wifi now works fine. But I'm staying as a guest now somewhere where this keeps happening:

[http://askubuntu.com/questions/458967/ubuntu-14-04-my-computer-sees-the-wireless-network-but-wont-connect-to-it-k](http://askubuntu.com/questions/458967/ubuntu-14-04-my-computer-sees-the-wireless-network-but-wont-connect-to-it-k)

It doesn't say the password is wrong, just keeps asking for it. My password is listed in the network connections and is right, as I'm sending this through a phone using the same password. 

Sudo service network-manager restart

hasn't worked, nor has adding the line

REGDOMAIN=BR

to /etc/default/crda

I've seen it suggested elsewhere that one should switch to pure WPA2 encryption instead of WPA/WEP but that doesn't seem to be an option when I edit the connection. What can I do to end this cycle?

---

### Post by X-RED_Tech on 2016-06-27
> **jdkcarlson said:**
> I've seen it suggested elsewhere that one should switch to pure WPA2 encryption instead of WPA/WEP but that doesn't seem to be an option when I edit the connection. What can I do to end this cycle?

Actually it has been suggested pretty much everywhere. But those changes you do at the router, not at any client.

---

### Post by QDR06VV9 on 2016-06-27
This has been an interesting ordeal...It also has been reported that "Gnome Key ring with Seahorse" installed will stop that also.
By me installing the two of those I no longer get asked for password for networking.

---

### Post by ashwin7 on 2016-06-28
Also try changing Authentication : in some cases Tunneled TLS works while in some cases Protected EAP (PEAP) works.

---

### Post by jdkcarlson on 2016-09-07
> **QDR06VV9 said:**
> This has been an interesting ordeal...It also has been reported that "Gnome Key ring with Seahorse" installed will stop that also.
By me installing the two of those I no longer get asked for password for networking.

I've installed both of them, but so far the problem persists. Would you be able to remember what you did after that?

ashwin7: the Authentication trick has not borne fruit.

**update-update**: It started working on the network in question. I still don't know why.

---

### Post by catchmeoutside99 on 2017-02-02
Changing from Tunneled TLS to Protected EAP (PEAP)  worked for me and I'm running Ubuntu 16.04.1 LTS on an HP Pavillion dv6000.

---

