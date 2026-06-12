---
title: "Server not found"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by TedinOz on 2010-12-29
Complete newby here and have much to learn about Ubuntu. I am running dual  set up of version 10.10 on Toshiba L300 laptop on which I have Vista also. I successfully installed and connected to the internet with wireless modem but my first problem is that I am unable to access the internet. I can open Firefox but any attempt to use that results in a Server not Found error page telling me to check firewall and/or proxy settings. I found my way into preferences through edit and have made various attempts to configure proxy settings using those that were running in windows but with no result. I have to admit now that I am completely lost as to what to do now. Can anyone help please?...I know I am going to love Ubuntu and feel I can understand most of it but need to get it working first.

---

### Post by SuaSwe on 2010-12-30
Hi there TedinOz! 

To start, could you copy and post the output of the following:

```

ifconfig

```

?

---

### Post by TedinOz on 2010-12-30
Thanks for looking at this...
I think this is the cut and paste info you wanted to see:

" TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:204944 (204.9 KB)  TX bytes:204944 (204.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:a5:9b:64  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:fea5:9b64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6226 (6.2 KB)"

It doesn't mean a lot to me but I hope you can make something of it and can help me on my way. Everything I do to try to connect to the internet including activating some chat services or Firefox(which is the only web browser I seem to have access to), all tell me I have no connection but the wireless network connection icon tells me I have 100% connection. I'm sure its something stupid I have done so any assistance will be greatly appreciated :)

---

### Post by TedinOz on 2010-12-30
A followup post to report a break through of sorts re this problem. As an after thought I connected the ethernet cable from my wireless modem, got instant connection and internet access, so it seems the earlier problem was with the Wireless connection which although indicating full power, was not connecting to the server. I have spotted numerous other posts here from people with wireless connectivity problems and will research on but if you or anyone else has a quick answer for this as a result of above descriptions I will certainly be pleased to hear from you.

Now that I have the system working I can see that I will love it!...and when completely setup will be able to say goodbye to Windows (and especially Vista) for ever :)

---

### Post by QLee on 2010-12-31
[QUOTE=TedinOz]...I connected the ethernet cable from my wireless modem, got instant connection and internet access, so it seems the earlier problem was with the Wireless connection which although indicating full power, was not connecting to the server. ...[/QUOTE]

What I would try in that situation would be to disconnect the ethernet cable and right click the Network Manager icon to Edit Connections, then go to the Wireless tab and delete the connection, then add a new wireless connection and see if it works. Not guaranteed but easy and quick to try.

---

### Post by TedinOz on 2010-12-31
> **QLee said:**
> What I would try in that situation would be to disconnect the ethernet cable and right click the Network Manager icon to Edit Connections, then go to the Wireless tab and delete the connection, then add a new wireless connection and see if it works. Not guaranteed but easy and quick to try.

It is in my nature to to look for the hardest solution to the easiest problem. You were so right and after a few clicks my problem is solved! Thank you so much! This is a wonderful forum that matches the spirit of Ubuntu and I am very happy to have proceeded with it! 

Thanks again!

---

### Post by QLee on 2010-12-31
When you are new at things it is easy to fall into traps.

Most of us are here to help, and you are welcome, both to the forum and to the help.

---

### Post by zoftware on 2011-05-11
Hello QLee,

Same problem "Server not found" on a friend's HP zd8000. This a new Ubuntu 11.04 only install. No wireless or wired connections.

I tried restarts, shutdowns, deleting, adding, and combinations thereof. The previous Windows XP was connecting just fine. The Macbook Pro and Dell desktop are on the same router and are having no problems.

I have not found an answer in the Ubuntu forums. A Google search is swamped with 63,700 results. I have already opened 100+ useless links.

My friend is very disappointed. Any suggestions would be appreciated.

---

