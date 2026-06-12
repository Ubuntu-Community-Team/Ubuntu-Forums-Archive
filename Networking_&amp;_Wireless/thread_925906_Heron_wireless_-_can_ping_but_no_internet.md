---
title: "Heron wireless - can ping but no internet"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by MickFlan on 2008-09-21
I have a netgear dg834t and a wireless card in my laptop that I've set up in Heron using ndiswrapper. Everything looks fine, I can ping the router, and the router can ping the laptop. But I can't get an internet connection? The laptop dual boots into xp where the internet access is ok.

---

### Post by nixscripter on 2008-09-21
First thing I think of would be to check to see if it's your DNS information. Where does Windows get it? Does your router give it to you over DHCP?

The simplest way to verify that this is the problem, and not something else, is to try and ping something by IP on the internet, say, one of google's server farms.

---

### Post by MickFlan on 2008-09-22
> **nixscripter said:**
> First thing I think of would be to check to see if it's your DNS information. Where does Windows get it? Does your router give it to you over DHCP?

The simplest way to verify that this is the problem, and not something else, is to try and ping something by IP on the internet, say, one of google's server farms.

Thanks for trying to help out. I'm new to all this so I do have understandable ignorance!

I've ping'd the ip address of google.com via a terminal, but no luck: 'Network is unreachable' is the response.

The browser just says 'Address not found' when looking for [www.google.com](www.google.com).

Commands output:
smejltd@smejltd-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:c2:e2:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xcd00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112604 (109.9 KB)  TX bytes:112604 (109.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0d:f0:45:51:6d  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


smejltd@smejltd-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

smejltd@smejltd-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.407 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:-2147483648 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


smejltd@smejltd-laptop:~$ lspci
00:01.0 Host bridge: Advanced Micro Devices [AMD] CS5536 [Geode companion] Host Bridge (rev 31)
00:01.1 VGA compatible controller: Advanced Micro Devices [AMD] Geode LX Video
00:01.2 Entertainment encryption device: Advanced Micro Devices [AMD] Geode LX AES Security Block
00:0c.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
00:0c.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
00:0c.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 ISA bridge: Advanced Micro Devices [AMD] CS5536 [Geode companion] ISA (rev 03)
00:0f.2 IDE interface: Advanced Micro Devices [AMD] CS5536 [Geode companion] IDE (rev 01)
00:0f.3 Multimedia audio controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] Audio (rev 01)
00:0f.4 USB Controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] OHC (rev 02)
00:0f.5 USB Controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] EHC (rev 02)

smejltd@smejltd-laptop:~$

---

### Post by MickFlan on 2008-09-22
Also, windows uses dhcp but if I use that with heron I get no response at all using the gui tool. I can only ping the router when using static ip address.

---

### Post by chongzivalve0809 on 2008-09-22
a professional [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) China manufactuer and supplier,established in 1983The main product is:cast steel [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm),forged steel gate valve ,pressure seal gate valve,plate [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm).  BFV Valve also possess the test lab with various of examination equipment for material chemical composition analysis, physical property and non-destructive examinat-ions such as RT,UT,MT,PT .[gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) manufacturer website:[www.valvesupplier.net/forged-steel-gate-valves.htm](http://www.valvesupplier.net/forged-steel-gate-valves.htm)

---

### Post by superprash2003 on 2008-09-22
how can router ping laptop?? from your ifconfig output it seems that your wifi interface is getting 192.168.0.1 .. which normally is router's ip.. so pinging 192.168.0.1 will be successfull as you end up pinging your on pc..in your terminal type lshw -C network and post output

---

### Post by MickFlan on 2008-09-22
> **superprash2003 said:**
> how can router ping laptop?? from your ifconfig output it seems that your wifi interface is getting 192.168.0.1 .. which normally is router's ip.. so pinging 192.168.0.1 will be successfull as you end up pinging your on pc..in your terminal type lshw -C network and post output

Router pings 127.0.0.1 which is laptop's ip address. Does that make sense?

---

### Post by MickFlan on 2008-09-22
> **superprash2003 said:**
> how can router ping laptop?? from your ifconfig output it seems that your wifi interface is getting 192.168.0.1 .. which normally is router's ip.. so pinging 192.168.0.1 will be successfull as you end up pinging your on pc..in your terminal type lshw -C network and post output

Sorry forgot to post lshw:

smejltd@smejltd-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:c2:e2:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0d:f0:45:51:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw35g driverversion=1.52+Winbond Electronics Corp.,0 ip=192.168.0.1 multicast=yes wireless=IEEE 802.11g
smejltd@smejltd-laptop:~$

---

### Post by nixscripter on 2008-09-22
"There's no place like 127.0.0.1" is a shirt in my closet. That's the address of whatever computer you are talking to, and is registered to the loopback interface (send packets back into the machine, so they don't actually go anywhere).

