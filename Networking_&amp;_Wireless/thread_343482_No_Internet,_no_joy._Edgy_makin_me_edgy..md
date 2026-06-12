---
title: "No Internet, no joy. Edgy makin me edgy."
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by Cyberbayne on 2007-01-21
The facts:

```
**lshw -businfo**
pci@00:11.0  eth0      network     ADMtek ADM8211 802.11b Wireless Interface
```
```
**sudo lshw -C network**
  *-network               
       description: Wireless interface
       product: ADMtek ADM8211 802.11b Wireless Interface
       vendor: Linksys
       physical id: 11
       bus info: pci@00:11.0
       logical name: eth0
       version: 11
       serial: 02:0d:10:eb:37:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=adm8211 multicast=yes wireless=IEEE 802.11b
       resources: ioport:ec00-ecff iomemory:d1000000-d10003ff irq:11
```
```
**lspci -v**
00:11.0 Network controller: Linksys ADMtek ADM8211 802.11b Wireless Interface (rev 11)
        Subsystem: Accton Technology Corporation Unknown device 3201
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at ec00 [size=256]
        Memory at d1000000 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <access denied>
```
```
**sudo lsmod**
Module                  Size  Used by
adm8211             62720    0
```
```
**sudo modprobe adm8211**
```
```
**sudo iwconfig**
lo        no wireless extensions.

eth0      IEEE 802.11b  ESSID:"linksys"  Nickname:""
          Mode:Managed  Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Tx-Power:255 dBm   
          Retry limit:3   RTS thr=2346 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

sit0      no wireless extensions.
```
```
**sudo ifconfig**
eth0      Link encap:Ethernet  HWaddr 02:0D:10:EB:37:D6  
          inet6 addr: fe80::d:10ff:feeb:37d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1008 (1008.0 b)
          Interrupt:11 Base address:0xec00 Memory:d1000000-d1000400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35140 (34.3 KiB)  TX bytes:35140 (34.3 KiB)
```
```
**sudo iwlist eth0 scan**
eth0      No scan results
```
```
**sudo dhclient eth0**
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/02:0d:10:eb:37:d6
Sending on   LPF/eth0/02:0d:10:eb:37:d6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
```
**ping -c 4 127.0.0.1**
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.076 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.053 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.055 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.058 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.053/0.060/0.076/0.012 ms
```
```
**ping -c 4 192.168.1.1**
connect: Network is unreachable
```

I thought the "Access Point: Not Accessible" message looked promising as a lead, but searching the forums for the phrase yielded no joy.

If I'm reading everything right, the wireless adaptor is detected, and the driver is active. The device is listed in the connections screen and is marked as active. ESSID is correct. DHCP is set for autodetect. I've rebooted the computer and I've rebooted the router. I've refreshed the DHCP scan on the router, but it does not see the adaptor. After reading enough to get a headache, I'm appealing to the community. Please help me become a member. Thanks for reading this far.

---

### Post by riven0 on 2007-01-21
Perhaps your network interface is not configured correctly? Can you post the output of this command?:

> cat /etc/network/interfaces

---

### Post by Cyberbayne on 2007-01-21
```
cat/etc/network/interfaces
bash: cat/etc/network/interfaces No such file or directory.
```

---

### Post by Cyberbayne on 2007-01-22
> **Cyberbayne said:**
> ```
cat/etc/network/interfaces
bash: cat/etc/network/interfaces No such file or directory.
```

Sorry riven0, my bad. I didn't notice the space between the cat command and the path.
Here is the result:

```
cat /etc/network/interfaces
auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp


