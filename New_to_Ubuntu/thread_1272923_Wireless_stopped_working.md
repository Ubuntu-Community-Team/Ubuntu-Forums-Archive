---
title: "Wireless stopped working"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by Bibi_Watson on 2009-09-22
Hello,

I would very much like to get my wireless to work again. I guess it stopped after the latest system update, however rolling back to the previous kernel had no impact. Another guess was about user privileges (I could mess things while adding another user to my PC) ,  but it shows that I have rights to access wireless network. I will appreciate any help.

I have Dell Laptop (Latitude E5500 )

[COLOR=Blue]$lspci [/COLOR]gives me (if I interpret it correctly ):
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5756ME Gigabit Ethernet PCI Express
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

[COLOR=Blue]$ifconfig[/COLOR]:
wlan0     Link encap:Ethernet  HWaddr 00:21:5d:b7:52:e4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[COLOR=Blue]$iwconfig[/COLOR]:
wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$lsmod:
Shall I post whole list? It's huge :-(

$dmesg:
The same here

[COLOR=Blue]$sudo lshw -C network[/COLOR]:
 *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:b7:52:e4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5756ME Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:23:ae:00:67:2d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5756m-v3.11 ip=10.0.0.3 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6e:72:88:92:4a:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[COLOR=Blue]
$iwlist scan[/COLOR]:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

[COLOR=Blue]$lsb_release -d[/COLOR]:
Description:    Ubuntu 8.10

 [COLOR=Blue]$uname -mr[/COLOR]:
2.6.27-14-generic x86_64
[COLOR=Blue]
$sudo /etc/init.d/networking restart[/COLOR]:
 * Reconfiguring network interfaces...                                                                                                        Ignoring unknown interface eth0=eth0.

Please help!

---

### Post by tgeer43 on 2009-09-22
If it was working before then I don't know why a recent update would have killed it.
This doesn't get to the heart of the matter but you could try adding the following to your /etc/rc.local file:
```
ifconfig wlan0 up
iwconfig wlan0 mode managed
iwconfig wlan0 essid *YOURESSID*
iwconfig wlan0 key open *YOURWEPKEY*
dhcpcd -d wlan0
```I've had to do this since day one with a similar Intel wireless adapter.

Give it a try - couldn't hurt.

tgeer

---

### Post by Bibi_Watson on 2009-09-23
At the line 3 (iwconfig with my session id) I get:

Error  for wireless request "Set ESSID" (8B1A):
Set failed on device wlan0 ; Resource temporarily unavailable.

tgeer43, funny avatar :-) I haven't looked at the mirror but I think I look similar

---

### Post by tgeer43 on 2009-09-23
It's been so long ago that I forgot one very important thing that I had to do. By default Ubuntu did not include the correct firmware for my Intel wireless adapter. I had to download it and copy it to the correct directory.

Look in /lib/firmware and tell me the names of any files you have in there that end with ".ucode".

tgeer

p.s. That's not an avatar. It's my senior class picture from 1977. :wink:

---

### Post by Bibi_Watson on 2009-09-23
iwlwifi-3945-1.ucode
iwlwifi-4965-1.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-1.ucode

tgeer,
shame on me! Where were my eyes? You look awesome! :-)

---

### Post by lkraemer on 2009-09-23
Try:
```

iwconfig wlan0 essid "YOURESSID"

```
as man iwconfig shows.

lk

---

### Post by tgeer43 on 2009-09-23
> **Bibi_Watson said:**
> iwlwifi-3945-1.ucode
iwlwifi-4965-1.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-1.ucode

tgeer,
shame on me! Where were my eyes? You look awesome! :-)There is a newer 5000 series firmware file - iwlwifi-5000-2.ucode. Here is the direct download link:

[COLOR=Blue]_[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz)_[/COLOR]

When I first installed Ubuntu the only firmware included for my Intel 4965 was the iwlwifi-4965-1.ucode. When I added the iwlwifi-4965-2.code, everything started working. I don't think I had to do anything special in order for the module to load automatically.

Perhaps by upgrading from the 5000-1 to 500-2 firmware you will have similar results.

tgeer

---

### Post by tgeer43 on 2009-09-23
> **lkraemer said:**
> Try:
```

iwconfig wlan0 essid "YOURESSID"

```as man iwconfig shows.

lkHow is that different than what I wrote in post #2?

tgeer

---

### Post by Bibi_Watson on 2009-09-23
No luck, I'm afraid. Does it mean I have to consider upgrading my Ubuntu 8.10?

---

### Post by tgeer43 on 2009-09-23
No, I don't think that's necessary. I have to step out for a few hours but will revisit this when I get home.

tgeer

---

### Post by Bibi_Watson on 2009-09-23
I do appreciate your help. I have a power point far away from the router. So it is either internet or electricity,  I can not have both at the same time. :)

---

### Post by lkraemer on 2009-09-23
Well,
It sure looks to me as if the two are different!
iwconfig wlan0 essid YOURESSID
iwconfig wlan0 essid "YOURESSID"

Might be worth reading up on "quotes", 'single quotes', and `backquotes`.

man iwconfig shows using quotes.

lk

---

### Post by Bibi_Watson on 2009-09-24
lkraemer, you are right, but the quotes did not help, sudo didn't help either.

---

### Post by tgeer43 on 2009-09-24
> **lkraemer said:**
> Well,
It sure looks to me as if the two are different!
iwconfig wlan0 essid YOURESSID
iwconfig wlan0 essid "YOURESSID"

Might be worth reading up on "quotes", 'single quotes', and `backquotes`.

man iwconfig shows using quotes.

lk
I thought that "YOURESSID" was just your way of designating the placeholder for the ESSID and I wasn't snooty about it - just asked a simple question.
BTW: The double quotes are apparently optional as I don't use them in my script and it runs without error and brings my wlan0 interface up without fail.
Been using that script for over a year now.

To the OP - I'm still looking onto this. I'll post back if I find anything useful.

tgeer

---

### Post by relay_man on 2009-09-24
Never open FF twice with two different threads showing....
Nevermind me.

---

### Post by Bibi_Watson on 2009-09-25
> **relay_man said:**
> Never open FF twice with two different threads showing....
Nevermind me.


FF stands for ..?

---

### Post by Bibi_Watson on 2009-09-25
> **tgeer43 said:**
> 

To the OP - I'm still looking onto this. I'll post back if I find anything useful.

tgeer

In the meanwhile I've tried to change my NetworkManager with Wicd. That was useless movement.

---

### Post by Bibi_Watson on 2009-10-12
Well, it turned out that the Dell box has a physical switch that enables/disables wireless...
If it is on, the wireless comes back. Thank you all for your help.

---

### Post by jsilve1 on 2009-10-19
> **lkraemer said:**
> Well,
It sure looks to me as if the two are different!
iwconfig wlan0 essid YOURESSID
iwconfig wlan0 essid "YOURESSID"

Might be worth reading up on "quotes", 'single quotes', and `backquotes`.

man iwconfig shows using quotes.

lk

In this case, the only difference is the use of double quotes. But that use is irrelevant. single, double, or no quotes would be equivalent here.

---

