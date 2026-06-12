---
title: "slow internet"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by spetsen on 2007-01-22
I have just installed Ubuntu Edgy on my new computer (together with an old windows xp) and I am brand new to this facinating world.  My problem now is that my internet connection is about 200 times slower than expected (compared to what I have when connecting my old lap top). I have looked through the forum for ages and tried both to "shut" the ivp6 and openDNS, however nothing seems to work. This, I should say, goes for explorer in XP as well.

I now wonder if this has to do with my partitioning during installation, which looks like follows:
/windows(NTFS) 20G
/linux (Ext3) 20 G
/extended
        home(Ext3) 110 G
        swap 2G

Could it be that home should be under "root" or is that irrelevant? Any other ideas to why my connection isso slow?

Thanks in advance!

---

### Post by Jussi Kukkonen on 2007-01-22
> I now wonder if this has to do with my partitioning 
No. That's not relevant.

Do you use a wireless connection? Do you know the make/model of the card?

Also, it might be worth the while to look at some logs. You can search for relevant stuff in your boot log like this:
```
dmesg | grep eth      ## assuming your connection name is eth0 or something

```
you can also skim through /var/log/messages and see if there is anything related.

---

### Post by spetsen on 2007-01-22
Thanks for your quick reply!

No I use cable. My mothercard is from MSI and is a P4M890

I get this info when running your command:

[17179584.712000] eth0: VIA Rhine II at 0x1d000, 00:16:17:e0:bb:77, IRQ 233.
[17179584.712000] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[17179585.212000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179598.312000] hda-intel: Invalid position buffer, using LPIB read method instead.
[17179607.292000] eth0: no IPv6 routers present

How do you skim /var/log/ messages (I am very new to linux/ubuntu)?

---

### Post by spetsen on 2007-01-22
Ok, I have searched through the messages but I am not really sure what to look for. Could find any suspicious errors though.

Does anyone know the implication of:
"hda-intel: Invalid position buffer, using LPIB read method instead."

Grateful for any kind of help

---

### Post by Jussi Kukkonen on 2007-01-22
The hda-intel line was just an "accident" in the search -- the command I gave searches for the term eth in the boot messages, and that line has the word m**eth**od in it...

So my suggestions were of no use. There was no new informaton there.

---

### Post by Jussi Kukkonen on 2007-01-22
This is mostly shooting around in the dark, but I thought of something you could also check: Run
```
cat /proc/interrupts
```
to see a list of interrupts (before you do that, make sure you've used all of your devices, like the network card, usb disks, etc.). Find eth0 in the right-most column. If there are other devices mentioned in the same row, this might be a problem.

Interrupts aren't really something a user should have to think about, but I don't have any other ideas and checking that is relatively easy, so...

---

