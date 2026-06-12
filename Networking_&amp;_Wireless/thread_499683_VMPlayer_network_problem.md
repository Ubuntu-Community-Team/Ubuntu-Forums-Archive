---
title: "VMPlayer network problem"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by kongwak on 2007-07-12
Hi,

I am experiencing some weird problem with VMPlayer under Feisty. 

I have windows with a shoutcast server installed in a virtual machine. Vmplayer starts and boots windows fine. Windows can connect to the internet and perform updates. I can ping ping the windows IP from Feisty. However, I can not access the shoutcast stream from feisty, nor can I find any drives that I have shared on the windows virtual machine. However, if I run the same virtual machine from with vmplayer on a windows box, all the services are available and working.

Just to see if I was going mad, tried a VM with  a LAMP server (gentoo linux). The same deal, worked fine under windows, but if I tried to access its services (http, ssh, smb)  when I tried to start it fro Feisty, I couldn't. Yet I can ping the IP and access the network from within the VM.

I don't get any error messages. For example, if I try to access a web page from the LAMP server or shoutcast server, the browser will think for a long time and eventually return a blank page. SSH just tries to connect and I eventually have to kill the process (ctrl + c).

I am stumped. Does anyone have any suggestions?

regards
Kongwak

---

### Post by Eazy© on 2007-07-13
Sounds like you have the firewall on. Think you need to open the port your shoutcast-server is using. 

Fyi. there is a shoutcast server for linux availible , so you dont need windows for that.

---

### Post by kongwak on 2007-07-15
Good suggestion Easyc. I will check it out.

kongwak

---

### Post by Oddvar on 2007-07-31
Hi, I have installed win xp pro like described in [http://bedr.se/how-to-install-windows-xp-on-linux.htm](http://bedr.se/how-to-install-windows-xp-on-linux.htm)
Windows start fine, but it have no access to internet!
And using Windows and Kazaa was the main reason for installing Windows. Can anyone please help me with this? All hardware and network seems to be in place in Windows, but it dont connect to internet. 
What can I do?

Thanks, Oddvar

---

