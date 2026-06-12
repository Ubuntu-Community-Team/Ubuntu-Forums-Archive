---
title: "Problem online using ubuntu 6.06"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by sekret on 2007-03-06
Hello guys,

I'm new at here and i need support from all of you.I done s few searching about my problem but cabot find the suitable way for me.By the way , here is the screenshot before i tell you guys the problem.

[IMG]http://img96.imageshack.us/img96/8008/screenshotcv4.png[/IMG]

I'm connecting to the internet using router to modem.The brand i'm using for the network card is Via compatable Fast athernet adaper.

The problem is i can't get to any site to the internet.Google,yahoo and etc.This problem same happend when i'm logging into my Gaim.There is progress when i'm typying at the browser but it didn't direct me to the website.

Anyone can help me solve this problem?

---

### Post by sekret on 2007-03-08
Bump...No one know the answer?

---

### Post by Mr. C. on 2007-03-08
Your DNS settings are incorrect, or are missing.

See  my recent post here:

[http://ubuntuforums.org/showthread.php?t=378984](http://ubuntuforums.org/showthread.php?t=378984)

MrC

---

### Post by Floppyjoe on 2007-03-08
Can you ping other sites? Like ubuntuforums.org?

---

### Post by sekret on 2007-03-08
Yes i can ping website.I have try pinging the google and etc website.And i got response from the pinging i do.

---

### Post by sekret on 2007-03-11
bump

---

### Post by Mr. C. on 2007-03-11
sekret, did you review the post I mentioned?

What is the output of :
```

ifconfig -a
cat /etc/resolv.conf
```

Also show your router's settings for the LAN IP Address, Netmask, Gateway, and DNS server(s).

MrC

---

### Post by sekret on 2007-03-14
Thanks for the help Mr.C .Well now i get the internet work in my ubuntu.But when i restart my PC the setting for my DNS back to the LAN setting which didn't give me authorized to access into the internet.I need setting the DNS each time i get into the ubuntu,.How can i solve this one?

---

### Post by Mr. C. on 2007-03-15
Your router is responsible for providing the DNS settings IF you choose to use DHCP.

If your router is providing Ubuntu with itself (the router) as the DNS server, Ubuntu obeys.

If you believe you have your ISPs DNS servers settings correctly configured in the router, and there is no option to disable using your router as the DNS server, a) check for a firmware update for your router, or b) configure a static IP on Ubuntu and do not use your router's unreliable DHCP service.

Make sense?
MrC

---

