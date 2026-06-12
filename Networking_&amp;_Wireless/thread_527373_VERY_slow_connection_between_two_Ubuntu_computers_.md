---
title: "VERY slow connection between two Ubuntu computers using crossover Ethernet"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by Dave54 on 2007-08-16
I got a new computer, so I'm transferring 40 GB from my old computer to my new one. Both computers are running Ubuntu Feisty, and they are connected by a five-foot crossover Ethernet cable (cat 5e). I shared the files using nfs and mounting the shared files. I began the transfer with the following command:```
cp -frv /oldcomp/dave/ /home/dave/backup/
```The transfer is VERY slow at 0.1 MB/s. At this rate, it will take almost 5 days to complete! I know the old computer has a very old network card, but it had no problem downloading from the internet at 600 KB/s (which is about 0.5 MB/s).

Does anyone have any idea why the transfer might be so slow?

---

### Post by tbfr on 2007-08-16
Maybe auto-negotiation didn't work. What does **sudo ethtool eth0** output on your two computers?

You can try to set the speed manually, see [http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)
If you got an older crossover cable somewhere it might be worth trying it out too.

---

### Post by Dave54 on 2007-08-16
Thanks for the reply tbfr.

I ran "sudo ethtool eth0" on both computers. The new one printed:```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```But the old computer only said:```
Settings for eth0:
No data available
```Is that bad?

When you suggested I might use an older crossover cable, did you mean an old one specifically, or just a different one? I don't have any other crossover cables, but I do have cat 6 cable and the tools to cut and make a new one. Does anyone know if the color code/pin arrangement is the same for cat 6 compared to cat 5e? (If not, I'm sure I can find out online.)

In the mean time, thanks for the link. I'll try what it says shortly.

---

### Post by Dave54 on 2007-08-16
So, after reading the link tbfr posted, I ran **sudo mii-tool eth0** each computer. Here's what the old computer said:```
eth0: no autonegotiation, 10baseT-HD, link ok
```Tbfr, looks like you hit the nail on the head :)

I'll work on setting the speed manually (I think that's what you do when autonegotiation fails), and I'll report back later.

---

### Post by Dave54 on 2007-08-16
Since the mii-tool returned "10baseT-HD" on the old computer, I ran the following on both computers:```
sudo mii-tool -F 10baseT-HD
```I started a new transfer, and now it's running at 0.7 MB/s! While that may be slow for most people, I welcome the speed boost. In about 16 hours I'll have the all the information transferred. :)

Thanks tbfr!

---

### Post by Dave54 on 2007-08-16
I did another check on the speed (now that it has had a while) and found that it has slowed down to 0.1 MB/s. :(

At this point, any other ideas are appreciated.

---

### Post by tbfr on 2007-08-17
A few more things you can check:
Are there collisions on the interface (netstat -i )?
Does it make a difference if you don't mount the volume via NFS but use scp or netcat to transfer the files?
There are some good tools to measure network throughput, namely netperf and Netpipe.

---

### Post by Dave54 on 2007-08-17
Thanks.

The transfer sped up a little again, so I'll just leave it. It'll be done soon enough.

---

