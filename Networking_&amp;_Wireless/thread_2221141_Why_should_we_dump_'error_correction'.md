---
title: "Why should we dump 'error correction'?"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by Ace..... on 2014-04-30
We have just been 'unbundled'.

Using speedtest.net, testing to Paris, our 3km line was giving us around 
3 - 5 Mbs down
0.8 Mbs up
70ms ping

Results now are:
7Mbs down
1Mbs up
32ms ping

Obviously good.... so I checked out my management page, and discovered that my options now were to move from standard mode, with error correction to:

. minimum latency but no error correction
. sync without clamping to 24Mbs no min threshold on noise
. FECS minimum errors (ideal for TV quality but could be slow)

I can understand that the odd error/ missed packet for TV changes nothing, however, people use their connection for everything eg. downloading files.

Am I misunderstanding error correction?

I thought that if you missed a packet..... it would be re-sent (so that the file will function).
I'd assumed that TV mode modified this to allow errors, in order to maximise the speed.
Yet here it seems I can setup my basic connection to remove error correction.

This seems crazy, so I'm guessing that I just don't understand it.

Can anybody cast some light on this?

:)

---

### Post by tgalati4 on 2014-05-01
Error correction is quite sophisticated.  Your modem could be using a satellite-style error correction ([PSK]("http://en.wikipedia.org/wiki/QPSK")) which imposes quite a bit of overhead, but corrects errors on-the-fly, which would be quicker than requesting that a packet be resent.  It depends on your Use Case and on measured performance in your network.

If turning off error correction gives you double the speed with no apparent loss of

---

### Post by Ace..... on 2014-05-01
> **tgalati4 said:**
> Error correction is quite sophisticated.  Your modem could be using a satellite-style error correction ([PSK]("http://en.wikipedia.org/wiki/QPSK")) which imposes quite a bit of overhead, but corrects errors on-the-fly

Hmmm!.... I would have thought that the digital modem is pretty basic.
I'm with 'Free':- one of the biggest ISPs in France.
They have driven innovation (forcing France to adopt free telephone calls to most of the world, for the past 5 years), but being on a 3km line, we missed out on their latest v6 Revolution box, when it launched a couple of years ago.
It is available now to us, but at a cost :(

I think that, before modifying my connection eg. dumping error correction to gain speed..... I first need to understand the consequences (and what they actually mean when they offer to drop error correction).
Eg. If I downloaded a file, am I at risk of it not working?
OR
**Does my computer provide the error check**, and demand that a missing packet is re-sent?

IE. Do I gain speed - everything arrives quickly - but lose speed, cos some packets need to be re-sent.
IE. Could be faster, could provide little change, could be slower.

But in all cases where file integrity is required, this integrity is assured????

I'm just guessing, based upon logic.... cos if all error correction was dumped then everything would just stop working.
I read somewhere that video streaming allows a level of errors cos 'missing a frame' has no impact, unlike all other file types.

So... can anybody confirm what the consequence are, if 'error correction is dropped'?

:)

---

### Post by tgalati4 on 2014-05-01
Only you can verify that.  You would have a very narrow audience of users with the exact same configuration as yours.  

In general, any file or data transfer has a checksum in the packet header that causes a retransmit request if the packet does not pass the checksum.  This is part of TCP/IP, the protocol that runs on Ethernet.  How your cable provider sends the signal to your cable modem is anybody's guess.  I'm guessing it is similar to a satellite signal transmission, with many channels being sent simultaneously.  How your ethernet gets sent over that cable is probably proprietary.  Turning off error correction may mess up your ethernet, but you will have to run several tests to see what works and what fails.

---

### Post by Ace..... on 2014-05-02
> **tgalati4 said:**
> Only you can verify that.  You would have a very narrow audience of users with the exact same configuration as yours.  
In general, any file or data transfer has a checksum in the packet header that causes a retransmit request if the packet does not pass the checksum.  This is part of TCP/IP, the protocol that runs on Ethernet. 

I think that this is the key.
The TCP/IP connection protocol ensures that a file download is not completed, until it is completed (the checksums match).

So from this we can guess that their offer, to dump error correction, is not based upon the desire to destroy one's PC.
It must be that they offer to switch off their error correction, leaving the task to TCP/IP....
..... knowing that, if the line is good, the overall result will be faster.

I think for me, with a 3km line.... I am probably not the target client for switching off error correction.

Though, perhaps I should try.

It's free to try :)

What do you think?

:)

---

### Post by tgalati4 on 2014-05-02
One test is worth a thousand expert opinions.

---

