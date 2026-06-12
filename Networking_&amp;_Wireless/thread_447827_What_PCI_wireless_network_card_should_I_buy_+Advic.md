---
title: "What PCI wireless network card should I buy? +Advice on WPA"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by FSHero on 2007-05-18
Hi all,

Sorry if this has been answered before; however, I can't seem to find the answers.

First, my computer specs. I have a Pentium 2 333 MHz computer lying around, and I want to have wireless networking on it. (Yes, laugh at the old machinery!) I am confident that it doesn't have USB2, so I want to steer clear of USB wireless network adapters and go with PCI.

I have a number of queries regarding wireless network adapters. Firstly, I recently (7 days ago), I bought a wireless network adapter -- a CNet CWP-854. I bought this because I it was listed on this site:
[http://ralink.rapla.net/](http://ralink.rapla.net/)
which in turn was reference by the page:
[http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)

In particular, on the ralink.rapla.net page, this card was not indicated as having a varying chipset. I decided to buy a Ralink-chipset wireless card because I have read good things about how it is compatible with Linux. (A chip is labelled RT2561ST on the card itself; the rt61pci module is loaded when booting with Knoppix 5.1 -- see later.)

However, I made a big mistake by not doing my 'homework' before buying: I was ignorant of the fact that WPA gives stronger protection than WEP, as described on Wikipedia:
[http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy]("http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy")

On the box of the CWP-854, it says: "Wireless Security: Up to 128-bit WEP". There is no mention of WPA.

Should I get a card with WPA? Is the security with WEP really as poor as I have heard? If so, I am planning to return this CWP-854 that I have currently. (I only have 7 days left to return it I think, lol.) Furthermore, I think I have read (on the Ubuntu forums themselves) that getting WPA to work is difficult. This complicates the issue: I am tempted to choose ease of use over security.

Unfortunately, I cannot get this working with Ubuntu: see my next post. (I separated it because it is not as big a priority for me.)

Please allow me to digress slightly. If I use Knoppix 5.1, the module "rt61pci" is loaded (I see this using lsmod). I see the KWLan icon in the bottom right of the screen (I can't remember what some things are called -- sorry!), plus two icons for eth0 and wlan0. Presumably wlan0 is the wireless card. But if I right-click wlan0's icon and click Enable, nothing happens. Also, if I single-click wlan0's icon and click New (to configure a connection, presumably), I can type in my "Profile name / SSID", but NOT my WEP key. The text boxes for WPA and WEP are disabled.

I tried to tinker on the terminal. Going into Konsole and gaining root user permissions, I typed:
```
# iwconfig wlan0 essid ABCDEFGH nwid My-ID-here channel 1
```
But an error message came up, which mentioned nwid, and said something like: Operation not supported.
(Unfortunately, I did not write the message down; I am remembering it from the top of my head.)
(I typed channel 1, because I saw something like that in KWLan.)
However, typing the following does not come up with errors:
```
# iwconfig wlan0 essid ABCDEFGH channel 1
```

(Note: fake ESSIDs and nwids given, to maintain security :-))

I tell you of my adventures in Knoppix, because I want to ask: Does this suggest that the network card will be problematic in Ubuntu (once I can actually boot into Ubuntu successfully)? If it is... then I'll probably just ditch my efforts, and try another card. (Failing this, I'll ditch wireless and go wired (Ethernet) :P)
(I appreciate that Knoppix problems may be out of an Ubuntu forum's 'jurisdiction', but I thought it may be helpful.)

Another question: is there a PCI wireless network card in existence that can work with *both* Ubuntu *and* Knoppix? (Any versions of each, but the "and" is crucial.) Preferably with WPA? Preferably needing only free-software drivers, preferably with no proprietary firmware needed? (This last point is important in the sense that I want to support Linux-friendly devices. I predict that such a device would satisfy the first point, anyway.) I would like Knoppix compatibility, since I plan to experiment with Knoppix, without trashing my Ubuntu install on my hard-disk. Furthermore, I'd prefer not to use ndiswrapper, as I have read elsewhere that it could cause the computer to crash. (Besides, why not just get a Linux-compatible card?)

Epilogue:
If anything, could someone *please* answer the following questions. I believe someone else could benefit from them.

1) Is the security with WPA considerably better than WEP? Is it worth getting a card with WPA, even if it is difficult to set up?
2) Is it worth risking buying a wireless network card whose chipset could vary, even in the same model-number? (e.g. the starred items on ralink.rapla.net)
3) Is there a card/cards that will work with both Ubuntu (eg. Feisty Fawn) and Knoppix (e.g. 5.1)?
4) Is there a card/cards that have WPA, and work in Ubuntu (or any other Linux)?
5) Is there a card/cards that can meet any combination of 2, 3, 4?

---

### Post by FSHero on 2007-05-18
Below is what I'd say I'd put, for completeness.

I put the CWP-854 card in, booted up Kubuntu Feisty Fawn, and it ... crashed, at the loading bar :(. I then used an Ubuntu Feisty Fawn LiveCD, but it crashed with this too -- however, I managed to see the GUI desktop. I tried a final time with the Ubuntu LiveCD, and pressed Ctrl+Alt+F1 to see boot-up messages. I got as far as seeing:
Running local boot scripts (/etc/rc.local).
But then I saw this error:

```
ubuntu@ubuntu:~$[ 44.957694] BUG: soft lockup detected on CPU#0!
```

What could this be about? Perhaps my motherboard is faulty. But Knoppix manages to boot, and Kubuntu/Ubuntu doesn't. Everything works when the network card is removed. I'm going to try the card in a different PCI slot, then look in the BIOS for any vaguely relevant settings.

If I can't get the CWP-854 working in Kubuntu/Ubuntu, I may or may not find a new card -- hopefully based on people's advice. Then, if no joy, I will just get a 'new' computer. ("New" meaning "different" -- probably a Pentium 3 -- something cheap :P)

P.S. Although I use words like "root" and "terminal" and "iwconfig", I am not really a Linux expert. Most of my knowledge and skill have been transferred from skills of wrestling with Windows.

---

### Post by FSHero on 2007-05-20
Hmm... looks like I've had to solve the problem myself.

For the record, I got my wireless network card working. I moved the wireless NIC into a different PCI slot. I booted up Kubuntu, then went to System Settings --> Network Settings. I enabled the "ra0" device.

I entered my SSID, and the WEP key corresponding to the one I set in my router. I had some weird stuff going on (e.g. wrong IP address being assigned), but after doing some stuff and disabling then re-enabling ra0, it worked. IP address: 192.168.0.3, just as predicted.

:D

Peace out.

---

