---
title: "Firefox can't find the server."
date: 2011-06-08
forum: New to Ubuntu
---

### Post by OldBoy44 on 2011-06-08
Hi all,

I really don't know what I am doing here - I have just purchased a new computer and I am having intermittent network connection problems. I am using the same ethernet modem that I was using on my old computer. I keep getting error messages such as the one above. After a search i came across the following sudo ifconfig command which produced the following output.
Does this help in giving some insight into what is wrong and perhaps how I can rectify the problem or is there more information needed?

Hoping that some kind person can help me!

eth0      Link encap:Ethernet  HWaddr 1c:6f:65:d6:d1:a4  
          inet addr:10.1.1.2  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fed6:d1a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2872 errors:0 dropped:2872 overruns:0 frame:2872
          TX packets:3438 errors:0 dropped:90 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2518947 (2.5 MB)  TX bytes:487689 (487.6 KB)
          Interrupt:41 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30385 (30.3 KB)  TX bytes:30385 (30.3 KB)

Thank you,

---

### Post by seawolf167 on 2011-06-08
That command used how you did shows your network status'. It looks like you are using a physical ethernet connection and maybe a Comcast modem?

Do the page(s) only fail to load a specific times, for specific websites or do they appear to be random? Do other browsers fail to load as well? (like Google Chromium?)

The first thing your ISP tech would tell you to do is unplug the power cable from the back of the modem, wait 30 seconds then plug it back in to "re-train" the modem. See if this helps at all, else we can see what else we can try.

---

### Post by OldBoy44 on 2011-06-08
Many thanks seawolf167, events appeared to be random - I followed your instruction and things appeared to improve - Couldn't find server twice in about 15 attempts. I haven't yet tried another browser as yet.
I do have a physical ethernet connection with a Sagem modem.

I will see how things go for a while - many thanks.

Cheers, :)

---

### Post by seawolf167 on 2011-06-08
Looks like it may be an intermittent signal from your router/ISP? Twice in 15 attempts is definitely annoying, but without a reproducible method to make it appear I wouldn't know what else to do other than to say to try another browser, if the other browse also gets timeouts, then call your ISP and ask if they can try to diagnose your issue from their end.

EDIT: Just thought you could also try to clear the Firefox cache by deleting the items in the Cache folder or through the Clear Recent History in the Tools menu bar (select to clear Everything under the Time Range) from within Firefox

the path to the folder is:
/home/your_user_name/.mozilla/firefox/xxxxxx.default/Cache

where the xxx's are random hex characters.

---

### Post by OldBoy44 on 2011-06-08
Hi again all,

I found another cause of concern - the result of the ping test as outlined in "Check the DNS" in the following -
[https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html)
showed 0% successful packets which I gather is a very poor result.

Any further input would be appreciated!

Thank you,

---

### Post by seawolf167 on 2011-06-08
> **aussiebean said:**
> Hi again all,

I found another cause of concern - the result of the ping test as outlined in "Check the DNS" in the following -
[https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html)
showed 0% successful packets which I gather is a very poor result.

Any further input would be appreciated!

Thank you,

I'm getting timed out requests for that IP. Try pinging Google's DNS server from a terminal instead

```
ping 8.8.8.8
```

---

### Post by OldBoy44 on 2011-06-08
You may not be around anymore seawolf167 - I tried pinging 8.8.8.8 but it just kept rolling - I didn't know what I should do to stop it. I apologize for the long delay, but I have been dropped off the system about 5 times.

I did get some more info from that site I mentioned before. I don't know if this would shed any light on the situation.

eth0      Link encap:Ethernet  HWaddr 1c:6f:65:d6:d1:a4  
          inet addr:10.1.1.2  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fed6:d1a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:556 errors:0 dropped:556 overruns:0 frame:556
          TX packets:624 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:546959 (546.9 KB)  TX bytes:120113 (120.1 KB)
          Interrupt:41 Base address:0xc000 

Thanks again seawolf167,

---

### Post by seawolf167 on 2011-06-08
> **aussiebean said:**
> I tried pinging 8.8.8.8 but it just kept rolling - I didn't know what I should do to stop it. I apologize for the long delay, but I have been dropped off the system about 5 times.You may not be around anymore seawolf167 - I tried pinging 8.8.8.8 but  it just kept rolling - I didn't know what I should do to stop it. I  apologize for the long delay, but I have been dropped off the system  about 5 times.

