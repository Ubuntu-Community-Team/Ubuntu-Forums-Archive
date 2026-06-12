---
title: "Wireless only works when router is unsecured"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by SupaFupa on 2006-11-10
Im brand new to linux, and installed ubuntu 6.10.  I can connect to the router with the wireless security off, but when I turn it on, it doesn't work.  Ive tried both WEP and WPA, and have been able to connect with windows, but not ubuntu.  Any help is much appreciated.

---

### Post by FrodoB on 2006-11-10
If you can connect without WEP then the only issue left is to get the same keys into both access point and wireless device. 

 Make sure that you enter the keys in HEX format on both sides, some router have issues otherwise.

Here is an excellent source for creating the various WEP keys that you might need in both ASCII and HEX formats.

Best of Luck

---

### Post by SupaFupa on 2006-11-10
I tried reentering the key, using uppercase letters, as that is how it is in the router, and that made no difference.  I was using DHCP, tried swithcing to static ip, to see if there was any change.  Doing this, I was able to access the router, but nothing else.  Here are the addresses and mask I used

IP: 192.168.1.103
SM: 255.255.224.0
Gateway : 74.132.224.1

I got these off of the router's status page, and decided to try them.  

Any Clues???

---

### Post by awakatanka on 2006-11-10
> **SupaFupa said:**
> Im brand new to linux, and installed ubuntu 6.10.  I can connect to the router with the wireless security off, but when I turn it on, it doesn't work.  Ive tried both WEP and WPA, and have been able to connect with windows, but not ubuntu.  Any help is much appreciated.
What brand/chipset you use?

---

### Post by SupaFupa on 2006-11-10
specs:
 
AMD AthalonXP 3200+ 2.2 GHz
1GB Ram
Via KT880 Chipset
Asus A7v880 motherboard

Wireless:

card: wmp54g 
router: wrt54g

---

### Post by scrooge_74 on 2006-11-10
> **SupaFupa said:**
> specs:
 
AMD AthalonXP 3200+ 2.2 GHz
1GB Ram
Via KT880 Chipset
Asus A7v880 motherboard

Wireless:

card: wmp54g 
router: wrt54g

Probably is the keys you are using check if they are hex or ascii in both router and computer.

Maybe you check the option of only allowing ethernet cards your router has its MAC address on file?

---

### Post by SupaFupa on 2006-11-10
Problem is fixed.  I reloaded the driver in windows.  Not really sure why that fixed the problem, but it did.

---

### Post by drfalkor on 2006-11-10
edit: nevermind

---

### Post by wekebu on 2006-11-18
SupaFupa,
What version of wrt54g & wpm54g do you have?  What did you do to get the wireless card to work?  I don't need wpa or wep, I'd love to get this card to work.  I've been reading so many different suggestions on getting the wmp54g to work that my head is spinning...

---

