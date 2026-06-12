---
title: "BitTorrent: Download/Upload Speed: 0 B/s"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by RyanPower on 2006-11-24
I started using Ubuntu (Breezy Badger) a few weeks ago so I'm *fairly* new to it all, but there's one thing I keep having to go to my XP partition and that's using BitTorrent.

Any BitTorrent clients I use in Ubuntu always have a download and upload speed of 0 B/s, whereas on a well seeded torrent on XP I can reach ~200 kB/s. The clients I've tried are the default "BitTorrent," "KTorrent" and "Azureus".

I've tried investigating into Firestarter, but it doesn't seem to help much apart from telling me that a lot of events are happening every second from the Service "BitTorrent".

I tried searching before posting this, and somebody was asked to give the output from the following code in the Terminal:

```
sudo iptables -L
```

Here it is when Firestarter *is* running:

```
Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.2.1          anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  192.168.2.1          anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             192.168.2.255
DROP       all  --  base-address.mcast.net/8  anywhere
DROP       all  --  anywhere             base-address.mcast.net/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.2.13         192.168.2.1         tcp dpt:domain
ACCEPT     udp  --  192.168.2.13         192.168.2.1         udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  base-address.mcast.net/8  anywhere
DROP       all  --  anywhere             base-address.mcast.net/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'
```

And here it is when it *isn't* running:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Strangely, the clients can display how many seeders and peers there are from the tracker but not downloading anything, not even a very very slow speed, but 0 B/s.

This would be something I might've had to begrudgingly go to XP to do, but it's recently Blue Screened me from booting it!

Anyways, thanks, I hope I gave as much information as I could!

---

### Post by FrodoB on 2006-11-24
Do you have a torrent that some of us can test download?

---

