---
title: "Internet download speed slower in ubuntu than Win 8.1"
date: 2015-11-02
forum: Networking &amp; Wireless
---

### Post by A4Skyhawk on 2015-11-02
My Acer AXC-603 is set up to dual boot Ubuntu 15.04 and Win 8.1.  My ISP  is Comcast with internet download speed "Blast" (up to 150 mbps).  In  Win 8.1, using Comcast Speed  Test, I get download speeds of 100 +/-  mbps.  In Ubuntu, I get 30 +/- mbps.  The cable is Cat5e, and I have  tried many combinations of terminal commands, but unsuccessful in  increasing downloads in Ubuntu.  Here is output from ~$ sudo lshw -C network:               
```
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: f8:0f:41:cc:5f:43
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=10.0.0.165 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:89 ioport:e000(size=256) memory:d0604000-d0604fff memory:d0600000-d0603fff
```

Output from ~$ sudo ethtool eth0
```
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes
```

Output from $ dmesg |grep eth0
```
[    1.597543] r8169 0000:02:00.0 eth0: RTL8168g/8111g at 0xffffc90000664000, f8:0f:41:cc:5f:43, XID 0c000880 IRQ 89
[    1.597548] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   35.332864] r8169 0000:02:00.0 eth0: link down
[   35.332889] r8169 0000:02:00.0 eth0: link down
[   40.546769] r8169 0000:02:00.0 eth0: link up
```

I'm wondering if the problem is in the difference between the drivers in Win 8.1 vs Ubuntu.  Any upgrades available for Ubuntu?
TIA for any other ideas you may have,
Bill

---

### Post by michi1983 on 2015-11-04
It would be nice to tell us what commands exactly you've tried in terminal.
Have you tried to set your eth0 to gigabit speed with full duplex? Because you are running it at 100Mbit right now.
```
sudo ethtool -s eth0 speed 1000 duplex full
```

Edit:
Sorry my mistake.
Your switch/router only supports 100Mbit

Please put this command in your command line and re-post the output:
```
wget -O /dev/null http://speedtest.wdc01.softlayer.com/downloads/test10.zip
```

---

