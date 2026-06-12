---
title: "Internet works on XP but not Ubuntu"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by president rich on 2008-06-08
My Ubuntu worked great with the internet for days after I installed it. Now it won't connect to the internet. This happened before, but I restarted my computer and it was fine. Now I can't get connection no matter what. XP connects to the internet with no problem. I haven't changed any settings or anything like that. What should I do?

---

### Post by rlzyoner on 2008-06-08
What type of connection are you trying to connect to, wireless or wired ?

---

### Post by Drumm3r4lyfe on 2008-06-08
I'm having the exact same problem...

<Drumm3r>

---

### Post by rlzyoner on 2008-06-08
But what type of connection are you trying to connect to ? 

If wireless, run the command
ifconfig wlan0 up (change wlan0 to the name of your wireless adaptor if necessary), this command enables your wireless adaptor
Now run the following command,
iwlist scanning
This will scan for wireless networks in range.
Alternatively, you could run nm-applet and use the gui provided by network manager

---

### Post by president rich on 2008-06-08
This computer is wired. It has a wireless router connected to it for another computer.

---

### Post by rlzyoner on 2008-06-09
Sorry for the delay in replying, work and college and what not.

Ok you could try System -> Administration -> Networking

Now select your ethernet adaptor (probably eth0 or something similar) and select properties.
If you wish to manually assign an Ip address etcm click Static IP address and fill in the fields as required.
Alternatively you can select DHCP and your router will take care of that.

Click ok

Now you can select the DNS tab and enter in the DNS server addresses of your ISP.
For some reason I have found that some wired connection will only work once you manually enter in the DNS addresses.

Tick the small box to the left of wired connection and this should enure the connection is activated.

Please advise if this works.

---

### Post by Mgiacchetti on 2008-06-09
I actually noticed this same problem, however with a few other sidenotes.  my windows box (same machine different boot) lost internet as well.. so i set static ip, nothing, had to insert dns (very important) that was the only way i could get online both in ubuntu and winshits (by the way, im on a wired wireless connection... lol wired to my client bridge if that makes any difference...)

if you are having problems finding dns, it should be on your router, (192.168.1.1 in the status page)

---

### Post by president rich on 2008-06-09
OK, OP here again...
I tried Ubuntu again (before trying posted solutions above) and it WORKS. What can I do to assure it won't go down again?

---

### Post by president rich on 2008-06-16
None of the solutions above seem to work, unless I'm doing something wrong.

---

