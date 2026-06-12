---
title: "Basic wireless security?"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by whitefort on 2007-03-21
Apologies if I should be posting this in 'beginners'.  I''m a complete newbie to wireless.

When I switched to Ubuntu, I had to get a new modem/router, since I couldn't get my old USB one to work.  So I decided to take the opportunity to switch to wireless. That was about 2 months ago.

I ***_thought_*** that all I had to do for basic security was to give my wireless network a name, then put that name (manually) in any computers that would be using the network.

Oops.  Yesterday I got my first laptop.  When I turned it on, it instantly found the name of my network, and connected with no problems.  This was a major wakeup call for me.  Presumably ***anybody*** could be sitting in a car outside the house and using my bandwidth (or worse?).

I'm totally new to this, and reading about WEP and MAC and wotnot makes my head spin.  I'd be REALLY grateful if anyone could point me to a 'wireless security for total nitwits' FAQ.  I want to keep my network safe, but I'm afraid of doing something that wrecks it all together.

Any help would be greatly appreciated.

Thanks!

---

### Post by horace on 2007-03-21
You should certainly make sure you enable WPA in your router - WEP is better than nothing, but is easily cracked by all accounts. For WPA guide on Ubuntu, try looking at [https://help.ubuntu.com/community/WifiDocs/WPAHowTo]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo")
hth

---

### Post by Fitzcarraldo on 2007-03-21
*whitefort*,

I recently configured Dapper to work with WPA-PSK ("WPA-Personal"), and the description of what I did at the PC end is in the following thread:

[http://ubuntuforums.org/showthread.php?t=378179](http://ubuntuforums.org/showthread.php?t=378179)

Regarding the hub or router end, I accessed my wireless hub using a Web browser -- which is usually the way to configure a router or hub, but see your router/hub's user guide -- to specify that the hub should operate under WPA-PSK (with TKIP encryption) and to define the SSID (network name) and Shared Secret (passphrase).

WEP-64 is apparently very easy to crack and WEP-128 a bit more difficult but still not that difficult to crack, so these days WPA-PSK is recommended over WEP. I found the following article, although oriented to Windows XP, a good introduction to WPA-PSK:

[http://www.microsoft.com/windowsxp/using/networking/expert/bowman_03july28.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/bowman_03july28.mspx)

EDIT: By the way, I would recommend that, when you configure your router/hub for WPA-PSK, you also turn off broadcasting of the SSID (network name). Then people will not be able to see your network in the list of Wireless Networks if the they click on the NetworkManager icon (in ubuntu) or click on Refresh Network List (in Windows XP). Expert crackers will still be able to find your network even if it is not broadcasting its SSID, but it will not be visible to others. To connect to your network from a PC in range, you then need to enter the SSID and Shared Secret (passphrase), which you do in ubuntu by clicking on Connect to Other Wireless Network... in the NetworkManager menu.

---

### Post by whitefort on 2007-03-22
Thanks for the replies, guys - this has been very helpful!

---

