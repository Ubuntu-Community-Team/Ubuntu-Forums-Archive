---
title: "Need easy HOWTO:   WPA, static IP, manual conifg"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by SeePU on 2008-02-10
I read the stickys, I googled and I have also configured manually, my /etc/network/interfaces file using WPA and DHCP.   But, I would like to have my wireless internet set up as follows:

Requirements:
1. WPA 
2. Static IP (I use port forwarding and there are more than one computer hooked up to the internet.  One is using dhcp and is not mine.  The others I need via static ip).
3. Pre-shared Key (WPA-PSK)
4. Hidden ESSID (?): I don't need this but would like the option

Most of all, I want to UNDERSTAND this inside out (if it will ever be possible) because the Wifi GUIs in all the distros give me trouble.

Please help/advise and if at all possible, present examples and easy-to-understand content/language so I can digest it.  

If I put it into numbers or percentages, I think I understand about 20%. :-/

I prefer to set up manually and it is inconvenient (and a bother since I share internet) to use a wired connection.   Not to mention, I plan to buy a laptop eventually so if I can understand/do this on my desktop, I can save myself some trouble, hopefully.   I use a usb wireless adapter which has worked before with DHCP, WPA as mentioned above.   The wireless chipset is zydas zd1211b and the router is Linksys WRT54G (the one that works well in Linux - ver. 2, I think).   My main issue is understanding the content of the network config file and the process involved.   There seems to be many variations in the content/text of the /etc/network/interfaces file so I'm not sure exactly what should be there (for WPA-PSK, STATIC IP).  Do I need to generate the key somehow or just make up my own password?   

Please help to understand so I can help others... Thanks.

---

### Post by kevdog on 2008-02-10
Take a look at this:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

