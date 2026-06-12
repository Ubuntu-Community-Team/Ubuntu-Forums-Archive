---
title: "Connect to Ubuntu-Server on Virtualbox from the Web"
date: 2015-09-10
forum: Networking &amp; Wireless
---

### Post by Alf_Wernersson on 2015-09-10
Last week I searched for information on how to install Ubuntu 4.14 Server on VirtualBox. I have come a long way, but a lot remains.

For the moment I can "ping" from my desktop to the server on VirtualBox and back to desktop. Likewise, I can ping from the ubuntu-server to google.com (IP 8.8.8.8). I can also connect to server with &#8220;ssh user@ipadress&#8221; from a terminal in desktop (Ubuntu 14.04).

It can connect FileZilla to ubuntu-server, it is probably any rights that need to be fixed.

However, I still can not connect to the Ubuntu server via the Internet. To begin I want to do it without own domain name to verify that it can communicate.

Would be extremely grateful if someone could tell me how I should do with that matter, and how I can see what is wrong.

(Do not blame me if my English is poor, blame Google Translate!) :D

---

### Post by houstonbofh on 2015-09-10
You need to have the Virtualbox nic in bridge mode with your desktop nic.  Right now your server is in a virtual network inside you desktop, and nothing can see it but your desktop.

---

### Post by Alf_Wernersson on 2015-09-11
Hi **[houstonbofh]("http://ubuntuforums.org/member.php?u=123056"), ****thanks for answering! **
Sorry I gave too little details. I have two interfaces. One NAT and one Bridged Adapter. I enclose also the "/ etc / network / interfaces" and "/ etc / host". Maybe they are not correct. I also suspect the configuration of Apache.
I think that I can connect to my server from the internet without an own domain. If that is true, how should I do?
My Desktop is Ubuntu 14.04 and on Virtualbox I have Ubuntu 14.04 Server. Virtualbox is 4.3.26
Do somebody else done the same installation?
Regards
Alf

---

