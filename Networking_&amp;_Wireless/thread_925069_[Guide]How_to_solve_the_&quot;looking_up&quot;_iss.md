---
title: "[Guide]How to solve the &quot;looking up&quot; issue"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by wendigo10 on 2008-09-20
**General description : **Firefox gets slow as hell, stops responding, or doesn't connect to specific sites. Sometimes it affects Pidgin as well."Looking up google.com" or similar phrases always appear on the status bar. It happens randomly, or when browsing specific sites.

**Ussually, it's a DNS problem, or some issues with IPv6. Highly recommended : try solutions 1, 2, 4 ,6 and 7 first. **

I had this problem, I've found out that many others have it. I've managed to solve it, so here's how I did it.

_Solution 1:_ Try to add your ISP's DNS to the list. Google your ISP's name, search for something like "<ISP name> DNS server". Then, left click the network icon, choose Manual Configuration. Then, click Unlock and enter your password. Move to the DNS tab, and add your ISP's DNS server's IP. I added both the primary and secondary IPs. That was the last thing I tried.**That worked for me.**

[IMG]http://i38.tinypic.com/2rop751.png[/IMG]

_Solution 2:_ Try to disable IPv6. Follow the guide [here]("http://ubuntuforums.org/showthread.php?t=6841").

_Solution 3:_ Try to disable or uninstall all your Firefox addons, one by one. After each uninstallation, check your connection. If the problem was solved, simply don't install the defective addons again, try to find alternatives.

_Solution 4:_ Reconnect your router/modem, all the RJ45 cabels and the RJ11 microfilter (if you have one).

_Solution 5:_ Open the terminal, and execute :

[B]firefox -ProfileManager
[/B]
Create a new profile, and delete your old one. All your personal data (history, etc') will be lost.

_Solution 6:_ Make sure that your router (if you have one) has no red lights when Ubuntu boots.

_Solution 7:_ Change your DNS server. Follow the guide [here]("http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html").


**After the problem is gone...** I recommend you to install the FlashBlock and AdBlock extensions, they speed up browsing drastically. Moreover, if the problem is gone, and you want to speed your browsing speed, you can disable IPv6 and change DNS servers. 

I hope this helped you.

---

