---
title: "Atheros card can't see networks"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by pytheas22 on 2008-01-10
I reinstalled Gutsy about a week ago, and everything has been working great.  Today I rebooted, however, and my Atheros PCI card (chipset AR2413, default interface name ath0) can no longer detect wireless networks.  None are visible in Network Manager, and "iwlist ath0 scan" returns no results.

It worked fine until the latest reboot, and the only change I made to the system before the reboot was that I compiled the rt73 driver from serialmonkey and blacklisted the unreliable mac80211 rt73usb driver that ships with Gutsy, but I don't think that that should have anything to do with my Atheros card.

The Atheros card is up as ath0 and appears in Network Manager; it just doesn't list any networks below it.  Using a Ralink USB card, NM shows the networks in range and connects to them without a problem, so NM seems to be working alright.

I can also create an interface for my Atheros card in monitor mode using wlanconfig, and it is able to run Airodump and sniff packets, so the hardware appears to work.

I tried recreating the ath0 interface in station mode using wlanconfig, but the problematic behavior persists.  Bringing the interface down and up again with ifconfig also doesn't help, nor does reinserting the ath_pci module or rebooting.

Any suggestions on what I can do to get this working without having to reinstall the system would be greatly appreciated.  I have my Ralink USB NIC to use in the meantime, but I went out and bought an Atheros card a month ago for the express purpose of finally having a headache-free wifi solution on Ubuntu (since Atheros using the madwifi drivers is supposed to the best way to go), so I would really like to figure out what the problem is.  Thanks in advance for any help.

Here's some information that might be helpful:

```
$ iwconfig ath0
ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
$ ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:19:E0:67:8A:F1  
          inet6 addr: fe80::219:e0ff:fe67:8af1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by pytheas22 on 2008-01-10
Alright, I've realized that the problem is probably that ath0 is being created in IEEE 802.11b mode instead of g mode, as iwconfig indicates.  This would explain why it can't see my wireless network, which is on g mode.

Unfortunately, I can't figure out how to make the interface use g mode.  Reading the wlanconfig man page and searching online, there doesn't seem to be an option for this.  Could anyone tell me how I could force the interface to be in g mode?

(incidentally, I put in a Gutsy live CD and the Atheros card gets set up in g mode without a problem and can connect to my AP, so the hardware itself is definitely not to blame)

---

### Post by raiwo on 2008-01-10
> If you have a multi-mode card, use one of the following commands to lock
the operating mode to one of 11a, 11b, or 11g:

  iwpriv ath0 mode 1		lock operation to 11a only
  iwpriv ath0 mode 2		lock operation to 11b only
  iwpriv ath0 mode 3		lock operation to 11g only
  iwpriv ath0 mode 0		autoselect from 11a/b/g (default)

try these, taken from madwifi

---

### Post by pytheas22 on 2008-01-11
Thanks for the response.  I tried that iwpriv command and it didn't work...it ran quietly but the card didn't change mode.

```
iwpriv ath0 mode 11g
```

which I found on the madwifi site as a later version of the iwpriv mode 3 command also did nothing.

I decided that just reinstalling the system would be a more time-efficient solution than fighting with the driver, so I did that.

If anyone has an idea why this happened in the first place or has had a similar experience, however, I would still be interested in knowing.

---

### Post by killstheweak on 2008-02-04
Same thing happened to me yesterday, i really don't wanna have to reinstall.

---

### Post by ounas on 2008-02-04
Have you tried install madwifi, wicd and removing network-manager.
It worked for me

-
Ounas:)

---

### Post by killstheweak on 2008-02-04
Tried wicd, wifi-radar, and network manager, than i did some looking and found out theres a dumb button in the front that turns off the wireless card, hit the button, and bam its back on (<---finds a screwdriver to rip that button out :P)

---

### Post by pytheas22 on 2008-02-19
I'm not sure if the two posters above had the same problem as me or not, but in case they did, and for the benefit of anyone else for whom the rt73 legacy driver causes madwifi to stop working properly, here's the fix.

After a lot of headache, some people in the rt73 forum have finally figured out what the problem was--apparently when rt73 gets compiled, it overwrites something and causes the rt73 module to be inserted whenever ath_pci is, even if you don't want it to be.  The solution (until the developers can come up with a better idea) is to edit the rt73 makefile and recompile.  Editing some other configuration files also seems to be necessary in some cases, although we're still trying to sort through it all and pinpoint the exact problem.

Take a look at [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4570&postdays=0&postorder=asc&start=0&sid=21f3c3aa1888a49038f3a873dd7f39c5](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4570&postdays=0&postorder=asc&start=0&sid=21f3c3aa1888a49038f3a873dd7f39c5) .  Solution begins towards the end of the first page, and is explained more thoroughly on the second page.

---

