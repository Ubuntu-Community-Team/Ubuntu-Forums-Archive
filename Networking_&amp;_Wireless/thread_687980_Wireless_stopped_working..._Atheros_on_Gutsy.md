---
title: "Wireless stopped working... Atheros on Gutsy"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by Dngrsone on 2008-02-04
My Dell Latitude C610 with an Atheros AR5212/5213 mini-PCI card (according to Hardware information) has been connecting to my wireless network for a good month.

Then, it stopped working.  It says connected, but there's no internet.  I have made no changes to the wireless, no changes to the Ubuntu install, as far as I know.

Any idea why it would spontaneously quit working?

I'm using WEP shared encryption.

---

### Post by forceofnature on 2008-02-04
I had the same issue and it turns out that removing network-manager and resinstalling it with a wired connection did the trick.

---

### Post by Dngrsone on 2008-02-04
Hrm... I'm running WiCD right now...

Worth a try, anyway.

---

### Post by Dngrsone on 2008-02-06
Hrm... network manager is not installed.  I will try reinstalling WiCD, though.

<edit>Nope... didn't help.  Any more ideas?</edit>

---

### Post by maddmike on 2008-02-06
Same problem here - I have a T41 but the same wireless chipset.  No solutions yet.  I have uninstalled knetworkmanager and installed wicd, and back and still no luck.  I wish I knew which update messed things up?

---

### Post by Dngrsone on 2008-02-07
Are you using WEP shared, Mike?

I'm thinking of moving to WPA, just to complicate matters even further.

---

### Post by Dngrsone on 2008-02-13
[IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/eh.gif[/IMG]  Now it's working.  I wonder if the kernel update I just installed had anything to do with it...  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

---

### Post by gimfred on 2008-02-13
I have the same problem on a DWL520  (PCI) card:
```
Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
        Subsystem: D-Link System Inc D-Link AirPlus DWL-G520 Wireless PCI Adapter(rev.B)
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at df8f0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

```
I can 
```

# ifdown ath0 
# ifup ath0
``` and it starts working again for an indeterminate time period, often just for a few seconds, but sometimes up to hours. Mostly I just use Knetworkmanager to restart ath0.
```
# uname -a 
Linux zandergraph 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux 
``` Kubuntu 7.10

I'm starting to think we have a bug.

---

### Post by ekmandyn on 2008-02-13
I have the same problem, I update ubuntu yesterday and my atheros 5006EG stop working. Is was working just fine for 5 months. I tried reintalling the ndiswraper drivers, widc, tec without any luck.

any ideas?:confused:

---

### Post by gimfred on 2008-02-14
I have a workaround in this [post](http://ubuntuforums.org/showpost.php?p=4333575&postcount=6).

---