### Post by RyanPower on 2006-11-24
Sure, it was the [3rd episode of Death Note](http://www.torrentspy.com/torrent/888977/Live_evil_Death_Note_03_82DA4482_avi) ([.torrent link](http://www.torrentspy.com/download.asp?id=888977)).

I had in fact managed to download the whole thing a few hours earlier, but like I said, XP Blue Screened so I was trying to download it again on my Ubuntu partition.

---

### Post by FrodoB on 2006-11-24
Work like a champ on Edgy Eft through a Linksys DSL router, comes down at my full DSL speed immediately.

---

### Post by RyanPower on 2006-11-24
Oh yeah that reminds me, I'm confident my router's (Belkin) configured correctly as far as port forwarding is concerned.

Do you know what could be the problem for me?

---

### Post by FrodoB on 2006-11-24
No idea, the port forwarding was the only issue I have ever had, but you said that XP worked fine, so I discounted that.

You don't have another firewall setup on Ubuntu do you?

I would surely make sure that I went to a command prompt and gave it an:

sudo iptables -F

to flush all firewall stuff just in case before I even browsed to the web site to start the torrent.

---

### Post by PurplePenguin on 2006-11-24
I'd try disabling the firewall to make sure that's what's causing the problem.  But that's just because I'm not smart enough to read logs and understand them. :)

---

### Post by kragen on 2006-11-24
I have the same problem - I've only really tried azurus - it works in windows, doesnt in linux. The weird thing is that for the downloads I started in windows, it starts off normally, then falls to 0 Kb/s after a while.

All the pretty green lights to show that firewall settings are ok are all on, and I cant figure out what else it might be. I'm using Azureus 2.5

I really need to get this working :( Any suggestions on how to solve / diagnose the problem would be greatly appreciated.

---

### Post by trubblemaker on 2006-11-24
yeah I'm going to have to side with frodoB.  Not all port settings are the same for torrent software, they decide on different ports.  You should try and find docuementation on your favorite one and double check the port forwarding.  the only thing a miss is that usually you'll still get 1kb/sec even with no forwarding.  but that might be answered by some ports being blocked under some mystic number unless you run as root.  try running the <torrent-software> as root and see if you get like 1kb/sec. if that works then I'd say it is portforwarding and you need to change some routing.

---

### Post by kragen on 2006-11-24
Well, now its changed - I have two downloads - one (which I started a while ago) is chugging along at 5-ish Kb/s, the other is doing nothing, but despite the fact that none of the settings involved have changed, the little red lights telling me that i'm firewalled and DHT firewalled have come on.

Just tried running it with sudo on - it works fine 100% - all the lights are on, and its downloading (for the moment)

Whats up with that?

---

### Post by trubblemaker on 2006-11-24
yeah there is a port thing 0 ~ 6000 or something that only root can use.  So you need to setup your ports, in the bittorrent settings or some other way, 

don't know howto fix that but atleast you have more search terms for google or this forum now.

---

### Post by FrodoB on 2006-11-25
> **kragen said:**
> Well, now its changed - I have two downloads - one (which I started a while ago) is chugging along at 5-ish Kb/s, the other is doing nothing, but despite the fact that none of the settings involved have changed, the little red lights telling me that i'm firewalled and DHT firewalled have come on.

Just tried running it with sudo on - it works fine 100% - all the lights are on, and its downloading (for the moment)

Whats up with that?

What is your client's name? Is is included in Ubuntu or is it one you installed seperately?

---

### Post by kragen on 2006-11-25
Its Azureus, and after having left it overnight, i've returned to a 0 upload 0 download.

It seems to be incredibly tempremental - I cant work out if its been sitting here doing nothing for the whole 11 hours, or if it's been downloading normally and then stopping for a while, downloading and then stopping...

---

### Post by kragen on 2006-11-25
> **trubblemaker said:**
> yeah there is a port thing 0 ~ 6000 or something that only root can use.  So you need to setup your ports, in the bittorrent settings or some other way, 

don't know howto fix that but atleast you have more search terms for google or this forum now.

I'm using a port in the 50,100 - 50,200 range.

---

### Post by GTvulse on 2006-11-25
RyanPower and kragen,

you both need to forward ports from your DSL modem/router, because **you are behind a [NAT]("http://en.wikipedia.org/wiki/Network_address_translation") router**, which btw is already acting as an excellent hardware firewall, no need to play with iptables nor any of its graphical interfaces such as Firestarter, **unless you really need it** and believe me, if you don't know you need it, you don't.

On how to forward ports, please see the entries pertaining your DSL boxes (or similar models made by the manufacturer) at [PortForward.com]("http://www.portforward.com/").

---

### Post by kragen on 2006-11-25
For the sake of the argument, can you just take my word for it that I did that and it still doesnt work? 

I can cope with setting a router up - unless there is something different that linux does and windows doesnt (something that fools azureus into thinking I'm connected properly as well), its not going to be my router.

I've just booted windows back up again, and everything seems to be fine for the moment.

One thing that I have noticed is that in linux azureus is really slow, and while checking torrents the whole computer becomes unusable - I have a core 2 duo, surely it's not meant to do that?

---

### Post by trubblemaker on 2006-11-25
k I take your word that you port forwarded but, I want to underline that linux and windows don't use the same ports, this is probably redundant but still worth underlining, 

>  One thing that I have noticed is that in linux azureus is really slow, and while checking torrents the whole computer becomes unusable - I have a core 2 duo, surely it's not meant to do that? 
The slowness would also point to ports not being routed properly, but I'm still believing that you routed them properly. just saying it would be something I would consider.  

don't think it's permissions.

again going back to downloading 0kb, 
**if ** you hadn't forward the ports you'd only get one port opened for downloading, this one port would be to one computer an d if they had no new packages to send you then you'd get nothing, then if you connected again you'd get one computer that might only have one package to send you then stop.... and so on and so on.  

Please consider checking out the firewall settings and also thinking about dropping the firewall behind a router. if you don't forward the ports, they don't go to your computer and the firewall on your computer is a wall behind a wall, strong protection yes. Necessary ~ not really.

In fact, again believing you forwarded the ports the firewall on the computer would be a second wall that would stop the ports from being open.

---

### Post by kragen on 2006-11-25
Ok, what I did... I told my router's DHCP server to assign be a static IP address, I then set up a port in the 50,100 - 50,200 range to be forwarded to my IP addess (both TCP and UDP), I then told azureus what that port was and away I went.

The configuration is idential for both windows and linux. I think at some point I might have had to click on a "allow this program to connect to the net" button in windows at some point, but from the fact that its connecting at all I dont see how there can be a linux firewall blocking azureus - its a standard base ubuntu 6.10 install - how do I make **sure** there is no firewall?

---

### Post by kragen on 2006-11-25
Just booted back into linux and given rtorrent a try out - seems to be working fine for now.

---

### Post by phatzmb on 2006-12-02
this may have nothing to do with your problem, but just in case...

i just fixed a very irritating bittorrent problem i've been having for the last few days with azureus and ktorrent. my downloads and uploads were stalling - every 5 seconds. they went up to around 5-15kb/s, then back down to zero for a few seconds and so on. my ports were forwarded fine.

just now i tried turning of uPnP, which solved the problem immediately. i'm not sure exactly how uPnP works, but it would seem that while trying to open my ports it was ruining the port forwarding i already had. 

btw is it just me or is azureus STILL the only bittorrent client with decent port forwarding / nat traversal capabilities? every time i have bittorrent woes i try all these different clients, before being disappointed and coming back to azureus and realizing i was doing something wrong.

---

