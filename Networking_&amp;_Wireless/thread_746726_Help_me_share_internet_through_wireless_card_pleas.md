---
title: "Help me share internet through wireless card please!"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by s3a on 2008-04-05
lspci:

"lspcideniz@deniz-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:04.0 Mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 13)
01:09.0 Communication controller: ESS Technology ES2838/2839 SuperLink Modem (rev 01)
01:0a.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
01:0b.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
04:00.0 VGA compatible controller: ATI Technologies Inc RV380 0x3e50 [Radeon X600]
04:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600] (Secondary)
deniz@deniz-desktop:~$"
________________________________________________________________________________________________
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101)
_______________________________________________________________________________________________
uname -a:

"uname -0deniz@deniz-desktop:~$ uname -a
Linux deniz-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
deniz@deniz-desktop:~$"
________________________________________________________________________________________________
I want to use my Airlink 101 wireless card to share my dial-up internet wirelessly. I am using Ubuntu 7.10 32-bit. Help me please!

---

### Post by dmizer on 2008-04-06
well, here's one part of what you'll need:
[https://help.ubuntu.com/community/InternetConnectionSharing?](https://help.ubuntu.com/community/InternetConnectionSharing?)

as for sharing it wirelessly ... you may not be able to.  can your card be configured as a wireless access point?  if so, it may be possible, but difficult (i've never done it so i don't know where to point you).

you may be better off buying another piece of equipment like a wireless hub or router.

---

### Post by s3a on 2008-04-06
Ok I did the host comp part, but on the client comp part I don't understand what to put in the parts of the terminal commands that I need to replace. 

I also don't understand how the hardware has to be put for this sharing to happen. By that I mean, do I use a router, do I just connect an ethernet cable from this comps' mobo ethernet to laptops built in ethernet? Like what kind of setup do I need in the first place?

I assume there was nothing to change in the host terminal commands except for the eth0 to be ppp0...am I right? (I am trying to share dial-up internet) I have a wired router, a wireless card and a wireless usb adapter...I can do it wirelessly or with a wire but I'd prefer using a wire.

I'm sure the what to replace in the terminal commands of the client comp part is not hard to figure out, but I'm stupid :(

Anyway, please help me!

---

### Post by dmizer on 2008-04-06
okay ... physical setup will look like this:

wall -ppp0-> ubuntu -ethernet-> router -ethernet-> rest of network.

you will have to go into your router settings and disable NAT, so the router does not do any routing (your ubuntu computer will be doing the routing instead).  this way, your router will not be functioning as a router but as a hub.

your iptables command should look something like this:
```
$sudo iptables -A FORWARD -i eth1 -o [COLOR="Red"]ppp0[/COLOR] -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
$sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
$sudo iptables -A POSTROUTING -t nat -j MASQUERADE
```
where eth1 is your WIRED gigabit ethernet adapter.

finally, you will need to set both eth1 and your second computer for static ip (specifically 192.168.0.x).

if you don't know what your gigabit adapter is designated as, you can find out by looking under system > administration > network

---

### Post by s3a on 2008-04-08
"finally, you will need to set both eth1 and your second computer for static ip (specifically 192.168.0.x)."

x being what in my case?
______________________________________________________________________________________
"if you don't know what your gigabit adapter is designated as, you can find out by looking under system > administration > network"

Where in network do I look? and the part where I set static ip is done on host comp, right?
______________________________________________________________________________________
The commands you told me...those are the commands I've typed in succesfully. What I need to know is what command(s) I type on the client comp (laptop).

---

### Post by s3a on 2008-04-08
Having read again...static ip has to be entered on both comps?? Is the static ip the exact same number for both comps?

Thanks!

---

### Post by s3a on 2008-04-08
borris.morris brought me a step further...for the client part though, in the terminal commands on that wiki link; ip=192.168.0.2 (host=192.168.0.1)? What's a nameserver and what would I type in the terminal for the <nameserver> blank part of the terminal command that I need to put, that the wiki says?

---

### Post by dmizer on 2008-04-08
yes, both the server and the client must not have the same ip address.

with the nameservers (DNS servers), you can do one of three things:
1) you can use your ubuntu machine's ip address (192.168.0.1)
2) you can use your ISP provided DNS server addresses
3) you can use a third party DNS service like OpenDNS

for testing, you should probably stick with option 1.

---

### Post by Six_Digits on 2008-04-08
Did you guys get this working? If so, do you think I could follow the same guidelines for [my problem]("http://ubuntuforums.org/showthread.php?t=749573")?

---

### Post by s3a on 2008-04-10
dmizer, 
1) i made my client 192.168.0.**2** and host 192.168.0.**1**...is that not ok?
2) I don't understand
3) I don't understand

Six_Digits,
I haven't solved my problem yet...

---

### Post by s3a on 2008-04-10
dmizer, would it be possible for u to check things for me through Remote Desktop please [for host comp] (to see if I did something wrong)?

P.S.
borris.morris told me to go to system-->administration-->network and made a static ip connection and when I tick the box to enable that connection my dial-up internet doesn't work.

---

### Post by dmizer on 2008-04-10
i could probably get you working by logging in via ssh (remote desktop would be impossible over dial up), but then you wouldn't have done it yourself.  > **s3a said:**
> dmizer, 
1) i made my client 192.168.0.**2** and host 192.168.0.**1**...is that not ok?
2) I don't understand
3) I don't understand

Six_Digits,
I haven't solved my problem yet...

your settings look perfect, but let's try a couple more things.  now, in windows, make sure the following information is entered under control panel > network connections > local area connection > properties > internet protocol (tcp/ip) properties:

"use the following ip address:"
IP address: 192.168.0.2
Subnet mask: 255.255.255.0
Default gateway: 192.168.0.1

"Use the following DNS server addresses:"
Preferred DNS server address: 192.168.0.1
Alternate DNS server address: blank

this is all you need for your client setup.

then from ubuntu, post the output of:
```
sudo ifconfig
```

i'll give you the exact ubuntu commands you'll need in order to get ICS working.

edit:
nearly forgot ... but unless you have a hub between your ubuntu computer and your windows computer, the ethernet cable between your ubuntu machine and your windows machine will have to be a "crossover" type cable.  you can pick one of these up at any computer store.  if you can't find them, just ask for a "crossover cable".  if they look at you like you're from mars, find a different computer store.

---

### Post by s3a on 2008-04-12
Changes in network inside windows affect Ubuntu?!?

My host comp dual-boots with Ubuntu 7.10 & Windows XP, my client (laptop) only boots Ubuntu. (Just making sure the situation is clear)

I'll go do what you said soon assuming, you didn't misunderstand my setup or anything.

I'm not sure if the cables for my router are crossover cables but I use to have a super short crossover cable for ftping to my xbox but its too short anyway...this last bit wasn't exactly useful information

---

### Post by dmizer on 2008-04-13
okay ... please explain your physical setup.  what computer/os is where, what cabling is where, and what other kind of equipment is where.

for example, my network is setup like so:

[wall] -ethernet-> [DSL modem/router] -ethernet-> [GB switch] -ethernet-> [ubuntu desktop]

yours might look something like this:

[wall] -phone line-> [ubuntu/windows desktop? (dual boot)] -ethernet-> [router?] -ethernet-> [ubuntu laptop?]

post the output of:
ifconfig

from the first (host) computer when booted into ubuntu, as well as the client.  you should be able to follow the howto nearly word for word.  the last part about "add gateways" should be ignored if you are using anything newer than dapper on your client.

---

