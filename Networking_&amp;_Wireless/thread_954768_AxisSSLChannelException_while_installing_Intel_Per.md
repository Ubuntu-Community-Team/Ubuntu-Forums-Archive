---
title: "AxisSSLChannelException while installing Intel Performance Primitives"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by darthshak on 2008-10-21
Hi

I had installed openCV on my ubuntu hardy install 32-bit. I decided to download the Intel Performance Primitives(IPP) for Linux as the application I am writing using openCV needs all the optimization it can get.

Now, I got the .tgz file off the Intel site. When I ran the install script, it was not able to connect. It asked me for my proxy server IP and port (I'm on a university network), which I furnished. The install script promptly terminated with the following :

terminate called after throwing an instance of 'AxisSSLChannelException'
  what():  23AxisSSLChannelException

I tried different proxies to no avail. Changing the proxy in the bash environment wouldnt make a difference either. Does anyone know what exactly this particular exception is and how I can work around it?

---

### Post by rogermexico45 on 2010-01-08
Hi darthshak,
 
unfortunately I can't help you, but I encountered the same problem when I tried to
install a demo of Intel Vtune. 
Did you find a fix meanwhile?

---

