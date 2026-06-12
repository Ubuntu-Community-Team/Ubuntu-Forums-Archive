---
title: "Edgey Eft: can't get WEP with passphrase to work"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by rstoya05-lx on 2007-05-05
Hi, I'm using nm_applet and am not able to connect to networks with a WEP passphrase. I know the passphrase is connect and the wireless network works but I can't connect to it. 

After I type the passphrase I see one sphere goes green but the second one never goes green and it eventually fails to accept and prompts for a passphrase again. 

Any suggestions on how to find out what's going on? I'm using Ubuntu 6.10 on a Lenovo T60. I am able to connect to open networks and to at least one WPA wireless network.

Thanks!

---

### Post by chili555 on 2007-05-06
Network Manager and nm-applet are graphical front-ends for *iwconfig* and some other commands. Here is a quote from the manual page for *iwconfig* referring to WEP:> key/encryption...Passphrase is currently not supportedSo, you will need to get into the administration page of your router or access point and find the hex or ASCII key that the passphrase translates to. In other words, 'ilovecoldbeer' will not work; 096c7f299e1154...etc. will.

Passphrase is an option for WPA and that's why Network Manager shows an input for passphrase.

---

### Post by rstoya05-lx on 2007-05-06
Thanks for the tip! I'm connected now.

It turns out what I had was a 10-character hexadecimal key so I entered it under the option "WEP 64/128-bit Hex" and it worked. 

The man page for iwconfig says "You can also enter  the  key  as  an  ASCII  string  by  using the s: prefix. So I wonder if in the case of routers set up with a password like 'ilovecoldbeer' one could enter this on the command line:

```
iwconfig eith1 key s:ilovecoldbeer

```

---

### Post by chili555 on 2007-05-06
I think some people mix apples and oranges. My example, 096c7f299e1154...etc., is an abbreviated example of a hex key. In many places, you see this referred to as a hex passphrase. However, many routers have a system to generate a hex or ASCII key from a passphrase, such as 'ilovecoldbeer.' Some people try to use 'ilovecoldbeer' as the passphrase, which, as we learned, *iwconfig* will not accept.

Moreover, 'ilovecoldbeer' has 13 characters, all of which are accepted ASCII characters and is the correct length for a 128-bit ASCII key. If one simply entered the ASCII key 'ilovecoldbeer' in the routers admin pages, assuming it accepted ASCII, then it would work fine with *sudo iwconfig eth1 key s:ilovecoldbeer*

Simple, isn't it?

---

### Post by rstoya05-lx on 2007-05-06
Makes sense. Thanks for your help.

---

