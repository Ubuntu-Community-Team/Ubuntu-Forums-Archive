---
title: "network attack even when network cable is unplugged"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by hiteshchopra on 2007-04-15
i use ubuntu dapper 6.06 lts..now ive been having this strange problem that my networks being attacked even when its disconnected. i use firestarter as a firewall and its shows that am constantly attacked whether am connected or disconnected. usually when am connected all the bandwith is taken away by the attacks and am not able to open any site or use any messenger ..i am able ot utilize only 1% of the availabel network speed.. i shifted to windows ot check if its happening there too and the end result was da same..my network provider clearly stated that his networks running fine and it isnt from hsi network. i reinstalled my drivers again but no improvement..the more i restart my comp it gets wors.. 

below r lsited soem of the ips which keep on attacking at a regular interval(as of now its every 17 minutes..logged on or off)..and goes upto an attack every 1 second too...

Time: Apr 15 14:29:43 Source: 172.35.15.78 Destination: 133.100.11.8 In IF:  Out IF: eth0 Port: 123 Length: 76 ToS: 0x10 Protocol: UDP Service: NTP

Time: Apr 15 14:29:46 Source: 172.35.15.78 Destination: 193.62.22.98 In IF:  Out IF: eth0 Port: 123 Length: 76 ToS: 0x10 Protocol: UDP Service: NTP

Time: Apr 15 14:46:47 Source: 172.35.15.78 Destination: 133.100.11.8 In IF:  Out IF: eth0 Port: 123 Length: 76 ToS: 0x10 Protocol: UDP Service: NTP

Time: Apr 15 14:46:49 Source: 172.35.15.78 Destination: 193.62.22.98 In IF:  Out IF: eth0 Port: 123 Length: 76 ToS: 0x10 Protocol: UDP Service: NTP

ive used the firetstarter policy to block the above 2 ips.

other ips that have been craeting problems are

63.245.209.31
133.100.11.8
193.62.22.98
clock.tl.fukuoka.ac.jp
ntp2.ja.net


and there r many more like these..please help me out...can it be a hardware problem..can a virus reside on the lan card?

NEED URGENT HELP!!!

Thanks .

---

### Post by chili555 on 2007-04-15
This seems to be related to NTP or Network Time Protocol. Your computer tries to set the time by going out to network servers and synchronizing the computers time to the remote server. Your install may be corrupted in some way. 

Notice the protocol is NTP and the activity is outgoing.

To test this, and I certainly may be wrong, I would completely remove ntp and ntpdate in Synaptic. After that, see if the problem remains.

---

### Post by hiteshchopra on 2007-04-15
hmm i had actually put it as a outbound policy in the firestarter firewall to restrict access...will try making sense of wad uve suggested..

---

### Post by hiteshchopra on 2007-04-20
theres a new error coming up on starting  "ipv6.ip_forward  error unknown key"

---

### Post by GTvulse on 2007-04-20
> **hiteshchopra said:**
> i use ubuntu dapper 6.06 lts..now ive been having this strange problem that my networks being attacked even when its disconnected. i use firestarter as a firewall and its shows that am constantly attacked whether am connected or disconnected. usually when am connected all the bandwith is taken away by the attacks and am not able to open any site or use any messenger ..i am able ot utilize only 1% of the availabel network speed.. i 

[snip]

NEED URGENT HELP!!!

Thanks .

You  are **not** under attack. What you see is the automatic internet time clock synchronization that happens every time a network interface goes up, that you have unwisely blocked by using Firestarter, as well who knows how many other outbound ports. 

You can disable this network time synchronization by opening a terminal window and typing "[FONT=Courier New]sudo chmod 644 /etc/network/if-up.d/ntpdate[/FONT]". 

But to be frank, you would be far better served by removing Firestarter and learning to live without a kitchen-sink firewall until you learn how to use it properly; a firewall is something you use in the perimeter of your LAN, namely your router, not on every client machine (unless you use MS Windows, that is). The default networking configuration in Ubuntu is safer than in most Linux distributions and thousands of times safer than that of an MS Windows system out of the box. You know, networking applications in your machine need to talk to the world out there.

Besides, the Linux firewall system called iptables, of which Firestarter is merely a graphical frontend, is incredibly powerful but it is not an Intrusion Detection System (IDS) as you apparently presume. Assuming that Linux works and behaves like Windows is the same as thinking that one cannot drive a Space Shuttle because it doesn't have a stick-shift; on the other hand, it is important to understand the principles of computer security, as well as being aware that implementations are different. One cannot speak Japanese as if it were English.

---

### Post by hiteshchopra on 2007-04-23
dude i wasnt able to open any site if i hadnt done that!!! ive formatted my system and installed the latest version of ubuntu but the problem doesnt seem to go!!!

---

