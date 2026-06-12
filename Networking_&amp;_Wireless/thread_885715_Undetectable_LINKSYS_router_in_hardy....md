---
title: "Undetectable LINKSYS router in hardy..."
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by HerCsD on 2008-08-10
[SIZE="2"]Did anyone had any router issues after upgrading ubuntu from Gutsy to Hardy?I have a Linksys router WAG200G.Before the upgrade internet connection was ok.After the upgrade no internet.Tried to login in router (192.168.1.1) but could not find address.Checked ISP's DNS servers and they were ok.Used the ping command and had a 100% packet loss.Also used nslookup [www.google.com](www.google.com) but nothing happened(could not find servers).Netstat -nr shows no gateway(0.0.0.0).Any ideas?

P.S.0:Weird thing:Two PCs connect via the router.Laptop through wireless connection which works perfectly(can also login to 192.168.1.1)and desktop(the one having the problem) through eth0.

P.S.1:The networking icon has two identical networking options when clicked -> Wired Network(nVidia Corporation MCP55 Ethernet.First option is selected and active,second option is disabled and inactive.Not properly configured network?

P.S.:2:Tried to use eth1 but again same results.[/SIZE]

---

### Post by caljohnsmith on 2008-08-10
Based on your description, I think the problem is not with your router, but with your wireless card/ethernet connection. First of all, which are you having problems with--wireless or ethernet, or both? How about posting the output of the following commands to give some idea of what state your networking is in right now:
```
sudo lshw -C network
ifconfig
iwconfig
```

---

### Post by HerCsD on 2008-08-10
[SIZE="2"]Router's wireless works great.Problem,as I have stated is with the desktop PC which is wired via the eth0 interface.Here is the output you requested:

sudo lshw -C network->
Doesn't output anything...don't know why.

ifconfig-> 
eth0      Link encap:Ethernet  HWaddr 00:04:4b:00:ad:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:04:4b:00:ad:ac
          inet6 addr: fe80::204:4bff:fe00:adac/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:222 Base address:0xe000 

eth1:avahi Link encap:Ethernet  HWaddr 00:04:4b:00:ad:ac
           inet addr:169.254.6.171 Bcast:159.254.255.255 Mask:255.255.0.0
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           Interrupt:222 Base address:0xe000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1911 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96524 (94.2 KB)  TX bytes:96524 (94.2 KB)

iwconfig ->
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

Hope this helps.[/SIZE]

---

### Post by caljohnsmith on 2008-08-10
That's certainly not a good sign that lshw couldn't find any NICs in your computer. Probably lspci will give the same, but have you tried it? 
```
lspci
```
Does the desktop computer have any other operating systems on it you can try, maybe Windows for example? Also, if you have an old Gutsy Live CD, can you boot that up, and use your internet OK again? And if that doesn't work, does Gutsy on a Live CD see your ethernet card (sudo lshw -C network or lspci)?

---

### Post by chili555 on 2008-08-10
> sudo lshw -C network->
Doesn't output anything...don't know why.It has to! Did you wait long enough? It takes a few moments to think up a good answer.

---

### Post by HerCsD on 2008-08-10
[SIZE="2"][QUOTE=]Does the desktop computer have any other operating systems on it you can try, maybe Windows for example?[/QUOTE]I have Windows XP and I do have access to the Net via router's eth0 interface.Besides even without Windows I should be able to have Net access since I have in my laptop.I personally think that something wrong is with Hardy.

> 
Quote:
sudo lshw -C network->
Doesn't output anything...don't know why.
It has to! Did you wait long enough? It takes a few moments to think up a good answer.I've tried running sudo lshw with output redirection to a text file since it produces a lot of of information.For the brave I've attached the text file in a zip archive(text was too big and couldn't upload).Do note that I've waited long enough when running sudo lshw -C network and the terminal output nothing but the shell dollar sign(that is the ~$ prompt which showed me it finished command execution)

[/SIZE]

Btw,a friend of mine said that he had the same problem when upgraded from Gutsy to Hardy and told me that it's the interface that the router doesn't see and needs to be set up(don't know why since Hardy should do that automatically) or the router does not assign an IP.We're trying to find a workaround here so I'll keep you updated if something important comes up.

---

### Post by chili555 on 2008-08-10
Here is the pertinant part:> *-bridge:0
             description: Ethernet interface
             product: MCP55 Ethernet
             vendor: nVidia Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: eth0
             version: a2
             serial: 00:04:4b:00:ad:ab
             capacity: 1000000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge pm msix msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.30 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MIIIt seems to have an IP address, 192.168.1.30. I assume, since it shows link=no, it got an IP because you assigned a static address.

The other interface is here:> *-bridge:1
             description: Ethernet interface
             product: MCP55 Ethernet
             vendor: nVidia Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth1
             version: a2
             serial: 00:04:4b:00:ad:ac
             size: 100000000
             capacity: 1000000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge pm msix msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.11 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yesIt also has an IP address, but shows link=yes.

The big mystery is why they show as 'bridge' and not 'network.' I hope one of our colleagues can help here.

---

### Post by Ayuthia on 2008-08-10
> **chili555 said:**
> 
The big mystery is why they show as 'bridge' and not 'network.' I hope one of our colleagues can help here.
I can't really provide an answer, but I have noticed that my laptop is now reporting the same result for my wired card.  It is now shown as a bridge instead of an ethernet controller in lspci.  I am guessing that it is a bug, but I could be wrong.  Fortunately the card does work so it does show promise that the original posters card should work.

---

### Post by HerCsD on 2008-08-13
[SIZE="2"]OK,I did a fresh install of Ubuntu 8.04.However,I do face the same issue as I have mentioned.It seems that the problem might be because my router does not "understand" IPv6 properly.I followed this thread:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

I tried this since I cannot even ping 192.168.1.1 and dig AAAA [www.google.gr](www.google.gr) or dig A [www.google.gr](www.google.gr) output a connection timeout (not to mention that other threads state you cannot even login to your router from Ubuntu's Firefox -> Ouch! :().Anyway,I followed the official solution about fixing IPv6 and choosing IPv4 but still nothing.Do you think that I should do a firmware upgrade?:confused::confused:
[/SIZE]

---

### Post by jimv on 2008-08-13
> **chili555 said:**
> It has to! Did you wait long enough? It takes a few moments to think up a good answer.

Actually, no it doesn't have to show his NIC.  My NIC is in the "bridge" class, not network (and it works just fine).

Can you post the contents /etc/network/interfaces?

---

### Post by HerCsD on 2008-08-13
[SIZE="2"]> Can you post the contents /etc/network/interfaces?
Yes.File contains:

auto lo
iface lo inet loopback

Hope this helps!
[/SIZE]

---

### Post by HerCsD on 2008-11-03
OK.The problem has been resolved for quite some time now so I believe I should post the solution.It all came down to a BIOS update.I was trying helplessly to connect from Ubuntu and when I could not get the internet connection working I started usng Windows XP.Because there I had a BSOD for a HW issue I did a BIOS update.After some days I though to try and figure out again the Internet problem.I login the next day after the successful BIOS update in Ubuntu and...voila.All working like a charm.I guess I should post that as this information may be useful to someone else.Btw,thank you all for your assistance.

P.S.:Mainboard was an eVGA nForce 680i SLI(Intel socket 775).

---

