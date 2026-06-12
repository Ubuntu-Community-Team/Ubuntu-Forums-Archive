---
title: "Transmission BitTorrent client"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by TRANQU111TY on 2008-05-29
I have opened up a port in my router but in the Transmission BitTorrent client still says 'Port is closed'. Is there another way in Ubuntu or something to open the port?

---

### Post by c0njur on 2008-05-30
Are you running a firewall on your Ubuntu machine, such as Firestarter or iptables?

If not, then your ISP may have closed the port and you should try choosing a different one in Transmission.

---

### Post by TRANQU111TY on 2008-05-30
Hmm well after a restart it is saying it is open but my speeds are still very slow. I could be getting up to 164 KiB/s but instead its around 25-30 KiB/s or so. Any tips on increasing my download speed?

Btw my ratio is 0.3 and I've capped my upload speed at 11 KiB/s.

---

### Post by c0njur on 2008-05-30
Really all you can do it open the port. Your speed is dependent on how many peers you can connect to in the swarm and how fast they can upload to you.

---

### Post by c0njur on 2008-05-30
Some more general Bittorrent tips:

Limit your upload speed

The upload speed affects the download speed in essentially two ways:

    * Bittorrent peers tend to favour those other peers that upload to them. This means that if A and B are leeching the same torrent and A is sending data to B at high speed then B will try to reciprocate. So due to this effect high upload speeds lead to high download speeds.
    * Due to the way TCP works, when A is downloading something from B it has to keep telling B that it received the data sent to him. (These are called acknowledgements - ACKs -, a sort of "got it!" messages). If A fails to do this then B will stop sending data and wait. If A is uploading at full speed there may be no bandwidth left for the ACKs and they will be delayed. So due to this effect excessively high upload speeds lead to low download speeds.

The full effect is a combination of the two. The upload should be kept as high as possible while allowing the ACKs to get through without delay. A good thumb rule is keeping the upload at about 80% of the theoretical upload speed. You will have to fine tune yours to find out what works best for you. (Remember that keeping the upload high has the additional benefit of helping with your ratio.)

If you are running more than one instance of a client it is the overall upload speed that you must take into account. Some clients (e.g. Azureus) limit global upload speed, others (e.g. Shad0w's) do it on a per torrent basis. Know your client. The same applies if you are using your connection for anything else (e.g. browsing or ftp), always think of the overall upload speed.


Limit the number of simultaneous connections

Some operating systems (like Windows 9x) do not deal well with a large number of connections, and may even crash. Also some home routers (particularly when running NAT and/or firewall with stateful inspection services) tend to become slow or crash when having to deal with too many connections. There are no fixed values for this, you may try 60 or 100 and experiment with the value. Note that these numbers are additive, if you have two instances of a client running the numbers add up.


Limit the number of simultaneous uploads

Isn't this the same as above? No. Connections limit the number of peers your client is talking to and/or downloading from. Uploads limit the number of peers your client is actually uploading to. The ideal number is typically much lower than the number of connections, and highly dependent on your (physical) connection.


Just give it some time

As explained above peers favour other peers that upload to them. When you start leeching a new torrent you have nothing to offer to other peers and they will tend to ignore you. This makes the starts slow, in particular if, by change, the peers you are connected to include few or no seeders. The download speed should increase as soon as you have some pieces to share.

---

