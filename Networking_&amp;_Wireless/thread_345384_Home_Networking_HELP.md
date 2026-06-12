---
title: "Home Networking HELP"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by shaunuel on 2007-01-24
Hi, 
Currently, I'm running Edgy v6.10 and have a DIRECT connection to the internet via a Motorola SURFboard (model:SB5101) modem (Rogers, high-speed). To date, everything works 100%. My girlfriend has a Compaq Presario V5000 laptop running WinXP (Home) and just bought a wireless router so that she can use the internet as well. How do I set up a network in Ubuntu that she can connect to wirelessly (with her WinXP laptop) to browse the internet? A friend (who actually turned me onto Ubuntu) said that Ubuntu to Windows networking is a little chaotic, so I thought I'd ask some experienced Ubuntu users for their help/opinions. Thanks for any and all help folks. 

Router Info: 
Linksys Compact WRT54GC

Desktop Info: (I want to "host" the network from this computer..)
Ubuntu (Edgy) v6.10
NIC: nVidia onboard 10/100Mb LAN (on ABIT NF7-S v2.0 motherboard)

Laptop Info: (..and connect wirelessly with this laptop)
Compaq Presario V5000
Windows XP (Home)
wNIC: Broadcom 802.11b/g WLAN (sorry, don't know the exact model)

---

### Post by scrooge_74 on 2007-01-24
The Motorola is a cable modem right?

Then hook the router to the cable modem and the PCs to the router.  the laptop is running the wireless so it should be very easy once you have the router configure.

You can hook the router to your PC and probably using your webbrowser you can configure the router, follow the instructions that came with the router

EDIT: what is a little chaotic is getting your PCs to see each other and share files and printers, but for getting online is very straight forward

---

### Post by shaunuel on 2007-01-24
scrooge_74, yes, the Motorola is a cable modem. I can easily hook up everything and even see/connect to the wireless network from my girlfriends laptop, but it has "Limited or No Connectivity". Also, once its hooked up, I can no longer use the internet from my Ubuntu desktop. I tried restarting my PC hoping it would auto-detect proxy config, but it didn't work. 

So essentially, the problem is: I can't get on the internet through the router. Everything is hooked up correctly and signal lights on both the modem and router indicate activity but I can't access the signal. Any ideas? Thanks.

---

### Post by scrooge_74 on 2007-01-24
Ok, that means you need to configure everything.  You shold follow the instructions to get the router working.

it probably connect to a webpage with an ip of 192.168.1.1, but check the manual.  Probably the router is not set up to assign IPs automatically, and your girlfriend laptop is detecting the network but needs to be configure properly.

After you check that the router is assigning IPs, check that your PCs are set to work using DHCP.

You have to set lots of things:

the IP handling
the router Firewall
Security for wireless

It may also be the case that your provider only wants to give you one IPs (that is why is good to have routers with firewalls so providers see only one PC online even if you have a dozen behind the firewall :D )

Check the manual and post any questions you have

---

### Post by AlanRogers on 2007-01-24
> **scrooge_74 said:**
> After you check that the router is assigning IPs, check that your PCs are set to work using DHCPThis is good advice but needs a little extra clarification. You should check that[LIST=1]
[*]only the router is running DHCP, not the cable modem as well
[*]the cable modem and the router have different IP addresses on the same subnet.
[/LIST]As an example, your router probably does have a factory-configured IP address of 192.168.0.1 but so might your cable modem, in which case it won't work. Similarly, your router might be 192.168.1.1 and your cable modem 192.168.0.1, which still won't work.

Set the cable modem to 192.168.x.1 and the router to 192.168.x.2, then set your DHCP leasing up on the router only, starting at 192.168.x.10 so that you have some spare IP addresses to allocate as static to other equipment at a later date.

---

### Post by scrooge_74 on 2007-01-24
usually those routers have a DHCP client and a server, since it has to receive the IP from the cable modem and then it will assign IPs for the internal LAN. 

Also cablemodems will either forward the IP from the DHCP server or run its own DHCP server  if it was a router itself

---

### Post by shaunuel on 2007-01-24
Hey guys, thanks a tonne for the info/help. I tried following the instructions for troubleshooting both the modem and the router. Unfortunately though, they're all step-by-step instructions for WinOS. For Linux/UNIX, both manuals suggest I consult my OS's manual. 

scrooge_74, your right. I connected to 192.168.1.1 and followed all the instructions, allowing the router to automatically assign IP(s), but still, I cannot get it to work. I then tried letting Firefox auto-detect proxy settings, but still no luck. Is there anything I should adjust in my "Networking", "Network Proxy" or "Network Tools" that'd help? 

Thanks for your patience fellas'.

EDIT: Is there a command or series of commands I can run from the Terminal that would help diagnose the EXACT problem(s)?

---

### Post by scrooge_74 on 2007-01-24
If both of your computers are receiving ips from the router and you can ping the router then the LAN should be ok.  Probably you should check again the router config, you still need to make it connect with the modem or receive and IP from the modem.  You probably can do all of that from a webbrowser. 

 Maybe you have to give your router the info from your provider, DNS servers, point him to the cable modem address or its proxy and such things.

Worst case ask the provider it should not have to be an OS dependent problem since it is between the router and the cable modem

---

### Post by AlanRogers on 2007-01-24
> **shaunuel said:**
> Is there a command or series of commands I can run from the Terminal that would help diagnose the EXACT problem(s)?Sort of. You obviously have a network connection now and I'm guessing you're using Windows so:[LIST]
[*]Start
[*]Run
[*]CMD [RETURN]
[*]C:\Documents and Settings\[user]> ping [www.bbc.co.uk](www.bbc.co.uk)
[/LIST]This will return```

Pinging www.bbc.net.uk [212.58.224.114] with 32 bytes of data:

Reply from 212.58.224.114: bytes=32 time=10ms TTL=245
Reply from 212.58.224.114: bytes=32 time=6ms TTL=245
Reply from 212.58.224.114: bytes=32 time=4ms TTL=245
Reply from 212.58.224.114: bytes=32 time=8ms TTL=245

Ping statistics for 212.58.224.114:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 4ms, Maximum = 10ms, Average = 7ms
```
When you're back home open a terminal and proceed as follows:[LIST=1]
[*]ping 127.0.0.1
[*]ping 192.168.1.1
[*]ping 212.58.224.114
[*]ping [www.bbc.co.uk](www.bbc.co.uk)
[/LIST]If it fails at:[LIST=1]
[*]Your network card isn't working correctly
[*]You aren't connected to the router
[*]Your router isn't connected to the internet
[*]You don't have DNS servers set, which may be down to you or your ISP
[/LIST]Repeat this on the other machine and you'll see where the broken link in either chain is.

---

### Post by shaunuel on 2007-01-24
Hi, 
I'm still troubleshooting and trying some different approaches and 3rd party config wizards, etc. But I had another question: When I "try" and run through the router, my system lags TERRIBLY. It takes forever for the OS to load, programs take 10 times as long to load, etc. Any idea as to what is causing this? 

Thanks again :)

