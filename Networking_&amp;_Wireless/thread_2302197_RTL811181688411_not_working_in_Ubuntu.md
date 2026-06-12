---
title: "RTL8111/8168/8411 not working in Ubuntu"
date: 2015-11-08
forum: Networking &amp; Wireless
---

### Post by ajthemacboy on 2015-11-08
There are seemingly lots of solutions online to this problem but none of them work for me.

I have a pretty cheap MSI motherboard on Ubuntu Server 15.04. I only use the machine for a home Java server. I've updated to Kernel 4.3 to see if it might be fixed in that version, and it isn't.

Using```
lspci  | egrep -i --color 'network|ethernet'
``` I found my Ethernet name: RTL8111/8168/8411

Right now I'm using a USB to ethernet adapter to get it working, but needless to say it's slow ping-wise. 

How can I fix my RTL8111/8168/8411 chip?

---

### Post by pqwoerituytrueiwoq on 2015-11-08
tried the 1st answer here?
[http://askubuntu.com/questions/396804/rtl8111-8168b-rev-06-ethernet-controller-not-working-with-amd64-kernels-2-6](http://askubuntu.com/questions/396804/rtl8111-8168b-rev-06-ethernet-controller-not-working-with-amd64-kernels-2-6)
this is the file it said to download
[http://12244.wpc.azureedge.net/8012244/drivers/rtdrivers/cn/nic/0002-r8168-8.040.00.tar.bz2](http://12244.wpc.azureedge.net/8012244/drivers/rtdrivers/cn/nic/0002-r8168-8.040.00.tar.bz2)
you will probably need to have [build-essential]("apt:build-essential") installed for the script to work

you will need to reinstall the driver after every kernel update

another solution is a pci card
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166017](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166017)
* that card will not operate at full gaiabit, iirc it can only do 60-80% (i have used one)
or if you just want a nic that does what it is supposed to do 100% of the time
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833106033](http://www.newegg.com/Product/Product.aspx?Item=N82E16833106033) (Intel addon NICs are not cheap)

---

### Post by ajthemacboy on 2015-11-09
Like I said, I've tried all the answers I could find and none of them worked.

I tried downloading the driver from Realtek, running sudo ./install.sh or the equvilent, I tried sudo make install, I tried blacklisting the R8169 module and building the driver to DKMS.

Nothing worked.

I've never done this before but the instructions were simple, so I can only assume I did they correctly.

Is there something else I can try without buying a NIC?

---

### Post by howefield on 2015-11-09
Hello ajthemacboy, let's try your thread here in the "*Networking & Wireless*" forum.

---

### Post by pqwoerituytrueiwoq on 2015-11-09
can you tell of your motherboard model?
this command should get the model if you don't know it
```
sudo dmidecode -t baseboard
```
edit: make sure your bios is up to date, you never know that could be the issue (slim chance)

---

### Post by ajthemacboy on 2015-11-09
My BIOS is up to date. I decided to just paste the whole output in case you needed it:
[FONT=system]
[FONT=lucida console]# dmidecode 2.12
# SMBIOS entry point at 0x000f04d0
SMBIOS 2.8 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: MSI
    Product Name: H81M-P33 (MS-7817)
    Version: 1.0
    Serial Number: To be filled by O.E.M.
    Asset Tag: To be filled by O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To be filled by O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x003A, DMI type 41, 11 bytes
Onboard Device
    Reference Designation:  Onboard IGD
    Type: Video
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:00:02.0

Handle 0x003B, DMI type 41, 11 bytes
Onboard Device
    Reference Designation:  Onboard LAN
    Type: Ethernet
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:00:19.0

Handle 0x003C, DMI type 41, 11 bytes
Onboard Device
    Reference Designation:  Onboard 1394
    Type: Other
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:03:1c.2[/FONT][/FONT]

---

### Post by pqwoerituytrueiwoq on 2015-11-09
[http://ubuntuforums.org/showthread.php?t=2227323](http://ubuntuforums.org/showthread.php?t=2227323) (note page 2)
maybe that?
or perhaps this:
[http://askubuntu.com/questions/579041/realtek-ethernet-card-disconnnects-randomly](http://askubuntu.com/questions/579041/realtek-ethernet-card-disconnnects-randomly) (Tweak Model settings)

one of the reviews mentions linux mint has drivers for the Ethernet chip (so i would assume ubuntu does)
but just for kicks does a live mint cd/dvd work with Ethernet? if so you can check the configs it uses and try to reproduce what works on your install

OP's motherboard (if anyone want to look at something):
[http://us.msi.com/product/mb/H81M-P33.html#hero-specification](http://us.msi.com/product/mb/H81M-P33.html#hero-specification)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813130731](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130731)

---

### Post by ajthemacboy on 2015-11-10
Tried both of these and neither worked. I tried all the answers on page 2 of the post you linked.

I found a chart somewhere that said it worked by default on older Linux kernels. I don't want to backdate, but surely there's a solution, right?

---

### Post by pqwoerituytrueiwoq on 2015-11-10
at this point i would say it is not worth your time to try to make it work and just use a PCI/PCIe card
if your budget is 0 you can pull a 10/100 nic from a old junk pc from 95-2004 or find a local pc shop with them for ~$5

have you confirmed the onboard chip works with windows to make sure it is not just defective, if it is RMA is a option, but RMAing a motherboard is a pain and involves down time when you could just get a card for about the cost of the shipping

you can try older but still maintained kernels, the mainline kernel installer i link you before can install them, go ahead and try 3.2, 3.4, 3.10, 3.12, 3.14, 3.18, 4.1, or 4.2
example command to get said kernel:
```
KernelUpdateChecker -r \* -f -v 3.2
```

---

### Post by ajthemacboy on 2015-11-11
I know the port was working fine before I swapped this motherboard into my server for a new Intel CPU. I've never broken anything on a motherboard before so I kindof doubt the port is broken. 

The light turns on when I plug a cable in.

According to this post: [http://askubuntu.com/questions/396804/rtl8111-8168b-rev-06-ethernet-controller-not-working-with-amd64-kernels-2-6](http://askubuntu.com/questions/396804/rtl8111-8168b-rev-06-ethernet-controller-not-working-with-amd64-kernels-2-6)

2.6 should support it, but I really don't want to go back that far.

---

### Post by pqwoerituytrueiwoq on 2015-11-11
im not saying you broke it, onboard NICs are not the most reliable thing
i have had a just disappear from the system as if they were physically removed and the only way to get it back was to cut the psu off (integrated into my old m4a79xtd evo)

found some more detailed instructions on driver installation
[https://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](https://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)

i just ordered one of these cause i want to get WOL working, if you like i will let you know how well the card works
[http://www.ebay.com/itm/381405410100](http://www.ebay.com/itm/381405410100)
* the Qualcomm Atheros Killer E2200 driver had WOL disabled for as far as i can remember under linux

---

### Post by him610 on 2015-11-12
FWIW, I once experienced symptoms similar to yours. I eventually determined that a nearby lightning strike had entered the network through the coax cable. It took out the first router it encountered, a laser printer network interface, and the motherboard internet interface of one of our computers. The printer was still under its initial service contract, replaced the smoked router, and replaced the defective motherboard.

---

### Post by ajthemacboy on 2015-11-13
I guess being broken is pretty plausible, considering all I've tried.

I'm considering upgrading to a new motherboard soon, since I want to overclock. If I order a NIC now, I want it to be worth it even if I buy a new motherboard, so the NIC needs to be faster and lower latency than any integrated chip I might get.

Any suggestions under 20$?

---

### Post by ajthemacboy on 2015-11-13
Also, does a PCI Express x1 card perform slower than a PCI Express x16 card? 16 has more bandwidth, but is it faster? And is this speed even noticeable?

---

### Post by pqwoerituytrueiwoq on 2015-11-13
yes PCIe x16 is faster than PCEe x1, however we are not using a fiber optic connection here, we are just use a mere gigiabit connection, or do you have some crazy fancy network setup callable of 10Gbps, if so a NIC of that ability will run a few $100 easy
* My $6.25 used PCIe x1 NIC from ebay should be here Monday so i will let you know how it goes  and compare it to my Qualcomm Atheros Killer E2200

---

### Post by pqwoerituytrueiwoq on 2015-11-16
my NIC arrived today and it looks brand new, not a spec of dust on it
```
chad@Z97K1LLER:~$ iperf -c 10.0.0.126
------------------------------------------------------------
Client connecting to 10.0.0.126, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 10.0.0.50 port 53461 connected with 10.0.0.126 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.10 GBytes   942 Mbits/sec
chad@Z97K1LLER:~$ iperf -c 10.0.0.126 -d
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 10.0.0.126, TCP port 5001
TCP window size:  366 KByte (default)
------------------------------------------------------------
[  5] local 10.0.0.50 port 53490 connected with 10.0.0.126 port 5001
[  4] local 10.0.0.50 port 5001 connected with 10.0.0.126 port 55373
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-10.0 sec  1.09 GBytes   938 Mbits/sec
[  4]  0.0-10.0 sec  1.08 GBytes   930 Mbits/sec
chad@Z97K1LLER:~$ ping 10.0.0.126
PING 10.0.0.126 (10.0.0.126) 56(84) bytes of data.
64 bytes from 10.0.0.126: icmp_seq=1 ttl=64 time=0.174 ms
64 bytes from 10.0.0.126: icmp_seq=2 ttl=64 time=0.207 ms
64 bytes from 10.0.0.126: icmp_seq=3 ttl=64 time=0.167 ms
64 bytes from 10.0.0.126: icmp_seq=4 ttl=64 time=0.190 ms
64 bytes from 10.0.0.126: icmp_seq=5 ttl=64 time=0.137 ms
64 bytes from 10.0.0.126: icmp_seq=6 ttl=64 time=0.221 ms
64 bytes from 10.0.0.126: icmp_seq=7 ttl=64 time=0.173 ms
^C
--- 10.0.0.126 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6000ms
rtt min/avg/max/mdev = 0.137/0.181/0.221/0.027 ms
chad@Z97K1LLER:~$ lspci | head -1
06:00.0 Ethernet controller: Intel Corporation 82572EI Gigabit Ethernet Controller (Copper) (rev 06)
```
edit:
spec sheet
[http://ark.intel.com/products/20719/Intel-82572EI-Gigabit-Ethernet-Controller](http://ark.intel.com/products/20719/Intel-82572EI-Gigabit-Ethernet-Controller)

---

### Post by praseodym on 2015-11-17
Have you tried a simple:
```

sudo apt-get install r8168-dkms
```

---