iface eth0 inet dhcp
wireless-essid linksys
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
```

In my efforts to connect, at one point I went into the admin-networking-connections screen and manually entered the values given above. When it didn't work I returned the setting to the auto-detect DHCP. 

So now I don't know if those values are in the interfaces file because I put them there earlier, or because they were auto-detected. I suspect the former, because the router still does not show this machine in its DHCP table. 

I guess the thing to do is go back to the interface and clear the manual fields (which still show the values even tho the fields are greyed out), then restore the default auto detect, reboot, and cat the interfaces file again.

Sound right?

---

### Post by updownleftright on 2007-01-22
This sounds almost exactly the same as my problem ([http://ubuntuforums.org/showthread.php?t=343882](http://ubuntuforums.org/showthread.php?t=343882)).

I have the same card, and virtually the same output from every command. Unfortunately I havn't solved it yet, so I have nothing constructive to add other than saying i'm in exactly the same boat! 

Is this going to turn out to be a problem with this model of card?

---

### Post by Cyberbayne on 2007-01-22
> **updownleftright said:**
> This sounds almost exactly the same as my problem ([http://ubuntuforums.org/showthread.php?t=343882](http://ubuntuforums.org/showthread.php?t=343882)).

I have the same card, and virtually the same output from every command. Unfortunately I havn't solved it yet, so I have nothing constructive to add other than saying i'm in exactly the same boat! Is this going to turn out to be a problem with this model of card?

Time will tell - I hope. I've subscribed to your thread. Hang in there...

---

### Post by updownleftright on 2007-01-22
Don't know if this will be useful to you, but I tried disabling the WEP encyrption on my router and then connecting again, and it's worked fine. Now I just need to go back through all my other changes and revert them one at a time and hope nothing breaks!

---

### Post by Cyberbayne on 2007-01-22
I never activated the WEP, figured I'd worry about that after I got things communicating with each other. 

I ran "man iwconfig", and using that as a guide I set each parameter to match my router's config. I made one change at a time using "sudo iwconfig eth0 <parameter> <new value>", and ran iwconfig after each change to confirm the change. When I finished the config changes I rebooted and still no connectivity. I ran iwconfig and it had reverted back to before I made the manual changes!

How do I make the changes to the iwconfig file persistent? Any idea?

---

### Post by Cyberbayne on 2007-01-31
Bump

Over 260 reads, one drive-by suggestion. Sigh...

---

### Post by fisherman783 on 2007-02-01
I'm far from an expert at Linux, but I set up Xubuntu on my mother's laptop and had some problems with the wireless config... what I did in the end was create a script to set the iwconfig commands and send a DHCP request.  It's a sub-optimal but working solution.

> When I finished the config changes I rebooted and still no connectivity. I ran iwconfig and it had reverted back to before I made the manual changes!
This may sound silly and obvious but... have you tried /not/ restarting?  That is, entering all the appropriate settings through iwconfig, running dhclient, and seeing if you get a connection?

---

### Post by stanh on 2007-02-01
Well I see I'm not alone. I have a HP/Compaq nc4010 laptop with a mini-pci card with Atheros chipset.  My results are almost exactly the same as Cyberbayne.

I started with Edgy, then read where someone had success with Dapper so rebuilt and tried that.  No go.  I have also tried Fedora 6 with same results.  I want to stay with Ubuntu.  I have even tried a NDISWRAPPER.  Same result.  However this laptop and wireless worked when I had XP installed.

There is a blue LED on the laptop that lights up when the wireless is enabled.  I haven't been able to get it come on which indicates that the card isn't enabled but the configurations show that it is.  I have even entered info manually and got same results as Cyberbayne.

I've subscribed to this thread and will let you know if I have any success.  I'm going to beat this thing yet.

---

### Post by stanh on 2007-02-01
Finally...after 1 week.  Problem solved.  I'm connected.  Don't have WEP working yet but I finally have wireless working.

Here's what I found buried on the MADWIFI site.  Seems on some mini-pci cards, pin 13 can cause the radio to be stuck off. Put some tape over the pin and Bingo, it works. This link has some pictures of the pin location.  My card looked a little different, didn't have all the foils shown but I figured it out.

This may not work for your card but it it worth looking into.

[http://madwifi.org/wiki/UserDocs/MiniPCI?format=txt](http://madwifi.org/wiki/UserDocs/MiniPCI?format=txt)

I'm sending this reply.....wireless!!

---

### Post by Cyberbayne on 2007-02-02
> **fisherman783 said:**
> I'm far from an expert at Linux, but I set up Xubuntu on my mother's laptop and had some problems with the wireless config... what I did in the end was create a script to set the iwconfig commands and send a DHCP request.  It's a sub-optimal but working solution.
Could you share the script please?
> This may sound silly and obvious but... have you tried /not/ restarting?  That is, entering all the appropriate settings through iwconfig, running dhclient, and seeing if you get a connection?
I did by pinging and via Firefox, but believe me, after all the grief and frustration, nothing sounds silly. I'm flying in a voodoo woman from sout' Louisian' next.

---

### Post by Cyberbayne on 2007-02-02
> **stanh said:**
> Finally...after 1 week.  Problem solved.  I'm connected.  Don't have WEP working yet but I finally have wireless working.

Here's what I found buried on the MADWIFI site.  Seems on some mini-pci cards, pin 13 can cause the radio to be stuck off. Put some tape over the pin and Bingo, it works. This link has some pictures of the pin location.  My card looked a little different, didn't have all the foils shown but I figured it out.

This may not work for your card but it it worth looking into.

[http://madwifi.org/wiki/UserDocs/MiniPCI?format=txt](http://madwifi.org/wiki/UserDocs/MiniPCI?format=txt)

I'm sending this reply.....wireless!!

Congratulations!

Unfortunately, my problem is with a USB wireless adaptor, Linksys WUSB11 V2.5, on a PC.

I've tried two of them on two different computers, with the same problem. I've tried replacing the usb adaptor with a Belkin FD56001 PCI adaptor with the same results. I've tried the linux driver, and the ndis wrappped windows driver. 

I've tried installing from the alternate CD which goes fine until:

> **Network autoconfiguration failed. Your network is probably not using the DHCP protocol. The DHCP server may be slow or some network hardware is not working properly.**

To which I respond:

**My router is using the DHCP protocol.** This same computer with Windows booted has no problems connecting with the router. I'm using it now. There are other computers on this home network that also work fine, and the router DHCP table populates accordingly. **The server is not slow**, but I had the install program try to detect the router twice more just in case. Finally, I really think the **network hardware is working properly**, considering that I'm posting this using the same hardware.

Needless to say, the Live CD doesn't connect either.

The network adaptor is a Linksys WUSB11 v 2.5. The driver is the linux-wlan-ng which is included on the install disc. Once in Edgy, I've installed the driver, network manager, network-manager-gnome, and wifi-radar. I can ping 127.0.0.1.

My thanks to you both for wanting to help.

---

### Post by Cyberbayne on 2007-02-11
Well, its not an 'elegant' solution, and certainly not a purist *nix solution, but I'm up and running and posting this from my distro (openSUSE - I got MUCH  more help there)  thanks to the Buffalo Ethernet converter model WLW-TX4-G54HP. Man, 5 minutes was all it took to overcome weeks of frustration. Be well, everyone, and thanks again to those from these forums (fora?) who tried to help.

---

### Post by nomaam on 2007-06-12
> 
Quote:
Network autoconfiguration failed. Your network is probably not using the DHCP protocol. The DHCP server may be slow or some network hardware is not working properly.
To which I respond:

My router is using the DHCP protocol. This same computer with Windows booted has no problems connecting with the router. I'm using it now. There are other computers on this home network that also work fine, and the router DHCP table populates accordingly. The server is not slow, but I had the install program try to detect the router twice more just in case. Finally, I really think the network hardware is working properly, considering that I'm posting this using the same hardware.



Hello:

I am experiencing the same problem...

I am new to Ubuntu and have just installed ubuntu-7.04-server-i386.iso onto another computer. The other computer was previously running Windows and had no problems automatically connecting to the internet through my router.

The install went well with only one problem: "Network autoconfiguration failed" 

My question now is how do I solve this problem? I have very little knowledge of the command line and am working with the server version that has no GUI. I was hoping to have an internet connection so I could obtain the GUI tool for using the LAMP features. 

Could someone please help me?

Thank you.

Note: I am not using wireless.

---

