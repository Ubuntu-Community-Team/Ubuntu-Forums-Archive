---
title: "Network bridge Ubunutu =&gt; Windows"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by HolyMarcell on 2008-12-02
Hey there,

I don't want to say "**** you Ubuntu" and give it a last chance, so please guide me ;)

Same problem as many here:
I have a Ubuntu-Box connected to the Internet per WLAN (eth1) and a Windows-Box connected to Ubuntu per Cross-Cable on eth0. This does not work at all!
As far as I can see I tried every Guide, read every manual and so on you can find in the web. Latest try was this post:

> **superprash2003 said:**
> install firestarter in the laptop [ the internet pc ] and enable internet connection sharing . or use this [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) . first try firestarter though


Dang, nothing worked. And I destroyed almost every config depending to network and rewrote it.

So there you are: I need (if possible and nessecary) a little help to configure my Network as default, so I can go on testing your steps.

Later on I need someone to help me fix this Ubuntu-Network-thing here.

The Windows-Box is well configured; I'm quite good in Windows-network-issues.
A (maybe selfresolving) problem is setting the WLAN (eth1) to the default network for ubuntu so I can browse the internet after setting up eth0 (LAN).
Then I think the real problem is the (in some guides needed) command:
$echo 1 > /proc/sys/net/ipv4/ip_forward
I'm not shure this works ( neither does: sh -c "[..]" I think). So howto check this?

I Hope this isn't confusing too much.

Regards,
HolyMarcell

---

