---
title: "wifi connected but can't open web pages"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by gambang07 on 2011-08-14
After setting static IP address on my dual boot netbook, it is OK on XP while on Ubuntu I can get connected on wifi but I can't open web pages. The wireless security is  WEP.

---

### Post by westie457 on 2011-08-14
> **gambang07 said:**
> After setting static IP address on my dual boot netbook, it is OK on XP while on Ubuntu I can get connected on wifi but I can't open web pages. The wireless security is  WEP.

Hi.

Which browser are you using and what is the error message you are getting.

A few details of your system will be helpful as well. In a terminal please run ```
lshw -C network
```
Copy and in a new reply hit the # at the top of the message pane and paste the output between the [CODE] tags. This makes it easier to read.

Thank you.

---

### Post by corncob on 2011-08-14
> **gambang07 said:**
> After setting static IP address on my dual boot netbook, it is OK on XP while on Ubuntu I can get connected on wifi but I can't open web pages. The wireless security is  WEP.

My friend had that problem but I was still able to download the latest version of Firefox which got it working.  I suspect just a re-installation would have done the trick too.

---

### Post by docbop on 2011-08-14
You say it is dual booting and the windows side is working.  Well boot windows and copy the settings its gets when connected.  The IP, mask, gateway, and DNS settings.  Then boot Ubuntu and put in all those settings.  

If you can't get webpages, can you ping the website or telnet into port 80 if the website. That will help determine if a connectivity or browser issue.

---

### Post by HereInOz on 2011-08-14
Can you open a terminal and ping an IP address - for example:

ping 74.125.237.18

If you get a response from that, but not from:

ping google.com

then you have a DNS issue.

If you don't get a response from either of them, then it is a network issue.

If you get a response from both of them, but still can't open a web page, then it is probably a browser or proxy issue.

---

