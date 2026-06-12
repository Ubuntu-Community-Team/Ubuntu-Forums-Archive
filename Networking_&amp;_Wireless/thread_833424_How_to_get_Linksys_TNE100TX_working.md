---
title: "How to get Linksys TNE100TX working?"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by Dawgwalker on 2008-06-18
Any mtbiking, HH specialist willing to tackle ethernet problem?

HH installed but couldn't configure network automatically.  HP Pavilion Celeron 2m RAM, 400mhz, Linksys TNE100TX Ver 1.2, self-installed, don't think HP had NIC at purchase.  I've network this card with W98 and W2K to my Linksys WRT54G router that has 4wired ports and 802.11G wireless.

I cannot get networking.

Manually enable network, configured for DHCP.  No networks show to connect to.

These command result come from screen prints and are not total results because I have to type on a internet capable Vista machine.  I'm trying to give the results that are garmane.

lspci

  Ethernet controller: ADMtek NC100 10/100

Note! Not Linksys!  May have been onboard the motherboard but never install a ADMtek pci card.

ifconfig eth0

  Link encap: Ethernet HWaddr XXXXXXXXXX
  RX packets: 0
  TX packets: 0
  collisions: 0
  RX bytes:0
  Base address: 0x3000

That's it.

No eth1

I'm thinking no Linksys.

The Linux drivers on install CD we are still struckling with.

Give me direction, please.

---

### Post by chili555 on 2008-06-18
Linksys is not the first, last or only manufacturer to market someone elses chipset in their shiny blue box. I have one of these in my desktop machine and it works perfectly.> No networks show to connect to.
That's for wireless; with wired ethernet, you have a connection to the network you are wired to, or you do not. With wireless, there may be 3-4 networks broadcasting for you to choose from.

Please try from a terminal:```
sudo modprobe tulip
sudo dhclient eth0
```Did you get an IP address? If the driver module *tulip* is not being loaded, we can force it.

If you do not connect, please post:```
sudo lshw -C network
```Thanks.> The Linux drivers on install CD we are still struckling with.For too many reasons to elaborate, forget about them.> Any mtbiking, HH specialist willing to tackle ethernet problem?Roadies need not apply?

---

### Post by Dawgwalker on 2008-06-18
sudo lshw -C network 
unable to resolve host "    "

I get the "unable to resolve host" for the sudo commands.

Sure I'm not getting a IP because non shows in my DHCP client tables at the router.

Appreciate roadies because they, as I was, are our best converts.
If you help me solve my problem I'll try to turn you from the dark side.

---

### Post by Dawgwalker on 2008-06-18
Roadie, went into root to execute your suggested commands got screens of info.  Most pertinent I think is
"No Network"

What bike do you ride?

---

### Post by chili555 on 2008-06-18
> I get the "unable to resolve host" for the sudo commands.Not good. Please let us see:```
sudo su
cat /etc/hosts
```Perhaps we need to fix problem #1 before we go on to #2. This smells like either a botched installation, perhaps because of a corrupted install disk, or someone (?) has wielded the light saber a bit too soon in their Jedi training. That is, made changes to files without realizing their full implications.> Most pertinent I think is "No Network"Actually, the most pertinent is the presence or absence of a logical name and driver, like this:```
 *-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: **eth0**
       version: 11
       serial: 00:0c:41:26:d1:bf
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes **driver=tulip** driverversion=1.1.15 ip=192.168.1.116 latency=32 maxlatency=128 mingnt=64 module=tulip multicast=yes
```Did our modprobe of *tulip* stick? Are any of the LEDs on the card glowing or blinking? Is the corresponding LED on the router on?

I know it's difficult to post the results of commands from a machine which is not connected to the internet. I have used a thumb drive. If you do:```
cat /etc/hosts > hosts.txt
```you will find a little text file in your Places -> Home Folder that you can drag-n-drop to the thumb drive.

I ride a Giant OCR2 Composite in glorious carbon-fiber...when I am not on my Trek 6700.

---

### Post by Dawgwalker on 2008-06-19
OCR is a beauty.  Trek 6700?  I'm thinking MTB. First MTB was an 8500.

Mine is a mid-ninties Litespeed Ultimate when I can't ride the Titus Switchblade.

My friend is a Linux programer who was trying to load the Linksys drivers but they error out when trying to compile.

Thanks!

---

### Post by chili555 on 2008-06-19
> Trek 6700? I'm thinking MTBCorrect.> Linksys drivers but they error out when trying to compile.Correct. I strongly suspect they are too old for a 2.6.24-xx kernel. However, the driver built in to your installation, *tulip*, should work perfectly. 

What happens when you:```
sudo su
/etc/init.d/networking restart
```Does it work or does it have lots of errors?

---

### Post by Dawgwalker on 2008-06-19
When running HH all out and on terminal sudo cannot resolve host name.

Reboot to recovery with terminal shell and at root

no errors but in abbreviated terms

DHCPDISCOVER on eth0
network down
no DHCP offers
autoipd exited with return code 2

My Linux buddy and I are going riding to ponder life and ubuntu.  Come join us.  We're outside of Greensboro, NC.

---

### Post by chili555 on 2008-06-19
I am still interested in your */etc/hosts* file. Something is fishy.

I wish I could ride today but my wife is recovering from surgery. I am on chicken soup duty.

---

### Post by Dawgwalker on 2008-06-19
chilli555, hope you wife is ok.  do you ever ride the charlotte area.  just got back from a mountain ride with my linux expert.  we decided to do a new install of hh.

of note is that hh install could not do auto net config from a router port or direc from the cable modem.  sys no dhcp service available and i went back to retry several times.

it's finishing now so we should have eliminated any linux changes.

do drivers reside in hh or do i get them elsewhere? i think there's no linksys driver installed.

---

### Post by chili555 on 2008-06-19
I ride locally, in and around Lake Wylie, not so much for the adventure or camraderie, but to keep the cardiologist and grim reaper at bay.

Many drivers reside in Ubuntu and, in general, in Linux. In particular, the driver you need, *tulip* is there waiting. If you can run:```
sudo lshw -C network
```you should see something like what I posted above, from my desktop machine. If the router and CAT5 cable are working correctly, you should be able to connect automatically on boot.

Since this is a desktop machine, and you will not be going down to Starbucks or the library to search for networks to connect to, I would uninstall Network Manager and dhcdbd and set up your /etc/network/interfaces file like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```Then it will connect on boot.

