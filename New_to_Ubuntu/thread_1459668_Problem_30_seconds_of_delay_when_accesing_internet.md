---
title: "Problem: 30 seconds of delay when accesing internet (Ubuntu 9.10)"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by Deniii on 2010-04-21
When an app tries to acces the internet, it takes about 30 second to start. For example:
-If I type and address in Firefox I have to wait 30 second until the browser start requesting the site
-If I want to download something form Synaptic, I have to wait about 30 seconds until the download begins
-When I want to conect to a server with IRC, I have to wait about 30 second until the connection request starts
-Etc

The internet conection was working perfectly fine until yesterday on Ubuntu and it still does on windows.
I have been installing a lot of things via Synaptic. Could some of those things be the problem?

I have a cable modem and my PC (wired, no Wifi) conected to a router.
I can tell the apps aren't accesing the internet for about 30 seconds because, when they do, the led on the router corresponding to the plug where the ethernet cable is conected, starts blinking and when no app is using the internet it stays lit.

So, if I type a web address on Firefox and then hit enter, the led stays lit for about 30 seconds and then it starts blinking and that's when Firefox starts accesing the internet.

Does anyone know how to solve this? (or at least what causes it so I don't do the same thing on the next install of Ubuntu)

Thanks.

---

### Post by wojox on 2010-04-21
Try disabling IPv6: [http://wojox.homelinux.org/?p=46](http://wojox.homelinux.org/?p=46)

---

### Post by Deniii on 2010-04-22
wojox: thanks for the reply.
IPv6 was disabled. In the link you posted, it's said IPv6 is on by default but I didn't disable it so:
A) It was disabled when I installed Ubuntu
B) Another app disabled it

Even though it's disabled, I still have the conection problem.
I have attached a screenshot that shows it's disabled.

The word &#28961;&#35222; inside the dropbox means "ignore". Among all the options, that's the only one which could have the same meaning as disabled. The others are "manual", "automatic", "automatic addresses only", "link local only" and "share with another computer"

Do you have another theory about this problem?

---

### Post by xboxmods3077 on 2010-04-30
Yep. I have this same problem in 10.04. When attempting to load a website, download updates, or install packages via Apt-Get. I remember this problem for sure in 9.10, and possibly 9.04, but I don't remember which version it started in.

Anyway, I have added the boot flag that wojox mentioned above, no go.

I have tried entering manual IP and DNS info into network manager for my connection.

I know it is not network hardware or computer hardware at fault because my system Dual-boots Windows 7 which does not suffer from this. It is looking more and more like this little problem is becoming a big problem. 

Any other ideas, thoughts, or suggestions. 

"All Donations Appreciated" :lolflag:

---

### Post by primetime34 on 2010-05-04
I have the same problem and would love to know what is causing it.  I also have ipv6 disabled

---

### Post by dearingj on 2010-05-04
Does this 30-second delay happen when you ping your router (system->administration->network tools->ping tab)?

---

### Post by xboxmods3077 on 2010-05-05
I am getting 1.36 Ms average ping time and I am not having the delay anymore. 

Variables since problem disappeared:

I changed internet providers. I was connected to a WiFi network being supplied by (Comcast) cable internet. Now, I am connected to a WiFi net provided by (verizon) DSL. I dunno if that makes a diffence but I threw it in.

Added the boot flag mentioned above. 

Manually entered alternate DNS servers. I first entered the 2 secure DNS's provided by Comodo Firewall (separated by commas, of course) and then entered the IP of my router (separated by a comma) as the third DNS, and the problem seems to have disappeared.

Not sure what caused it but for reference, here are the secure DNS servers provided by Comodo: 

DNS 1) 156.154.70.22  
DNS 2) 156.154.71.22

Maybe the geniuses here can come up with a possible cause based on the info I have provided here.

---

### Post by primetime34 on 2010-05-05
Mine's never been 30 full seconds but pinging ubuntu.com gave an average time of 175.67ms.  There just seems to be a delay...

---

### Post by jaytek13 on 2010-05-05
Same problem with 10.04 64bit edition here. I also have the 32bit edition installed on a different computer which hasn't presented any issues. There is no delay abnormal delay when pinging or tracerouting to a domain name.

---

### Post by xboxmods3077 on 2010-05-06
I forgot to mention, my problem was with 64-bit 10.04.

---

