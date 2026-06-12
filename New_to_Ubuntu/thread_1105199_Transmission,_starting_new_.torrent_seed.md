---
title: "Transmission, starting new .torrent seed"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by towoha on 2009-03-24
Hi. 
I have created a new .torrent file that I want to share. I have uploaded the .torrent file to a tracker. But I can't get the file to seed in "Transmission" How do I do that???

Regards
Torbjorn
*The Norwegian newbie*

---

### Post by Roanoke on 2009-03-24
Just open it and wait for it to download.

---

### Post by towoha on 2009-03-25
I have tried that, but I get: Data not fully available. Any hint to what I'm doing wrong?

---

### Post by towoha on 2009-03-25
:popcorn: SOLVED! 
The problem was that I didn't have the files that I wanted to share in the same folder as my default download folder, and my .torrent file was stored in another place also. I put all in the same folder and moved my default destiantionfolder to the right place, then everything workes smooothly =)

---

### Post by K9. on 2010-02-01
I have the following message in the torrent file properties:

Announce
Tracker:
Last announce at :    [the date]
Tracker responded:    Success
Next announce in :    15min
Manual announce allowed in  20seconds....


When I'm in Transmission > All
Torrentfile name 

Seeding to 0 of 0 connected peers

On the other computer I'm trying to test download to (different ISP) I get 

Error
Problem connecting to tracker  (10060, 'Operation timed out')

Anyone know what I could have missed? Why is it not seeding on PC1, why can't I download on PC2?

---

### Post by K9. on 2010-02-02
Ok now I get Transmission telling me that there's one seeder and one leecher. (I am both)   But nothing is happening up- or download wise...

The error is gone from my bittornado client on my seperate pc... but the "traffic light" in right hand corner is RED. "connecting to peers"...

Nothing happening on Transmission side. Just "seeding to 0 of 0 connected peers"

Scrape and announce are "success"

Any ideas for solutions appreciated....

---

### Post by warfacegod on 2010-02-02
[http://ubuntuforums.org/showthread.php?t=1259923]("http://ubuntuforums.org/showthread.php?t=1259923")

---

### Post by K9. on 2010-02-02
Well all is well. I went away from my pc for 45min and when I came back the file was on the other pc...

Guess it just needed time. As I'm not use to that from downloading other files I was a bit worried.

Thx for link.

---

### Post by warfacegod on 2010-02-02
Sure. It helped me allot with ktorrent.

---

### Post by wowiesy on 2013-04-02
I am running Ubuntu 10.04 Server (although installed desktop components already) as a torrent server mostly to download files. 

Now I have a need to share huge files to particular people and I thought of using torrents to do this.  

Have transmission-daemon and transmissioncli installed 1.93 (10621) version... 

i use the command: 

```
transmissioncli -n <<FILE TO SHARE AS TORRENT>> -a http://open.tracker.thepiratebay.org/announce <<OUTPUT.TORRENT>>
```

Output is:
```

Transmission 1.93 (10621) - http://www.transmissionbt.com/
[01:34:40.817] Transmission 1.93 (10621) started
[01:34:40.817] RPC Server: Adding address to whitelist: 127.0.0.1
[01:34:40.818] DHT: Generating new id
creating torrent "OUTPUT.TORRENT"




```

FILE TO SHARE AS TORRENT as well as OUTPUT.TORRENT are all on my default download folder (where all my other earlier downloads are)

the OUTPUT.TORRENT is created, and if i use this same torrent to upload on the same machine (same server), there are no seeders or leechers, even if this is practically the same machine (where the source torrent resides).. trying to download on a Mac using this output.torrent file, from my office network also has zero seeders and leechers even if I have left it running for a couple of hours...  

reading on some threads over the internet... I was pointed to possible network / routing issues...

I use port 51413 and this is forwarded from my router to this particular machine, the machine itself has a fixed ip, and my ISP doesn't give me a fixed IP, but I am signed up with DynDNS....  no firewall on the router itself.. no firewall on the torrent machine itself... 


am I missing something to make this work?  from the transmissioncli side? or config on transmission-daemon?  network side?  

I leave this particular machine pretty much on 24/7.. I am about 3 - 4 timezones away from the people who needs the file I am sharing...   so I think sharing through torrent is quite a good way under this circumstances...   Please help! =)

---

### Post by oldos2er on 2013-04-02
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---

