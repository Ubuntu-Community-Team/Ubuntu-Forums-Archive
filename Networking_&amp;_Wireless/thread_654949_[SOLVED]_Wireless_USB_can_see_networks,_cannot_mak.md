---
title: "[SOLVED] Wireless USB can see networks, cannot make connection..."
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by Nrbelex on 2007-12-31
Hi, I have a USB wireless network card ([Linksys WUSB 11 V2.6]("http://linux-wless.passys.nl/query_hostif.php?hostif=USB")) which IS compatible with 2.6.x kernels and it can see networks, but cannot connect.... Is it normal for the system monitor to show zero outgoing activity during the making of a connection?

Thanks,
~ Brett

---

### Post by Nrbelex on 2007-12-31
After turning off the WEP key, I now have outgoing bytes, but still no connection...

---

### Post by Predator[23rd] on 2007-12-31
Hi!

WEP is the weakest possible encryption method you can use. once you have sorted out your connectivity issues try WPA-PSK or anything else, BUT NOT WEP. :)

if you can see wireless networks with the network manager it means your wireless card is being recognized and working properly. the problem might be somewhere in finding the right settings for the wireless network you are trying to connect to. maybe some encryption or authentication method is used which can not be handled by either your wireless router or wireless card.

---

### Post by Nrbelex on 2008-01-02
I'm still looking for help here...

I can see networks but I cannot connect - secured or not.

~ Brett

P.S. - when doing a tail and grep to the syslog for the NetworkManager, I usually get a string of "old device 'wlan0' activating, won't change." and then it re-asks me for a WEP key...

---

### Post by Nrbelex on 2008-01-03
B-b-b-bump

I bought another wireless USB card and tried that too... no dice, so I'm returning it.

The original one (Linksys WUSB 11 V2.6) was working before without anything special - just worked out of the box - but stopped working when I upgraded to 7.10. 

A typical attempt to connect with this card - with or without any form of encryption - looks like:

```
rebecca@rebecca-linux-desktop:~$ tail -f /var/log/syslog | grep -i networkmanager
Jan  3 21:56:50 rebecca-linux-desktop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jan  3 21:56:59 rebecca-linux-desktop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jan  3 21:57:04 rebecca-linux-desktop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jan  3 21:57:09 rebecca-linux-desktop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jan  3 21:57:14 rebecca-linux-desktop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jan  3 21:57:24 rebecca-linux-desktop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jan  3 21:57:29 rebecca-linux-desktop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jan  3 21:57:35 rebecca-linux-desktop NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), asking for new key. 

```

Any thoughts are truly appreciated!
~ Brett

---

### Post by Nrbelex on 2008-01-06
bump... and sigh...

It was working before!

~ Brett

---

### Post by Nrbelex on 2008-01-06
Had to switch to wicd instead of the network manager... but it's now working.

:)

~ Brett

---

### Post by svenkatesan on 2008-01-06
I too have this problem..
by the way what is wcid? where to activate?
thanks in advance.

---

### Post by Nrbelex on 2008-01-07
> **svenkatesan said:**
> I too have this problem..
by the way what is wcid? where to activate?
thanks in advance.

[wicd]("http://wicd.sourceforge.net/") is a wireless network manager for Linux. Instructions for its installation on Ubuntu can be found [here]("http://wicd.sourceforge.net/wiki/doku.php?id=faq"). It's pretty simple but you'll need a way to get the computer temporary internet access (i.e. via wire) or transfer the packages via  disk or something. 

~ Brett

---

