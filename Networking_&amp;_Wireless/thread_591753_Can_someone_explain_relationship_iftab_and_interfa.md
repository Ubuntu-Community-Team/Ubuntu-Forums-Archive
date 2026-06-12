---
title: "Can someone explain relationship iftab and interfaces please?"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by CounterStrike on 2007-10-25
Trying to understand something.....what exactly is the relationship between /etc/iftab and /etc/networking/interfaces? You can specify mac addresses in both, and they seem to interact/overlap with each other but is the magic just determined by which one is processed last with respect to the nic designation that it gets? 

   Here's my situation......running ubuntu server dapper and have 2 onboard intel gb nics and have a pci express card that has another 4 intel gb interfaces.  before I installed teh pci express card (when the 2 onboard nics existed) dmesg reported eth0 and eth1starting at the lower numbered mac of the onboard nic. The interfaces file had eth0 and eth1 configured and running a ifconfig, sure enough eth 0 matched the mac address in dmesg and iftab as well as eth1. Fast forwward and I install the 4 port GB card. in dmesg, the onboard nics still report as eth0 and eth1, but the 4 port card in dmesg says it has eth0, eth1,eth2,eth3. I manually listed the mac addresses in iftab for the new 4 gb ports and assigned them eth2, eth3, eth4, eth5. I then went into the interfaces file and added a line like this:

auto eth2
iface eth2 inet static
       address 192.168.1.2
       netmask 255.255.255.0

and so on for the other 3 new gb ports (eth3,eth4, eth5)

When I did /etc/init.d/networking restart it said  eth4 and eth5 were unknown and upon doing an ifconfig, I find out that indeed I have 4 interfaces (eth0,eth1,eth2,eth3) and eth 0 and eth1 are the two onboard nics as before, but eth 2 and eth 3 are actually the mac addresses I had assigned in iftab to eth4 and eth5. 

I looked into this and found some other posts saying that the kernel assigns the order based upon the order they are detected upon startup and that all bets are off if you have more than one of the same chipset nic, as it could potentially switch the order each time it is rebooted. So I found one person's suggestion to specify the mac address in teh interfaces file under each interface like this

auto eth2
iface eth2 inet static
mac 00:03:34:56:78:91
address 192.168.0.2
netmask 255.255.255.0

but when I did that  for all 6 nics, the same result happened after restarting networking where the 3rd and 4th nics of the 4 port card came up as eth2 and eth3 but there was eth4 and eth5 (which were the first 2 ports of the card). I am okay with this being like this, I just can't afford the nics to come up as different interfaces upon a reboot and am really puzzled as to the relationship between the kernel detecting the card and interfaces, the iftab file and the interfaces file.

Of course there is the possibility that I am doing something completely wrong and causing all this mess - which I would welcome at this point if someone could correct me. I just don't want to put this server out in a production role with so much voodoo going on with this aspect of it.

Thanks,

CounterStrike](*,)

---

### Post by kevdog on 2007-10-25
Interesting -- I thought iftab assigned the alias interface to each mac address.  Obviously its not working for you.  I have a feeling its not working as it is designed.  Wonder if there have been any improvements with the convention in feisty or gusty.

---

