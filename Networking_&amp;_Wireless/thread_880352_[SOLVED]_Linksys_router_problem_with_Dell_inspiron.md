---
title: "[SOLVED] Linksys router problem with Dell inspiron 6000"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by vedanta_2004 on 2008-08-04
Hi,
I recently upgraded my router to Linksys WRT54G2. But now I can't connect to internet using wireless. My old router ( a microsoft mn-500 ) worked really well with my ubuntu hardy disro.. 
My system is Dell inspiron 6000 with Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

My router is currently reset to factory settings. I can connect to it using
ip address 192.168.1.1 but can't connect to internet.

Following is the output of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:12:3f:d1:84:f4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20018568 (19.0 MB)  TX bytes:1875743 (1.7 MB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:76:3c:4e  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe76:3c4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:3363988 (3.2 MB)  TX bytes:458175 (447.4 KB)
          Interrupt:17 Base address:0x2000 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2990 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2990 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:552197 (539.2 KB)  TX bytes:552197 (539.2 KB)



Any help is highly appreciated...

Thanks,
Vedanta.

---

### Post by vedanta_2004 on 2008-08-04
btw, following is my iwconfig
iwconfig

iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:29:88:3D:3B   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/100  Signal level=-53 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

---

### Post by superprash2003 on 2008-08-05
shouldnt you reconfigure your router since you resetted it..

---

### Post by vedanta_2004 on 2008-08-05
Hi,
I've tried many different configurations..could you please give me some instructions on how you think it should be configured ?

Thanks for all the help.

-Vedanta_2004

---

### Post by caljohnsmith on 2008-08-05
From your ifconfig and iwconfig outputs, it appears you may be connected to your router fine. But your router may not necessarily be set up correctly with your internet connection and preventing you from accessing the internet. Do you have any other computers that connect to the router and use the internet OK? And do you have any other operating systems on your computer (like Windows) that you can try to connect with? 

Try doing:
```
ping -c5 192.168.1.1
```
Is pinging your router successful? I'm assuming that 192.168.1.1 is the address of your router, if it isn't, use the correct one. If that does work, can you access your router settings via:
```
http://192.168.1.1/ 
```
Of course use your correct router IP address.

---

### Post by vedanta_2004 on 2008-08-05
Unfortunately, I don't have any other machine or any other operating system to test this thing...
pinging 192.168.1.1 works fine...I don't know what to change in router settings..
Thanks for all the help...
-Vedanta_2004

---

### Post by caljohnsmith on 2008-08-05
> **vedanta_2004 said:**
> Unfortunately, I don't have any other machine or any other operating system to test this thing...
pinging 192.168.1.1 works fine...I don't know what to change in router settings..
Thanks for all the help...
-Vedanta_2004
Vedanta, the fact that you can ping 192.168.1.1 means that most likely your computer's connection with your router is fine, but accessing the internet is a problem because of your router's settings at this point. do you have any idea how you had your other router set up when it was working? Are you using a DSL connection and have a DSL modem? You should be able to access your router settings in a web browser with that previous URL I gave you:
```
http://192.168.1.1/
```
That's the default address of most Linksys routers I believe. If the settings are back at default, then when it asks for a user/password, just leave the user field blank and enter "admin" for the password. That should get you in.

---

### Post by vedanta_2004 on 2008-08-05
Hi caljohnsmith,
Thanks for your reply...
I can get into my router using 192.168.1.1...Then I thought leaving everything to default ( as adding any security key would add another level 
of complexity to the debugging process.. ) So now is there anything special
I need to configure to access the internet..could this be some sort of firewall issue ( I dont know if I've firewall enabled in ubuntu )...

Thanks,
-Vedanta

---

### Post by caljohnsmith on 2008-08-06
Vedanta, you need to let me know what kind of internet connection you have if you want my help troubleshooting your problem. Without knowing whether it is DSL, cable, etc I won't know how your router should be set up.

---

### Post by dmizer on 2008-08-06
This should fix your problem:

1) disable ipv6: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
2) use opendns DNS servers: [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

That should get you going.

---

### Post by vedanta_2004 on 2008-08-06
Hi caljohnsmith,
Sorry for not clearing up it earlier...it is a cable modem and my router supports wireless as well as wired connection. I'm trying to use the wireless connection...


Hi dmizer,
I think you were correct in that I had ipv6 enabled..so I disabled it by following 
the instruction on the webpage and rebooted. Then I checked that ipv6 is not 
enabled any more..Then I changed the dns servers to use opendns as given
in the instructions on the second link...but even after this I could not get my 
wireless connection working..

Is there something I did wrong..

Thanks guys for all the help so far..

-Vedanta.

---

### Post by caljohnsmith on 2008-08-06
Vedanta, do you know the IP address of your cable modem? It is probably 192.168.0.1; whatever it is, try pinging that address and see if you get any response:
```
ping -c5 192.168.0.1
```
If you don't, then your router is most likely setup incorrectly to work with your cable modem.

If you are using the default settings that came with your Linksys router, then it is most likely using DHCP to try and get an IP address from your cable modem. I know that works great with DSL modems, but I don't know how cable modems are configured and if they support DHCP. 

In your Linksys router configuration web page, look under the "setup" tab for "basic setup", and there you should find whether your router is set for DHCP, PPPoE, Static IP, etc. You'll need to check the documentation for your cable modem to find out how you should set up your router to work with your cable modem. My guess it will be PPPoE if it is not DHCP, but I'm not sure.

---

### Post by dmizer on 2008-08-06
Another alternative would be to simply elminate the router completely.

Just plug your computer directly into the modem and check:
1) What IP do you get.
```
sudo ifconfig
```
2) Can you browse online?

