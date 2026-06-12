---
title: "No internet. Wired &amp; Wifi. Does connect to local net. Worked fine before. Intel NICs"
date: 2018-03-31
forum: Networking &amp; Wireless
---

### Post by greyfaux01 on 2018-03-31
Ubuntu 14.04 with LXDE on top. Dell latitude, 82577LM Gigabit, Centrino Ultimate-N 6300.

Its my main laptop for school, I've done all the troubleshooting that i  know of. It connects to the wireless network with good signal, also  connects  to the wired network no problem, but i cannot ping an outside  address  or go to any websites, tried multiple browsers. It was working  fine  previously, made no changes (unless something changed that i  wasn't  aware of). The only thing i can think of, a couple weeks prior i  connected to  the wifi network at the library. I can't remember if i  was able to get online at home since that time though, i didn't use the  laptop for a few weeks after getting on at the library. Comfortable with  ubuntu but noobish still.

-Im able to ping my default gateway, this is on wired and wireless connection, but ping to 8.8.8.8 and [www.google.com]("http://www.google.com") both fail.

-When using the network app 'Fing' for phone, it sees the laptop   connected to my home network. I can actually ping from my mobile phone   to the laptop and it succeeds with 0% packet loss.

-Tried rebooting laptop, router, left router and laptop off for a few   hours. Also tried deleting the wireless connection in Network Manager   and re-adding it.

-Could be irrelevant, but i am able to access my routers web interface   from the laptop. When using the routers built in Diag tool, everything   lists as 'pass'. I can also successfully ping the DNS via the routers   web interface, (although i think im going from router to the outside  internet at this point, so again probably not relevant).

-All other devices on same network work fine.

-I read the sticky thread before posting, i put the tool on a usb drive,  ran it on the laptop, and will include  the output in my next post.  Just guessing, my routing table is  corrupted..?.. purely a guess from  people with similar, but  different problems. I also have the outputs of  ifconfig/netstat on the  thumbdrive as well. Again no internet access  so to run any commands i'll  have to copy/paste them to thumbdrive or  type  them by hand. Im totally appreciative of either method.

Thanks for any help, i hope ive done everything i can to help myself   first, im hesitant to make any changes to the routing table because i   dont really know what im doing, i dont want to make it worse. I have a   busy schedule but will definitely be coming back asap. Thanks again.

---

### Post by greyfaux01 on 2018-03-31
Output from the networking tool provided in the sticky thread:

[https://paste.ubuntu.com/p/yRvXDQYq4S/](https://paste.ubuntu.com/p/yRvXDQYq4S/)

---

### Post by greyfaux01 on 2018-04-02
Love you ubuntu forums;)..

---

### Post by praseodym on 2018-04-02
Your firewall is blocking:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```
Reboot

---

### Post by greyfaux01 on 2018-04-03
Thanks so much for looking at it for me. Just checking in to let you your help is appreciated. If I get time today I'll put in those commands. I'm also gonna look at my pastebin and make sure I can see/understand (at least a little) why the firewall is blocking.

Will be posting back when competed.

---

### Post by praseodym on 2018-04-04
> ```
[ 3616.291169] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:9c:ef:d5:fe:b7:b9:86:dd SRC=2602:0306:b888:ce40:a0c7:8238:c46e:82cb DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=234870 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 3616.292326] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:9c:ef:d5:fe:b7:b9:86:dd SRC=2602:0306:b888:ce40:a0c7:8238:c46e:82cb DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=294169 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 3616.293424] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:9c:ef:d5:fe:b7:b9:86:dd SRC=2602:0306:b888:ce40:9eef:d5ff:fefe:b7b9 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=520747 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 3616.294661] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:9c:ef:d5:fe:b7:b9:86:dd SRC=2602:0306:b888:ce40:9eef:d5ff:fefe:b7b9 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=875017 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 3616.295790] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:9c:ef:d5:fe:b7:b9:86:dd SRC=fe80:0000:0000:0000:9eef:d5ff:fefe:b7b9 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=464800 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 3616.296921] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:9c:ef:d5:fe:b7:b9:86:dd SRC=fe80:0000:0000:0000:9eef:d5ff:fefe:b7b9 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=15069 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 3616.300041] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:9c:ef:d5:fe:b7:b9:86:dd SRC=2602:0306:b888:ce40:a0c7:8238:c46e:82cb DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=234870 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 3616.301218] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:9c:ef:d5:fe:b7:b9:86:dd SRC=2602:0306:b888:ce40:a0c7:8238:c46e:82cb DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=294169 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 3616.302380] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:9c:ef:d5:fe:b7:b9:86:dd SRC=2602:0306:b888:ce40:9eef:d5ff:fefe:b7b9 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=520747 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 3616.303491] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:9c:ef:d5:fe:b7:b9:86:dd SRC=2602:0306:b888:ce40:9eef:d5ff:fefe:b7b9 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=875017 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
```
UFW=Ubuntu Firewall

---

### Post by greyfaux01 on 2018-04-04
Cool. Awesome. Thanks man, internet is NOW WORKING!! =d>, updating computer as we speak.

Yea i definately noticed the UFW at the bottom there, i did indeed install the GUFW a long time ago. It was working perfectly fine for years. I was adding individual rules (using the gui of course) to allow things like my Kodi remote app, and it was indeed allowing the individual items i wanted it to. Its weird it started blocking ALL outbound connections, for what appears to be no reason at all.

Either way its working now. I guess i'll just leave the firewall off since im not knowledgeable enough to prevent it from messing up again or to fix it myself  (from what i understand linux only opens ports as needed anyway).

I am curious though as to what the iptable commands you had me type in do. From what i understand iptables can block/allow things, i guess kind of like a firewall maybe. Were you having me reset my iptables settings or something to fix the problem..?.. im also curious as to why my UFW started blocking all outbound connections randomly.. Im curious about all of it really.. I would like to know how to actually use a firewall while being able to not mess up my internet in the future, not because i need one, just for the experience..

Either way im sure your busy so thanks so much for your help. I've read about UFW and iptables in the past, in fact i learned about iptables when i was trying to install peerblock for linux, that said, with no gui, it seems a lot to learn. I read a lot, but was having trouble understanding it and putting it into context. Its not like i dont try to learn, its just it all seems immediately over my head from jump street. One day i'll read one of the linux+ certification books, then maybe i can have a more basic understanding of a variety of topics..

Thanks again for your help.

---

