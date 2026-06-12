---
title: "No network detected"
date: 2015-04-07
forum: Networking &amp; Wireless
---

### Post by mike311 on 2015-04-07
Hi all, I have an issue with a program called Hidownload. It loads in fine but for some reason there are no options listed in the network adapter list box. It's a similar problem that I had in windows, when I told Wincap not to automatically load on start up. This was fixed easily by making it open on startup then I  had options in the box. I had simiiar problems with Wireshark, but a few commands later and this was fixed. Please could anyone advise me on this topic?

As I'm new to Linux,  please treat me as a complete novice .

Regards

---

### Post by mike311 on 2015-04-08
No good guys? Please help getting desperate here .Thanks

---

### Post by Bashing-om on 2015-04-08
mike311; Hello;

We are in the dark as to what you have done; per:
```

sysop@1404mini:~$ apt-cache search Hidownload
sysop@1404mini:~$

```
that application does not exist in the ubuntu software repository for 14.04.
What is this application, and what is it's purpose ?

So, how did you get it ? What steps did you undertake to install ? What steps have you undertaken to configure it ?

difficulties are increased
[INDENT][INDENT][INDENT]once you depart from the system's package management
[/INDENT][/INDENT][/INDENT]

---

### Post by mike311 on 2015-04-08
Thanks for your reply .Hidownload is a rtmp sniffing software.I used wine to load the program .When i click on the icon it shows no network adapters,i have read a few posts and it seems i have a problem with Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01) 
i get this in terminal
IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready. I have not configured any settings,as it normally works automatically
  
I downloaded Hidownload from their website, it has a free trial if you have the time and patience to test it 
Hope this helps Bashing-om

---

### Post by Bashing-om on 2015-04-08
mike311; yeah ..

Helps, But I do not know Wine and have little experience with WIFI.
I will have to defer this to others to assist,

[INDENT][INDENT]some things I just
[INDENT][INDENT][INDENT][INDENT]do not want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mike311 on 2015-04-09
Thanks very much, just thought I`d mention the wireless lan  is being used talking on here right now ,so its working but not registering up with hidownload Bashing-om

---

