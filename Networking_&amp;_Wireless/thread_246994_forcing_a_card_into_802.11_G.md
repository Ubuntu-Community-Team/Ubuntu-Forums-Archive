---
title: "forcing a card into 802.11 G"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by maniacmusician on 2006-08-30
I have a Belkin 802.11b/g wireless PCI card.

I've installed the necessary drivers using ndiswrapper, and am reasonably happy with the performance. However, with iwlist scan, the output tells me that my "protocol" is IEEE 802.11b. Is there any way I can force it to use G instead, or will I have to live with B?

Also, when I do iwlist rate

```

6 available bit-rates :
          6 Mb/s
          9 Mb/s
          12 Mb/s
          18 Mb/s
          19.5 Mb/s
          500 kb/s
          Current Bit Rate=54 Mb/s
```

How can I get 54 Mb/s (which is the advertised speed of my card) when it's not technically available?

any help would be appreciated

thanks.

---

### Post by tturrisi on 2006-08-30
You could try setting thye bit rate using iwconfig:
iwconfig xthX rate 11M
IF your access point supports higher bit rates.
[http://www.linuxcommand.org/man_pages/iwconfig8.html](http://www.linuxcommand.org/man_pages/iwconfig8.html)

---

### Post by funchords on 2006-08-30
The output may be garbage.  What kind of download/upload speeds are you getting?

---

### Post by maniacmusician on 2006-08-31
> **funchords said:**
> The output may be garbage.  What kind of download/upload speeds are you getting?

i had somewhat suspected this, but dont know of a way to be sure. on a normal speed server, my downloads usually start out at about 350 KB/s (450 on faster ones) and drop to 250 kb/s within about 10 seconds of the download beginning. 

I'm fine with ^ that speed, I am more concerned about BitTorrent speeds. I've never been able to get download speeds as high as other people, even with an excellent client like Azureus. my upload speed in bittorrent is generally very poor as well (about 20-30 kb/s max). sadly, thats sometimes better than the download speeds are get. this is partly to torrents being badly seeded, but on the stats page, i see other people getting higher speeds than me all the time.  but i dunno, i figure even with http downloads, i should  be getting at least 500 kb/s (I have a 3 Mbit/s connection, i think).

---

### Post by tturrisi on 2006-08-31
> **maniacmusician said:**
> ...i should be getting at least 500 kb/s(I have a 3 Mbit/s connection, i think).
A 3 Megabit connection is approx 375 KiloBytes/sec download (maximum).  But having a 3Mb connection does not mean you will always get that rate, and is very unlikely on adsl, but on cable it is usually more consistant. As well, it depends on the server you download from.

You card, even at 11 Megabits/sec is NOT slowing down your Internet connection.  Your card is cabable of almost 4x your isp bandwidth cap. Downloads are slow because of either: (in no particular order)
1. packet loss
2. latency
3. actual connection rate
4. router-firewall-ap misconfigured
5. server bandwidth rate
6. routing between host & server.

---

### Post by maniacmusician on 2006-08-31
I see. I was gonna try upgrading my connection anyways, to at least 5 MBits/s. I'll take something better if i can get it. 

I always thought that bit torrent was slow for me due to the nature of the router, by which I mean that the router couldn't keep up with the number of incoming connections. I realize it can broadcast them fast enough, but maybe it just couldn't process them fast enough and because bit torrent requires a LARGE number of incoming connections, i suppose it makes sense it would be a bit slow. I want to try connecting directly to the cable modem to see if I get faster speeds, but thats not possible for me here. oh well. Thanks for your suggestions. I was just wondering why iwlist scan told me i was in 802.11B mode when I shouldve been G. But i guess thats not really an issue because theoretically i should be able to still get speeds as fast as my internet connection. 

Thanks.

---

### Post by tturrisi on 2006-08-31
Test your connnection speed at some of those test sites...
and check the router-ap, it may be set to B only.
Also, realize that the advertised speed of an adapter is the potential speed on a LAN (local network), not the Internet.

---

### Post by maniacmusician on 2006-08-31
I have checked my speed on some of those sites before, and they usually tell me that my speed is a little below average. how do i check the router-ap?
I know the advertised speed of an adapter is only the speed of the LAN, i dont expect to get internet at 54Mb/s lol, though that would be awesome.

---

### Post by tturrisi on 2006-08-31
Access the router control panel via a web browser by typing the specified ip address of the router.  For example, linksys uses 192.168.1.1.  Once there you will be able to config the wireless settings, security, etc.

---

### Post by funchords on 2006-09-01
> **maniacmusician said:**
> i had somewhat suspected this, but dont know of a way to be sure. on a normal speed server, my downloads usually start out at about 350 KB/s (450 on faster ones) and drop to 250 kb/s within about 10 seconds of the download beginning. 

I'm fine with ^ that speed, I am more concerned about BitTorrent speeds.

The test of your card is that you can download ~350 KB/s.  Trust me on this one: wireless cards either work real well or they barely work at all.  There is very little in between.  So if you're getting 350 KB/s wirelessly through your 3 Mbps broadband connectionn, you're not going to improve on that much.

At your speeds, your bandwidth limiter is the WAN port of your router, not your wireless card.  

On Bittorrent:  Others get better download speed because of their proximity (in distance) to a larger number of speedy peers and a fewer number of distant/slower peers.  If you "ping" your sources, and record their average up/down speed and ping times to you, the results will show you that those with the longest ping returns are also the slowest peers.  That's just the way P2P is.  Since you can't pick your peers, nor can you control their upload speed, nor can you fix internet congestion, then you're stuck with the luck of the draw.

---

### Post by maniacmusician on 2006-09-01
> **funchords said:**
> The test of your card is that you can download ~350 KB/s.  Trust me on this one: wireless cards either work real well or they barely work at all.  There is very little in between.  So if you're getting 350 KB/s wirelessly through your 3 Mbps broadband connectionn, you're not going to improve on that much.

At your speeds, your bandwidth limiter is the WAN port of your router, not your wireless card.  

On Bittorrent:  Others get better download speed because of their proximity (in distance) to a larger number of speedy peers and a fewer number of distant/slower peers.  If you "ping" your sources, and record their average up/down speed and ping times to you, the results will show you that those with the longest ping returns are also the slowest peers.  That's just the way P2P is.  Since you can't pick your peers, nor can you control their upload speed, nor can you fix internet congestion, then you're stuck with the luck of the draw.

ah, thanks for the explanation, I understand it better now. Can I adjust WAN settings on my router so it doesnt limit my bandwith? I dunno if i've ever seen that before

> **tturrisi said:**
> Access the router control panel via a web browser by typing the specified ip address of the router.  For example, linksys uses 192.168.1.1.  Once there you will be able to config the wireless settings, security, etc.

oh, i thought you meant a command from the terminal. Yeah, i've used that control panel, but I never saw a setting for B/G. I remember there was something about faster file transfers and I had it set to "Turbo", which i was told would get the best performance out of the router

---

### Post by tturrisi on 2006-09-01
> **maniacmusician said:**
> oh, i thought you meant a command from the terminal. Yeah, i've used that control panel, but I never saw a setting for B/G. I remember there was something about faster file transfers and I had it set to "Turbo", which i was told would get the best performance out of the router
OK.
Well, on my Netgear AP there is an option for mode B, G or B & G.  Perhaps your AP has a similar config.

---

### Post by maniacmusician on 2006-09-01
nope, i checked, it doesnt. but from what you guys have been saying, i doubt it would boost my performance much. I'm more interested in what i asked in my last post:

> Can I adjust WAN settings on my router so it doesnt limit my bandwith? I dunno if i've ever seen that before

---

### Post by tturrisi on 2006-09-02
Some home routers, the high end ones, have built in bandwidth regulators, but this feature cannot affect the wan, only from the router > lan.  The only other way to get more bandwidth would be to hack the cable modem, which can be done, depending on the model, but that's illegal, and usually what happens is the cable isp reprovisions the modem anyway, so such a hack does not stick.

---

### Post by maniacmusician on 2006-09-02
oh, i see. thanks for the info.

---

