---
title: "Trouble with Transmission/Pidgin"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by lilredcougar07 on 2009-10-05
Hey everyone. I'm think I'm having a little trouble with my ports. I am trying to download on transmission and it's saying "Downloading from 0 of 0 connected peers." There are over 3000 seeders and 700 leechers. I don't know how I could not be connected to any of them. My transmission has worked up until today. I am also trying to use Pidgin, but it will not connect either. Again, it's been working fine until today. In Transmission, I've tried switching to other ports, but every one I've checked has been closed. I don't know what to do. I'd really appreciate the help. Thanks!

---

### Post by ankspo71 on 2009-10-05
Hi,
51413 is open, says my transmission.
If you got your .torrent file from PirateBay, the site no longer works for me, and I never get any connections with them as a tracker anymore.

As far as your ports being closed and you not being able to make connections, I wouldn't know what to do. Your torrent problem might be a tracker problem though... especially if the tracker announce?? url is piratebay.

James

---

### Post by lilredcougar07 on 2009-10-05
Well, I tried that port and transmission says it's closed. The tracker is not from piratebay. I've tried restarting my computer, resetting my connection, and trying to connect to different torrents. I have no idea why pidgin isn't working. I'm really confused as this has never happened to me before. I did install the updates today that my Update Manager notified me of. I don't remember what all it had updates for, but that is the only thing I can think of that I have done differently in the last 24 hrs. The updates have never done anything like this to my computer before though.

---

### Post by lovinglinux on 2009-10-05
See the Troubleshooting section of [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923). It will guide you though the necessary steps to find the culprit and solve your problem.

---

