---
title: "Ubuntu 14.04 no eth0?"
date: 2015-03-06
forum: Networking &amp; Wireless
---

### Post by DD1 on 2015-03-06
newbee question. Is there a way to turn on eth0? My laptop is on the internet and using wifi. My server is not on the internet and has a static IP I assigned. No router between them. I want to transfer files from laptop to server through eth0 with a direct connect, but it wont let me connect. I also tried once before to hook up the internet through eth0 on my laptop and will not connect. So I believe it is either off or not installed or......

Here is ifconfig

ifconfig
eth0      Link encap:Ethernet  HWaddr 04:7d:7b:66:58:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:9059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:865125 (865.1 KB)  TX bytes:865125 (865.1 KB)

wlan0     Link encap:Ethernet  HWaddr e0:ca:94:c9:ce:af  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2ca:94ff:fec9:ceaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:132744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39769385 (39.7 MB)  TX bytes:7916455 (7.9 MB)



route doesnt even show eth0.

route
Kernel IP routing table
Destination          Gateway               Genmask                 Flags     Metric     Ref        Use   Iface
default                    192.168.1.1      0.0.0.0                   UG            0              0              0    wlan0
192.168.1.0             *                           255.255.255.0     U               9               0              0    wlan0



I am at a loss on what to do from here. Some stuff I researched is pretty dated and I dont know how much would work with newer OS. Any help in getting eth0 up would be greatly appreciated.

---

### Post by TheFu on 2015-03-06
Please use "code tags" so things line up and are easier to read.
Put both systems on the same subnet (static IPs), then set a specific route between each (both systems) with the route command. The metric needs to be lower than the default interface route on both systems. It is easier if the wlan and wired ethernet are not on the same subnet. Then you can just setup a network-based route.

**sudo ifup eth0** will bring up the xface - be certain you've specified the desired config already.

---

### Post by DD1 on 2015-03-06
Ummm ya, static, got it. Does anyone have an example of what this is suppose to look like?

---

### Post by TheFu on 2015-03-06
Which OS are you running?  desktop or server?

---

### Post by DD1 on 2015-03-06
Laptop Ubuntu 14.04 desktop, Server Ubuntu 14.04 Server edition.

I dont want to lose the wifi on my laptop. Right now its the only one on the internet, thats why im kinda hesitant and want to know what the config file should look like when I go to make it static.

---

### Post by TheFu on 2015-03-06
I don't use desktop versions.

On the server, drop something like this into the interfaces file. 

```
auto eth0
iface eth0 inet static
  address 172.22.22.11
  gateway 172.22.22.1
  netmask 255.255.255.0
  dns-nameservers 8.8.8.8
```

BTW, this is well documented all over the internet. There are Server and Desktop Guides for Ubuntu: 
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)
[https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)

---

### Post by DD1 on 2015-03-06
I changed the server to static, its my desktop i need to get configured for eth0 and keep my wifi.

---

### Post by DD1 on 2015-03-06
I have went through the second one and nothing. That was the first thing I tried. Then I read a bunch on the net but there all old posts. Im talking back to version at least 8.04. I dont know if those will still work with the new versions. Thanks anyways.

---

### Post by DD1 on 2015-03-06
So, just went through all of that again, this time lost wifi and still no connection. Getting frustrated. 

Setup ubuntu on wifi lose eth0, setup ubuntu on eth0, lose wifi. They cant seriously put a script in to just shut it down and restart it after install instead of spending hours messing around with stuff that doesnt work!??????

---

### Post by TheFu on 2015-03-06
The capabilities in Linux networking are fantastic - pretty much anything that can be done in networking can be accomplished with Linux. Most of the simple stuff "just works" - the complex stuff needs a little more help. Not much has changed since the DNS-stuff got moved into the interfaces (from resolv.conf) in 2012 - at least on the server side.  On desktops, i usually remove network-manager and configure things with text files - old school-style. Network manager is for simple stuff - when you need to do something else, disable it and do things manually.

* Setup the IPs/subnets for any internfaces you want on both systems.
* Add a route between the 2 systems.

Do this the "server way" on both systems.  [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic) seems to have the best answers.  It is always best to start with help.ubuntu.com vs some random blog article. The DNS part is wrong in that article. I'd fix it, but haven't figured out how to do that.  Don't touch /etc/resolv.conf since 12.04 or later.

That's it.  Well, assuming you either have a cross-over cable or 1 of the NICs handles it. Newer NICs should, but older ones may not.  It is part of the GigE spec, so if both are Gige - you're good.

