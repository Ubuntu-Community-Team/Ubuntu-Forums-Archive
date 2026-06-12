---
title: "Thinkpad T61 WPA2 Enterprise on Hardy"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by tsfraser on 2008-07-25
Work supplied me with a Lenovo T61. 

The wireless **does** work for open wireless connection, and it works at home with my WPA2 Personal connection. It successful sees the networks available. 

But when I try to hook up to my works wireless which uses a WPA2 Enterprise EAP of TLS my Idenity passing a Client Certificate File, CA Certificate File and Private Key File and giving my Private Key password. It will not connect to the network.

I don't have much experience with using Linux with wireless. I have more experience using it with servers with a wired connection which for the most part "Just works" so I have been using the Network Manager applet. Which may or may not be the problem. 

I did down grade to Gusty and I was able to connect to the corporate WPA2 Enterprise with Gusty however it came at a cost of more bugs in other areas which Hardy fixed.

If anyone knowes if this has been posted before or a patch to fix the problem it would be helpful.

---

### Post by vevel on 2008-09-05
Are you still having problems?

I am running fine with 8.04 (Hardy) using the built-in wpa_supplicant (used more or less transparently by Gnome network manager).   

I'm connecting to a WPA2 Enterprise system with PEAP with phase2 mschapv2.   There are also certs working, but everything was auto-detected.   

I was struggling with this for a while until I wiped everything and let network manager/wpa_supplicant/Ubuntu do things magically.   I expected to have to edit conf files manually, but no.   I was prompted for my user id and password, and everything else worked.  

If you're still having trouble, let us know what exactly you're trying.

---

