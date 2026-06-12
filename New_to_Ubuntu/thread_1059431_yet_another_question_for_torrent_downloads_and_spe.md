---
title: "yet another question for torrent downloads and speed"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Acradon on 2009-02-03
Hi there, 

Could somebody try to explain in plain words what all this stuff about ports and uPnP and seeds and peers and swarms and PPPoe and DHCP and TCP and UDP and all the other jazz is. I am not completely inept when it comes to computers, but I have been trying to increase my torrent downloading speed (using Vuze) for days now, and everything that I read on the net brings up new questions. So I got to the point where I realize that changing my port in my router has something to do with the speed Vuze can download. I am using a Siemens 6520 SpeedStream router, that apparently does not support all the functions that people are talkinmg about on the net. I have configured Vuze to use a port other than the one which was defaulted. So for a laugh I tried 50000. Vuze said it was OK. When trying to configure my router (I found out how after 2 hrs of navigating in this black box) it said the port was already in use. So I put in the old default port (some 32000 number) and it worked. Than I reset Vuze back to the old port. Now the previously listed port in the router is gone again. When I try to reenter it, it gives me the same error message saying the port is in use. DO I really have to set the router as well as my torrent client to the same port, maybe I misunderstood the whole thing, because I have absolutely NO IDEA what in the name of whoever I am doing!!!!!! HELP!!!!! I need plain english (or german). 

Thanks in advance

Acradon

P.S.: I am using a 5Mbit connection, 3GB RAM, AMD64 5000+ with intrepid (8.10). My current max download speed is hovering just under 150KB/s. Is that really my max??

---

### Post by stchman on 2009-02-03
> **Acradon said:**
> Hi there, 

Could somebody try to explain in plain words what all this stuff about ports and uPnP and seeds and peers and swarms and PPPoe and DHCP and TCP and UDP and all the other jazz is. I am not completely inept when it comes to computers, but I have been trying to increase my torrent downloading speed (using Vuze) for days now, and everything that I read on the net brings up new questions. So I got to the point where I realize that changing my port in my router has something to do with the speed Vuze can download. I am using a Siemens 6520 SpeedStream router, that apparently does not support all the functions that people are talkinmg about on the net. I have configured Vuze to use a port other than the one which was defaulted. So for a laugh I tried 50000. Vuze said it was OK. When trying to configure my router (I found out how after 2 hrs of navigating in this black box) it said the port was already in use. So I put in the old default port (some 32000 number) and it worked. Than I reset Vuze back to the old port. Now the previously listed port in the router is gone again. When I try to reenter it, it gives me the same error message saying the port is in use. DO I really have to set the router as well as my torrent client to the same port, maybe I misunderstood the whole thing, because I have absolutely NO IDEA what in the name of whoever I am doing!!!!!! HELP!!!!! I need plain english (or german). 

Thanks in advance

Acradon

P.S.: I am using a 5Mbit connection, 3GB RAM, AMD64 5000+ with intrepid (8.10). My current max download speed is hovering just under 150KB/s. Is that really my max??

Port Forward website is a wealth of information.

Here is a tutorial on how to open the proper port for uTorrent.

[http://www.portforward.com/english/routers/port_forwarding/Siemens/Speedstream-6520/Utorrent.htm](http://www.portforward.com/english/routers/port_forwarding/Siemens/Speedstream-6520/Utorrent.htm)

You need to find your torrent client's port that needs to be opened.  The default torrent client for Ubuntu is Transmission.

---

