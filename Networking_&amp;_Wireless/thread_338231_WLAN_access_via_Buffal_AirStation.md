---
title: "WLAN access via Buffal AirStation"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by middlewordie on 2007-01-14
I am new to Linux, but having just installed ubuntu 6.10, i am unable to connect to the internet.

My PC specs are:
AMD Sempron 2800
K8Upgrade NF3 motherboard
2x512MB RAM
Radeon 7000 graphics card
6.4GB Samsung HD and 160GB WD HD
DVD Combo
CDRW

As the title suggests, I'm using (or trying to use) a buffalo airstation WL1-T1-S11G-1 to provide access to a local wireless network - this works under windows. I was under the impression that on plugging the network cable from this into the pc, it would connect automatically (like in windows). It does not - I am posting this from my other pc which is running windows xp.

---

### Post by middlewordie on 2007-01-14
This is what happens when I typed ifconfig

nick@samsung:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8F:7E:D0:EF  
          inet addr:192.168.254.194  Bcast:192.168.254.194  Mask:255.255.255.255
          inet6 addr: fe80::213:8fff:fe7e:d0ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:322266 (314.7 KiB)  TX bytes:3612 (3.5 KiB)
          Interrupt:185 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21316 (20.8 KiB)  TX bytes:21316 (20.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3F:13:6F:10  
          inet6 addr: fe80::217:3fff:fe13:6f10/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:5832 (5.6 KiB)
          Base address:0x8000 

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-13-6F-10-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000

---

### Post by middlewordie on 2007-01-15
I've not had any responses on this today, but I still can't get it to work. Am I missing something about setting up a network connection? I ask this because when I've plugged this  pc into another network, it picked up the internet straight off.

Is there a firewall I don't klnow about, or some setting that I need to adjust manually?

For background info:

My wireless connection is external - I'm trying to connect to a cooperative local network - see [http://boundless.coop](http://boundless.coop) for details. There are a number of nodes around me, two of which give a decent signal and I can access using wondows xp machines.

I've gone into network manager and I have eth0 configured for dchp, so that I get assigned an ip address by the boundless node i'm connecting to. However, I still get the errors listed above. Note I also have Belkin FD7050 USB wirelss card, but this also fails to conect. That's why I borrowed the airstation, to see if connecting via the ethernet card would be better. Any suggestions on what my problem might be - apart from not really understanding linux!

---

### Post by teaker1s on 2007-01-15
could be DNS can you ping a numeric ip?:-k

---

### Post by middlewordie on 2007-01-15
I don't know. What number should I try?

---

### Post by teaker1s on 2007-01-15
panel click system administration networking tools 
select ping
enter this google ip address
64.233.167.99
if you have internet access but DNS ISSUE you should see result like screenshot attached

---

### Post by middlewordie on 2007-01-15
Thanks. I'll run upstairs to try this and report back...:)

---

### Post by middlewordie on 2007-01-15
Results in attached pics. This doesn't look like what you posted

---

### Post by teaker1s on 2007-01-15
networking tools-select the devices tab and your ethernet connection
try again

failling that try the ip address in a web browser-if you see google.com it's DNS

---

### Post by middlewordie on 2007-01-15
more results - see attached

i am encouraged because the numbers of bytes received appears to be going up. however, no transmitted byte increase and no google when i entered the numbers into firefox - same old no connection blurb

---

### Post by teaker1s on 2007-01-15
:-k well it :-k appears you have ethernet up try pinging again in network tools
if you get a ping back look at this link for dhcp DNS stabilize 
[http://ubuntuforums.org/showthread.php?t=282034]("http://ubuntuforums.org/showthread.php?t=282034")
OR
if you can do static ip on your network the set it in administration networking and manually enter your isp DNS

OTHER THAN THAT POSSIBLY IPV6-SEARCH FORUMS


I'm off for a bath and bed,I'll watch the thread-if you post, I'll reply when I'm back on again

---

### Post by middlewordie on 2007-01-15
thanks for your help - i'll keep going for a bit and see if i make any fundamental breakthroughs!!

---

### Post by middlewordie on 2007-01-15
last post tonight. i've attached some more terminal output

---

### Post by middlewordie on 2007-01-16
It has been suggested to me that as this airstation works on windows, perhaps I ought to plug it into that and then check the connection settings there. It may be that the airstation uses fixed ip addresses for providing wireless connection and that is why dchp isn't working. :-k

---

### Post by middlewordie on 2007-01-16
> **teaker1s said:**
> 
if you can do static ip on your network the set it in administration networking and manually enter your isp DNS

what is my network isp dns? where might i find it?

---

### Post by teaker1s on 2007-01-16
okay well computers understand number ip addresses so when we type [www.google.co.uk](www.google.co.uk) the computer sends a request to a Dynamic Name Server which tells the browser to go to a number ip address corresponding to the name you type in. 
Now if we can get google by pinging with a number ip but not when we type a name this would be a DNS issue. DNS server settings are quicker if you use ones your isp provide, in theory you could use any DNS server if your service provider won't tell you.

search the forums for IPV6 and see if it sounds like your issue;)

---

### Post by middlewordie on 2007-01-17
now i'm very confused. I thought that I'd check the airstation by installing winxp on my box and trying it there. it did not work then either, even with the drivers installed. ](*,) 

i then reinstalled edgy, so at least i now have dual boot system against which to check future wireless escapades.

the airstation is borrowed, so i think at this stage i shall give it back as a bad job and look for an alternative client for dchp networks that works with linux! ;)  that can be another thread though...

cheers for the help provided! :)

---

### Post by teaker1s on 2007-01-17
belkin cards with Broadcom chipset and ndiswrapper work well.
the BCM4311 AND BCM4306 well with this guide
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")

---

