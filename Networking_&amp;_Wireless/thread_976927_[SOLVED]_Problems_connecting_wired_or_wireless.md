---
title: "[SOLVED] Problems connecting wired or wireless"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by Nachoo on 2008-11-09
Hi, I have gone through lot of reading. I installed ndiswrapper, I tried what was told on the forums, but my wireless and also wired connections can not connect to the internet.

I can see the wireless networks around me and I can ping a server but it just won't surf or check email.

Any help would be very very very welcome!

I'm new in Ubuntu.

---

### Post by DrDagostino1 on 2008-11-09
Which version of Ubuntu are you using?
If you don't know, just got to the System Monitor by going to System>Administration>System Monitor then click on the System tab.
Most of the Ubuntu versions have a network applet installed by default, but you may have to add it to the top panel.
To do this, right click on the top panel and click "Add to panel". Once there, scroll down and look for network monitor and add it. It should tell you everything you will need to know. Wireless networks, connection info, etc.

---

### Post by Nachoo on 2008-11-09
I'm using 8.10.

Yeah, the network icon is up there, running and looking good. It says I'm connected wirelessly to my router, and so does when I connect wired. I can ping websites, but can't get websites or email. 

I have installed ndiswrapper and new drivers, and uninstall others, it didn't work before and still doesn't now but regarding all the drivers stuff I don't really know where am I at.

Thanks for taking your time to help!

---

### Post by DrDagostino1 on 2008-11-09
Could you post your Connection info. To do this, right click on the network icon and click Connection Information.

---

### Post by Nachoo on 2008-11-09
Interface: 802.11 wifi (eth1)
HW address: 00:22:68:D3:11:2c
Driwer: wl
Speed: 2Mb/s
Security: none

And then it says the ip addresses which they all look fine.

---

### Post by DrDagostino1 on 2008-11-09
Can you get to your router control panel?

---

### Post by Nachoo on 2008-11-09
Nope!

---

### Post by DrDagostino1 on 2008-11-09
Ok, It sounds like you are not actually connected. One of my friends had the same problem which he fixed by just going wired.

---

### Post by Nachoo on 2008-11-09
I can't go wired either.

---

### Post by DrDagostino1 on 2008-11-09
What exactly did you get when you tried wired? Didit connect or did it just stay unactive?

---

### Post by Nachoo on 2008-11-10
It did connect just as it does when wired.

---

### Post by utnubuuser on 2008-11-10
The router we've been using will sometimes not pass traffic (it connects, but no access to internet).  Then  I turn of the router, push the reset buton, wait 15-20 seconds for it to re-populate and the connection is ok again.

did you get a promt for wireless key/password?

Try re-setting the router. (no reset? turn it off and then on again)

---

### Post by Nachoo on 2008-11-10
Already gone through that. I thought it would be a drivers thing.... I have no idea...

---

### Post by DrDagostino1 on 2008-11-10
Do you happen to have another computer you can access your router control panel from?

---

### Post by Nachoo on 2008-11-10
It does connect.

---

### Post by DrDagostino1 on 2008-11-10
Your other computer? Can you get internet at all with the router in any way? What is your ISP?

---

### Post by Nachoo on 2008-11-10
I am running the liveCD and I will probably reinstall the whole thing but first I want to see if I can get it running from the CD. Apparently it all works flawlessly, it is stable and says I am connected. I can ping sites. If I run wget [www.google.com](www.google.com) it says connecting, then connected and then it says waiting when it has sent the HTTP query.

---

### Post by DrDagostino1 on 2008-11-10
Try:
```

wget -P / www.google.com

```
and check your home directory for index.html - To do this go to Places>Home Folder, if the file is there, you should be connected.

---

### Post by Nachoo on 2008-11-11
If I run wget -P / [www.google.com](www.google.com) I get nothing or it is too slow and didn't wait long enough. I have tried it against different sites and the same happenned to all of them BUT [www.amazon.com](www.amazon.com) so I guess (as already showed the ping command) that I am connected but just can't get http to work.

My ISP is Telefonica in Spain. 

I can access internet and my router through a different computer running winXp or using this very same computer which also runs Vista.

---

### Post by sanemanmad on 2008-11-11
Ok so from what I gather you are able to 'connect' and get an 'ip_address' and then ping a local server? can you perform an nslookup or dig any websites? 

what do each of these commands reveal?

ifconfig -a
iwconfig

on your wincrap machine

ipconfig /all


Thanks

---

### Post by Nachoo on 2008-11-11
Alright got it guys!!

Thanks for helping. It seems the Ubuntu doesn't like the firewall of the router. There wasn't any problem with windows but ubuntu would not get the http through, I disabled it and it is working amanzingly great!

Thanks lots for your help!!

---

### Post by metallicamike on 2008-11-16
u should marked this solved then :p

---

### Post by metallicamike on 2008-11-16
and ur welcome (not that i helped lol)

---