---

### Post by scrooge_74 on 2007-01-24
Do you mean opening web pages? If that is so then you can give your DNS ips directly to your PCs to speed things up

---

### Post by shaunuel on 2007-01-24
scrooge_74, no, I mean ALL programs and system functions are sluggish. Boot-up is slow as hell, opening ANY program takes forever, etc. This ONLY happens however when I proceed to hook up the router and try to get this shared internet/network going. Any ideas? 

AlanRogers, I don't have a network connection on my Ubuntu machine, yet. Thats what I'm trying to accomplish. The WinXP laptop can find and connect to the router the second its powered up, but has no connectivity/signal (Packets Sent: 0).

Thanks so much for your help guys :)

---

### Post by scrooge_74 on 2007-01-24
i am still confuse, which machine is slow now, the Ubuntu or the XP?

The XP can detect a network but can't get online? If that is so then definetly the router needs further config, check the manual again.

---

### Post by AlanRogers on 2007-01-25
> **shaunuel said:**
> It takes forever for the OS to load, programs take 10 times as long to load, etc. Any idea as to what is causing this?This sounds like traffic confusion on the network and, yes, you do have a network. Two computers connected to a router is a network, albeit a small one.

What I suggest you do is this:[LIST]
[*]Turn the router off - does the problem go away?
[*]If so, turn the modem off and the router on - still no issues?
[*]If so, you need to follow Step 3 in my post below - the router and the modem either have the same IP address or aren't on the same subnet
[/LIST]You haven't posted back the results of what I suggested. Without that, I can't really offer any further assistance - I'd be guessing, not helping.

---