---

### Post by steeldriver on 2015-03-06
You should be able to configure/bring up your static eth0 on the laptop via /etc/network/interfaces and let the default NetworkManager handle the wireless - it will ignore ("not manage") the static interface

---

### Post by DD1 on 2015-03-07
> **steeldriver said:**
> You should be able to configure/bring up your static eth0 on the laptop via /etc/network/interfaces and let the default NetworkManager handle the wireless - it will ignore ("not manage") the static interface

 Last time I tried this, my wifi got dropped. I am probably doing it wrong. This has not defeated me yet, it will work when I am done.

---

### Post by TheFu on 2015-03-07
After fighting NM for a few years, I gave up.  
Now I to it manually with the interface file and wicd-curses for any wifi needs. It is possible to use wicd to manage both wifi and wired, but that might ask for issues.  I don't usually need both working at the same time - only when doing like you are - need connectivity to 2 different subnets. Then it works fine.  

Perhaps if you posted the interfaces file from both systems, we could help more?

---

### Post by DD1 on 2015-03-07
I dont need to have wifi and eth0 working at the same time. I put files on my laptop, I need to transfer to my ubuntu server, via eth0, if wifi shuts down while plugging in eth0, thats fine, until I unplug the eth0, then wifi needs to come back on. It seems as though when I setup my eth0, I lose my wifi or vice versa, which is what im going through right now. When I plug my eth0 in, it does nothing, even if I setup it up it does nothing. It refuses to talk to the server. Apparently I just need to understand how to setup eth0 better then what I do. I did make my server a static ip. I know it is on my end of doing something wrong.

But I have notice in the past, when setting up ubuntu desktop on my laptop, if im on wifi, it drops eth0, if im on eth0, it drops wifi. This was in reference to my earlier post. It seems no matter what I do, Im jumping through hoops to get the other back up and working again, like now.

Otherwise, only alternative is to wait until i get my wifi router, then i should be able to shoot it to my server through wifi. But, thats slow, but if thats what it needs, then its what i will have to do. But im still being persistent to have my eth0 working.

Ill post what you ask later, I really have no time at the moment.

---

### Post by TheFu on 2015-03-07
Without a router, you need to manually set route between the 2 machines.  On each side, use the **route** command. This assumes both machines are on the same subnet.

I'll say again - > 
Perhaps if you posted the interfaces file from both systems, we could help more? 

---

### Post by DD1 on 2015-03-07
I got someone coming in to look at this as I havent the faintest thing your talking about. (I know nothing about networking except to plug this in here and go) I wanted to try to figure it out, but its way over my head. I have read so much stuff I am totally lost and confused. So therefore, I thank you for you trying to help and just pay for someone to come in and hook it up and be done with it.

---

### Post by TheFu on 2015-03-08
You modified the interface file on the server already.  That file exists in the desktop too - which you also said was modified.  Posting those files from each machine will tell us much - copy/paste here.

Or you could spend $15 on a cheap router and connect them up that way too. Just be certain that router is on a different subnet. That would be cheaper than any technical house-call.

We all don't know what we don't know until confronted by it. I understand completely and have been there. Your choice.

If you'd like a networking primer that is easy to understand - episode 25 of grc.com/sn is the beginning.

---

### Post by DD1 on 2015-03-08
One more time. But you need to talk so I can understand you. I am not a network manager let alone a server admin.  Saying technical things makes no sense to me.
Route this, subnet etc. is all a foreign language to me. Please explain what I need to do.

I did find an old Etherfast cable/dsl, 4 port switch router linksys model befsr41 hiding in the closet. It is hooked into my laptop right now, which i believe is why now i have an ip under eth0.. I have done nothing with the router yet, minus a reset on it, but I did make sure I could log into it which I can.

I am assuming something in here needs to be matched to the router?
Server ifconfig;
The primary network interface
auto lo eth0
iface to inet loopback
iface eth0 inet static
address 192.168.0.155
netmask 255.255.255.0
gateway 192.168.1.1

Laptop ifconfig; I removed the text lo and wlan to make it shorter. If needed I can put it back in.

eth0      Link encap:Ethernet  HWaddr 04:7d:7b:66:58:cd  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::67d:7bff:fe66:58cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1400 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:642033 (642.0 KB)  TX bytes:140395 (140.3 KB)


Before we go further, if you need anything else, say so now and I will get it for you before starting.

---

### Post by DD1 on 2015-03-09
Thanks anyways. Got it to work. I can now access my server. One number will make it so nothing works.

---

