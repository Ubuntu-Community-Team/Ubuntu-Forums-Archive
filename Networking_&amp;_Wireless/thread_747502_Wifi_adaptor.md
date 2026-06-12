---
title: "Wifi adaptor"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by 2j4ez on 2008-04-06
Just set up ubuntu on my laptop again got a new wifi card a EDIMAX EW7318usG i want to use this card with my laptop

I downloaded a the windows wireless driver tool it asks me for the INF file but on the CD and on there website it only got a EXE file no inf file 
its got on the CD files for DEBAIN,FEDORA,MANDRAKE,SUSE linux can i use one of these??

thanks

---

### Post by jimrz on 2008-04-06
> **2j4ez said:**
> Just set up ubuntu on my laptop again got a new wifi card a EDIMAX EW7318usG i want to use this card with my laptop

I downloaded a the windows wireless driver tool it asks me for the INF file but on the CD and on there website it only got a EXE file no inf file 
its got on the CD files for DEBAIN,FEDORA,MANDRAKE,SUSE linux can i use one of these??

thanks

 I would suggest searching these forums for card model to see how others have been able to get it functioning properly. If no luck, I would first try the Debian one from your cd, as Ubuntu is Debian based.

---

### Post by 2j4ez on 2008-04-06
have no clue how to install the debain driver just got a loads of files nothing to double click i'm still new to ubuntu

---

### Post by brian_p on 2008-04-06
> **2j4ez said:**
> Just set up ubuntu on my laptop again got a new wifi card a EDIMAX EW7318usG i want to use this card with my laptop

Coincidently I intended to buy one of these yesterday but the supplier was out of stock.

> I downloaded a the windows wireless driver tool it asks me for the INF file but on the CD and on there website it only got a EXE file no inf file 
its got on the CD files for DEBAIN,FEDORA,MANDRAKE,SUSE linux can i use one of these??

thanks

The card's chipset is supported within Ubuntu. There is no need to touch Windows drivers.

```
apt-cache search rt25
```

I think rt2570-source is what you want. The module-assistant package will be needed to compile the kernel module.

Look here and follow the link  to the Linux Emporium.

[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=7241](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=7241)

---

### Post by 2j4ez on 2008-04-08
not having much luck typed out what you said and got this

rt2500 - configuration tool for wireless RT2500 network cards
rt2500-source - source for rt2500 wireless network driver
rt2570-source - RT2570 wireless network drivers source
rt2x00-source - RT2x00 wireless network drivers source


now what do i do?

thanks

---

### Post by brian_p on 2008-04-08
> **2j4ez said:**
> not having much luck typed out what you said and got this

rt2500 - configuration tool for wireless RT2500 network cards
rt2500-source - source for rt2500 wireless network driver
rt2570-source - RT2570 wireless network drivers source
rt2x00-source - RT2x00 wireless network drivers source


now what do i do?

thanks

Read post #4 and

[http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto](http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto)

---

