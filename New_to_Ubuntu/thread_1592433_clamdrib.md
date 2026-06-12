---
title: "clamdrib"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by hifly1231 on 2010-10-10
Is there a clamdrib extention yet that is compatible with Thunderbird 3.1.*?

---

### Post by paNIX on 2010-10-18
Hi

Please check out the enclosed file:

I made a slight modification of the clamdrib-0.2.0.2.xpi extension which made it work with my Ubuntu 10.10 64bit and Thunderbird 3.1.6b setup. As it is not tested thoroughly on viruses I will advise to monitor its behaviour thoroughly. For those interested - all that was needed was to edit the version compatability line in the (internal) install.rdf file,

Enjoy;
paNIX

---

### Post by paNIX on 2011-04-04
..any kind of feedback would be nice, but none so far - and 50 x dl's. oh well...

---

### Post by blaineclrk on 2011-06-01
Hey paNIX, I tried this out and I'm getting a status of 'Connection Problems' on each account. Got TBird on LMint 10 with two Comcast and two Gmail accounts. I've got a bunch of MS friends I don't want to send a virus to and according to the last system scan I did I had 5 positives from SPAM from one friend's yahoo account that got hacked.

---

### Post by chollyc on 2011-06-08
Thanks paNIX! Just installed on TBird 3.1.10 running on Natty. All seems to be working. I'll post more if/when it detects.
:P

---

### Post by paNIX on 2011-06-08
Chollyc; Great! And thanks for being a decent guy. Im certain it does what its supposed to, no glitches has been reported. 

@blaineclrk: sounds like a firewall problem to me, try deactivating your firewall to check if behaviour changes. What version of tbird do you run?

Im sorry im not able to be of much help these days, my linux-box has broken down so now im stuck with win and mac for a while.

---

### Post by blaineclrk on 2011-06-09
Hey paNIX, I double checked on a firewall status through System Monitor because some time back I had one set up on Ubuntu then didn't get back into it when I recently switched to Mint. There's no firewall process on my unit yet, but will have it at some point soon, so we might as well cover that eventuality now if you don't mind.
In the meantime, I'm running Tbird with this for the package;
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.17) Gecko/20110424 Lightning/1.0b2 Thunderbird/3.1.10

---

### Post by paNIX on 2011-06-09
OK, blaineclrk, here's an idea;

First make a backup of your /etc/clamav/clamd.conf file in case this operation doesnt solve it and you need to reverse the modification. Then edit  the /etc/clamav/clamd.conf file by adding the lines *TCPsocket 3310* and *TCPAddr localhost*. Restart puter and hopefully it works.

---

### Post by blaineclrk on 2011-06-14
Argh ... too many projects going on here. I finally got a round tuit - :) - ! Added the lines, restarted and still burping Connection Problems at me.

---

