---
title: "Wierd Wlan problem"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by timohnani on 2007-08-10
Hi,

I have this annoying problem I just can't seem to solve. I installed Kubuntu Feisty on my laptop. After some initial hiccups I managed to get my system going and connected to the internet. Everything was fine for about a week or so including my WiFi. 

Then I decided that KNetwork Manager is just crap. So I uninstalled it. I tried to install another programme but that didn't work. So I re-installed KNetwork Manager. But once I reinstalled it, it can't seem to find my wlan interface. Before in KNetwork Manager there were two sections one for wiered and one for wlan (showing access points). Now there is only the wierd section. No matter what I've done I can't seem to fix it. 

In trying to solve the problem I've installed knemo (which is great. it shows networks with the little icons like in windows) and Wireless assistant (another great programme). KNemo recognises my wlan adapter but it shows that its always disconnected. Wireless Assistant shows me all the access points available. However when I click on my access point and error tells me I can't connect. 

When I go and check my network settings I have eth0 (wired) and eth1 (wireless) they both seem to be ok. The only problem that turns up is that when I save or apply some changes I get an error explaining that my default gateway id is invalid. It seems to be set at 0.0.0.0

Can anybody point me in the righ direction? 

Timo

---

### Post by Alibabac on 2007-08-10
Just to tell, I have the same problem, tried with various W-managers, nothing happens, they  just mess up the connection(IP, gateway,dns), and I saw only once wifi networks in Knetwork manager. As soon I choose connection, the wifi networks vanish from menu. To resume : Knetwork manager works fine  for the first time you connect to access point. When you move to other location and try to connect to other wifi network, there is no way to do it via knetwork manager. Any help ?

---

### Post by Alibabac on 2007-08-10
It's seems the only solution is: I've installed wifi radar, just to see available networks. Do not connect with this tool, rather go to manual configuration in Knetwork manager, enter ESSID and wep, and you are back in game.

---

### Post by timohnani on 2007-08-11
HI,

But thats the problem. Knetwork manager doesn't give you the option to enter your access point manually. The whole section to manage your wlan network has disappeared. 

Timo

---

### Post by timohnani on 2007-08-11
Hi,

Maybe this might provide somebody with more information:

ipwconfig:

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Malta"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig:

> eth0      Link encap:Ethernet  HWaddr 00:0A:E4:21:31:E0
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe21:31e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1437269 (1.3 MiB)  TX bytes:432994 (422.8 KiB)
          Interrupt:10

eth1      Link encap:Ethernet  HWaddr 00:04:23:75:9D:32
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x4000 Memory:e0203000-e0203fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9736 (9.5 KiB)  TX bytes:9736 (9.5 KiB)



Hope this helps.

Any help would be appreciated. 

Timo

---

### Post by karachuonyo on 2007-08-11
I also think the knetworkmanager is rubbish. In the 2 years or so of using kubuntu i have never managed to connect wireless networks using it. It's alright using wired internet. I' m running feisty on my laptop and i just installed wireless assistant (it's in the repo's) and connects first time. The only downside is it works only with the less secure WEP and not WPA.

---

