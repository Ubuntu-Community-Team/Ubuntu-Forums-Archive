---
title: "Joining two connections dpc0 &amp; ppp0 (iptables/route?)"
date: 2005-12-04
forum: Networking &amp; Wireless
---

### Post by MistaED on 2005-12-04
Hello, I have set up both a ppp ISDN connection and a dpc/ppp satellite connection (direcway-based). I am using the driver from sourceforge.net/projects/direcpc and it works fine, I get about 97% signal like on windows.

Now, the satellite is only 1-way, and the ISDN is both ways. Using iptables, the route command or by any other means, can someone help me write up a bash script which can join these two? The devices are ppp0 and dpc0. Also, is it possible to just combine ppp0 into dpc0 so firestarter can still be used?

Thanks
-MistaED

---

### Post by cwaldbieser on 2005-12-04
[QUOTE=MistaED]Hello, I have set up both a ppp ISDN connection and a dpc/ppp satellite connection (direcway-based). I am using the driver from sourceforge.net/projects/direcpc and it works fine, I get about 97% signal like on windows.

Now, the satellite is only 1-way, and the ISDN is both ways. Using iptables, the route command or by any other means, can someone help me write up a bash script which can join these two? The devices are ppp0 and dpc0. Also, is it possible to just combine ppp0 into dpc0 so firestarter can still be used?

Thanks
-MistaED[/QUOTE]

Well, can you explain a little more specifically by what you mean by "joining" the two interfaces?  Do you always want to sent outgoing traffic over one of them, or alternate sending packets between them, or something else?

---

### Post by mips on 2005-12-04
I think he wants to do something similair to PPP multilink or channel bonding. Combine the sattelite with the isdn on the incoming side as one interface. This is my understanding.

---

### Post by MistaED on 2005-12-04
Yes sorry, I want to make ppp0 for the main upstream and never the dpc0 as there is no satellite upstream, so dpc0 is strictly only for downstreaming data. And if possible, combine ppp0's downstream as well. Windows has a little direcway utility called navigator which does this automagically, using the PPP device (ISDN) for upstream and the direcway (satellite) modem to downstream only.

The direcpc project from sourceforge has a script which does this for you, only it doesn't. So I'm asing if someone could help me out to write a script which uses the route command, iptables or by other means. If you want to look at the route scripts which the direcpc project made, download v1.1.5 from [www.sourceforge.net/projects/direcpc](www.sourceforge.net/projects/direcpc) but bear in mind this version is too old to run in the latest 2.6.x kernels (I use v1.1.6 as one of the authors of the driver sent it to me via email, but he wants to release it later as it has a small bug with it). The route scripts are the same though. The author hasn't replied to my pleas and I have until Tuesday/Wednesday to do this for my uncle. :(

Thanks
-MistaED

---

### Post by cwaldbieser on 2005-12-04
[QUOTE=MistaED]Yes sorry, I want to make ppp0 for the main upstream and never the dpc0 as there is no satellite upstream, so dpc0 is strictly only for downstreaming data. And if possible, combine ppp0's downstream as well. Windows has a little direcway utility called navigator which does this automagically, using the PPP device (ISDN) for upstream and the direcway (satellite) modem to downstream only.

The direcpc project from sourceforge has a script which does this for you, only it doesn't. So I'm asing if someone could help me out to write a script which uses the route command, iptables or by other means. If you want to look at the route scripts which the direcpc project made, download v1.1.5 from [www.sourceforge.net/projects/direcpc](www.sourceforge.net/projects/direcpc) but bear in mind this version is too old to run in the latest 2.6.x kernels (I use v1.1.6 as one of the authors of the driver sent it to me via email, but he wants to release it later as it has a small bug with it). The route scripts are the same though. The author hasn't replied to my pleas and I have until Tuesday/Wednesday to do this for my uncle. :(

Thanks
-MistaED[/QUOTE]

Well, I don't know too much about modifying the networking code in the kerenl, which is what it seems like the program you mentioned does.  As far as using iptables-- I have some ideas, but I am not sure how they would work in practice, since I don't really have the hardware to test the ideas out on.

My though is that if you could alter the source address of the outgoing packets so that roughly half of them appear to be coming from the dpc0 IP address and half appear to be coming from the ppp0 address, then everything should work out the way you want it.  You default route would simple be to ppp0 (since that is the only interface you want to upload data on).

So maybe something like this (assumes no firewall):
```

$ export $DPC_ADDR=192.168.0.2 #or whatever the IP address is for this interface
$ sudo iptables -t nat -F
$ sudo iptables -t nat -A POSTROUTING -o ppp0 -m nth --every 2 --packet 0 -j ACCEPT
$ sudo iptables -t nat -A POSTROUTING -o ppp0 -m nth --every 2 --packet 1 -j SNAT --to-source $DPC_ADDR

```
That may be totally wrong.  If so, you can clear out the nat table with:
```

$ sudo iptables -t nat -F

```
Basically, what it is saying is:
1) Clear out the nat table.
2) Add a rule that says the first of every two packets going out on ppp0 should be left alone.
3) Add a rule that says the second of every two packets going out on ppp0 should be changed so it looks like it came from dpc0.

I have no idea if it will work, but unless you can find someone who knows what to do, your best bet will be to experiment a little bit.

---

### Post by MistaED on 2005-12-04
Thanks for the reply, I just want to ask if it's easier, I could just set the incoming only to be dpc0 and the outgoing only be ppp0. Because when you say every second packet, it seems like they need to both sync together for incoming, and I don't think this would work, being two different bandwidth speeds and latency.

-MistaED

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=MistaED]Thanks for the reply, I just want to ask if it's easier, I could just set the incoming only to be dpc0 and the outgoing only be ppp0. Because when you say every second packet, it seems like they need to both sync together for incoming, and I don't think this would work, being two different bandwidth speeds and latency.

-MistaED[/QUOTE]
Well, this is still all theoretical, but if you took out the "nth" match rule and mangled the outgoing packets so they appeared to come from dpc0 and then mangled the incoming packets on dpc0 so they all get rerouted to pppo, that might work.  I am not exactly sure what that would look like-- you will have to experiment.  Maybe something like:
```

$ export $PPP_ADDR=192.168.0.3 #or whatever the IP address is for this interface
$ export $DPC_ADDR=192.168.0.2 #or whatever the IP address is for this interface
$ sudo iptables -t nat -F
$ sudo iptables -t nat -A POSTROUTING -o ppp0 -j SNAT --to-source $DPC_ADDR
$ sudo iptables -t nat -A PREROUTING -i dpc0 -j DNAT --to-destination $PPP_ADDR

```
Something about that doesn't seem quite right to me-- maybe the mangle table would be more appropriate.  I am not entirely sure from the literature.

---

### Post by MistaED on 2005-12-05
I tried what you said, but no luck sadly :( I believe there is something else to the driver which is not working but I have no idea until the author replies back. Thanks anyway though.

-MistaED

---

### Post by lordfoul on 2006-06-18
Can anyone confirm that this [Load Balancing Guide ]("http://tetro.net/misc/multilink.html")works?

---

### Post by mips on 2006-06-18
[QUOTE=lordfoul]Can anyone confirm that this [Load Balancing Guide ]("http://tetro.net/misc/multilink.html")works?[/QUOTE]


Why don't you just try it, nothing to loose ? Will only take a few minutes to copy&paste to the relevant files.

Backup the relevant files first, if it doesn't work simply restore the backups.

---

### Post by lordfoul on 2006-06-18
I don't have two connections with which to try this with.  I was wondering if someone with two might be able to confirm this will work.  For the sake of the community

---