superprash is right. There should be another IP in question. When you're in windows, what is the IP of the router (the "gateway"), and what is the IP of the laptop? You should be able to check under the Network Connections control panel (somewhere).

---

### Post by MickFlan on 2008-09-22
> **nixscripter said:**
> "There's no place like 127.0.0.1" is a shirt in my closet. That's the address of whatever computer you are talking to, and is registered to the loopback interface (send packets back into the machine, so they don't actually go anywhere).

superprash is right. There should be another IP in question. When you're in windows, what is the IP of the router (the "gateway"), and what is the IP of the laptop? You should be able to check under the Network Connections control panel (somewhere).

Here's the router info:

Router Status 
   
Account Name  
Firmware Version  V1.02.04  
   
ADSL Port  
MAC Address  00:1B:2F:79:D3:E1  
IP Address  81.155.136.92 
Network Type PPPoA 
IP Subnet Mask  255.255.255.255 
Gateway IP Address 217.47.158.142 
Domain Name Server  194.74.65.69
62.6.40.178 
   
LAN Port 
MAC Address  00:1B:2F:79:D3:E0 
IP Address  192.168.0.1 
DHCP  On 
IP Subnet Mask  255.255.255.0 
   
Modem  
ADSL Firmware Version A2pB018e.d16f 
Modem Status Connected 
DownStream Connection Speed 6368 kbps 
UpStream Connection Speed 448 kbps 
VPI 0 
VCI 38 

Laptop IP:
IP Address   192.168.0.2

Thanks a bunch!

---

### Post by superprash2003 on 2008-09-23
your output says that laptop ip is 192.168.0.2 but i didnt see it in your ifconfig output??? please post ifconfig output again.. ping router again.. and post output

---

### Post by MickFlan on 2008-09-23
> **superprash2003 said:**
> your output says that laptop ip is 192.168.0.2 but i didnt see it in your ifconfig output??? please post ifconfig output again.. ping router again.. and post output

Hi

192.168.0.2 is from laptop when in XP. IFCONFIG is from ubuntu, so don't understand what you mean?

---

### Post by nixscripter on 2008-09-23
So in XP, it looks like the router assigns it an IP okay.

