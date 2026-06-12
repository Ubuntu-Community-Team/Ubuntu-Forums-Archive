---
title: "Can't Specify No Wep Key?"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by kvidell on 2005-10-14
Hey everyone.
I was at my favourite coffee shoppe last night and attempted to take advantage of their free wireless service... But something went wrong.
How do I tell the system that it's an open AP, no WEP key required?
Choices in the gnome manager for that are "Hexadecimal" and "Ascii", but I can't tell it "none".

What to do?
I tried 00000000, "anonymous" and I even tried the following:
iwconfig eth1 key off commit
key none
and key open
none of them worked.
Something else I noticed is that it was broadcasting for an IP address on subnet 255.255.255.255. Is that normal? I think it should be .0 but I don't know how zis silly wireless works yet.

Thanks for any help.
- Kev

---

### Post by Dr. Nick on 2005-10-14
In /etc/network/interfaces set the ssid of the ap and then add the line
```
wireless_enc off
``` try that and see if it helps. You have to run
```
sudo /etc/init.d/networking restart
```

Here is a thread discussing my problems with connecting to another ap then mine at home, you can connect at home right?

[http://ubuntuforums.org/showthread.php?t=72362](http://ubuntuforums.org/showthread.php?t=72362)

some of that you can ignore if your not using wlan-ng drivers pretty much anyhing with "ng" anywhere in it. But some of the scanning and iwlist commands may help. 

You can reconfigure your home router ( I assume you have one ) to encryption on/off for testing and try setting a different ssid to test out that aswell , thats what I did.

Good luck and let us know how it goes

---

