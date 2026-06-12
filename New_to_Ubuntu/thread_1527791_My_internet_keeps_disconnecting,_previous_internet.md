---
title: "My internet keeps disconnecting, previous internet didnt"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by nevertomorrow on 2010-07-09
hi im new to ubuntu. im using the latest version, and i just recently switched from windows xp. which worked perfectly fine. it was pretty fast and didnt disconnect at all, but now that ive switched to ubuntu sometimes it randomly all of a sudden stops working for like 10 seconds. its not that bad when just surfing the internet or on facebook, but like if im playing a game i cant play it because it just disconnects it because it always has to be connected to the internet. im pretty sure its something with ubuntu because my internet worked perfectly fine before. Any help would be greatly appreciated :) :D

---

### Post by jtarin on 2010-07-09
Tell us more about how you are connected.DSL,modem,router,ethernet card etc;
Also post the results of this command entered in a terminal
```
ifconfig -a
```

---

### Post by nevertomorrow on 2010-07-09
i connect with a wireless network
uhmm when i type that in i get this:

eth0      Link encap:Ethernet  HWaddr 00:19:21:ec:ae:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55463 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1625091 (1.6 MB)  TX bytes:1625091 (1.6 MB)

wlan0     Link encap:Ethernet  HWaddr d8:5d:4c:af:98:a3  
          inet addr:192.168.2.172  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::da5d:4cff:feaf:98a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21312532 (21.3 MB)  TX bytes:6437884 (6.4 MB)

---

### Post by jtarin on 2010-07-10
```
wlan0
```is your wireless connection and this shows it up and no errors at this point. The only thing I can suggest at this point is the next time this happens and before it comes back up is the command ```
dmesg | grep -i wlan0
```to see if anything is shown that is affecting it.

---

### Post by nevertomorrow on 2010-07-11
well i typed that in when the internet stoppped working
and i got this:

ben@bennnyboy:~$ dmesg | grep -i wlan0
[   10.822358] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.829814] wlan0: deauthenticating from 00:13:f7:a4:53:8c by local choice (reason=3)
[   28.831911] wlan0: direct probe to AP 00:13:f7:a4:53:8c (try 1)
[   28.836196] wlan0: direct probe responded
[   28.836202] wlan0: authenticate with AP 00:13:f7:a4:53:8c (try 1)
[   28.837947] wlan0: authenticated
[   28.837972] wlan0: associate with AP 00:13:f7:a4:53:8c (try 1)
[   28.841315] wlan0: RX AssocResp from 00:13:f7:a4:53:8c (capab=0x431 status=0 aid=5)
[   28.841319] wlan0: associated
[   28.847367] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.636010] wlan0: no IPv6 routers present

---

### Post by jtarin on 2010-07-11
It sounds as if dhclient isn't releasing when your isp issues you a new
lease; next time it goes down try this:

Open the terminal and run the following command to release

   ```
 sudo dhclient -r
```

Open the terminal and run the following command to renew

   ```
 sudo dhclient
```

or

   ```
 sudo dhclient wlan0
```

---

### Post by nevertomorrow on 2010-07-11
will that permantely fix the problem or would i hafto type that in whenever the internet goes down? :popcorn:

---

### Post by jtarin on 2010-07-11
> **nevertomorrow said:**
> will that permantely fix the problem or would i hafto type that in whenever the internet goes down? :popcorn:
Let me know if that fixes the problem or not. It seems that there are some issues with your ISP and renewing addresses. See [here]("http://manpages.ubuntu.com/manpages/lucid/en/man8/dhclient.8.html") for further info and let me know of your progress.

---

### Post by nevertomorrow on 2010-07-13
it worked for about the next five minutes after i did it, but then it constantly keeps disconnecting. and im sorry, i just installed ubuntu a couple days ago i cant really do anything by myself :(

---

### Post by jtarin on 2010-07-14
Ok the next time it disconnects enter the command ```
ifconfig -a
```then post the results and also post a copy of your /etc/dhclient.conf file.

---