Boot into Ubuntu, and see what ```
ifconfig wlan0
``` says. If it doesn't work, try adding the static IP it assigned like this: ```
sudo ifconfig wlan0 192.168.0.2 up
sudo route add default gw 192.168.0.1
```

And see if that fixes it.

---

### Post by MickFlan on 2008-09-24
> **nixscripter said:**
> So in XP, it looks like the router assigns it an IP okay.

Boot into Ubuntu, and see what ```
ifconfig wlan0
``` says. If it doesn't work, try adding the static IP it assigned like this: ```
sudo ifconfig wlan0 192.168.0.2 up
sudo route add default gw 192.168.0.1
```

And see if that fixes it.

Thanks - here's the output:

smejltd@smejltd-laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0d:f0:45:51:6d  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

smejltd@smejltd-laptop:~$ sudo ifconfig wlan0 192.168.0.2 up
smejltd@smejltd-laptop:~$ sudo route add default gw 192.168.0.1
SIOCADDRT: File exists
smejltd@smejltd-laptop:~$ 

Also, can you confirm that I have my Network Settings correct:
Under Hosts I have:
127.0.0.1 localhost
127.0.1.1 smejltd-laptop.Blades01
and then some others that look like defaults.
Under DNS tab there are no entries.
Under General tab:
Host name: smejltd-laptop
Domain name: (nothing entered)
Under Connections tab:
Wireless connection is ticked with blue mast showing:
Properties:
ESSID Blades01
Password type WEP key (hex)
Network password (entered)
Configuration Static IP address
IP address 192.168.0.1
Subnet mask 255.255.255.0
Gateway Address 217.47.158.142

Thanks again!

---

### Post by shanix on 2008-09-24
Try to set ur DNS to a public DNS server 4.2.2.2 and see if you will be able go on the internet after that.

---

### Post by MickFlan on 2008-09-24
> **shanix said:**
> Try to set ur DNS to a public DNS server 4.2.2.2 and see if you will be able go on the internet after that.

Thanks. But no change - still get 'page load error' and 'cannot find the host server'.

---

### Post by nixscripter on 2008-09-24
What is your DNS on the windows side? Try copying in the values.

---

### Post by MickFlan on 2008-09-24
> **nixscripter said:**
> What is your DNS on the windows side? Try copying in the values.

In XP under Wireless Network Connection Status I've got:
Address Type: Assigned by DHCP (is that the DNS?)
IP Adress 198.162.0.2
Subnet Mask 255.255.255.0
Default Gateway 192.168.0.1
DHCP Server 192.168.0.1
DNS Server 192.168.0.1
WINS Server (blank)

---

### Post by MickFlan on 2008-09-24
> **MickFlan said:**
> In XP under Wireless Network Connection Status I've got:
Address Type: Assigned by DHCP (is that the DNS?)
IP Adress 198.162.0.2
Subnet Mask 255.255.255.0
Default Gateway 192.168.0.1
DHCP Server 192.168.0.1
DNS Server 192.168.0.1
WINS Server (blank)

Further info:

When I try to configure the Wireless Interface (wlan0) within Devices - Network Tools, I get a pop-up message saying the interface does not exist. Maybe that's obvious, but didn't I see wlan0 specified when running one of the commands earlier?

---

### Post by superprash2003 on 2008-09-24
in your terminal type ping 192.168.0.1 and post output

---

### Post by MickFlan on 2008-09-24
> **superprash2003 said:**
> in your terminal type ping 192.168.0.1 and post output

It started:

From 169.254.6.34 icmp_seq=1 Destination Host Unreachable

Its kept pinging and is now seq=179, rest of info is same just incrementing the seq value, and still going.

---

### Post by nixscripter on 2008-09-25
That looks like a generated IP address (one that was made up). What do your routing tables look like? ```
route
```

Also, please post the output in [code] tags so that it is more readable.

---

### Post by superprash2003 on 2008-09-25
go to system->admin->network and go to wlan0 properties.. there disable roaming mode.. select your wifi network manually. and set it to DHCP and then try..

---

### Post by MickFlan on 2008-09-25
> **nixscripter said:**
> That looks like a generated IP address (one that was made up). What do your routing tables look like? ```
route
```

Also, please post the output in [code] tags so that it is more readable.

Code tags? I'm copying from one laptop to another (xp):
Route output:
Destination link-local
Gateway *
Genmask 255.255.0.0
Flags U
Metric 0
Ref 0
Use 0
Iface wlan0
Destination default
Gateway *
Genmask 0.0.0.0
Flags U
Metric 1000
Ref 0
Use 0
Iface wlan0

Explain what code tags are and I'll try to add them in - thanks.

---

### Post by MickFlan on 2008-09-25
> **superprash2003 said:**
> go to system->admin->network and go to wlan0 properties.. there disable roaming mode.. select your wifi network manually. and set it to DHCP and then try..

Thanks but its already set up this way. Which tutorial am I looking for?

---