---

### Post by Dawgwalker on 2008-06-20
ifconfig eth0


eth0      Link encap:Ethernet  HWaddr 00:14:bf:5b:9c:29  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x3000 
 
Chilli555, from your instructions I've learn to make text files.
The above is my response to if config.  Can now sudo from terminal.  

Verified cat 5 cable, router port on laptop running XP. Every attempt to force network indicates no contact with dhcp server.

Even riding off a bridge into the creek yesterday seems easier than this.

Doug

---

### Post by chili555 on 2008-06-20
Is *tulip* loaded?```
lsmod | grep tulip
```What happens when you do:```
sudo dhclient eth0
```I don't need to see the whole thing, just tell us if you connected or timed out. What does:```
dmesg | grep eth0
```tell us? Thanks.

---

### Post by Dawgwalker on 2008-06-20
lsmod | grep tulip

tulip 535360

dmeg | grep eth0

[   29.605910] eth0: ADMtek Comet rev 17 at Port 0x3000, 00:14:bf:5b:9c:29, IRQ 0.

---

### Post by chili555 on 2008-06-20
All looks fine. What about *dhclient*?

---

### Post by Dawgwalker on 2008-06-20
doug@coxnet:~$ ifconfig eth0 > ifconfig
doug@coxnet:~$ sudo dhclient > dhclient.txt
[sudo] password for doug: 
There is already a pid file /var/run/dhclient.pid with pid 6143
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
Listening on LPF/eth0/00:14:bf:5b:9c:29
Sending on   LPF/eth0/00:14:bf:5b:9c:29
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
doug@coxnet:~$ sudo dhclient eth0  > dhclient.txt
There is already a pid file /var/run/dhclient.pid with pid 6330
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
Listening on LPF/eth0/00:14:bf:5b:9c:29
Sending on   LPF/eth0/00:14:bf:5b:9c:29
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
doug@coxnet:~$ 


Had a little problem making test file.  Apologies for volume of info.

---

### Post by chili555 on 2008-06-20
I feel like the harder we pedal, the slower we go! Every post is a new revelation that's muddier than before. Please show me:```
dmesg | grep IRQ
sudo ethtool eth0
```Thanks.

---

### Post by Dawgwalker on 2008-06-20
[   24.266101] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.270934] 00:10: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.277500] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[   24.278469] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.937259] PCI: No IRQ known for interrupt pin A of device 0000:01:0e.0. Please try using pci=biosirq.
[   29.383758] uhci_hcd 0000:00:1f.2: irq 11, io base 0x00001820
[   29.498446] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x1800 irq 14
[   29.498460] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x1808 irq 15
[   58.536061] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]

---

### Post by chili555 on 2008-06-21
I believe you gave me:```
dmesg | grep irq
```but I asked for:```
dmesg | grep IRQ
```Let's get case out of the equation with:```
dmesg | grep -i IRQ
```This is a bit troubling already:> PCI: No IRQ known for interrupt pin A of device 0000:01:0e.0. Please try using pci=biosirq.It makes me wonder how the IRQs are set in the computer's BIOS.

---

### Post by Dawgwalker on 2008-06-21
You may be hitting on something with the BIOS.  I remember Windows allowed multiple devices on a single IRQ and there were setup requirements for that.  Will take a look at that and then get the suggested command responses.

Thanks so much for the help.  I know this is time better spent riding the bike.

Doug
[email]dcox61@triad.rr.com[/email]

---

### Post by Dawgwalker on 2008-06-21
Chilli555

This reply comes from the ubuntu machine.  I made changes in the bios and internet came up.

How do I give you one of the ¨Thanks¨ for solving a problem?

---

### Post by chili555 on 2008-06-21
Great! Glad it's working for you! Now we can both wash and Bike Lust the bikes.

There is a medal with a star at the bottom of my posts. Please click it and I thank you for your kind comments.

---