Hit [CTRL][C] to kill the running ping (though you've probably have closed the terminal by now killing the process in the process :P

Since you do have a connection, try a different browser for a day or two and see if you continue to have the issues. The one I suggest is google chrome

Open a terminal and type

```
sudo apt-get install chromium-browser
```the browser will then be put under Internet in the Applications menu, or you can hit [CTRL][ALT][F2] then type in the name and hit enter to run it

---

### Post by OldBoy44 on 2011-06-08
Yes thanks seawolf167 - I will try chromium although I still feel that there is something basically wrong with my setup. I did notice when pinging 8.8.8.8 that part of the output read "Destination Host Unreachable"

Cheers, :p

---

### Post by OldBoy44 on 2011-06-08
Results of command ping 8.8.8.8

[HTML]
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=52 time=170 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=52 time=170 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=52 time=171 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=52 time=170 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=52 time=172 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=52 time=171 ms
64 bytes from 8.8.8.8: icmp_req=7 ttl=52 time=171 ms
64 bytes from 8.8.8.8: icmp_req=8 ttl=52 time=172 ms
64 bytes from 8.8.8.8: icmp_req=9 ttl=52 time=171 ms
64 bytes from 8.8.8.8: icmp_req=10 ttl=52 time=170 ms
64 bytes from 8.8.8.8: icmp_req=11 ttl=52 time=169 ms
64 bytes from 8.8.8.8: icmp_req=12 ttl=52 time=170 ms
64 bytes from 8.8.8.8: icmp_req=13 ttl=52 time=170 ms
64 bytes from 8.8.8.8: icmp_req=14 ttl=52 time=170 ms
64 bytes from 8.8.8.8: icmp_req=15 ttl=52 time=169 ms
From 10.1.1.2 icmp_seq=59 Destination Host Unreachable
From 10.1.1.2 icmp_seq=60 Destination Host Unreachable
From 10.1.1.2 icmp_seq=61 Destination Host Unreachable
From 10.1.1.2 icmp_seq=62 Destination Host Unreachable
From 10.1.1.2 icmp_seq=63 Destination Host Unreachable
From 10.1.1.2 icmp_seq=65 Destination Host Unreachable
From 10.1.1.2 icmp_seq=66 Destination Host Unreachable
From 10.1.1.2 icmp_seq=67 Destination Host Unreachable
From 10.1.1.2 icmp_seq=68 Destination Host Unreachable
From 10.1.1.2 icmp_seq=69 Destination Host Unreachable
From 10.1.1.2 icmp_seq=70 Destination Host Unreachable
From 10.1.1.2 icmp_seq=73 Destination Host Unreachable
From 10.1.1.2 icmp_seq=74 Destination Host Unreachable
From 10.1.1.2 icmp_seq=75 Destination Host Unreachable
From 10.1.1.2 icmp_seq=76 Destination Host Unreachable
From 10.1.1.2 icmp_seq=77 Destination Host Unreachable
From 10.1.1.2 icmp_seq=79 Destination Host Unreachable
From 10.1.1.2 icmp_seq=80 Destination Host Unreachable
From 10.1.1.2 icmp_seq=81 Destination Host Unreachable
From 10.1.1.2 icmp_seq=84 Destination Host Unreachable
From 10.1.1.2 icmp_seq=85 Destination Host Unreachable
From 10.1.1.2 icmp_seq=87 Destination Host Unreachable
From 10.1.1.2 icmp_seq=88 Destination Host Unreachable
From 10.1.1.2 icmp_seq=90 Destination Host Unreachable
From 10.1.1.2 icmp_seq=91 Destination Host Unreachable
From 10.1.1.2 icmp_seq=92 Destination Host Unreachable
From 10.1.1.2 icmp_seq=94 Destination Host Unreachable
From 10.1.1.2 icmp_seq=95 Destination Host Unreachable
From 10.1.1.2 icmp_seq=98 Destination Host Unreachable
From 10.1.1.2 icmp_seq=99 Destination Host Unreachable
From 10.1.1.2 icmp_seq=100 Destination Host Unreachable
From 10.1.1.2 icmp_seq=101 Destination Host Unreachable
From 10.1.1.2 icmp_seq=102 Destination Host Unreachable
From 10.1.1.2 icmp_seq=105 Destination Host Unreachable
From 10.1.1.2 icmp_seq=106 Destination Host Unreachable
From 10.1.1.2 icmp_seq=108 Destination Host Unreachable
From 10.1.1.2 icmp_seq=109 Destination Host Unreachable
From 10.1.1.2 icmp_seq=111 Destination Host Unreachable
From 10.1.1.2 icmp_seq=112 Destination Host Unreachable
From 10.1.1.2 icmp_seq=113 Destination Host Unreachable
From 10.1.1.2 icmp_seq=114 Destination Host Unreachable
From 10.1.1.2 icmp_seq=115 Destination Host Unreachable
From 10.1.1.2 icmp_seq=116 Destination Host Unreachable
From 10.1.1.2 icmp_seq=118 Destination Host Unreachable
From 10.1.1.2 icmp_seq=119 Destination Host Unreachable
From 10.1.1.2 icmp_seq=120 Destination Host Unreachable
From 10.1.1.2 icmp_seq=122 Destination Host Unreachable
From 10.1.1.2 icmp_seq=123 Destination Host Unreachable
From 10.1.1.2 icmp_seq=124 Destination Host Unreachable
From 10.1.1.2 icmp_seq=126 Destination Host Unreachable
From 10.1.1.2 icmp_seq=127 Destination Host Unreachable
From 10.1.1.2 icmp_seq=128 Destination Host Unreachable
From 10.1.1.2 icmp_seq=129 Destination Host Unreachable
From 10.1.1.2 icmp_seq=130 Destination Host Unreachable
From 10.1.1.2 icmp_seq=131 Destination Host Unreachable
From 10.1.1.2 icmp_seq=133 Destination Host Unreachable
From 10.1.1.2 icmp_seq=134 Destination Host Unreachable
From 10.1.1.2 icmp_seq=135 Destination Host Unreachable
From 10.1.1.2 icmp_seq=136 Destination Host Unreachable
From 10.1.1.2 icmp_seq=137 Destination Host Unreachable
From 10.1.1.2 icmp_seq=138 Destination Host Unreachable
From 10.1.1.2 icmp_seq=140 Destination Host Unreachable
From 10.1.1.2 icmp_seq=141 Destination Host Unreachable
From 10.1.1.2 icmp_seq=142 Destination Host Unreachable
From 10.1.1.2 icmp_seq=144 Destination Host Unreachable
From 10.1.1.2 icmp_seq=145 Destination Host Unreachable
From 10.1.1.2 icmp_seq=146 Destination Host Unreachable
From 10.1.1.2 icmp_seq=147 Destination Host Unreachable
From 10.1.1.2 icmp_seq=148 Destination Host Unreachable
From 10.1.1.2 icmp_seq=149 Destination Host Unreachable
From 10.1.1.2 icmp_seq=151 Destination Host Unreachable
From 10.1.1.2 icmp_seq=152 Destination Host Unreachable
From 10.1.1.2 icmp_seq=153 Destination Host Unreachable
From 10.1.1.2 icmp_seq=154 Destination Host Unreachable
From 10.1.1.2 icmp_seq=155 Destination Host Unreachable
From 10.1.1.2 icmp_seq=156 Destination Host Unreachable
From 10.1.1.2 icmp_seq=158 Destination Host Unreachable
From 10.1.1.2 icmp_seq=159 Destination Host Unreachable
From 10.1.1.2 icmp_seq=160 Destination Host Unreachable
From 10.1.1.2 icmp_seq=161 Destination Host Unreachable
From 10.1.1.2 icmp_seq=162 Destination Host Unreachable
From 10.1.1.2 icmp_seq=163 Destination Host Unreachable
From 10.1.1.2 icmp_seq=165 Destination Host Unreachable
From 10.1.1.2 icmp_seq=166 Destination Host Unreachable
From 10.1.1.2 icmp_seq=167 Destination Host Unreachable
From 10.1.1.2 icmp_seq=168 Destination Host Unreachable
From 10.1.1.2 icmp_seq=169 Destination Host Unreachable
From 10.1.1.2 icmp_seq=170 Destination Host Unreachable
From 10.1.1.2 icmp_seq=172 Destination Host Unreachable
From 10.1.1.2 icmp_seq=173 Destination Host Unreachable
From 10.1.1.2 icmp_seq=174 Destination Host Unreachable
From 10.1.1.2 icmp_seq=175 Destination Host Unreachable
From 10.1.1.2 icmp_seq=176 Destination Host Unreachable
From 10.1.1.2 icmp_seq=177 Destination Host Unreachable
From 10.1.1.2 icmp_seq=179 Destination Host Unreachable
From 10.1.1.2 icmp_seq=180 Destination Host Unreachable
From 10.1.1.2 icmp_seq=181 Destination Host Unreachable
From 10.1.1.2 icmp_seq=182 Destination Host Unreachable
From 10.1.1.2 icmp_seq=183 Destination Host Unreachable
From 10.1.1.2 icmp_seq=184 Destination Host Unreachable
From 10.1.1.2 icmp_seq=186 Destination Host Unreachable
From 10.1.1.2 icmp_seq=187 Destination Host Unreachable
From 10.1.1.2 icmp_seq=188 Destination Host Unreachable
64 bytes from 8.8.8.8: icmp_req=189 ttl=52 time=180 ms
64 bytes from 8.8.8.8: icmp_req=190 ttl=52 time=170 ms
64 bytes from 8.8.8.8: icmp_req=191 ttl=52 time=169 ms
64 bytes from 8.8.8.8: icmp_req=192 ttl=52 time=170 ms
64 bytes from 8.8.8.8: icmp_req=193 ttl=52 time=170 ms
64 bytes from 8.8.8.8: icmp_req=194 ttl=52 time=169 ms
64 bytes from 8.8.8.8: icmp_req=195 ttl=52 time=169 ms
64 bytes from 8.8.8.8: icmp_req=196 ttl=52 time=170 ms
64 bytes from 8.8.8.8: icmp_req=197 ttl=52 time=170 ms
64 bytes from 8.8.8.8: icmp_req=198 ttl=52 time=170 ms
^C
--- 8.8.8.8 ping statistics ---
198 packets transmitted, 25 received, +103 errors, 87% packet loss, time 197184ms
rtt min/avg/max/mdev = 169.283/171.012/180.604/2.114 ms, pipe 4[/HTML]I haven't got a clue about what to do with Destination Host Unreachable,

Cheers, :(

---

### Post by OldBoy44 on 2011-06-09
Bump,

Hi all,

I managed to tweak Firefox as outlined in -
[http://davestechsupport.com/blog/2008/03/08/how-to-setup-internet-connections-in-ubuntu/](http://davestechsupport.com/blog/2008/03/08/how-to-setup-internet-connections-in-ubuntu/)
The result showed a much improved response from the browser -

However with regard to -
[https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html)
it still concerns me that there are 0% successful packets as outlined in "Check the DNS"

Regarding -
[https://help.ubuntu.com/8.04/internet/C/networking-enable.html#networking-enable-nm](https://help.ubuntu.com/8.04/internet/C/networking-enable.html#networking-enable-nm)
 sudo ifdown eth0
returns - ifdown: interface eth0 not configured

Any help would be appreciated,

Cheers, :)

---

### Post by seawolf167 on 2011-06-09
I haven't abandoned this - I'm just not quite sure what the next step in troubleshooting this issue would be, hopefully someone else more knowledgeable in this area chimes in!

---

### Post by el_koraco on 2011-06-09
I also have no idea, but maybe it could be something as simple as disabling IPv6?

---

### Post by OldBoy44 on 2011-06-09
It's good to hear from you again seawolf167 - Firefox has now been running with no problems for a number of hours. I downloaded some packages with Download Manager and it took an age - I don't know if that is also an indication of a poor internet connection

Anyway, thanks very much for your interest seawolf167, :p

Thanks el_koraco,

What is IPv6 and how is it disabled?

---

### Post by seawolf167 on 2011-06-09
At this point I can't help but wonder if it is a physical problem since it is randomly occurring and sometimes works for hours, and sometimes only minutes (so maybe only packets are being dropped). How are you receiving your internet service? Cable via coax? DSL/dialup via phone lines?

I remember back in the day when I first upgraded to DSL from dialup my house had a wiring problem that the filters wouldn't solve and I kept getting dropped packets. Something about the copper phone lines running into the house were creating interference between the telephone pole and my splitter in the basement. Had to have the phone/internet provider/tech come out and update my physical phone box to something current, then I didn't have any problems with that house and DSL from then on.

---

### Post by OldBoy44 on 2011-06-09
I have dsl via phone line - there was no operating problems with my old computer which I had been operating with Ubuntu as the sole OS for the last five months. At this stage I think it may be best to monitor the browser problems over the next days or weeks, however the internet connection problem remains an annoying situation to deal with.

Edit - As my initial Firefox problem appears to be solved, I will mark this thread as solved and pursue network problems on another thread.

Cheers, :)

---