---

### Post by vedanta_2004 on 2008-08-06
Following is the output after I bypass router and directly connect to modem.

eth0      Link encap:Ethernet  HWaddr 00:12:3f:d1:84:f4  
          inet addr:98.207.41.247  Bcast:255.255.255.255  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1618152 (1.5 MB)  TX bytes:270915 (264.5 KB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:76:3c:4e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:45211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30121 (29.4 KB)  TX bytes:30121 (29.4 KB)

---

### Post by vedanta_2004 on 2008-08-06
btw, I can browse online if I bypass router.

---

### Post by dmizer on 2008-08-06
Well, as far as I can tell, you should be browsing away with no problems when the router is connected.

Reconnect the router, and make sure that the cable from the modem to the router is connected to the wlan port on the router.  Sounds silly, but it does happen.

Do you have a live CD other than Ubuntu like Knoppix?  If so, boot to it, and see if you can get online with it.

---

### Post by vedanta_2004 on 2008-08-07
Hi Dmizer,
I tried just a wired connection through my router. That is following type of 
configuration :
cable-modem -> Router -> Laptop

Following was the ifconfig output : 

eth0      Link encap:Ethernet  HWaddr 00:12:3f:d1:84:f4  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:436156 (425.9 KB)  TX bytes:69564 (67.9 KB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:76:3c:4e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9438 errors:0 dropped:1 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20659 (20.1 KB)  TX bytes:24833 (24.2 KB)
          Interrupt:17 Base address:0x4000 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38749 (37.8 KB)  TX bytes:38749 (37.8 KB)


It shows same symptoms as the wireless one ...
Also I noted one more thing in my network settings in the hosts tab:
after initial localhost (127.0.0.1) and my laptop following type of hosts are 
listed :
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
...

Is it suspicious that they still mention ip6 even after I disabled ip6..

Thanks for all the help so far..I'll try to borrow somebody's window laptop
and try with it..

---

### Post by caljohnsmith on 2008-08-07
Vedanta, did you try to ping your modem like I mentioned before? If you can ping your router fine and access your router's configuration settings via its web interface, and yet not ping your modem, that would be a strong indication that the problem is entirely with the way you have your router set up.

---

### Post by cszikszoy on 2008-08-07
The problem isn't with ubuntu.  You said you could browse just fine when bypassing the router.  What you need to do is get into contact with Linksys' tech support.  They have (free) phone numbers on their website.  Linksys' tech support is very good, I've called them many times, and have also used the online chat tech support.

I don't think the online chat option will really apply to you in this case though :)

Just call linksys' tech support and tell them you're having problems connecting to the internet.  Don't mention anything to them about ubuntu or linux, because then they will just tell you its a problem with ubuntu.  Specifically tell them that when you bypass the router, you can browse the internet fine.

---

### Post by dmizer on 2008-08-07
> **caljohnsmith said:**
> Vedanta, did you try to ping your modem like I mentioned before? If you can ping your router fine and access your router's configuration settings via its web interface, and yet not ping your modem, that would be a strong indication that the problem is entirely with the way you have your router set up.

Maybe there's something I don't understand about what you're suggesting here, but it's not possible to ping a modem that's functioning as a modem.  According to post 14, the modem is handing a routable ip address to the computer.  The modem does not have a reachable private subnet.

The only thing that remains to be confirmed (from what I've seen) is:
- Is the lan cable connected correctly (lan port on modem to wan port on router)
- Are there any bad cables
- Can another computer ... or another OS connect to the internet with the router in place?

However, I am willing to admit that I have missed something.  It certainly wouldn't be the first time.

---

### Post by caljohnsmith on 2008-08-07
> **dmizer said:**
> Maybe there's something I don't understand about what you're suggesting here, but it's not possible to ping a modem that's functioning as a modem.  According to post 14, the modem is handing a routable ip address to the computer.  The modem does not have a reachable private subnet.
Dmizer, I would disagree with you about that, unless I'm missing something here: when Vedanta connects to his cable modem directly, it acts as a gateway to the internet; the cable modem is assigned an internet IP address by his ISP, and the modem gives Vedanta's computer a subnet address (192.168.x.x) via DHCP. That means the modem also has to have a subnet address itself so the computer can use it as a gateway to the internet. If Vedanta runs:
```
route -n
```
He will be able to see the subnet IP address of his gateway, i.e. his modem, when he is hooked up directly to his modem. Most modems that I'm aware of will respond to ping requests, which is why I asked him to ping his modem, but to ping it when he is trying to use his router. The fact that he can ping his router fine and access its configuration web page fine via wireless seems to me is a really strong indication that there is no problem between his computer and router when he is using wireless; and that would indicate that the problem most likely exists further upstream, namely between his router and modem, because using his modem directly works just fine.

For instance, I'm using a DSL modem with a router, and my DSL modem has a LAN address of 192.168.0.1 and my router's is 192.168.1.1; both are on different subnets, but both are accessible since the modem is a gateway to the router. I can ping either one, and I can also access their configuration web pages via those addresses. 

If I am missing something here though, my apologies, and please correct me.

---

### Post by dmizer on 2008-08-07
> **caljohnsmith said:**
> Dmizer, I would disagree with you about that, unless I'm missing something here: when Vedanta connects to his cable modem directly, it acts as a gateway to the internet; the cable modem is assigned an internet IP address by his ISP, and the modem gives Vedanta's computer a subnet address (192.168.x.x) via DHCP. That means the modem also has to have a subnet address itself so the computer can use it as a gateway to the internet. If Vedanta runs:
```
route -n
```
He will be able to see the subnet IP address of his gateway, i.e. his modem, when he is hooked up directly to his modem. Most modems that I'm aware of will respond to ping requests, which is why I asked him to ping his modem, but to ping it when he is trying to use his router. The fact that he can ping his router fine and access its configuration web page fine via wireless seems to me is a really strong indication that there is no problem between his computer and router when he is using wireless; and that would indicate that the problem most likely exists further upstream, namely between his router and modem, because using his modem directly works just fine.

For instance, I'm using a DSL modem with a router, and my DSL modem has a LAN address of 192.168.0.1 and my router's is 192.168.1.1; both are on different subnets, but both are accessible since the modem is a gateway to the router. I can ping either one, and I can also access their configuration web pages via those addresses. 

If I am missing something here though, my apologies, and please correct me.
Your DSL modem is also a router.  According to post 14, vendanta's modem is not.

According to the following information, when vendanta's computer is connected directly to the modem, there is no private subnet (192.168.x.x).  The following information shows that vendanta is getting a routeable IP address directly from the ISP (emphasis mine):
> **vedanta_2004 said:**
> Following is the output after I bypass router and directly connect to modem.

```
eth0      Link encap:Ethernet  HWaddr 00:12:3f:d1:84:f4  
          inet addr:[COLOR="Red"]98.207.41.247[/COLOR]  Bcast:255.255.255.255  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1618152 (1.5 MB)  TX bytes:270915 (264.5 KB)
          Interrupt:19 
```
[snip]
Some modems function both as a modem and are capable of NAT.  If the modem is capable of NAT, then you will see a non-routable subnet ip (usually 192.168.x.x).  But many have no NAT functionality at all.  If the modem has no NAT functionality, the modem simply hands off the WAN routable IP address assigned by the ISP. Vendanta's modem clearly does not have NAT functionality (or NAT is disabled).  Thus, no amount of pinging will get a response from the modem.

The Linksys router's configuration page may show if the modem is talking to the router though ...

---

### Post by caljohnsmith on 2008-08-07
I see your point Dmizer, I didn't read his post #14 carefully enough and missed the part about his computer being assigned his internet IP address and not a subnet IP address. I was remembering his previous post where he was getting a subnet address from his router. Considering it was 7:00 AM here when I responded to your post, guess I better wait until I'm more awake next time before responding--thanks for pointing out my mistake. :)
> **dmizer said:**
> Your DSL modem is also a router.
Actually that's not true because my DSL modem does not perform any type of NAT capability, and to my understanding all routers use NAT. My modem has only one input and one output, so even though the address on the output is a subnet address, it is a one-for-one correspondence with the internet IP address--no network address translation takes place, thus all incoming/outgoing TCP ports are exactly the same. For instance,  see the [Wikipedia article on routers (residential gateways)]("http://en.wikipedia.org/wiki/Residential_gateway"):
> A modem (or ADSL modem) provides none of the functions of a router. It merely allows digital Ethernet data traffic to be modulated into analogue information suitable for transmission across telephone lines, cable wires, optical fibers, or wireless radio frequencies. On the receiving end is another modem that re-converts the transmission format back into digital data packets.

> **dmizer said:**
> Some modems function both as a modem and are capable of NAT.  If the modem is capable of NAT, then you will see a non-routable subnet ip (usually 192.168.x.x).  But many have no NAT functionality at all.  If the modem has no NAT functionality, the modem simply hands off the WAN routable IP address assigned by the ISP.
Again, that's not true for my modem and any other DSL modem, because the modem does assign my router a subnet IP address and not the WAN (internet) IP address. Yet it does not perform NAT, otherwise I would be able to hook up more than one computer to it. If the modem does perform NAT, then it would be incorrect to call it just a modem, and instead call it a "residential gateway" since it combines both a modem and router.

But regardless, let's concentrate on helping Vedanta solve his problem--sorry I gave erroneous advice earlier.

---

### Post by vedanta_2004 on 2008-08-08
Hi Guys,
I borrowed a windows laptop yesterday..reseted the router to factory configuration and tried connecting through wireless with windows..it connected..Then I did a ipconfig on windows command line and found the DNS address were different as
I had configured it to use OpenDNS on my ubuntu machine..I modified my ubuntu dns settings to dns address from windows machine and voila .. I was online..I don't know whether I had configured DNS address incorrectly or if there is an issue in using opendns with Linksys router ... I'll try experimenting again tonight with opendns and let you know....
Thanks for all the help..I could never have figured out the ipv6 issue on my own..
Thanks again,
-Vedanta.

---

