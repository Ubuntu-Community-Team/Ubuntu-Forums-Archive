---
title: "Missing Something?  Bittorrent and Opening Ports"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by Mookawaka on 2007-02-11
I am trying to set up my Ubuntu system to download via bittorrent trackers but am having problems of late.  I apparantly am missing some essential detail in getting a good connection while working with Ubuntu.

I have tried many of the available clients, settling on Ktorrent but keeping an eye on Deluge to see how it develops.
I have set up a static IP address.
I have forwarded a number of ports in my router both TCP and UDP.
I have downloaded Firestarter and set up inbound policies corresponding to the forwarded ports.
I have set up my bittorrent client of choice to use the same ports.
I am experimenting with this using healthy torrents with lots of other peers.
I doubt that my ports are being blocked by my ISP as I have used many different port ranges and I have few issues on those rare occasions that I decide to use Windoze.

After all is said and done I am unable to get incoming connections of any merit, I am able to connect to a fraction of the available peers, and my torrents tend to be stalled.

I am rather confused now.
Firestarter shows peers connecting through a number of ports but rarely the ones that I have forwarded, which appears odd to me and inexplicable.  I have checked my iptables after trying to set this up but this information in the console is unintelligible to me.

:confused:

---

### Post by amgeex on 2007-02-13
I'd like to get some help too, as I'm on the same situation. :(

---

### Post by NewBlood on 2007-02-16
Note: I apologize in advance if I have "resurrected" a topic when it's presumably dead, but it beats creating another one.

I am also experiencing a problem like this on Ubuntu Edgy 6.10, with the bittorrent program Azureus.

Apparently the program is cappable of leeching from seeders just fine, but it fails at uploading to other peers. The NAT shows green, and i know the correct ports are opened, but i still only manage to connect to around 16 out of 317, as opposed to my windows installation on the same machine, where it'll quickly fill up to the maximum allowed connections and upload without any issues.

As far as i can tell - from reading through the console output of azureus - the connection/handshake to the peer is somewhat established at first, but then gets disconnected due to the lack of new messages getting through.
e.g:
*Connection [/***.***.***.100:55468] forcibly timed out after 60sec due to socket inactivity*

Another symptom I have is in my router's status page, where the clientname for ubuntu on the network seems to be missing on the list with connected dhcp clients. My windows installation shows up fine, though.
Could this have anything to do with my azureus disfunctionality? I've spendt most of my time searching for a solution to the bittorrent problem, therefore I haven't looked into this particular issue to see if there's any connection between the two problems at all.

At the time of writing I have tried opening ports in iptables. Changed around network settings in ubuntu, and fidling around with my router. Nothing have worked yet, so any help on this subject would be greatly appreciated - from all the topic's current participants.

NewBlood

---

### Post by Mookawaka on 2007-02-20
I appear to have resolved this bittorrent issue for myself, and I am pleased to report that I was mistaken when implying that this was an Ubuntu problem even after going through the steps that outlined above.  There apparently was a grumpy witch living in my router that was not allowing ports to be forwarded correctly.  Upon updating the firmware on the router, which included a better port forwarding interface, I am able to get bittorrent clients running normally.
My download speeds are still not incredibly impressive but I think that has more to do with the coding of individual clients than anything.
I also am having trouble with my system locking up on occasion, I am unable to pass large files to other partitions due to errors, and cdrecord (the backend to Gnomebaker and the rest of the Ubuntu disk burning programs) works terrible since sometime around the advent of Dapper; but these problems are likely better addressed in other posts . . .

---

