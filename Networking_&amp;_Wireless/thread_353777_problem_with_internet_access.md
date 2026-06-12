---
title: "problem with internet access"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by cpehrson on 2007-02-05
Hello,
I just installed 6.10 on my toshiba laptop and everything is working nicely except internet.

I am connected via the onboard ethernet card to my router, with DHCP enabled by default.
I can access the routers' admin page and I can even ping external websites, but trying to access them via Firefox times out. (disabling DHCP and using a static IP address causes all the above to fail instantly)
I also get time outs when trying to download emails.

Any ideas would be greatly appreciated.

---

### Post by kingmonkey on 2007-02-05
Can you resolve domain names?

---

### Post by cpehrson on 2007-02-05
Hi,
No, only IP addresses.
I tried checking the DNS server details and manually setting them as per my router settings, although I hoped that it would find that automatically if using DHCP (it gets an IP address ok).
I intend to use it from at least 2 different locations, so would prefer not to reconfigure my network settings each time I move, but for now I'd settle for whatever I can get.

---

### Post by cpehrson on 2007-02-05
Hi Again,
I think my problem goes a bit deeper than just internet/network.
I just started up my laptop while connected to a different network and it wouldn't start up properly. ie. I got past the login screen, then just got the mouse pointer in a blank screen. It would only load properly if disconnected to the network.
I also noticed that when starting up in recovery mode, I was able to resolve domain names using wget and dig, but was unable to do this via a terminal after starting up fully and then connecting the network cable.
I also sometimes get errors upon startup about not being able to load certain applications like Nautilus, I assumed this was because I hadn't yet established internet access, bur perhaps its all related, as if the way the laptop is connected to a network has a profound impact on how it starts up.
BTW, I partitionned the disc and put XP on half of it so I could use the internet from there (where I'm typing this from) but I don't think thats relevant because I had the same behaviour when I put Ubuntu on the whole thing.
If anyone can offer any pearls of wisdom, I'd really appreciate it.
Cheers!

---

### Post by rahulthewall3000 on 2007-02-05
Hi!
I am facing the same problems. I have a dell latitude D520 and I reinstalled my ubuntu. Now, I realized that my internet just doesn't work. I have a dual boot system and my internet works fine on windows but for some strange reason it doesn't work in Ubuntu. The internet connection doesn't even work with the live CD and that is surprising because it worked previously with the Live CD perfectly.
The internet connection that I have is a LAN connection and I am at a university so there is a common LAN connection. Can someone out their suggest as to why my internet connection is not working now with Ubuntu as it was working previously. Please help, I don't want to use the net on Windows.

Many thanks in advance
Rahul Jain

---

### Post by cpehrson on 2007-02-06
Hi There,
I managed to get mine working with a little tweaking...

Firstly, I found that I couldn't start Ubuntu if connected to the network, I could log in but then I just got a blank screen.

When running in recovery mode, I could use [FONT="Courier New"]wget -p [http://slashdot.org](http://slashdot.org)
[/FONT] and it resolved the IP address with no problem. I noted that the server 192.168.0.6 (I assume it means DNS server) was different to my routers address, and different to the one provided by my ISP.  I did think it might be telling me my own IP address, but thats 192.168.0.8 currently.

I can connect by doing the following:

1. start up Ubuntu making sure the network cable is unplugged.
2. plug in network cable
3. run [FONT="Courier New"]sudo dhclient[/FONT]

If I then look at the network interface via the GUI, I notice that under DNS servers, it has the routers address of 192.168.0.1 as well as the previously noted 192.168.0.6

Hope this helps anyone else with similar problems. I'd be interested to hear any explanation as to why I get this behaviour.
Cheers,
Chris.

---

### Post by kingmonkey on 2007-02-06
192.168.0.6 is a internal network address,

Do you run your own DNS server?

I would double check the settings you have put on your router.

Also paste the output of ifconfig here.

---

### Post by cpehrson on 2007-02-06
Hi,
I'm not actually using my own network, I'm at my mothers house, so I'm not sure how its set up (although she does have several PCs and a Mac all connected ok)
I'll be home tomorrow so will check my router settings, although I think all looks ok, the router is configured to point to a DNS server as specified by my ISP.

Heres my ifconfig output

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:B5:B5:00  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:feb5:b500/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113701 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24467821 (23.3 MiB)  TX bytes:15990101 (15.2 MiB)
          Interrupt:201 Base address:0x2000 


Thanks for you help!

---

### Post by ajag22 on 2007-02-06
Hi,
I had the issue where I could see my router 169.254.1.1 and ping external sites but not resolve names. Found my router was set as DNS server so I just added the BT external DNS servers under network settings and the web is working now. Hope this helps some people. 
Guess it will affect those with routers to connect to the internet and Ubuntu sees and sets the router as the only DNS.

Thanks,
Adam.

---

