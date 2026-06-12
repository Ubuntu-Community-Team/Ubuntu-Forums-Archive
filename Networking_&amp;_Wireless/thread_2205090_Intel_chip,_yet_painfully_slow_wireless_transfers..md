---
title: "Intel chip, yet painfully slow wireless transfers."
date: 2014-02-11
forum: Networking &amp; Wireless
---

### Post by Roasted on 2014-02-11
Hello friends. I have a laptop here with an Intel Centrino 6230 N wireless card. I'm running Ubuntu 13.10 64 bit. I have a Netgear WNDR3700v3 (N) router. This particular laptop experiences, what I consider to be, painfully slow wireless connectivity. Usual browsing doesn't seem to be an issue, but transferring files to/from my file server however is. I don't have any immediate neighbors and have played with the channels/spectrm width/blah/blah/blah. I even got a new router (Dlink 850L), which did absolutely nothing to help.

The laptop with the 6230 card transfers files, whether a directory of lots of small files or a single large ISO file, at about 550 KB/s on average. Meanwhile, other laptops running Ubuntu 13.10 64 bit with other wireless cards (even Broadcom chips - what in the world?) will put out exponentially faster speeds in the 3-5 MB/s range.

I did a dist-upgrade just now and none of the available updates made a change. I also disabled bluetooth since I heard of some reports online where bluetooth interferes with the wireless card. I've done power cycles to my modem/router, 30-30-30 resets, and as I mentioned, even swapped routers. No dice.

At one point I had DD-WRT running on my Netgear, which exhibited identical speeds. So overall there's the current Netgear with stock (updated) firmware, Dlink 850L with stock firmware, and the same Netgear with DD-wrt - all same speeds. Clearly this is isolated to this particular unit.

I'm going to see if I can find a different wireless chip that'll fit in this slot. Fortunately Toshiba doesn't seem to whitelist their wireless cards, unlike the Lenovo I'm typing from who cripples my ability to do this trivial task. I'm oddly thankful that the issue resides on a laptop where I have this flexibility. 

Thanks ahead of time for any and all insight!

---

### Post by varunendra on 2014-02-13
Are you using N-channel in the routers? If yes, my first suggestion would be to try disabling it for a test.

Also try disabling it at the driver -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi 11n_disable=1
sudo modprobe -v iwldvm
```

Some additional parameters you may (should) try (I'm using them all at once in the example below, you may (and should) also try them individually) -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi **[COLOR="#800000"]swcrypto=1[/COLOR] [COLOR="#FF0000"]11n_disable=1[/COLOR] [COLOR="#0000CD"]bt_coex_active=N[/COLOR]**
sudo modprobe -v iwldvm
```
These would be temporary changes that would be lost at next boot (or at next driver unload/reload cycle). If they seem to help, can be made permanent.

If they don't help, and you wish to dig deeper, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Roasted on 2014-02-13
I didn't get a chance to test what you mentioned above, but some interesting tidbits to add...

At work on all wireless N gear, it's the same awful speeds as it is as home both with a Dlink AC router and Netgear N router. For kicks and giggles I swapped out the Intel Centrino 6230 card for a spare Intel WifiLink 1000 card. To my surprise, same terrible speeds, at work and at home. If anything the average was about 100 KB/s less than the 6230 card. The WifiLink 1000 card is draft N, not final N, so perhaps that factors in as well. Even setting the Dlink and Netgear to wifi N only it has zero effect on the performance. Changing channels does nothing as well.

So we have two Intel cards with seemingly terrible speeds... meanwhile this Broadcom chip which requires what I always felt was the dreaded STA driver works remarkably better. Granted, different laptop, but still.

Once I get my cars dug out of the driveway (I can't really see them anymore thanks to the snow getting dumped today) I want to put the Broadcom in the other laptop and see how it does. I can't think of any reason the rest of the hardware would be limiting the performance of the unit. It's a somewhat neutered i5 processor (1.6GHz... ultrabook) with one of those tiny 128 GB SSDs, but it does the job and should be a better wifi performer than that, I would think. The other laptop is a 2.5GHz i5, but... would that matter much? I would think even an Atom with a card like this would fly...

---

### Post by varunendra on 2014-02-13
> **Roasted said:**
> The other laptop is a 2.5GHz i5, but... would that matter much?
Nope, not at all. Not atom, even a basic ARM processor has much more power to handle both the OS tasks and the wifi driver/encryption. So practically, CPU power is unrelated.

---

