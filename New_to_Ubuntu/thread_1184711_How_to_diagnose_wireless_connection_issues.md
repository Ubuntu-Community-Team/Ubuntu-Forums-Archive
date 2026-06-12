---
title: "How to diagnose wireless connection issues"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by mrdzone on 2009-06-11
So here's my situation. I'm new to linux and using ubuntu jaunty. 

Have 2 main networks I connect to. One at home and one at school. Both are unsecured and are completely automated (dhcp etc...) 

Everything was working good until yesterday. 

When I try to connect at school it simply doesn't connect, i'm using the applet in the system tray and everything looks good on the automated connection (ssid (auto) and everything in there looks good) however it just keeps trying to connect and never does.

If i'm in the same (phsyical) location and boot into windows I can connect no problem and likewise connecting at home is not an issue. 


How would I go about bein able to see where the issue is? 

One thing I've tried that may help the diagnosis is a 
sudo ifconfig wlan0 down 
followed by a
sudo ifconfig wlan0 up 

to try to shake the card into action, however when I try to brin itup (it goes down ok) i get (and i'm sorry I dont remember the exact error, i'm on the school network now from windows) something akin to "resource temporarily unavailable"

Any ideas are greatly appreciated.

thanks

-zone

---

### Post by Dougie187 on 2009-06-11
you could check your syslog or dmesg logs to see if they have any useful information after it doesn't connect.

---

### Post by rafac24 on 2009-06-12
I am having the exact same issues. I upgraded my computer, along with my sister's, to Jaunty. Ever since then, both our computers RARELY connect to the home network. My dad, running Intrepid, has no issues connecting to the home network. And likewise, when I open Vista, subsequent to the Ubuntu network breakdown, the internet loads just fine on Vista. 

I will try the commands.
Any more help will be appreciated.

Thanks

---

### Post by rafac24 on 2009-06-12
For others that may be having a similar problem, I found a solution that worked for me:
[http://ubuntuforums.org/showpost.php?p=7276275&postcount=8](http://ubuntuforums.org/showpost.php?p=7276275&postcount=8)

I do not know the reason why this works, but I am now connected to the internet on Jaunty after a few days of no connectivity. This seems to be a temporary fix...I hope they find a permanent fix soon.

Hope it helps others out there!

---

