---
title: "rt61 &amp; rt61pci drivers"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by tangibleorange on 2008-01-02
Hello,

I have a wireless card with a RaLink RT2561/RT61 chipset. When I click "connection info" on network manager, i see that I am using the rt61pci driver which works fine for web browsing. However, I would like to use the rt61 driver in order to use a program which works only with the rt61 version. How do I switch from the rt61pci driver to the rt61 driver? I am pretty new to linux in general so any help would be much appreciated!

Thanks

---

### Post by wieman01 on 2008-01-02
What issue do you have with the RT61PCI? What sort of program do you plan to use?

---

### Post by tangibleorange on 2008-01-03
i was planning to try out the aircrack-ng suite with my card, which says that only the enhanced legacy drivers work with my card - not the new generation ones (which i understand to be rt61pci)

---

### Post by wieman01 on 2008-01-03
Makes sense now. 

You would have to blacklist the rt61pci (see my Ralink tutorial... there is a section on how to blacklist drivers), then install the enhanced legacy driver (rt61). You cannot use both driver at a time.

Where would you get the patched driver from?

---

### Post by tangibleorange on 2008-01-03
I was planning to get the legacy driver from the serialmonkey website. After I've blacklisted the rt61pci, can I just follow the instructions at [[COLOR="Blue"]this[/COLOR]]("http://www.aircrack-ng.org/doku.php?id=rt61") link on the aircrack website for installing the legacy driver?

---

### Post by wieman01 on 2008-01-03
> **tangibleorange said:**
> I was planning to get the legacy driver from the serialmonkey website. After I've blacklisted the rt61pci, can I just follow the instructions at [[COLOR="Blue"]this[/COLOR]]("http://www.aircrack-ng.org/doku.php?id=rt61") link on the aircrack website for installing the legacy driver?
Yes, you can. That's what I did as well with the rt2560. Post here if you encounter problems, I can help.

---

### Post by tangibleorange on 2008-01-03
when using the 'make' command, I get the following messages:
> !!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt61.ko built successfully
However I can go on to 'make install' and modprobe without any problems. the rt61pci is on my blacklist and the rt61 seems to have successfully been modprobed, so should I just restart and hope for the best?

---

### Post by wieman01 on 2008-01-03
> **tangibleorange said:**
> when using the 'make' command, I get the following messages:

However I can go on to 'make install' and modprobe without any problems. the rt61pci is on my blacklist and the rt61 seems to have successfully been modprobed, so should I just restart and hope for the best?
Just ignore the warning, no big deal. Yes, restart and see if a scan yields any results:
> sudo iwlist scan
If you like you can follow my WEP Crack tutorial (signature) and see if reinjection works.

---

### Post by tangibleorange on 2008-01-03
well i got the rt61 driver working, but after about a minute of being logged in, my system basically freezes. I can't open any applications, shut down, or type terminal commands. all i can do is move my mouse. i guess this must mean my card doesn't work with the driver (NWM can't connect to any networks, and if i try and stop it (untick enable wireless) the whole thing freezes like i described above. of course i could just unblacklist rt61pci but then no aircrack...
is there anything else i can try with the rt61 driver to get it working?
(thanks for all your help so far by the way)

---

### Post by wieman01 on 2008-01-03
> **tangibleorange said:**
> well i got the rt61 driver working, but after about a minute of being logged in, my system basically freezes. I can't open any applications, shut down, or type terminal commands. all i can do is move my mouse. i guess this must mean my card doesn't work with the driver (NWM can't connect to any networks, and if i try and stop it (untick enable wireless) the whole thing freezes like i described above. of course i could just unblacklist rt61pci but then no aircrack...
is there anything else i can try with the rt61 driver to get it working?
(thanks for all your help so far by the way)
NM won't work with NM. No Ralink drivers do so far, at least not the legacy ones (for they have a slightly different design).

One what version of Ubuntu are you on? Gutsy 32-bit?

---

### Post by tangibleorange on 2008-01-03
yeah Ubuntu 7.10 Gutsy Gibbon. i guess i need to disable network manager somehow?

---

### Post by wieman01 on 2008-01-04
> **tangibleorange said:**
> yeah Ubuntu 7.10 Gutsy Gibbon. i guess i need to disable network manager somehow?
You can remove it via Synaptic, the package manager. No problem.

---

### Post by tangibleorange on 2008-01-06
OK I've got the rt61 working for aircrack-ng but I can't inject with aireplay-ng. when i try to inject i get this:
> 17:54:09  Packets per second adjusted to 37554 packets...(185 pps)
17:54:11  Packets per second adjusted to 282
17:54:13  Packets per second adjusted to 212
17:54:15  Packets per second adjusted to 159
17:54:17  Packets per second adjusted to 120
17:54:19  Packets per second adjusted to 90
17:54:21  Packets per second adjusted to 68
17:54:23  Packets per second adjusted to 51
17:54:25  Packets per second adjusted to 39
17:54:27  Packets per second adjusted to 30
17:54:29  Packets per second adjusted to 23
17:54:31  Packets per second adjusted to 18
17:54:33  Packets per second adjusted to 14
17:54:35  Packets per second adjusted to 11
17:54:37  Packets per second adjusted to 9
17:54:39  Packets per second adjusted to 7
17:54:41  Packets per second adjusted to 6
17:54:43  Packets per second adjusted to 5
17:54:45  Packets per second adjusted to 4
17:54:47  Packets per second adjusted to 3
write failed: Resource temporarily unavailable
don't know if it's related, but in synaptic (after uninstalling NWM) i've still got something called "network management framework daemon". should i get rid of this as well?

---

