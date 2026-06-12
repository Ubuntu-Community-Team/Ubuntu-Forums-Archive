---
title: "Lost my internet connection"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by slvfx on 2009-09-28
I lost my connection to the internet. I ran sudo pppoeconf. It showed my eth0 but could not connect.
 
I was having a problem setting up my printer and may have changed something that I shouln't have.
 
The router shows the connection as active. I have a laptop pc running vista which is what I am writing from here.
 
My printer is now working

---

### Post by Darkwing-Duck on 2009-09-28
What is the output of ifconfig? This will help us in further tracking down your problems.
 
Hope we can further assist you.

---

### Post by slvfx on 2009-09-28
[FONT=Batang][SIZE=3]config[/SIZE][/FONT]
[SIZE=3][FONT=Batang]eth0      Link encap:Ethernet  HWaddr 00:24:8c:55:c8:a3  [/FONT][/SIZE]
[SIZE=3][FONT=Batang]          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          inet6 addr: fe80::224:8cff:fe55:c8a3/64 Scope:Link[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          RX packets:6495 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          TX packets:570 errors:0 dropped:0 overruns:0 carrier:1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          collisions:0 txqueuelen:1000[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          RX bytes:1330697 (1.3 MB)  TX bytes:112543 (112.5 KB)[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          Memory:dffc0000-e0000000[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[SIZE=3][FONT=Batang]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          RX packets:37 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          RX bytes:23179 (23.1 KB)  TX bytes:23179 (23.1 KB)[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]pan0      Link encap:Ethernet  HWaddr 92:06:47:ec:18:0a  [/FONT][/SIZE]
[SIZE=3][FONT=Batang]          inet6 addr: fe80::9006:47ff:feec:180a/64 Scope:Link[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

---

### Post by Darkwing-Duck on 2009-09-28
Okay, connect wireless, disconnect then reconnect.
 
Once you are done with that pastebin ([http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/)) the output of /var/log/messages and post the link in here.

---

### Post by slvfx on 2009-09-29
I am having trouble getting the output on the /var/log/messages. It was suggested I install yagiuda which wouldn't install because it needed to check fixes but with no fixes available because of not being hooked to the internet I wasn't able to install. I went to the internet with my other machine and downloaded it but it was an older copy and wouldn't install.
 
It was then suggested I install mailutils but it couldn't fetch some archives. Is there something in my desktop program that would give you the information your looking for to help me.
 
thanks
\
 
ps how about my sys log?

---

