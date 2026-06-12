---
title: "Slow gigabit, edgy and win2003"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by cytg on 2007-01-19
reading is 15-20 meg/sec
writing is ~7-10 meg/sec

here's my setup

ubuntu 6.10, gigabit nic, 500G pata hd
dlink gigabit switch (lights up green = gigabit for the two pc's yellow for the router = 100mbit)
windows2003 gigabit nic too (3ghz p4)

got samba going figured i'd use it as a nas box
problem is reading from the samba share is max 20megs/sec and writing is max 10megs.. i think i should see better speeds than that right ?
I did all the hdparm on the ubuntu box, should be good.
weird thing is, especially when writing, it seems to go in bursts .. it will run, pause, run, pause (using totalcommander, gives me kbs measuring)

I figure the gigabit connection is established since the switch is glowing green and i got 20megs/sec with is over 100mps...

CPU on the ubuntu is ~30% max


But i'd sure like it to go faster, any ideas ?

---

### Post by cytg on 2007-01-19
[http://www.ubuntuforums.org/showthread.php?t=143982&page=2&highlight=slow+gigabit](http://www.ubuntuforums.org/showthread.php?t=143982&page=2&highlight=slow+gigabit)

same issue different hardware ? no resolution though

nic in nix is dlink dge 530t, windows is Broadcom NetXtreme Gigabit Ethernet

everything was autodetected in ubuntu install

---

### Post by cytg on 2007-01-20
help ?

---

### Post by MetalMusicAddict on 2007-01-20
How long would it take to move say, a CD .iso image? On my gigabit network it takes about 25 seconds. Im unsure but your  speeds look about right.

---

### Post by cytg on 2007-01-20
then you're still getting around 28megs/sec wich is still on the low side isnt it? plus you're still about 50% above me ..

---

### Post by MetalMusicAddict on 2007-01-20
Thats not slow at all. To get a real 28mb/ps? I actually think when I look at my stats its about 17mb/ps. You'll never actually get 1000mb throughput. I can move a DVD-9 image in about 5 mins. Im cool with that. ALOT better then 10/100. Its no faster on windows than linux.

Hopefully someone can better explain it than me.

So how long does it take you to move a CD .iso?

---

### Post by netztier on 2007-01-20
> **MetalMusicAddict said:**
> You'll never actually get 1000mb throughput. 

Actually coming close to full gigabit means a bit of work. At work, we run (almost) all our servers with Gigabit, a whole mixture of Solaris 9 and 10, Windows Server from 2000 to 2003 at different SP levels. Even some Aplha boxes with VMS are still left.

On the backup server (a Sun Fire V480, with 4x 900MHz UltraSPARC III) , it took a true TCP/IP-on-Solaris guru a whole week fine-tuning the parameters on the IP stack until it would max-out the server's Gigabit NIC. Turning on TCP offload on the NIC and making sure that gigabit flow control modes were properly agreed on by both switch port and NIC was among the first steps. Finally, the server it would reach sustained ~120MBytes/s (> 97% bandwith usage) for several hours through the night, and this only while pulling data from several servers simultaneously.

On the other hand, stuffing away or delivering >120MBytes/s is nothing trivial, not for a normal PC with normal harddisks, be that SATA, PATA or SCSI. In our case, it's done by a storage box two kilometers away from the server, connected via a 2Gbit/s FibreChannel-SAN.

If you'd like to get a rough estimation of what your NICs and network are capable of, try **iperf** from the universe repositories. It's also available for Windows and other OSs at [http://dast.nlanr.net/Projects/Iperf/](http://dast.nlanr.net/Projects/Iperf/) .

The same executable file can be ran in "server" or "client" mode, on each of the involved machines. If no special parameters are used - the client sends data to the server at max speed for 10 seconds on tcp/5001 and then reports throughput it has reached.

Using multiple streams at once (parameter **-P 4**) and increasing the tcp window size to someting like 256kBytes (parameter **-w 256k**), you can increase throughput considerably.

But remember: this is only raw TCP throughput with generated packet payload. It is  avoiding disk and other bus I/O. But it can help you find out where the bottleneck might be. Chances are good that it's not the NICs nor the switches but rather bus systems and I/O performance on the end systems.

best regards

Marc


PS: if you have two linux or unxoid boxes, use NFS for a try. On my personal 100Mbit/s network, Samba (6-7MByte/s) is just not able to keep up with NFS (>11MBytes/s).

---

### Post by cytg on 2007-01-20
Thanks !! I'll get right on it :-)

---

### Post by cytg on 2007-01-20
results so far!

standard settings
windows server, ubuntu client : 200mbits/sec
windows client, ubuntu server : 250mbits/sec

-P 4, -w 256K
windows server, ubuntu client : 320mbuts
windows client, ubuntu server : 390mbits/sec
 
its somewhat higher numbers, to be expected i suppose, but still not 'there' ? (ill cont. to play around with it)

---

### Post by cytg on 2007-01-20
would a loopback connection with said tool test the local nic only ? or would it bypass the actual hardware ?

---

### Post by cytg on 2007-01-20
doing loopback tests with two iperf's, interresting things surfaces..

loopback test on the ubuntu reports 1.63Gbits/sec .. nice right, cpu at 80% (700mhz K7-tbird)

loopback test on the win2003 reports 230Mbits/sec .. wtf right ? cpu is maxed out and this is hyperthreading and all at 3.0Ghz... could indicate the windoze box is the problem child no ?

---

### Post by netztier on 2007-01-21
> **cytg said:**
> 
standard settings
windows server, ubuntu client : 200mbits/sec
windows client, ubuntu server : 250mbits/sec

-P 4, -w 256K
windows server, ubuntu client : 320mbuts
windows client, ubuntu server : 390mbits/sec
 

Hm. That's not really high. What type of Gigabit NICs are these? Do you know how they are connected to the system? PCI Cards, PCI-X 66MHz, PCI-Express? Part of the chipset sitting right on the system bus?

Check driver settings for TCP offload or "TCP Checksum Rx/Tx" features and activate them. On Linux, use **ethtool** or **mii-tool** and **mii-diag** to see if flow-control is active or not.

Offloading TPC cecksum calculation to the card will leverage the load on the CPU somewhat. On the other hand: keeping a gigabit pipe full is a bit of work, however many MHz of CPU clock and bits of system bus width you throw at it.

Checking against a loopback interface is not a bad idea, but might also rather reveal the IP stack's performance instead of the NICs. I'm not sure how to interprete such a result.

---

### Post by cytg on 2007-01-21
both nics are on the pci bus, the slow one is integrated and on the 3ghz windows box, the other is a dlink-something and on a underclocked 700mhz K7(the fast one).

I've done some futher testing in the meanwhile

tested winxp vmware wich got ridicculus low performance, so thats irrelevant.
tested win2003server 4-way 800mhz at work (still iperf) wich also came back very slow at 200Mbps
tested a loopback ftp session on the windoze box at home, wich topped around 290Mbps.

about to install XP SP2 on my home box here, dualboot with win2003, just to test this ****.

ed. the integrated(slow) nic is broadcom netextreme 5780 .. allready updated the driver to the newest, same result!

---

### Post by cytg on 2007-01-21
fresh install of XP SP2 and the loopback test came back 450-480Mbps .. thats almost double up.. while still not good even for a pci giga nic, its a hell of alot better!

---

### Post by cytg on 2007-01-21
550mbps with a driver update .. or rather downgrade.. for the netxtreme nic..

---

### Post by netztier on 2007-01-22
> **cytg said:**
> 550mbps with a driver update .. or rather downgrade.. for the netxtreme nic..

still: is this a loopback test? Then take into consideration that might not be measuring your NIC's performance but also a great deal of internal shoving-around of data chunks in memory. These results might not be representative if you can't compare between different OSs on identical hardware.

Again: have you checked the availability of "TCP offload" in the Windows driver and activated it?

Another hint: take the LAN switch out of the equation and use a direct cable. With 1000baseTX, it doesn't even have to be a crossover one. Like this, you remove one component that could have an influence.

best regards

Marc

---

