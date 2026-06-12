---
title: "Transmission bittorrent fails with &quot;Tracker hasn't responded yet. Retrying...&quot;"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by mdecler2 on 2009-12-15
I am an absolute beginner with bittorrent'ing.

I am getting the following message continuously in the Transmission bittorrent client: "Tracker hasn't responded yet. Retrying..."

I have ports 6881-6889 open for TCP on my firewall NAT router. My iptables are blank. I have google searched "transmission bittorrent tracker hasn't responded yet" and got an interesting thread: 

[http://www.google.com/url?sa=t&source=web&ct=res&cd=5&ved=0CBUQFjAE&url=http%3A%2F%2Fforums.avistaz.com%2Findex.php%3Fshowtopic%3D9580&rct=j&q=transmission+bittorrent+tracker+hasn't+responded+yet&ei=t-AnS7u1JoqINKen2YgM&usg=AFQjCNHohYw5yGsS-BjxzpFewicHYgI4pw](http://www.google.com/url?sa=t&source=web&ct=res&cd=5&ved=0CBUQFjAE&url=http%3A%2F%2Fforums.avistaz.com%2Findex.php%3Fshowtopic%3D9580&rct=j&q=transmission+bittorrent+tracker+hasn't+responded+yet&ei=t-AnS7u1JoqINKen2YgM&usg=AFQjCNHohYw5yGsS-BjxzpFewicHYgI4pw)

Can someone confirm an error in Transmission version 1.06 with the "scrape" functionality (I have no idea what that is, so maybe you could enlighten me)?

---

### Post by mikewhatever on 2009-12-15
Tracker hasn't responded means just what it says, and has nothing to do with transmission. The tracker you are trying to connect to may be down for example.

---

### Post by mdecler2 on 2009-12-15
> **mikewhatever said:**
> Tracker hasn't responded means just what it says, and has nothing to do with transmission. The tracker you are trying to connect to may be down for example.

So I understand "tracker" to be the bittorrent server for handling peer communication: [http://en.wikipedia.org/wiki/BitTorrent_tracker](http://en.wikipedia.org/wiki/BitTorrent_tracker)

Could it not be possible that something is hindering the tracker's responses? Like the http proxy I just setup?

The torrent is: [http://cdimage.debian.org/debian-cd/5.0.3/i386/bt-dvd/](http://cdimage.debian.org/debian-cd/5.0.3/i386/bt-dvd/). If you can confirm that the Debian Lenny DVD torrents are not down, please do so.

---

### Post by ankspo71 on 2009-12-15
Hi,

The first file on the link you provided "debian-503-i386-dvd-1.iso.torrent" is not down as I type this. I am able to connect and start downloading using Transmission. I also have "require encryption" set, and the blocklist enabled. Can you set Transmission to use a direct connection? I don't use a proxy so... that might be the reason why you can't start the download... unless maybe where you are at is harder to connect at the moment.... which means having to wait a while

---

### Post by oldgeekster on 2009-12-15
> **mdecler2 said:**
> So I understand "tracker" to be the bittorrent server for handling peer communication: [http://en.wikipedia.org/wiki/BitTorrent_tracker](http://en.wikipedia.org/wiki/BitTorrent_tracker)

Could it not be possible that something is hindering the tracker's responses? Like the http proxy I just setup?

The torrent is: [http://cdimage.debian.org/debian-cd/5.0.3/i386/bt-dvd/](http://cdimage.debian.org/debian-cd/5.0.3/i386/bt-dvd/). If you can confirm that the Debian Lenny DVD torrents are not down, please do so.Just as a test I started downloading the update file at the bottom of the list on the link you provided - it worked, (although it did seem a bit slow).  After a few minutes watching it progress, I canceled the request and deleted the files.  Hope this helps.

---

### Post by mdecler2 on 2009-12-15
> **ankspo71 said:**
> Hi,

I also have "require encryption" set, and the blocklist enabled. Can you set Transmission to use a direct connection? I don't use a proxy so... that might be the reason why you can't start the download... unless maybe where you are at is harder to connect at the moment.... which means having to wait a while

What client are you using? Perhaps I need to try another client?

I have no "direct connection" option. One thing I noticed in the preferences though "Automatically map port" is checked, and the port is 51413, which doesn't make sense to me. I have opened this port for TCP on the firewall NAT...same error about the tracker.

---

### Post by mdecler2 on 2009-12-15
The proxy I am using is called squid. I won't post the configuration file here, it is too big. The http_port is set to the default 3128.

But is a torrent an HTTP connection? I thought it wasn't.

Here is a screenshot with the "Automatically map port" box checked. Ther is an indicator that "port is closed" even though I have it open on the firewall NAT router.

---

### Post by t0p on 2009-12-15
When ankspo71 said use a direct connection, he meant don't use a proxy.  Is it absolutely necessary for you to use a proxy?  Are you absolutely sure that the proxy allows bittorrent traffic?

There's certainly nothing wrong with transmission as a program.  And the fact other forum members can download the torrent in question makes me think the proxy is the problem.

---

### Post by ankspo71 on 2009-12-15
> **t0p said:**
> When ankspo71 said use a direct connection, he meant don't use a proxy.

Yes, that's exactly what I meant. ;) Disable any proxy settings that you have made  and see if it works. Is there a reason for using a proxy to download Debian?

---

### Post by mdecler2 on 2009-12-15
You two are absolutely right. I don't need the proxy to download Debian.

The reason why I just set it up was for a DansGuardian configuration with the Firefox web browser (the configuration isn't transparent, which explains blank iptables).

In any case, I just shut down squid and DG, and unconfigured Firefox to use no proxy.

I still have the same error, "Tracker hasn't responded yet. Retrying..."

I have changed the port in Transmissions preferences to 6881, still says that "port is closed" after a testing cycle.

---

### Post by mdecler2 on 2009-12-15
Does Bittorrent protocol use TCP and UDP sockets? I was told that it only uses TCP, which might eplain why these ports are being detected as closed. I only have the firewall ports open on the router for TCP connections...

---

### Post by t0p on 2009-12-15
> **mdecler2 said:**
> You two are absolutely right. I don't need the proxy to download Debian.

The reason why I just set it up was for a DansGuardian configuration with the Firefox web browser (the configuration isn't transparent, which explains blank iptables).

In any case, I just shut down squid and DG, and unconfigured Firefox to use no proxy.

I still have the same error, "Tracker hasn't responded yet. Retrying..."

I have changed the port in Transmissions preferences to 6881, still says that "port is closed" after a testing cycle.

That error message doesn't always mean the torrent isn't going to work.  I use transmission, and sometimes I get that message; I wait, and eventually the message goes away and it downloads.

I would also recommend you try downloading something else.  That way you might be able to ascertain whether the problem lies with your machine or some other network problem.

Finally, I wouldn't worry too much about that "port is closed" message.  I get that, even as transmission is downloading.  I think there's some kind of bug in there, though I haven't a clue about the inner workings of bittorrent.  All I know is that message doesn't mean much.

---

### Post by mdecler2 on 2009-12-15
> **t0p said:**
> That error message doesn't always mean the torrent isn't going to work.  I use transmission, and sometimes I get that message; I wait, and eventually the message goes away and it downloads.

I would also recommend you try downloading something else.  That way you might be able to ascertain whether the problem lies with your machine or some other network problem.

Finally, I wouldn't worry too much about that "port is closed" message.  I get that, even as transmission is downloading.  I think there's some kind of bug in there, though I haven't a clue about the inner workings of bittorrent.  All I know is that message doesn't mean much.

Well, nmapping my router shows that 6881-6889 are NOT open. Which explains the closed message. There seems to have been at least one other person with a Bittorrent issue and the router that I use. I will be working on the router, because those ports _should_ be open.

---

### Post by lovinglinux on 2009-12-15
See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by mdecler2 on 2009-12-15
The verdict on Motorola SBG900 wireless router:
"This router consistently fails while using Bittorrent wirelessly. If you plan on using bittorrent, it is strongly recommended you get the wired based modem from Telstra and connect your own third party router.

However, if you need to use bittorrent, you can use the single ethernet port on the back of the router which will work reliably." 

[http://bc.whirlpool.net.au/bc/hardware/?action=h_view&model_id=181](http://bc.whirlpool.net.au/bc/hardware/?action=h_view&model_id=181)

According to the following forum, guess what? I can DISABLE THE FIREWALL to make bittorrents work over wireless: [http://www.ibece.org/archives/2006/01/23-motorola-sbg900-and-bittorrent](http://www.ibece.org/archives/2006/01/23-motorola-sbg900-and-bittorrent)

How is that for security? No. I refuse.

Thanks for the help y'all! I'll have to stick with HTTP for now. I consider this solved.

---

### Post by mdecler2 on 2009-12-15
> **lovinglinux said:**
> See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

Hey, this is a great resource! Thanks for the link!

---

### Post by mikewhatever on 2009-12-15
The link you posted does not suggest disabling the firewall. The guy talks about lowering the number of global connections, which is reasonable, since home routers aren't really expected to handle very heavy loads. Your problem, however, was of a different nature, namely, closed ports. There is no need to open a range of ports,such as 6881-6889, one is enough, but it has to be the port your bittorrent client is set to use, 51413 in your case. To test the port, use ShieldsUp from grc.com.

---

### Post by mdecler2 on 2009-12-15
> **mikewhatever said:**
>  but it has to be the port your bittorrent client is set to use, 51413 in your case. 

Yes, I changed the incoming port in Transmission to the ports I had opened in the firewall with no change. I also tried using a different client rtorrent, with the same basic problem: connection timeout.

The issue is exactly opening the ports. And none of the ports I do open appear to be open, so I am left confused.

---

### Post by mdecler2 on 2009-12-15
> **mikewhatever said:**
>  To test the port, use ShieldsUp from grc.com.

Are you serious? Are you recommending that I buy software to check if ports are open? How about ```
nmap 192.168.0.1 -p 6881-6889
```

---

### Post by lovinglinux on 2009-12-15
> **mdecler2 said:**
> Yes, I changed the incoming port in Transmission to the ports I had opened in the firewall with no change. I also tried using a different client rtorrent, with the same basic problem: connection timeout.

The issue is exactly opening the ports. And none of the ports I do open appear to be open, so I am left confused.

It seems, as already suggested, that you have a tracker issue. Opening the BitTorrent port has nothing to do with the error you are getting from the tracker, since it is an outgoing connection, which is not affected by the opened ports in the client or the router. The firewall only affects it if you do not allow outgoing connections on the tracker port, which is not the same as the torrent port. Most firewall managers in Ubuntu would allow any outgoing connections by default and if you can browse the web, then you probably can connect to the tracker, since most of them use port 80. Nevertheless, check the tracker address to see if it uses other port, like 6969.

---

### Post by mikewhatever on 2009-12-15
ShieldsUp is a free service, possibly a little obstructed by commercial advertisements on the same web site. That's nothing unusual, at least if we use the same internet. I am no expert with nmap, but aren't you testing the outgoing connection this way, instead of incoming?
On the second thought, is your ISP known for blocking bittorrent traffic?

---

### Post by mdecler2 on 2009-12-15
> **lovinglinux said:**
> It seems, as already suggested, that you have a tracker issue. Opening the BitTorrent port has nothing to do with the error you are getting from the tracker, since it is an outgoing connection, which is not affected by the opened ports in the client or the router. The firewall only affects it if you do not allow outgoing connections on the tracker port, which is not the same as the torrent port. Most firewall managers in Ubuntu would allow any outgoing connections by default and if you can browse the web, then you probably can connect to the tracker, since most of them use port 80. Nevertheless, check the tracker address to see if it uses other port, like 6969.

```
[View: main]
   debian-503-i386-DVD-2.iso
               0.0 / 4464.7 MB Rate:   0.0 /   0.0 KB Uploaded:     0.0 MB [ 0%] --d --:-- [   R: 0.00]
  Tracker[0:0]: Connecting to http://bttracker.debian.org:6969/announce

```

It is 6969. So are you saying that I have to have port 6969 open as well? How would I have known that in advance?

---

### Post by mdecler2 on 2009-12-15
> **mikewhatever said:**
> ShieldsUp is a free service, possibly a little obstructed by commercial advertisements on the same web site. That's nothing unusual, at least if we use the same internet. I am no expert with nmap, but aren't you testing the outgoing connection this way, instead of incoming?
On the second thought, is your ISP known for blocking bittorrent traffic?

You are right, nmap only checks from the inside. I have opened those ports on both inbound and outbound traffic, so they should register as open from the inside, but they don't.

My ISP is known to be suspicious. It is Comcastic(TM)! My uncle has had large bittorrents open (much bigger than 4GB) over night and has had his traffic shutoff by Comcast. What I am doing here is completely legal, but I suppose the ISP can still shut me off if they'd like. But then I will switch to AT&T :)

---

### Post by mdecler2 on 2009-12-15
Having port 6969 open did not help.  I think I have to shut off DHCP in order to port forward, and I can't do that without p0wning other DHCP leases.

---

### Post by lovinglinux on 2009-12-15
> **mdecler2 said:**
> It is 6969. So are you saying that I have to have port 6969 open as well? How would I have known that in advance?

You don't have to open the port on the router, but you must allow OUTGOING connections on that port in the firewall.

To know in advance you need to check each torrent address. If it uses a port other than 80, the port will be included in the address. Nevertheless, most trackers I know use port 80 or 6969.

The easiest method is in fact to allow ALL OUTGOING connections on ALL ports in the firewall, since you will be connecting to hundreds of peers and each peer will have a different incoming port. If you block OUTGOING connections on the firewall, then you won't connect to most of the peers and it's unfeasible to manually allow each destination port.

I suggest you read my tutorial, since it explains how BitTorrent works, why ports need to be opened, how the tracker interacts with your client and what are the possible culprits of slow connections and connection errors.

---

