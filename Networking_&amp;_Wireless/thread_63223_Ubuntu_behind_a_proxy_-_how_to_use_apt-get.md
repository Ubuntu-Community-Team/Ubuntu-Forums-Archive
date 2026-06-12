---
title: "Ubuntu behind a proxy - how to use apt-get"
date: 2005-09-07
forum: Networking &amp; Wireless
---

### Post by slooksterpsv on 2005-09-07
I'm running Hoary Hedgehog (5.04) on the iBook in my signature: G3, 500 MHz, 320MB RAM, 20GB HDD, etc. Anyways, I'm connecting through dial-up internet behind a proxy server. My moms computer - Win XP SP2 Home Edition - is connecting to the internet via dial-up. We are networked together so that I connect through the internet through her from a program called FreeProxy 3.8.1 - we're using a Belkin Router also. How would I go about using apt-get via bash terminal to connect and download packages? My Network Proxy is configured as well.
I've set my proxies to 80 for http & ssl - I know, that's not good - , 21 for FTP, and 1080 for SOCKS 4 & 5.

Anymore information, I'll gladly post.

---

### Post by kirsche on 2005-09-07
Hi,

check this article, it talks about security issues, but it should contain the info you need:
[http://www.linuxquestions.org/questions/archive/26/2005/04/3/313207](http://www.linuxquestions.org/questions/archive/26/2005/04/3/313207)

---

### Post by slooksterpsv on 2005-09-07
[QUOTE=kirsche]Hi,

check this article, it talks about security issues, but it should contain the info you need:
[http://www.linuxquestions.org/questions/archive/26/2005/04/3/313207](http://www.linuxquestions.org/questions/archive/26/2005/04/3/313207)[/QUOTE]
 Theres no apt.conf file in that folder, it creates a new file when editing it and that. So do I just put in 
```

APT {
Acquire {
http::*my_proxy_number*;
};
}

```
Right?

---

### Post by mlomker on 2005-09-07
I poked through Google a bit and ran across this idea...set an environment variable in your terminal window prior to running apt-get.  Here's the syntax:

export http_proxy=http://my.proxy.server:3128/

---

### Post by slooksterpsv on 2005-09-07
[QUOTE=mlomker]I poked through Google a bit and ran across this idea...set an environment variable in your terminal window prior to running apt-get.  Here's the syntax:

export http_proxy=http://my.proxy.server:3128/[/QUOTE]
 Way to go mlomker, you just fixed my problem. Thank you thank you thank you

---

### Post by Jimmy The Clown on 2005-09-21
Thank you so much.

---

