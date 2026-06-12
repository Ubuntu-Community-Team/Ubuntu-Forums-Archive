---
title: "network slower after installing gigabit hardware - why?"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by dwasifar on 2007-06-26
I just upgraded the wired portion of my home network to gigabit hardware, and found to my irritation that network throughput is far SLOWER.

I have an Edgy box in the basement that functions as a file server, and various machines throughout the house that connect to it.  My main desktop in my office is a Feisty box.  I upgraded that first, with a Linksys gigabit ethernet card, and performance was unchanged.  Then I changed out the switch in the office for a D-Link gigabit 8-port switch; all still fine.  Then I went to the basement where all the network hardware is, added another D-Link gigabit switch, and upgraded the network card in the Edgy box with another of those same Linksys cards.  

Now I find I cannot make an NFS connection to the Edgy box from the Feisty box at all.  I can connect using Samba, but it's really slow; it wants to take 9 minutes to copy an 18MB file.  To make matters even more confusing, I CAN connect NFS from my wireless laptop, also running Feisty, and the throughput is better.

The hardware path from the Feisty desktop to the Edgy server: Linksys gigabit ethernet --> D-Link gigabit switch #1 --> D-Link gigabit switch #2 --> Linksys gigabit ethernet

The hardware path from the wireless Feisty laptop to the Edgy server: Intel wireless g --> Linksys draft-N wireless router --> D-Link gigabit switch #2 --> Linksys gigabit ethernet

I seriously don't understand this.  I can't point to one specific thing that's not working right; they just don't seem to want to share the sandbox when taken as a group.

---

### Post by dwasifar on 2007-06-27
And to make things even weirder, a Windows XP box going through the same two switches and using identical hardware has good throughput.

---

### Post by t4thfavor on 2007-06-27
Did you at least upgrade your cables to cat5e or cat6? Believe it or not that will usually make all the difference. Also hand made cables are hard to make perfect, and can lead to throughput loss.

Buy good cable, with machine crimped ends if possible. Find someone with a cable tester, and have them check your cables. My guess is that you have hand made cat5 cables that are not up to par with gigabit speeds.

---

### Post by kevdog on 2007-06-27
Try another card -- I mean wired PC cards nowadays are like $5-$10.

---

### Post by netztier on 2007-06-27
> **dwasifar said:**
> 
I seriously don't understand this.  I can't point to one specific thing that's not working right; they just don't seem to want to share the sandbox when taken as a group.

Try **iPerf** from the universe repos or [http://dast.nlanr.net/Projects/Iperf/#download](http://dast.nlanr.net/Projects/Iperf/#download) (for the Windows Version) to get some throughput values that are not depending on any service such as NFS or Samba.

Measure all combinations of two systems, so you might detect a pattern or spot a faulty link in your network. Try "within" the same switch, across the inter-switch-link etc.

Oh yes, and I support t4thfavor's statement to check cabling - Gigabit Ethernet absolutely needs all 8 wires of a cat 5 cable to work properly.


best regards

Marc

---

### Post by dwasifar on 2007-06-27
> **t4thfavor said:**
> Did you at least upgrade your cables to cat5e or cat6? Believe it or not that will usually make all the difference. Also hand made cables are hard to make perfect, and can lead to throughput loss.

Buy good cable, with machine crimped ends if possible. Find someone with a cable tester, and have them check your cables. My guess is that you have hand made cat5 cables that are not up to par with gigabit speeds.

Interesting.

Okay, first, I found part of an issue that improved things considerably.  I did some pings and they were all coming back with 0.05 to 0.07 times, so it looked like the machines were communicating well.  This made me think there was a problem with the shares themselves and not with the communication.  I went to change the mounting options for the remote shares from the Feisty desktop.  I went to unmount one of the shares using "sudo umount /remote/mp3" and got back a message telling me that share was mounted more than once.  I tried the other share and it was the same.  So I did a warm boot, and the startup hung with a share-related error message.  A cold boot restored everything to normal functioning, and I can mount the shares as NFS again.

The throughput to those shares is much better now, but the Windows box that sits next to it is still better.  So I came back here and read your message, and I was all ready to say no, when I wired up this network I used the proper cables, but I decided I'd check, and sure enough, the Windows box has a new cat5e cable and the Feisty box is connected to the switch with an older cat5; both machine made but the Feisty one is not cat5e.  So simple I missed it.  Most of the other cables here in my office are a motley collection of random junk, so I guess I'll just replace all those today to keep things consistent.

The rest of the network is up to spec.  The house was built last year and professionally prewired throughout with structured cable that includes cat5e, and all the cables in the network area are also new cat5e.

Thanks for the help!

---

### Post by t4thfavor on 2007-06-27
hmmmm I also have tried certain cards that were not very good, and had horrible throughput. A good 3com card will go a long way. I have a few linksys cards that are horrible (100meg cards). And they barely work at all. I don't know about linksys gig cards, but maybe they are of the same quality of the older ones.  I believe they have the "Tulip" chipset.

Just throwing out some information that may help.

---

