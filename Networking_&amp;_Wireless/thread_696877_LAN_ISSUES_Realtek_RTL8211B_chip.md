---
title: "LAN ISSUES: Realtek RTL8211B chip"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by msjones on 2008-02-14
Hi,

Big problems getting my new mobo to work in ubuntu. I bought a GA-73PVM-S2H which has an   NVIDIA GeForce 7100 / nForce 630i Chipset.

I had big problems getting my audio to work (realtek ALC882 HDA chip) which is all set now, just cant get it to retain my setting for FRONT audio.... not a big issue.

The main problem is my LAN every time I boot it changed eth allocation. It should be eth0 but at the time of writing its eth24.

Also on boot it does not assign a dhcp address from my router, I have to power down my router and power up before my box gets an IP.

Is there anyway I can sort this?

Thanks

---

### Post by OffAxis on 2008-02-14
what's your 
```
/etc/network/interfaces
```
file look like?

How about

```
ifconfig
```

Are you running any sort of VLAN or VPN software (like Hamachi) that might be screwing you up?

---

### Post by msjones on 2008-02-14
Hi my interfaces reads:
[B]
auto lo
iface lo inet loopback[/B]

and ifconfig outputs:

eth24     Link encap:Ethernet  HWaddr 00:00:6C:2A:BF:36  
          inet addr:10.0.10.4  Bcast:10.0.10.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fe2a:bf36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3123365 (2.9 MB)  TX bytes:725444 (708.4 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1154 (1.1 KB)  TX bytes:1154 (1.1 KB)

I had openswan installed but i have just removed it, do you think this was the issue??

Thanks!

---

### Post by OffAxis on 2008-02-14
Might have been; I see a previous bug fix in the changelog regarding eth numbering.
Only one way to tell for sure; reboot.

---

### Post by msjones on 2008-02-14
Well removed openswan and have rebooted 4 times and have got a DHCP assigned IP everytime, although my eth number is still increasing (currently on eth28)

Is this a major problem?

---

### Post by msjones on 2008-02-15
Well just got home and booted up, no IP had to go and restart the router again. Also my lan card is now assigned to eth30, so its still increasing. Im going for a drastic measure and I am going to do a clean install to see if this fixes any issues.

If anybody can shed any light on the subject I would be very greatful.

Thanks

UPDATE: Also my mac address seems to keep changing, so i am unable to assign a dedicated IP on my router.

---

### Post by remark on 2008-02-17
I have the same motherboard paired with an Intel E2160 and I'm struggling with the same issue...

I found that getting a new MAC address on every boot might be a motherboard issue.
See here: [http://davehall.com.au/blog/dave/2008/02/10/flakey-bios-gigabyte-ga-m68sm-s2l-makes-mac-address-change-reboot](http://davehall.com.au/blog/dave/2008/02/10/flakey-bios-gigabyte-ga-m68sm-s2l-makes-mac-address-change-reboot)
> Looks like Gigabyte (and ASUS) have been shipping invalid MAC addresses on some of their boards, and forcedeth isn't happy about it, so it just generates a new (valid yet) random MAC address.

The solution suggested in the above article did not help me so I switched to a PCI network card as a temporary solution.

But, I found on Gigabyte's site that in a new BIOS version they fixed some kind of LAN function failure. The F5 version of the BIOS has a fix for "LAN function failed when system use Intel Yorkfield CPU". (I couldn't find more details on this.)
The Intel E2140 you probably using is not a Yorkfield, but it just gave the idea that it might worth trying a BIOS update. What do you think?

---

### Post by msjones on 2008-02-17
I will give it a shot and report back to let you know if the bios update works!

Thanks dude :)

---

### Post by moe120 on 2008-02-22
to assign a fix mac address on every reboot try this:
[http://ubuntuforums.org/showthread.php?p=4156690#post4156690]("http://ubuntuforums.org/showthread.php?p=4156690#post4156690")

should fit your problem as far as i read it ;)

---

