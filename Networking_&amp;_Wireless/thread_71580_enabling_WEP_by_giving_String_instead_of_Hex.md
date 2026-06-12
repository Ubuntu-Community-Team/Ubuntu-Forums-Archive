---
title: "enabling WEP by giving String instead of Hex"
date: 2005-10-03
forum: Networking &amp; Wireless
---

### Post by siku on 2005-10-03
I've searched the forum for help on enabling WEP on wireless network. Most of them gave different methods but how to enable WEP by giving passphrase as a string instead of a hex key.?
The reason is that I use windows XP, and use the same wireless connection. In windows I can give the passphrase as a string. 
Another alternative I saw was to find a hex key for my passphrase. Can I do that in windows? or 
can I use a different program in Ubuntu to do that all.
help

---

### Post by MetalMusicAddict on 2005-10-03
You can usually find the "Hex" of your passphrase in your router config. I can in my Linksys. [HERES]("http://www.powerdog.com/wepkey.cgi") a link to a converter if you cant get it in the router. 

If you wanna add the WEP key as a passphrase I think you add a "a:" before the passphrase. Like **a:sandwitch**

---

### Post by bs_ on 2005-10-03
You can specify the key as an ASCII string with the **s:** prefix. For example:

```
iwconfig eth0 key s:password
```

You can learn more about the option by reading the iwconfig man page.

---

### Post by siku on 2005-10-04
Another problem is that there's a  bunch of wireless netowrk.
This is what I usually do for an unsecured one:
> iwlist eth0 scan
iwcofig eth0 essid "Wifi_name"
dhcp eth0

where would I insert the passphrase would I do it in the same line as 
iwconfig eth0 essid ?
Help

---

### Post by siku on 2005-10-06
I tried to solve this by generating the hex key in the above given website and pasting it on the key field. But the connection fails. 
Once again where Do I put the key in

---

### Post by MetalMusicAddict on 2005-10-06
Do this:
```
sudo gedit /etc/network/interfaces
```

Where it says "wireless-key" paste in your Hex string.

ie: **wireless-key 12345678901234567890123456**

I have always had to input Hex. The **s:password** option never really worked for me.

---

### Post by siku on 2005-10-10
how do you apply the changes.? without restarting that is.

---