### Post by ankspo71 on 2009-10-05
Here is more info in regards to the firewall/security mentioned in the above link. [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by jward3010 on 2009-10-05
> **ankspo71 said:**
> Here is more info in regards to the firewall/security mentioned in the above link. [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
Yes, sounds firewally (if thats a correct word). Do you have access to the firewall or are you in a college, office what?

---

### Post by jward3010 on 2009-10-05
> **lilredcougar07 said:**
> Well, I tried that port and transmission says it's closed. The tracker is not from piratebay. I've tried restarting my computer, resetting my connection, and trying to connect to different torrents. I have no idea why pidgin isn't working. I'm really confused as this has never happened to me before. I did install the updates today that my Update Manager notified me of. I don't remember what all it had updates for, but that is the only thing I can think of that I have done differently in the last 24 hrs. The updates have never done anything like this to my computer before though.
You say you tried that port (51413) but did you open that port on your firewall? 

Please also note that the likes of piratebay and mininova have had their lists disrupted recently, I have no idea why (the law-suits undoubtedly or a massive server failure). Recently I searched for some stuff on mininova.org, found tons of results but not a seed or leech for any, as if it had cleared out its torrent lists or something. As lots of people know, both are being targetted for being shut down so don't expect a stable torrent service. Download an ubuntu torrent, which runs off its own tracker - [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.iso.torrent)

See how you get on with this one. If you're not getting anywhere with this either its a problem your end.

---

### Post by lilredcougar07 on 2009-10-05
As far as I know, I have never set up a firewall on my computer. I am currently at a student residence in Ireland with an ethernet connection, and like I said before today is the first day that I've not been able to download a torrent or use Pidgin. I've been living here for a month now. I got the torrent off of isohunt. I've checked my ports on canyouseeme and the site says it cannot.

---

### Post by jward3010 on 2009-10-05
> **lilredcougar07 said:**
> As far as I know, I have never set up a firewall on my computer. I am currently at a student residence in Ireland with an ethernet connection, and like I said before today is the first day that I've not been able to download a torrent or use Pidgin. I've been living here for a month now. I got the torrent off of isohunt. I've checked my ports on canyouseeme and the site says it cannot.
Ha, I'm writing this from South William Street in Dublin's fair city. I also am from Ireland. HA! How's the form fella!

This would be less likely a firewall issue on your machine and more so a firewall issue you have to battle against in your college, which college out of interest?

Colleges hate torrent and IM clients. They can use sizeable bandwith, torrent especially. They can be blocked easily enough because of the fact that they use ports to talk on. Maybe they enforced that this morning. Do the following, go to [www.whatismyip.com](www.whatismyip.com) and report the IP here.

---

### Post by lilredcougar07 on 2009-10-05
I'm not on campus though. I'm at a privately owned student accommodation, a flat which I've payed for the internet at. My ip is[SIZE=2] 
[/SIZE]**[FONT=Verdana][SIZE=2]79.97.146.46[/SIZE][/FONT]**


I go to NUIG, btw.

---

### Post by ankspo71 on 2009-10-05
Hi,

I am at home, but I use a router (with a built in firewall) to connect two computers together (to share the internet). The UFW firewall that comes with Ubuntu is disabled by default, and it is still disabled on my computer. It is a command line only utility to make rules for ubuntu's IP tables. IF for any reason you need to make a rule, it is there if you need it. I have never needed it to chat when I used to chat, and I don't need it now to use a torrent downloader (including seeding), but it might help you if your ports actually are being blocked.
James

---

### Post by jward3010 on 2009-10-05
> **lilredcougar07 said:**
> I'm not on campus though. I'm at a privately owned student accommodation, a flat which I've payed for the internet at. My ip is[SIZE=2] 
[/SIZE]**[FONT=Verdana][SIZE=2]79.97.146.46[/SIZE][/FONT]**


I go to NUIG, btw.
Gotta love Galway...

Change port numbers in the settings and see if it works. Change it to anything between 34000 and 62000, anything. It could be blocking dynamically as torrent clients make attempts to get out. So it might work for a while.

Also try T1 shopper's port scanner: [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by lilredcougar07 on 2009-10-05
I tried a few different ports and it didn't work. all of them were closed. I did the T1 shopper and this is what I got.

9.97.146.46 isn't responding on port 5965 ().
79.97.146.46 isn't responding on port 5966 ().
79.97.146.46 isn't responding on port 5967 ().
79.97.146.46 isn't responding on port 5968 (mppolicy-v5).
79.97.146.46 isn't responding on port 5969 (mppolicy-mgr).
79.97.146.46 isn't responding on port 5970 ().
79.97.146.46 isn't responding on port 5971 ().
79.97.146.46 isn't responding on port 5972 ().
79.97.146.46 isn't responding on port 5973 ().
79.97.146.46 isn't responding on port 5974 ().
79.97.146.46 isn't responding on port 5975 ().
79.97.146.46 isn't responding on port 5976 ().
79.97.146.46 isn't responding on port 5977 ().
79.97.146.46 isn't responding on port 5978 ().
79.97.146.46 isn't responding on port 5979 ().
79.97.146.46 isn't responding on port 5980 ().
79.97.146.46 isn't responding on port 5981 ().
79.97.146.46 isn't responding on port 5982 ().
79.97.146.46 isn't responding on port 5983 ().
79.97.146.46 isn't responding on port 5984 ().
79.97.146.46 isn't responding on port 5985 ().
79.97.146.46 isn't responding on port 5986 ().
79.97.146.46 isn't responding on port 5987 (wbem-rmi).
79.97.146.46 isn't responding on port 5988 (wbem-http).
79.97.146.46 isn't responding on port 5989 (wbem-https).
79.97.146.46 isn't responding on port 5990 (wbem-exp-https).
79.97.146.46 isn't responding on port 5991 (nuxsl).
79.97.146.46 isn't responding on port 5992 (consul-insight).
79.97.146.46 isn't responding on port 5993 ().
79.97.146.46 isn't responding on port 5994 ().
79.97.146.46 isn't responding on port 5995 ().
79.97.146.46 isn't responding on port 5996 ().
79.97.146.46 isn't responding on port 5997 ().
79.97.146.46 isn't responding on port 5998 ().
79.97.146.46 isn't responding on port 5999 (cvsup).
79.97.146.46 isn't responding on port 6000 (x11).

and so on for almost 300 ports.

---

### Post by lovinglinux on 2009-10-05
Opening ports has nothing to do with your problem, specially considering the torrent has more than 3000 seeders.

I think it's indeed a tracker issue, as already suggested. I know you said that the tracker used is not from the piratebay, but there are other trackers that go through the same network and in fact has the same IP number, just a different name. The Pirate Bay is unaccessible right now due to [pressure from an Anti-Piracy bureau](http://torrentfreak.com/brein-disconnects-the-pirate-bay-for-now-091005/). So I would try to download an Ubuntu torrent as already suggested and check if you can connect to any peers.

Nevertheless, I strongly recommend that you follow the troubleshooting questions from the tutorial [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923). It will guide you trough a series of questions to determine the problem and provide a solution. That tutorial will also help you understand what can and cannot cause connection and speed issues.

---

### Post by lilredcougar07 on 2009-10-05
I tried to do an Ubuntu torrent, and it did nothing, just like the others. Won't connect. None of my torrents are seeding either. I went through the troubleshooting guide. I got down to question 10 and it told me that it's the tracker. I've tried several different torrents, none of them have worked. I don't have a firewall running that I know of, unless the default firewall UFW is all of a sudden blocking the port.

---

### Post by lovinglinux on 2009-10-05
> **lilredcougar07 said:**
> I tried to do an Ubuntu torrent, and it did nothing, just like the others. Won't connect. None of my torrents are seeding either. I went through the troubleshooting guide. I got down to question 10 and it told me that it's the tracker. I've tried several different torrents, none of them have worked. I don't have a firewall running that I know of, unless the default firewall UFW is all of a sudden blocking the port.

UFW comes disabled by default. Besides, your problem is related to outgoing connections, not incoming. So opening the port used by Transmission won't solve the problem, because that port is used only for unrequested incoming connections. So a blocked port would only reduce the number of connected peers, but wouldn't prevent you from connecting to at least some of them. That's why this looks like a tracker issue, because you are not connecting to any peers, which is what happens when a tracker is down. Additionally, UFW does not block outgoing connections, so there is no reason for not being able to connect to any peers.

Nevertheless, please post the output of the command below, just to make sure:

```
sudo iptables -L
```

---

### Post by lilredcougar07 on 2009-10-05
Chain INPUT (policy ACCEPT)
target     prot opt source           destination

Chain FORWARD (policy ACCEPT)
target     prot opt source           destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source           destination

---

### Post by lovinglinux on 2009-10-05
> **lilredcougar07 said:**
> Chain INPUT (policy ACCEPT)
target     prot opt source           destination

Chain FORWARD (policy ACCEPT)
target     prot opt source           destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source           destination

So, as expected, you have no firewall rules preventing your connections, either incoming or outgoing. So, the problem must be the connection between your client and the tracker. 

Try to download [this torrent](http://releases.ubuntu.com/releases/9.10/ubuntu-9.10-beta-desktop-i386.iso.torrent) and tell me if the result is the same.

---

### Post by jward3010 on 2009-10-05
Like I said it's a controlled network. More than likely the administrators have got screamed at in the ear about slow speeds and are putting the crosshairs on torrents and IM, so they're filtering at the packet level now or they've blocked all ports out except 80. I know in UCD, everything goes through a proxy so little hope for a lot of communication. The next thing to try is an nmap of your network. First do the following:
```
route -n
```
In the third (possibly second line) under gateway column is your default gateway. Or you can right-click on network-manager icon > Connection Information and get your DG there.

Now, install nmap:
```
sudo apt-get install nmap
```

And then run:
```
nmap "default-gateway-IP"
```
Paste the output here.

Depending on what ports are open we'll be able to tell what type of access you have. This is a bit of a long shot but will most likely tell us something.

Just to be sure, you are using the residences internet, not your own DSL modem setup from an ISP?

---

### Post by jward3010 on 2009-10-05
> **lovinglinux said:**
> Try to download [this torrent](http://releases.ubuntu.com/releases/9.10/ubuntu-9.10-beta-desktop-i386.iso.torrent) and tell me if the result is the same.
I've already got him to do this with no luck, so definitely stronger blocking going on.

---

### Post by Enigmapond on 2009-10-05
This sounds like a Firewall problem. I had the same. Install Firestarter...this is an easy front-end application for the ufw firewall. Make sure that port 51413, (transmission default port) is open to everyone and do the same for 1024-2048. These last are what Pidgin uses. Also I would get rid of Transmission and use Deluge...this is a better client..IMHO:). Just be sure to set it's port, in options to 51413 to match the Firewall. UFW/iptables is standard in Ubuntu and if on, which I believe yours is, the default is to deny all incoming.

If you have a wireless connection...be sure to forward all the above ports in your router, as well.

Cheers!!

---

### Post by jward3010 on 2009-10-05
What was found out earlier is ufw is disabled and not having any effect.

---

### Post by lovinglinux on 2009-10-05
> **Enigmapond said:**
> This sounds like a Firewall problem.

No, it's not. His firewall is allowing all traffic, incoming and outgoing.


> **Enigmapond said:**
> Install Firestarter...this is an easy front-end application for the ufw firewall.

Firestarter is not a front-end for UFW, but for iptables. It just creates iptables rules for you. UFW does the same thing.

Firestarter is not recommended anymore.

> **Enigmapond said:**
> Make sure that port 51413, (transmission default port) is open to everyone 

The OP problem has nothing to do with opening ports. Opening ports only affects incoming unrequested connections from other peers, but you should still be able to request connections and actually connect to some peers, specially considering a big swarm like the one the OP is trying to join. Nevertheless, he can't connect to any peers, what suggest Trasmission is not even scraping the tracker.

> **Enigmapond said:**
> Also I would get rid of Transmission and use Deluge...this is a better client..IMHO:). 

At least we agree on something :)

> **Enigmapond said:**
> Just be sure to set it's port, in options to 51413 to match the Firewall.

While opening the port helps to connect to more peers and thus get better speeds, it does not prevent the client from requesting connecting and downloading from them. 

> **Enigmapond said:**
> UFW/iptables is standard in Ubuntu and if on, which I believe yours is, the default is to deny all incoming.

It is not on. The OP already posted the iptables rules and it's set to allow all traffic, incoming and outgoing.

---

### Post by lilredcougar07 on 2009-10-06
> Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-10-06 11:12 IST
Interesting ports on 192.168.1.1:
Not shown: 994 closed ports
PORT     STATE    SERVICE
22/tcp   open     ssh
53/tcp   open     domain
80/tcp   open     http
443/tcp  open     https
3128/tcp filtered squid-http
8888/tcp open     sun-answerbook

Nmap done: 1 IP address (1 host up) scanned in 1.45 secondsI am using my residence's internet. My Pidgin is working now for some reason...And I'm connected and downloading from 1 peer. I'm so confused.

---

### Post by jward3010 on 2009-10-06
I'm really surprised your residences gateaway has a 192.168.1.1 address, it's not incorrect just odd. What if they need to expand!

Maybe they messed up for a bit, like I usually say I'm surprised you're actually able to get torrent running in a large network - are you in a large residence or just a flat or what. I'm not asking this to be nosey but to understanf what kind of internet you might have.

---

### Post by lilredcougar07 on 2009-10-06
I live in a large residence, with many different flats. I'm going to talk to the office tomorrow and ask for the computer services guy to come and check. I don't know if it will help, but the guy seemed to like the fact that I used Ubuntu the first time he came to our flat, so hopefully he won't mind the fact that I'm downloading shows.

---

### Post by lilredcougar07 on 2009-10-08
Ok, so they said that they can't help me until the guy comes back next week. Is there anything else anyone can think of that may help me? I can't download any torrents, not only here at my accommodations but at my school as well, where I have done before but only very sparsely just to get like the last few pieces down.

---

### Post by lilredcougar07 on 2009-10-13
UPDATE: I want to thank you all for trying to help. I talked to the IT guy today. He has blocked all the incoming connections. So, programs like Transmission are not able to connect. He'll be adding Pidgin to the open ports as soon as he gets the time. No more downloading for this chick until she's back stateside. That's right. I'm a girl.

---

### Post by jward3010 on 2009-10-13
What, you're a girl! Uhhhhhh! I can't believe I talked to a girl!

Jokin'. I thought so (not in relation to you being a girl, in relation to the port blocking), colleges are getting strict on things like IM and torrent, well usually things other than port 80 (www) and 443 (https) are blank not allowed.

Slán abhaile!

---

