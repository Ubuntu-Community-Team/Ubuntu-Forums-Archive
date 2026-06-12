---
title: "NIC can't communicate with DHCP"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by Zyrshnikashnu on 2007-07-11
Today I installed Ubuntu 7.04 on a brand new Dell Inspiron 1420 laptop. It has two networking adapters: A Broadcom Dell Wireless 1390 WLAN Mini-PCI card and a Broadcom ethernet card in the 57xx series.

I am completely disconnected from my home network. When wireless failed to connect, I thought I'd connect an ethernet cable and try using NDISWRAPPER. Unfortunately, my router won't give the laptop an address. The adapter functions properly in Windows, however.

It's difficult to post terminal outputs when the computer is in no way connected to this one, so I'm afraid I won't post any here, aside from one:

sudo ifup eth0
```
Listening on LPF/eth0/00:18:8b:fc:7f:9f
Sending on   LPF/eth0/00:18:8b:fc:7f:9f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
Another note: DHCP seems to work fine otherwise. It assigns addresses to two other computers and a Playstation without issue.

---

### Post by kevdog on 2007-07-11
So let me get this straight

The wired ethernet connection will not connect??? 

Ok here is what I would do to just test the wired connection to get it up and running.  Type at command prompt:

Try the following assuming eth0 is you interface name:

```

sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.100 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1

```

Check with  
ifconfig

Again substitute numbers that are appropriate for you

---

### Post by Zyrshnikashnu on 2007-07-11
No output from your three listed commands (I presume that's a good thing), and ifconfig says I'm at IP 192.168.1.100, but I still can't access my network. Pointing my browser to [http://192.168.1.254](http://192.168.1.254) (my router gateway, fow which I replaced 192.168.1.1 in your above example) still gets me a "server not found" error.

Furthermore, the Network Manager icon next to the clock indicated that I am not connected to a network.

---

### Post by DaveTRG on 2007-07-12
Same problem here on my new Inspiron e1420 laptop, only I have the Intel wireless card so I have wireless working but WIRED ETHERNET DOESN'T WORK =P  

ifconfig does return the MAC address of the card and I can successfully load the kernel module using "modprobe tg3"

I tried to download the driver and recompile from Broadcom's site, but it errors out during the make.

Here's what I get when I try to compile:

```
dave@computer02:~/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d$ sudo make
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.o
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c:18:26: error: linux/config.h: No such file or directory
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c: In function &#8216;tg3_start_xmit&#8217;:
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c:3905: error: &#8216;CHECKSUM_HW&#8217; undeclared (first use in this function)
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c:3905: error: (Each undeclared identifier is reported only once
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c:3905: error: for each function it appears in.)
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c: In function &#8216;tg3_start_xmit_dma_bug&#8217;:
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c:4043: error: &#8216;CHECKSUM_HW&#8217; undeclared (first use in this function)
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c: In function &#8216;tg3_request_irq&#8217;:
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c:6855: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c: In function &#8216;tg3_test_interrupt&#8217;:
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c:6872: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c:11683:47: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c: In function &#8216;tg3_init_one&#8217;:
/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.c:11683: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
make[2]: *** [/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d/tg3.o] Error 1
make[1]: *** [_module_/home/dave/Server/Linux/Driver/tg3-3.66d/debian/tg3/tg3-3.66d] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2

```

Next, I tried to take the rpm that they provide and convert it using alien but they don't have a 64bit (amd64) option and I'm using that build of Feisty.  

At this point I'm kind of lost, the card appears to get an address if I use ifconfig to configure it, but I can't even ping the default gateway.  Wireless works fine using the same commands to configure (I usually take it down through "ifconfig eth1 down" when testing the wired as well)

Any assistance will be greatly appreciated.  Thanks.

---

### Post by DaveTRG on 2007-07-14
Upgrading to Gutsy got this working (but broke compiz fusion).

I used the following method, which is probably not the recommended one:

```
sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
```

---

