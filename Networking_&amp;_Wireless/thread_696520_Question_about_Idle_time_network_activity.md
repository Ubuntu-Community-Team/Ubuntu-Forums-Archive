---
title: "Question about Idle time network activity"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by blueturtl on 2008-02-14
One day out of curiosity I opened the System Monitor. The network history graph shows that I'm constantly receiving data at a rate of 600 bits - 3 KB per second. I turned off all applications that might be using bandwidth but the transfer rate has not changed. After starting my system today I thought I'd check again and sure enough the same thing continues. I checked my wife's laptop to see if it does the same thing and it does not. Received data on the laptop is at a total of 5.7 KB and the receive rate is flatlining at 0 bytes/s.

I did a ```
sudo netstat -platu
``` which on my system returns:
> Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp         0      0         localhost:mysql         *:*                     LISTEN     6528/mysqld         
tcp         0      0         localhost:ipp             *:*                     LISTEN     6674/cupsd          
udp        0      0         *:32778                    *:*                                    6628/avahi-daemon:  
udp        0      0         *:bootpc                   *:*                                    4996/dhclient3      
udp        0      0         *:mdns                     *:*                                   6628/avahi-daemon:  

I one by one turned off each service until I came to dhclient3. The data receiving continues. Curiously my wife's laptop has even more active connections (like portmap and rpc.statd) but still on her system there is no constant flow of data.

The actual question is, why is my system constantly receiving data and how do I find out who/what is the recipient?

---

### Post by blueturtl on 2008-02-18
Bump. Anyone?

---

### Post by walmartshopper67 on 2008-02-22
Well, it's been awhile since my Cisco training, but lemme take a stab at it. First though - are you on a broadband or LAN connection? Is it wireless? and do you and your wife connect through a router and share a connection? All networks have a certain level of overhead - determining any differences in connection between your computer and wifes laptop is key. I'm not sure, and i'm sure one of the good people here will correct me - but the traffic rates you described don't seem unreasonable for overhead. It could just be normal, but again I'd need to know how the computers are networked to be sure.

That being said, if you're really curious (which is great - that's how I learn pretty much everything), you can run the Wireshark application (it's in the repositories) to see exactly what they are, and post anything interesting that you're curious about and if I can I'll try to explain what it might be (be careful if you're computer is hooked directly to the internet - right to the broadband/DSL router. If it is, make sure it's not running the network card in "promiscuous mode", (basically showing you all the packets on the network, instead of the way they usually work, only showing packets meant for your computer), a lot of internet service providers are touchy about that, and while you'd *probably* be ok, i'd hate to see you get into any kind of beef with them without knowing about it. 

Have fun:cool:

---

### Post by blueturtl on 2008-03-13
I have a wireless xDSL router that connects to the internet. The web connection is shared to the PCs in NAT mode. Both computers connect to the router wirelessly so basically we're in the same situation. We both run Ubuntu Gutsy at this time of writing, so the only major difference I suppose is the wireless interface in both machines.

For both, I had to manually compile and install serialmonkey drivers as the support for Ralink chips in Gutsy is still lacking. I have a manual connection and my wife uses the rtutil to connect to wireless LANs. She has a RT2500 series and I have an RT61.

I installed wireshark and ran it after turning off all things that might be using the network connection. I ran it side by side with system monitor and to my surprise...

Wireshark reports no packets whatsoever. None, zip, nada. All the while System Monitor is showing constant 1 kb/s activity.

So I guess this must overhead like you were saying.:-k

How do I know if the wireless card is operating in promiscuous mode?

Thanks for your input!

---

