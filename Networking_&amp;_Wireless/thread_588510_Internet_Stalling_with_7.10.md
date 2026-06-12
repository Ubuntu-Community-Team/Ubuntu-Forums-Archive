---
title: "Internet Stalling with 7.10"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by rmstone1s on 2007-10-23
I upgraded to 7.10 a few days ago and things are great except I have an issue with my internet connection now.

For some reason when I do anything internet related it stalls up and nothing happens for several seconds before finally kicking in.  For instance I open firefox and click a bookmark, then it stalls for 5-10 seconds... doing nothing... and then it kicks in and fires up the page super fast.  same thing on downloads, long stall before they start and then it works fine full speed.

I don't know if this is directly 7.10 related or if I just have some lingering configuration from  7.04 causing this issue.  Any ideas?

---

### Post by negated on 2007-10-23
You might want to check your IPV6 settings in Firefox and in the OS itself.

For Firefox, type in "about:config" in the URL bar, then search for IPV6. You want **network.dns.disableIPV6** set to **true**.

For the OS, edit **/etc/modprobe.d/aliases** and change the line:

**alias net-pf-10 ipv6**

to

**alias net-pf-10 off**

Reboot and see if that makes a difference!

-S

---

### Post by boozker on 2007-10-23
OMG negated you are my hero. After hours and hours of trying to fix my intel 3495 it wouldnt work with the 7.10 update. People are having problems all over, at least 200 and counting from the polls. I changed that and it works fine now. Thank you so much. You really should reply to some other posts with intel people and see if it works.

---

### Post by rmstone1s on 2007-10-23
Worked great!! THANKS!

---

### Post by negated on 2007-10-23
> **boozker said:**
> OMG negated you are my hero. After hours and hours of trying to fix my intel 3495 it wouldnt work with the 7.10 update. People are having problems all over, at least 200 and counting from the polls. I changed that and it works fine now. Thank you so much. You really should reply to some other posts with intel people and see if it works.

> **rmstone1s said:**
> Worked great!! THANKS!

No problem guys. Glad I could help. 

Boozker: If you don't mind, just point people to this thread from the others.

-S

---

### Post by element on 2007-10-25
This fixed my problem on a Dell D820 Latitude.  Thanks!

---

### Post by handy on 2007-10-26
Here's a link to a detailed how-to on IPv6 prob's & stabilising DNS addresses, (if anyone still has that problem?):

***_[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)_***

---

### Post by philinux on 2007-11-11
Is it just firefox?

Try disabling ipv6 in ```
about:config
```

---

### Post by philinux on 2007-11-11
Sorry missed the explanatory link

[http://kb.mozillazine.org/Network.dns.disableIPv6](http://kb.mozillazine.org/Network.dns.disableIPv6)

---

### Post by Scott-271 on 2007-11-11
I tried changing it in the OS, but when I try to save it, I get an error: *Can't open file to write*, where am I going wrong? and how much more beer will it take? ;-)

---

### Post by handy on 2007-11-21
Details please?

Did you open your text editor with ***sudo*** ?

---

