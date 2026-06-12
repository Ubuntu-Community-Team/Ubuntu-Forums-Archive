---
title: "Qualcomm Atheros Killer E2201 Wake-on-LAN; 14.04 server amd64"
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by csimbi2 on 2014-08-02
Hi all,
I just built a NAS (SSH and Samba only) using a Gigabyte Z97 motherboard ([GA-Z97MX Gaming 5]("http://www.gigabyte.com/products/product-page.aspx?pid=4968#sp")):
```
Linux xxx 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
```

Ubuntu installed just fine from the mini.iso, and the network seems to be working just fine.
However I can't get Wake-on-LAN working.

The user's manual mentions only one BIOS setting - which is only remotely related to WOL:
> **ErP**: Determines whether to let the system consume least power in S5 (shutdown) state. (Default: Disabled)
Note:  When this item is set to Enabled, the following functions will become  unavailable: PME event wake up, power on by mouse, power on by keyboard,  and wake on LAN.

It was 'Disabled' by default, so I did not touch that setting.
On the contrary to the manual, a "PME event wake up" setting is not visible in the BIOS, regardless of the state of the "ErP" setting.
I tried sending a magic packet with the normal MAC as well as the reversed MAC address, but nothing happens.

The onboard adapter seems to be picked up as E2200:
```
lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller [1969:e091] (rev 10)

```

Wake events are not listed by ethtool:
```
sudo ethtool p2p1
Settings for p2p1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: Symmetric Receive-only
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: Symmetric
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Current message level: 0x000060e4 (24804)
                               link ifup rx_err tx_err hw wol


```

When I try enabling WOL, I get an error:
```
sudo ethtool -s p2p1 wol g
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol

```

The LEDs next to the LAN socket (on the rear I/O panel) turn off when the system powers down.
AFAIK, one of them should be on for WOL to work - though thus far I owned only Intel and Realtek network controllers.

A server is useless without WOL, so it's vital that I get this working.
Any tips/workarounds?
Much apprecitated, thanks!

---

### Post by chili555 on 2014-08-02
> Wake events are not listed by ethtool:Because they are apparently disabled in your driver* alx*: [https://bugzilla.kernel.org/show_bug.cgi?id=61651](https://bugzilla.kernel.org/show_bug.cgi?id=61651)> It has come to my attention that Wake-on-LAN has been explicitly disabled due to another bug, which would make the system wake-up twice for each magic packet.
([http://www.spinics.net/lists/netdev/msg242477.html](http://www.spinics.net/lists/netdev/msg242477.html))
> > Unfortunately, WoL is broken and the system will immediately
> resume after suspending, and I can't seem to figure out why.
> Remove WoL support until the issue can be found.
> 
> Signed-off-by: Johannes Berg <johannes@xxxxxxxxxxxxxxxx>

Applied, thanks.I am unable to find any later fix or work-around.

---

### Post by csimbi2 on 2014-08-02
@chili555
Thanks for the info, at least I know that there is nothing wrong with the board itself.
I hope they'll resolve it ASAP.

BTW, I had to return an [Asus Z97M-PLUS]("http://www.asus.com/Motherboards/Z97MPLUS/specifications/") board for exhibiting the very symptoms described in that thread.
It kept rebooting - by itself - on shutdown. You can hear that the HDDs barely swith off and start spinning down and after half a sec (or so) delay they are turning back on.
You can read the discussion about this issue (regarding the Asus board) - eventually leading to the product return - [here]("https://vip.asus.com/forum/view.aspx?id=20140728200215329&board_id=1&model=Z97M-PLUS&page=1&SLanguage=en-us").

The network controllers on these two boards are different. One is *Intel I218V*, the other is *Qualcomm Atheros Killer E2201*.
I wonder if there's nothing wrong with the network controllers and the problem lies with the Z97 chipset itself.
The other thing these two boards have in common is the M.2 slot.
I sure hope someone can check it out.

Thanks!

---

### Post by csimbi2 on 2014-08-15
Just read [this]("http://techreport.com/news/26911/errata-prompts-intel-to-disable-tsx-in-haswell-early-broadwell-cpus"). It seems that the last generations of Intel CPUs are royally screwed (Broadwell and Haswell at least).
Could it be the reason? It is, after all, "Unpredictable system behaviour".

---