### Post by A4Skyhawk on 2015-11-06
Sorry for the long delay in responding.  My Acer died after only 3 days of use.  Amazon sent a replacement free of charge, and it took me a day to get it set up and do some additional testing/fact finding.  I also worked thru some cable issues.  The cable that I use that runs thru the walls of the house   to get to the modem is limiting the download to 100Mbps max.  I purchased about 100' (equivalent length of the wiring thru the walls) and ran it down the halls and up the stairs to the computer and now get 1Gbps speed &#8211; debugging/upgrading the wiring thru the walls will be another project.   
 Getting back to the original topic, I have tested the down load speed of Ubuntu vs Win 8.1, using the 1 Gbps cable and also using the &#8220;in the wall&#8221; cable (100 Mbps max) on my new Acer AXC-603 UB17 (Win 8.1 and Ubuntu 15.04).  With both cable set ups, the download speed is faster in Win than in Ubuntu.  Here are the results:
 
 
 Ubuntu       1Gbps cable      15 ms latency/153 Mbps downlaod/12 Mbps upload
 Win 8.1      1 Gbps cable      11 ms latency/179 Mbps downlad/12 Mbps upload
 
 
 Ubuntu       100 Mbps cable     14 ms latency/33 Mbps download/12 Mbps upload
 Win 8.1      100 Mbps cable     13 ms latency/93 Mbps download/12 Mbps upload
 
 
 Results of ~$ sudo lshw -C network:  
        *-network                
        description: Ethernet interface
        product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:02:00.0
        logical name: eth0
        version: 11
        serial: f8:0f:41:cd:b4:c8
        size: 1Gbit/s
        capacity: 1Gbit/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=10.0.0.138 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
        resources: irq:89 ioport:e000(size=256) memory:d0604000-d0604fff memory:d0600000-d0603fff
 
 
 Results of ~$ sudo ethtool eth0
 	Supported ports: [ TP MII ]
 	Supported link modes:   10baseT/Half 10baseT/Full  
 	                        100baseT/Half 100baseT/Full  
 	                        1000baseT/Half 1000baseT/Full  
 	Supported pause frame use: No
 	Supports auto-negotiation: Yes
 	Advertised link modes:  10baseT/Half 10baseT/Full  
 	                        100baseT/Half 100baseT/Full  
 	                        1000baseT/Full  
 	Advertised pause frame use: Symmetric Receive-only
 	Advertised auto-negotiation: Yes
 	Link partner advertised link modes:  10baseT/Half 10baseT/Full  
 	                                     100baseT/Half 100baseT/Full  
 	                                     1000baseT/Half 1000baseT/Full  
 	Link partner advertised pause frame use: Symmetric Receive-only
 	Link partner advertised auto-negotiation: Yes
 	Speed: 1000Mb/s
 	Duplex: Full
 	Port: MII
 	PHYAD: 0
 	Transceiver: internal
 	Auto-negotiation: on
 	Supports Wake-on: pumbg
 	Wake-on: g
 	Current message level: 0x00000033 (51)
 			       drv probe ifdown ifup
 	Link detected: yes
 
 
 Results of ~$ wget -O /dev/null [http://speedtest.wdc01.softlayer.com/downloads/test10.zip](http://speedtest.wdc01.softlayer.com/downloads/test10.zip)
 --2015-11-06 17:37:52--  [http://speedtest.wdc01.softlayer.com/downloads/test10.zip](http://speedtest.wdc01.softlayer.com/downloads/test10.zip)
 Resolving speedtest.wdc01.softlayer.com (speedtest.wdc01.softlayer.com)... 2607:f0d0:3001:78::2, 208.43.102.250
 Connecting to speedtest.wdc01.softlayer.com (speedtest.wdc01.softlayer.com)|2607:f0d0:3001:78::2|:80... connected.
 HTTP request sent, awaiting response... 200 OK
 Length: 11536384 (11M) [application/zip]
 Saving to: &#8216;/dev/null&#8217;
 
 
 /dev/null                                   100%[==========================================================================================>]  11.00M  10.8MB/s   in 1.0s    
 
 
 2015-11-06 17:37:53 (10.8 MB/s) - &#8216;/dev/null&#8217; saved [11536384/11536384]

---

### Post by michi1983 on 2015-11-07
> **A4Skyhawk said:**
> Sorry for the long delay in responding.  My Acer died after only 3 days of use.  Amazon sent a replacement free of charge, and it took me a day to get it set up and do some additional testing/fact finding.  I also worked thru some cable issues.  The cable that I use that runs thru the walls of the house   to get to the modem is limiting the download to 100Mbps max.  I purchased about 100' (equivalent length of the wiring thru the walls) and ran it down the halls and up the stairs to the computer and now get 1Gbps speed &#8211; debugging/upgrading the wiring thru the walls will be another project.   
 Getting back to the original topic, I have tested the down load speed of Ubuntu vs Win 8.1, using the 1 Gbps cable and also using the &#8220;in the wall&#8221; cable (100 Mbps max) on my new Acer AXC-603 UB17 (Win 8.1 and Ubuntu 15.04).  With both cable set ups, the download speed is faster in Win than in Ubuntu.  Here are the results:
 
 
 Ubuntu       1Gbps cable      15 ms latency/153 Mbps downlaod/12 Mbps upload
 Win 8.1      1 Gbps cable      11 ms latency/179 Mbps downlad/12 Mbps upload
 
How is this possible if Comcast gives you 'only' up to 150 Mbps download speed??

> **A4Skyhawk said:**
> 
Ubuntu       100 Mbps cable     14 ms latency/33 Mbps download/12 Mbps upload
 Win 8.1      100 Mbps cable     13 ms latency/93 Mbps download/12 Mbps upload
 
 
 Results of ~$ sudo lshw -C network:  
        *-network                
        description: Ethernet interface
        product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:02:00.0
        logical name: eth0
        version: 11
        serial: f8:0f:41:cd:b4:c8
        size: 1Gbit/s
        capacity: 1Gbit/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=10.0.0.138 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
        resources: irq:89 ioport:e000(size=256) memory:d0604000-d0604fff memory:d0600000-d0603fff
 
 
 Results of ~$ sudo ethtool eth0
 	Supported ports: [ TP MII ]
 	Supported link modes:   10baseT/Half 10baseT/Full  
 	                        100baseT/Half 100baseT/Full  
 	                        1000baseT/Half 1000baseT/Full  
 	Supported pause frame use: No
 	Supports auto-negotiation: Yes
 	Advertised link modes:  10baseT/Half 10baseT/Full  
 	                        100baseT/Half 100baseT/Full  
 	                        1000baseT/Full  
 	Advertised pause frame use: Symmetric Receive-only
 	Advertised auto-negotiation: Yes
 	Link partner advertised link modes:  10baseT/Half 10baseT/Full  
 	                                     100baseT/Half 100baseT/Full  
 	                                     1000baseT/Half 1000baseT/Full  
 	Link partner advertised pause frame use: Symmetric Receive-only
 	Link partner advertised auto-negotiation: Yes
 	Speed: 1000Mb/s
 	Duplex: Full
 	Port: MII
 	PHYAD: 0
 	Transceiver: internal
 	Auto-negotiation: on
 	Supports Wake-on: pumbg
 	Wake-on: g
 	Current message level: 0x00000033 (51)
 			       drv probe ifdown ifup
 	Link detected: yes
 
Okay that's good. That means that your router/switch supports Gigabit and it just didn't get advertised with auto negotiation because of the cable.

> **A4Skyhawk said:**
> 
Results of ~$ wget -O /dev/null [http://speedtest.wdc01.softlayer.com/downloads/test10.zip](http://speedtest.wdc01.softlayer.com/downloads/test10.zip)
 --2015-11-06 17:37:52--  [http://speedtest.wdc01.softlayer.com/downloads/test10.zip](http://speedtest.wdc01.softlayer.com/downloads/test10.zip)
 Resolving speedtest.wdc01.softlayer.com (speedtest.wdc01.softlayer.com)... 2607:f0d0:3001:78::2, 208.43.102.250
 Connecting to speedtest.wdc01.softlayer.com (speedtest.wdc01.softlayer.com)|2607:f0d0:3001:78::2|:80... connected.
 HTTP request sent, awaiting response... 200 OK
 Length: 11536384 (11M) [application/zip]
 Saving to: &#8216;/dev/null&#8217;
 
 
 /dev/null                                   100%[==========================================================================================>]  11.00M  10.8MB/s   in 1.0s    
 
 
 2015-11-06 17:37:53 (10.8 MB/s) - &#8216;/dev/null&#8217; saved [11536384/11536384]
The 10.8MB/s is 86 Mbps which would be fine if you have a up to 150 Mbps contract. It just doesn't makes sense that with Windows you achieve speeds over these 150mbps.

---

### Post by A4Skyhawk on 2015-11-07
Could you please explain what is being done by running [http://speedtest.wdc01.softlayer.com/downloads/test10.zip](http://speedtest.wdc01.softlayer.com/downloads/test10.zip)
 and what is to be learned from the results?  Is this a better test than speedtest.Comcast.net?
 
 
 As far as the speed test results that I showed above, I did a comparison of 5 different test sites, and all of them showed download speeds exceeding the &#8220;up to 150Mbps&#8221; speed promoted by Comcast.:
 Geeksquad      157/12 Mbps download/upload  
 AT&T              179/12
 Speedtest         155/12
 Time Warner    162/12
 Comcast           156/12
 
 
 But why is the download speed slower, as indicated by the data that I show in my post #3, in Ubuntu than in Windows?

---

### Post by michi1983 on 2015-11-08
> **A4Skyhawk said:**
> Could you please explain what is being done by running [http://speedtest.wdc01.softlayer.com/downloads/test10.zip](http://speedtest.wdc01.softlayer.com/downloads/test10.zip)
 and what is to be learned from the results?  Is this a better test than speedtest.Comcast.net?
 
It just downloads a file from a server but in the command line and those tests are way more accurate than all these website speedtest (at least that is my opinion).
You can learn from it that you achieved (as I stated in my last post) a download speed of 86mbps which is a good value for an up-to 150 mbps contract.
 
> **A4Skyhawk said:**
> 
 As far as the speed test results that I showed above, I did a comparison of 5 different test sites, and all of them showed download speeds exceeding the “up to 150Mbps” speed promoted by Comcast.:
 Geeksquad      157/12 Mbps download/upload  
 AT&T              179/12
 Speedtest         155/12
 Time Warner    162/12
 Comcast           156/12
  
This really is weird to be honest. When you really have an up-to 150mbps contract, there is almost no way that they deliver you more speed than you pay for.
So either these tests are simply faulty or you have a better contract with Comcast than you know :-)

 > **A4Skyhawk said:**
> 
 But why is the download speed slower, as indicated by the data that I show in my post #3, in Ubuntu than in Windows?
 [/QUOTE]
It looks like that with the 100mbps cable you had some sort of auto-negotiation problem with Ubuntu.
Linux is way more sensitive here than Windows.
But with ethtool eth0 you could see that with the new 1gbps cable your Ubuntu NIC get set correctly to 1000mbps and Full Duplex and the speed is accurate again.

---

### Post by praseodym on 2015-11-08
Lets try:
```

sudo ethtool -s eth0 speed 1000 autoneg off
```
and/or changing the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by A4Skyhawk on 2015-11-10
@praseodym:
I entered the commands that you suggested  and rebooted.  On rerunning the Comcast  speed test, I got virtually the same results as I got previously (this is on the 1Gbps cable; I did not rerun the speed tests on the 100 Mbps cable):

 
 
 Ubuntu 1Gbps cable 14 ms latency/150 Mbps download/12 Mbps upload

 Win 8.1 1 Gbps cable 11 ms latency/179 Mbps download/12 Mbps upload

 
 
 Here are the results of ~$ sudo lshw -C network:
   *-network                
        description: Ethernet interface
        product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0

        bus info: pci@0000:02:00.0
        logical name: eth0
        version: 11
        serial: f8:0f:41:cd:b4:c8
        size: 1Gbit/s
        capacity: 1Gbit/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.040.00-NAPI duplex=full ip=10.0.0.138 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
        resources: irq:91 ioport:e000(size=256) memory:d0604000-d0604fff memory:d0600000-d0603fff
 
 
 Here are the results of ~$ sudo ethtool eth0:
 	Supported ports: [ TP ]
 	Supported link modes:   10baseT/Half 10baseT/Full  
 	                        100baseT/Half 100baseT/Full  
 	                        1000baseT/Full  
 	Supported pause frame use: No
 	Supports auto-negotiation: Yes
 	Advertised link modes:  10baseT/Half 10baseT/Full  
 	                        100baseT/Half 100baseT/Full  
 	                        1000baseT/Full  
 	Advertised pause frame use: Symmetric Receive-only
 	Advertised auto-negotiation: Yes
 	Speed: 1000Mb/s
 	Duplex: Full
 	Port: Twisted Pair
 	PHYAD: 0
 	Transceiver: internal
 	Auto-negotiation: on
 	MDI-X: Unknown
 	Supports Wake-on: pumbg
 	Wake-on: d
 	Current message level: 0x00000033 (51)
 			       drv probe ifdown ifup
 	Link detected: yes

Note that the autonegotiation status remained ON even after running your first command.

---

### Post by michi1983 on 2015-11-11
> **A4Skyhawk said:**
> @praseodym:
I entered the commands that you suggested  and rebooted.  On rerunning the Comcast  speed test, I got virtually the same results as I got previously (this is on the 1Gbps cable; I did not rerun the speed tests on the 100 Mbps cable):
 
Ubuntu 1Gbps cable 14 ms latency/150 Mbps download/12 Mbps upload

Win 8.1 1 Gbps cable 11 ms latency/179 Mbps download/12 Mbps upload

Well that's almost even. Speedtests are never identical. You could make 3 of them, add the speeds up and divide it by 3 to get an average speed.
But it looks like it works now as expected.

---

### Post by A4Skyhawk on 2015-11-12
Agreed that I am now getting over 100 mbps download - now that I have reliable cat5e cable setup.
And I understand that "download speed test" results can fluctuate.  All the results that I quoted above are, in fact,
averages of multiple test runs.  And ALL results of multiple speed tests, done over the course of almost 2 weeks, show that:
1) on 100 mbps cable, downloads on Win 8.1 are approx. 3x faster that on Ubuntu.
2) on 1 G cable, downloads on Win 8.1 are approx. 20% faster than on Ubuntu.

This variation between Win and Ubuntu seems statistically significant.  Just wondering if there is another explanation for it.

---

### Post by A4Skyhawk on 2015-11-13
After reading a few more threads on this subject, I found a reference to a different test site - [http://speedtest.dslreports.com](http://speedtest.dslreports.com).
Using this website, I get the same speeds (on my 100 mbps cable - did not test the 1 G cable) in Win 8.1 and Ubuntu 15.10 - averaging 93 Mb/s down and 12 Mb/s up.
When doing these tests, I also closed all other tabs in the browser, and all other apps as well.
Looks like my question/concern has been answered.  Thanks, all, for your help.

---

