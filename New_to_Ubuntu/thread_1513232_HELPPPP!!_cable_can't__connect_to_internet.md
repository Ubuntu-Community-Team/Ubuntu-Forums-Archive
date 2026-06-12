---
title: "HELPPPP!! cable can't  connect to internet"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by wiisg on 2010-06-19
Just installed ubuntu 9.10 this morning. I am using rj-45 cable connects to my modem. I plug in the cable but still can't connect to internet but on my network card i see LED shines. Is it because of driver something? BTW this is my first time using ubuntu have no prio knowledge about linux and everything hereee.. pls help!!!! tq

---

### Post by HereInOz on 2010-06-19
My guess is that you have a DNS issue.  Some modems do not handle DNS properly when they assign IP configuration via DHCP.  

The first step is to open a terminal window and type in:

ping google.com

then press enter.  You should get a response from google.com, but in your case, I am guessing that you will not, and the ping request will fail to get a response.

If you don't get a response, try:

ping 66.102.11.104

then press enter.

If that succeeds, then your problem is DNS.  

One remedy is to set a static IP address for your Ubuntu machine in Prederences > Network Connections > auto eth0, and set the DNS address to your ISPs DNS server address.

See how you go.

---

