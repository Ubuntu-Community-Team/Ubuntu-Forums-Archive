---
title: "Wired connection to eduroam"
date: 2017-11-23
forum: Networking &amp; Wireless
---

### Post by corryolis on 2017-11-23
This issue is driving me crazy!

I can't connect my pc via ethernet to my university wifi.

I've looked up many guides and followed them word by word and I just can't figure it out.

So, eduroam is secured with 802.1x authentication, I'm just trying to connect to the network. Here's what I did, step by step:
[LIST=1]
[*]I hooked up my ethernet
[*]I opened Network connections, clicked 'Add' and selected Ethernet
[*]I named the connection eduroam, selected my device then moved to the 802.1x security tab and entered the following:
[/LIST]

Authentication: Protected EAP (PEAP)

Anonymous identity: (left this blank, I have tried putting my username here.)

CA certificate: AddTrust_External_Root.pem (this is from the etc/ssl/cert directory)

PEAP version: automatic

Inner authentication: MSCHAPv2

Username: [email]myUsername@myUni.ac.uk[/email]

Password: myPassword


I'm just baffled by this issue!

---

### Post by blackbird34 on 2017-11-23
What about digging around on your university website for a tutorial? 

Also, Ethernet is a wired internet connection. Wi-fi is a wireless network. There should be a wireless network that you can connect to called "eduroam", whose settings you configure with your username, password, etc. The Ethernet connection (in my experience -am currently  a doctoral student in Europe) is nothing to do with eduroam.

---

### Post by corryolis on 2017-11-23
It's the same login, the name matters very little, but it is the name used in the tutorials 

I've contacted the uni and they have said that they are inexperienced with Unix.

---

### Post by blackbird34 on 2017-11-26
The eduroam association of university sysadmins have a tool that should help you configure your connection. You need to specify which university you are from so it gives your the correct settings. There's a Linux version. See [https://cat.eduroam.org/#](https://cat.eduroam.org/#)

---

