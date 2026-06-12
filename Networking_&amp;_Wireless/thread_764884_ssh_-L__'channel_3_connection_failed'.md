---
title: "ssh -L  'channel 3: connection failed'"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by Luke771 on 2008-04-24
My ISP, Fastweb.it is the only company in the country where I live (Italy) that is capable of providing some real speed, especially on upload which I badly need for Freenet, i2p, BitTorrent seeding, and possibly other stuff that I may set up if I get around the problem caused by the 'dark side' of fastweb.

Abusing their de-facto monopoly on almost-high speed connections they use what I call "mobster marketing", which gies pretty much like this:
"I'm the only one who has this product, so you pay my price and stick to my rules: take it or leave it".
I'm not gonna discuss their policy here, what'm looking for is a solution to a practical problem.

The problem that I have to solve is that the ISP does the NAT and I can't port forward, and to get a routable address I should pay €4 a (!) which are to be added to the €65 a month (!!) that I already pay for my 10/10Mbit cable connection (includes a VoIP markedted as a "land line")

Some days ago, a friend who lives in another country got himself a 100/100Mbit connection, so routing my 10Mbit _max_ (often much less) wouldn't be a problem for him.
I asked him if he could set up a limited ssh account for me and let me forward a bunch of ports to his box, which he agreed to.

Now the problem is that once opened the tunnel, I can't connect to the remote port that is supposed to be listening.

Some details:
I run a Ubuntu 8.04 64bit and the remote system is a well mantained and efficient Windows box running WinXP Pro.
The server is Winsshd, the guy on the other end made an account for me and opened the ports that I need to open even tho they should be opened by my remote command, because it wasn't working and that was a try.

I use the command:

ssh -L <localport>:<remotehost>:<remoteport> user@remotehost shellserver 

(I also tried:
ssh -L <localport>:<remotehost>:<remoteport> user@remotehost sleep 150
no difference)

The connection seems to work, the tunnel is open, I can access my directory on the remote box everything, but when I try to open a connection to the forwarded port through the tunnel using another terminal window, on the tunnel window appears the output:

\channel 3: open failed: connect failed: 

without any explanation of why the connection failed.

Any suggestions?

---

