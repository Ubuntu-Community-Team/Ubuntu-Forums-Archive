---
title: "Information: Making Intel 7260ac wireless bluetooth work in Ubuntu 12.04"
date: 2015-12-12
forum: Networking &amp; Wireless
---

### Post by weatherman2 on 2015-12-12
I don't have any current issue - not asking a question.  Just posting this for information for people who might have the same problem, to try to save them a few hours of time!

I have an Acer AO756 netbook with Ubuntu 12.04.2.  I originally upgraded the wireless card (a Broadcom or Atheros card, forget which) to an Intel 6235 card, which is dual band WiFi + bluetooth.  This card worked pretty much automatically and very well, including bluetooth which I used a lot.

Recently I tried upgrading to the Intel 7260HMW 802.11ac card (it has various names, but 7260 is in all of them) and a new 802.11ac router.  I had to build a new iwlwifi driver from backports and then copy the right firmware file for 12.04 - that was fairly easy.  It looks like newer versions of Ubuntu (which I booted to test) will support the card automatically.  I'm not yet ready to upgraded from 12.04 however.

But getting bluetooth to work was a challenge.  It was not recognized at all, even in Windows.  I found this perplexing.  If you do web searches, there are lots of mentions of bluetooth issues with this card.  I tried a lot of the solutions.  Finally, the one that worked: a hardware fix.  I had to put a piece of electrical tape over pin 51 of the card.  It seems that the bluetooth function of these cards uses a USB channel in the mini-PCIe slot (so the kernel thinks you've got a USB bluetooth card plugged in) and on the 7260, this pin may tell your BIOS to disable the USB function for some reason.  If you cover it up with tape, it can't make the connection to the BIOS so it is still enabled.

My Acer laptop BIOS not surprisingly has very limited controls, and there is no option at all to disable the wireless card or bluetooth.   Perhaps your BIOS or firmware does.

(Do a web search for "intel 7260 pin 51" to find pictures.  When looking at the card face up with the pins facing you, it is the RIGHT-most pin.)

Once I did that, I managed to get bluetooth to work - mostly.  I still have issues with the card after it resumes from suspend - bluetooth does not get automatically re-enabled.  I have to use the laptop's hardware switch to re-enable it.  On the Acer AO756, this the Fn + F3 key.  But it is not a straightforward toggle ON-OFF.  It seems there are numerous states and you have to hit the key combo a few times to cycle through them.  One state is just WiFi enabled; one is just bluetooth; one is both enabled.

If bluetooth is enabled in hardware then the command "rfkill list all" shows this on my Acer:

```

ubuntu>rfkill list all

1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
10: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

If I toggle Fn+F3 to disable bluetooth, the three lines at the bottom regarding hci0 disappear completely - like a USB bluetooth dongle that has been physically unplugged.  If you DO NOT have those last three lines at all, you're not going to get bluetooth at all.  Your hardware may differ from mine - but in my case, toggle the Fn+F3 key (may be Fn+F2 on other laptops) to cycle through the combinations and run the "rfkill list all command" again.  This may also differ depending on Ubuntu version - not sure.

---

