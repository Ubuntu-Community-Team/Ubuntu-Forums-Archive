---
title: "No network connection - Please help!"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by BallisticBanana on 2007-01-19
Hi anyone!

Brand new user with multiple problems (network, sound, plus totally screwed the Windows XP dual-boot), but the first one I need to solve is that I cannot get a network connection.  

Version installed is Ubuntu 6.10

I have disabled sound as the system was unbelievably slow - now speed is OK.

Overview...
LAN chip is onboard the motherboard - Realtek RT8139
ADSL Modem/Router is Netgear DG834G
IP address of the router is 192.168.1.1
DHCP is ON

Ubuntu appears to recognise the device when running 'Device Manager' - though I can't be sure as the interface is new to me..

I have tried setting the device within 'Network Settings' to be configured automatically using DHCP and also by setting up manually - I used the same settings that I know worked in WinXP (IP: 192.168.1.100, Subnet mask: 255.255.255.0, gateway: 192.168.1.1).

I hope that if I can at least get a network connection I can then look for drivers (working?) for the Audigy card and maybe even fix my WinXP setup without re-installing everything!

Any help would be greatly appreciated...

---

### Post by mssever on 2007-01-19
First, are we talking about wired or wireless networking? If wired, let's do some troubleshooting. First, go to Applications > Accessories > Terminal. Type ```
ifconfig
``` If you have an IP address, you should see it listed--normally under eth0. If not, then try to set a static IP for now.

Next, try to ping your router: ```
ping 192.168.1.1
```
If that succeeds, then you're connected so far--you should be able to ping yahoo.com unless your router or modem is mis-configured; otherwise, I need more information. Please post the results of these troubleshooting steps.

---

### Post by BallisticBanana on 2007-01-19
Thanks for the reply MSSEVER.

Firstly, this is wired networking.

Currently, I have set the static address to be 192.168.1.101, mask to 255.255.255.0, gateway to 192.168.1.1

ifconfig brings up a load of text .. (I'll have to type it in here as no network connection to copy it over with...)

eth1
Link encap:Ethernet  HWaddr 00:20:ED:33:18:98
inet addr:192.168.1.101  Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::220:edff:fe33:1898/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metrix:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)  TX bytes:(0.0b)
Interrupt:10 Base address:0xcd00

lo
<a lot of stuff in here also - guessing you don't need this?  Save me typing it all out again!>


'ping 192.168.1.1' brings up :

...
From 192.168.1.101 icmp_seq=xx Destination Host Unreachable
...

Just lots of 'unreachables' (and its still going!)



Been searching through lots of previous questions and thought I'd try to disable IPv6 as that seems to have worked for some people, but no luck doing that yet.

Thanks again for the help - anything else I can try?

---

### Post by koenn on 2007-01-19
your config looks fine on first sight.
see if you can ping your own computer by executing the following commands

```
ping 127.0.0.1
```
```
ping 192.168.1.101
```
you can stop the pinging by hitting Control + C

tell us what you get from these.
Also, check that thecable between you computer and the router is plugged in correctly - it's quite strange that you get "host unreachable" while your ip addresses are correct.

---

### Post by BallisticBanana on 2007-01-19
Koenn,

Can ping both 127.0.0.1 and 192.168.1.101 with minimal response times.

The cable is in both sockets just fine.  However, a strange thing I've noticed is that when I try to ping the router (192.168.1.1) the port indicator on the router flashes a couple of times then stays constantly on - so it looks like some signal is getting through but is not being interpreted correctly.

I'll look for any info on incompatibilities between Linux and the Netgear DG834 on their website.  Plus, will switch off and on the router again.

---

### Post by koenn on 2007-01-19
do you happen to know what kind of cable you are using ? can you be pretty sure it is not a cross-link (cros-over, whatever you wnat to call it) cable, just an ordinary (straight through) network cable ?

Does the nic in your pc has any indicator lights that could give a clue (such as 'link', 'activity', ...)

---

### Post by BallisticBanana on 2007-01-19
Koenn,

The cable is not a crossover, but I have just connected another to check - no difference.
There is a green light at the PC port showing a connection.  When I ping it it just does 1 flash of the yellow activity LED every 3 or 4 seconds (or so).

Also, power cycle of the ADSL modem/router made no difference.
Can't find any specific info on the Netgear website.

Could it possibly be an IPv6 issue?  Obviously, as a noob, I'm shooting in the dark here.

---

### Post by mssever on 2007-01-19
> **BallisticBanana said:**
> Koenn,

The cable is not a crossover, but I have just connected another to check - no difference.
There is a green light at the PC port showing a connection.  When I ping it it just does 1 flash of the yellow activity LED every 3 or 4 seconds (or so).

Also, power cycle of the ADSL modem/router made no difference.
Can't find any specific info on the Netgear website.

Could it possibly be an IPv6 issue?  Obviously, as a noob, I'm shooting in the dark here.
It might be IPv6...or it might not be. I've never had to mess with it before.

Do you perhaps know someone who would lend you their router for a bit? You could then find out whether the problem is your computer or the router. It wouldn't even have to be connected to the Internet during the test.

As far as I can tell, all your computer's settings are correct.

---

### Post by koenn on 2007-01-19
I agree, pc config looks OK and working, and physical stuff looks fine as well.
Is there any way you can verify that the router's ip address is really 192.168.1.1 ? 
You said you used that address as gw in xp so it should be ok, unless you can remember something you've done that may have changed it.

---

### Post by BallisticBanana on 2007-01-19
MSSEVER,

I'll have to try and borrow a router tomorrow.  I'm giving up for tonight.

It looks like the DG834 doesn't support IPv6 so I'm going to try and disable it tomorrow to see if that makes any difference.  

Thanks for everyone's help - I shall be back tomorrow asking for more!

---

### Post by BallisticBanana on 2007-01-19
Koenn,
Just spotted your post.

Yep, can confirm the router address is 192.168.1.1 - I've been connecting my MacBook to the webserver on it so I can check status etc.

This is an interesting one eh?  Another thing I will try tomorrow is disabling the onboard LAN chip through the BIOS and installing a network card in a PCI slot - I found one earlier this evening.  Worth a try anyway ...

---

### Post by koenn on 2007-01-19
interesting. and weird. Especially as your Mac seems to connect without trouble. 
testing with an other NIC could indeed be a 'you never know' kinda good idea. 
also worth a check : any firewall on the router or the pc ? 
try ```
 iptables --list
