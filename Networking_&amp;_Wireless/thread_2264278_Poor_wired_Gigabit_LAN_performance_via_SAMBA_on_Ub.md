---
title: "Poor wired Gigabit LAN performance via SAMBA on Ubuntu Gnome 14.04 64bit"
date: 2015-02-06
forum: Networking &amp; Wireless
---

### Post by Smokin Whale on 2015-02-06
Hey guys, 

Bit of an issue that I'm dealing with at the moment. I've recently setup a simple Ubuntu based media PC which doubles as a NAS. Here are my system specs:

Intel C2D 2.6ghz 
4gb ddr2 
Gigabyte GA-P965- S3
40gb sata boot 
2X 3tb sata in ZFS mirror
256gb SSD 
PCI Realtek rtl8189 gigabit nic 

I get over 180MB/s between the SSD and ZFS array so that's not an issue. However when copying data from my Windows box, which has very fast drives, I can only sustain 30MB/s, which is quite slow. On the contrary, with the exact same hardware on Windows, I can sustain 95MB/s no trouble. I have tried a range of Realtek nics and on board chips as well on similar systems and I still can't do better than 30MB/s. Could anyone offer any advice where to go from here? Never had this issue with Ubuntu 12.04, and my RAM and CPU aren't under huge amount of stress. 

Thanks in advance :)

---

### Post by TheFu on 2015-02-08
What happens if ZFS is removed?  Poor ZFS performance seems to happen when the RAM isn't sufficient for the storage.
On my 14.04 systems, I usually see 65MB/s for samba xfers. I think that is limited more by the slow laptop HDD and blue WD target. 

I've never used ZFS at home beyond just playing with it in user-mode and this was before kernel-mode zfs was relatively easy, but I recall something about recommended RAM being ECC and 1G RAM for every 2TB of storage. Is that not still true?

---

### Post by Smokin Whale on 2015-02-09
ZFS makes no difference whatsoever. I even bumped RAM up to 8GB temporarily and it made zero difference. Tried a fresh install of Ubuntu Gnome 32bit this time on a 128GB SSD with the ZFS drives disconnected and I got the same results of around 30mb/s (28.5MB/s to be precise) to the same server.

I tried another Core2Duo system with similar hardware with Ubuntu Gnome 14.04 64bit and tried copying an 8GB file from the SSD of PC A to the SSD of PC B. Could only do 35MB/s :(

Tried disabling IPv6 as well, no difference. Kinda at a loss here. No performance problems on Windows on any PC here.

Edit: Good news! Further testing revealed that I can saturate gigabit on my H61 sandy bridge workstation using the same Ubuntu setup. The key difference is my Core2Duo systems are all using PCI Gigabit NICs based on Realtek chipsets (8191 IIRC). Appears to be a driver issue then with these PCI Realtek based cards. Are there other drivers I can try for my card? This is my card: [http://support.dlink.com/ProductInfo.aspx?m=DGE-530T](http://support.dlink.com/ProductInfo.aspx?m=DGE-530T)

Otherwise I'm waiting on a PCI-e NIC to arrive, might try that to see if it helps with performance.

---

### Post by TheFu on 2015-02-10
How do you know that ZFS doesn't matter? Did you setup a small ext4 partition and test? I ask because you just say it isn't the issue, but don't say why.

I learned long ago that Intel PRO/1000 NICs were cheap and "just worked."  Before they were cheap, I didn't buy them and my network performance was in the 200-300Mbps range.  Sure, some systems here come with onboard marvel and realtek networking ... generally add another NIC - Intel PRO/1000 - much more consistent throughput, IME.

Windows drivers are well tested by the vendors. Linux drivers, not so much.
[http://www.dedoimedo.com/computers/kubuntu-realtek.html](http://www.dedoimedo.com/computers/kubuntu-realtek.html) shows someone else troubleshooting a realtek NIC issue too.

---

### Post by Smokin Whale on 2015-03-08
Yeah I tested a system without ZFS and the result was the same. It was just the NICs after all, and maybe something to do with nautilus as well, since performance appears to be better if the transfer is done from a Windows client. Anyway it seems these cheap PCIe NICs work well too so I'll be using those from now on.

---

