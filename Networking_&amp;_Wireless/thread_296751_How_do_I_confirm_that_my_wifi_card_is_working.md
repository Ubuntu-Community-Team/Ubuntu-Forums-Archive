---
title: "How do I confirm that my wifi card is working?"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by manishk on 2006-11-10
Hi,
   After many failures I finally installed **fwcutter** and extracted the firmware of the bcm43xx driver into **/lib/firmware**. 

I even '**modprobe**'d it. And I see some new lines containg *bcm43xx*.

The question is how do I connect to the net now? I can't install gnome-network manager until I get a connection since wireless is my only option.

Pls help.

---

### Post by manishk on 2006-11-10
I just noticed this:

In System>Admin>Networking i can see only my LAN card and my modem only. No wireless card.

---

### Post by ciscosurfer on 2006-11-10
You can try issuing **iwconfig** in a terminal.

---

### Post by manishk on 2006-11-10
Thanks a lot but...

I'm a noob...can you pls tell me what result I should expect from this if my card has been set up properly

---

### Post by ciscosurfer on 2006-11-10
You can look at the man pages for info on using it```
man iwconfig
```

---

### Post by manishk on 2006-11-11
iwconfig returned this result

> lo         no wireless extensions.

eth0     no wireless extensions.

sit0      no wireless extensions.


and lsmod gave this 

Module                  Size  Used by
bcm43xx                127628   0
 
ieee80211softmac        32640   1 bcm43xx

ieee80211               39240   2 bcm43xx,ieee80211softmac

ieee80211_crypt          8448   1 ieee80211

ipv6                   300416   6

---

### Post by ciscosurfer on 2006-11-11
I would suggest searching ubuntuforums with keyword **wireless** and you will get many topics and threads that will attempt to answer your question.

You can also check the [Hardware compatibilty list]("http://doc.gwos.org/index.php/Networkwifi") on UDSF

---