```

---

### Post by autobus83 on 2007-01-19
I am having sort of the same problem.  I am new to linux.  I have a dual boot system with an onboard network card.  In xp my internet is fine but in unbuntu when I go to the internet it loads up google just fine but that is about the only site it will load.  Any other site the computer just reports waiting for website and never connects.

Adam

---

### Post by BallisticBanana on 2007-01-20
Koenn,

OK, have disabled onboard LAN chip and installed add-on NIC - no joy still.  Pretty much the same as before: tried using DHCP/static address etc. without success.

Your question on the firewall: the router has a hardware firewall, but I thought that was to protect it from the outside.  PC firewall - yes, ZoneAlarm, but that's within Windows, so I guess it wouldn't matter here?  Is there some kind of firewall thats activated by default within Ubuntu?  I can't see any obvious pointer to it ...

Within the router interface the only protection that can be enabled is on the wireless connection - I have MAC address filtering set up already, even allowing the wired MAC addresses access through this page, though this shouldn't make a difference.  I will disable all filtering just in case and try that.

---

### Post by BallisticBanana on 2007-01-20
OK, tried disabling MAC address filtering - no effect.
Have now removed the add-on NIC and back to the onboard LAN chip (spotted that both the add-on and onboard use the same chipset)

Koenn - your suggestion to try the code 'iptables --list' produced some errors:

WARNING: Error inserting x_tables (/lib/modules/2,6,17-10-generic/kernel/net/netfilter/x_tables.ko): Operation not permitted
FATAL: Error inserting ip_tables (/lib/modules/2.6.17-10-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
iptables v.1.3.5: can't initialize iptables table 'filter': Permission denied (you must be root)


I know that will mean more to you than to me :)  But I can see it doesn't look too good.  Perhaps a re-install of Ubuntu?

---

### Post by BallisticBanana on 2007-01-20
With the notice that 'You must be Root' I guessed that by adding a 'Sudo' command at the front that would indeed run as root - please let me know if I'm out here as I'm just guessing from reading loads of other posts :)

When running 'sudo iptables --list' I get the following:

Chain INPUT (policy ACCEPT)
target     prot opt source         destination
Chain FORWARD (policy ACCEPT)
target     prot opt source         destination
Chain OUTPUT (policy ACCEPT)
target     prot opt source         destination


Does this information help at all?

---

### Post by koenn on 2007-01-20
```
'iptables --list' produced some errors:
```
yeah, sorry, you need sudo (as you figured). I always forget about that as I usually use a root terminal to do my sysadmining

iptables is ubuntu's default firewall, and the "ACCEPT" policies show nothing is blocked coming to, from, or through your ubuntu system, so no interference with networking there.

The firewall in WIndows is irrelevant as it is not running. 
The firewall on the router *might * operate on both interfaces, not just at the WAN/internet side, but it didn't interfere with your Mac or your WIndows system, so i'm assuming it does not interfere now either. To make sure, you could disconnect it from the internet, disable the firewall or set it to "allow anything", and see if it makes a difference. 

You could also post the firewall settings here so we can review them, but if there are weaknesses in there,  you'd be making them publically known - your call. 

-------------
Other than that, i'm running out of ideas here. I can simply not imagine a situation that would explain such behaviour, So either you found a flaw in the universe, or we're overlooking some crucial detail, or I lack imagination. (not sure which of those i'd prefer)

If you have a crossover cable, or two straight-through cabels and a switch/hub, you could see if you can connect the ubuntu machine to the MacBook (simply by giving both an ip address in the same network + matching subnet mask,  and ping between them)
(you might also try with just 1 straight-through between the twoo machines, but it is less reliable as it depends on the autoconfiguration feature of both NICs to adjust for the lack of a switch/crossover)

oh, and when you switch between dhcp and static config, you do check that your NIC has indeed been configured correctly (ifconfig), don't you ?

---

### Post by BallisticBanana on 2007-01-20
Maybe there are some bigger problems with my system...  

I can't get any USB devices recognised when I plug them into either a USB2.0 port or a USB1.1 port, but looking under 'Device Manager' I can see 4 USB1.1 devices and 1 USB2.0 devices.  (On my mobo though I have 2x USB2.0 connectors and thus 4 USB2 ports, and 1x USB1.1 connector and thus 2x USB1.1 ports)  Incidentally, the motherboard is a Gigabyte GA-7VRXP - a couple of years old, but its always seemed to work under XP.

The Creative Audigy soundcard isn't working - but I've turned off all sound (I think in the right place!).

Oh, and I've screwed my WinXP installation anyway!  It won't dual-boot at all so I've just been out to buy an external HDD to do a full backup onto, but as its USB2.0 then I can't use it!  ](*,) ](*,) ](*,) 

So much for my 15minutes to get a Linux distribution working!

----------
I think I'll try removing the Audigy card first to see if that makes any difference.  Im going to assume that the video card (GEForce 4 Ti4200) is working fine.

Will post any interesting finds.....

---

### Post by BallisticBanana on 2007-01-20
Something else I just noticed - when the OS starts up, before the 'Ubuntu' screen shows, a text message flashes up which says something like: ACPI - can't load system ... something or other - it flashes up so quickly and disappears that I don't know what it actually says.


Anyway, I've now taken out all cards except the video card....

... and no difference still.


OK, its time to give up I think.


My next questions will be along the lines of 'how can I remove the dual-boot facility of Ubuntu to get my system back working again' - but they're probably better posted in another forum.


Many thanks to all who have given their time trying to help me out with these issues.  I'll no doubt try a different Linux distribution eventually at a later date.

Cheers

---

### Post by koenn on 2007-01-20
hm ... sorry to hear that. 
At this point, i'd probably start considering a reinstall - to get rid of all the changes, and to see if something during install indicates a problem. 
On the other hand, ubuntu has Live CD's - you could run one of those and see if they work with your hardware (and can connect to that router or lets you use that usb hard drive). 


I wouldn't worry about the ACPI  - it's something to do with power management, and I tend to ignore it completely. (you could retrieve the boot up msg you mention with dmesg )

---

### Post by BallisticBanana on 2007-01-20
It was a LiveCD that I downloaded in the first place, but similar problems with no connection etc.  I wanted to use the LiveCD to test out the OS and see if it was worth trying to run - it looked pretty good, hence my attempt at getting to run it.  I also heard some great comments in various other places (esp. TWiT), so I wanted to try it out - anything to ditch M$ eh?

Unfortunately, I think that without a network connection it will just be too difficult to get everything up and running - working out what is needed, d/l onto Mac or WinXP, burn CD, install on Ubuntu, etc.  - you get the picture.

I'm still thinking its hardware related somewhere - maybe my PC has problems in the mobo elsewhere, maybe the router is not up to scratch, I just don't know.  

I will have another go again at some later date for sure as I downloaded a gParted LiveCD and managed to recover the WinXP installation on the PC: I may be able to diagnose problems more easily in that environment which I more fully understand.  Or I could just go out and buy/build a new system.  After I rob a bank :) 


As I think I said before, thanks for all the help you (and others) offered.

Kind regards

---

### Post by koenn on 2007-01-20
good luck with the next steps

---

