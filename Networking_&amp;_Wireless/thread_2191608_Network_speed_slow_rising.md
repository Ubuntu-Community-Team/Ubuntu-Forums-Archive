---
title: "Network speed slow rising"
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by Edemoe on 2013-12-03
Hi Guys,
I have the following problem with the network:
[ATTACH=CONFIG]248307[/ATTACH]
i.e. when I send a large amount of data from the client to server I see the speed smoothly increasing from start to the end of the transfer.
But when data is being received from the server the network speed is constant:
[ATTACH=CONFIG]248308[/ATTACH]
Server PC is running Ubuntu 12.04 completely standard with all the latest updates installed.
Client PC is running elementaryOS Luna (which is actually 12.04 too) but with newer 3.10 kernel and other non-standard packages installed.
The graphs are created by running 'iperf -s' on the server  and 'iperf -c xxxxxx -t 30' on the client (and vice versa) so there is no any disk i/o impact...

Please anybody give me an idea what could be wrong?

---

### Post by aromo2 on 2013-12-03
You're tests are inconclusive.  It could be your client not being able to send at full throughput from the beginning -OR- your server not being able to handle receiving traffic very well.  Can you test the other way around (server sending, client receiving)?  Can you upload a file from CLIENT to, say, Google Drive and see how it behaves?  On your server, try downloading a file from the Internet and see if it downloads at a constant throughput.

---

### Post by Edemoe on 2013-12-03
> **aromo2 said:**
> Can you test the other way around (server sending, client receiving)?
I did it (see the  second screenshot). It's OK.

> **aromo2 said:**
> Can you upload a file from CLIENT to, say, Google Drive and see how it behaves?
As you can see from the 1 screenshot the transfer starts at about 20 Mbytes/sec and grows up to 100 Mbytes/sec.
It's 1Gbit network between PCs. My internet connection is only 50Mbits/sec so this test can't be done...

> **aromo2 said:**
> On your server, try downloading a file from the Internet and see if it downloads at a constant throughput.
As above it's not useful. 
But I tested another client OS (Arch Linux all updates installed) on the same client PC and it seems works ok for both directions.

So apparently the problem is on the client elementaryOS i.e. it's not able to send data at full speed. But I still have no idea what could be a reason...

---

### Post by Edemoe on 2013-12-06
Hello,
an update on this:
- I've updated clint's kernel to the latest stable 3.12.2 and iperf shows now the perferct result **~930Mbit/s both directions**.
- When I copy 1.3Gb file from server to client via NFS the speed is about 80-100Mbytes/s which is fine (blue graph):
[ATTACH=CONFIG]248379[/ATTACH]
- But when I copy the same file from client to server (via NFS) back the things are much worse (red graph):
[ATTACH=CONFIG]248380[/ATTACH][ATTACH=CONFIG]248381[/ATTACH][ATTACH=CONFIG]248382[/ATTACH]
It starts about 10x slower. And as you can see the graph has some steps, which looks like the speed is 	
knowingly limited BY SOMETHING and it increases the limit from time to time! i.e. it starts with ~8Mbit/s, then 16Mbit/s, then ~24Mbit/s up to ~48 at the end.
But iperf tests shows the network is capable to work at 930Mbit/s! That looks completely weird to me...

To exclude the possible disk i/o impact I tried to copy the same file within the sever PC:
[ATTACH=CONFIG]248383[/ATTACH]
It's about 100Mbytes/s which is great result I think.

I'm completely puzzled now! Please, guys, any ideas!?

---

