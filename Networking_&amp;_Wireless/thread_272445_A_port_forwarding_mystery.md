---
title: "A port forwarding mystery"
date: 2006-10-06
forum: Networking &amp; Wireless
---

### Post by Mookawaka on 2006-10-06
I am trying to get a bittorrent client fully operational on my Ubuntu 6.06 system but have not had incredible success thus far.
I have a FRITZ!BoxSL router which I have configured a number of times (both pre- and post- Ubuntu discovery) using the tips from portforward.com.  Specifically the walkthrough on this [web page]("http://www.portforward.com/english/routers/port_forwarding/FRITZ/WLAN3030/BitTorrent.htm").

For reasons unknown to me, even with my computer set to a static IP and the proper ports forwarded in the router, I can not get any of the bittorrent clients that I have tried to begin downloading and uploading properly.
Linux Bittorrent is entirely unresponsive, Bittornado and Ktorrent run but at an incredibly hindered rate (yellow speed indicators and whatnot), and while I did not explore Azureus too much due to the bloat that is brought with it, similar difficulties were encountered.

I take this to mean that there are problems with the NAT of the router, but I was under the assumption that is why one sets a static IP and forwards ports.  I do not have firestarter on my system.  I am at loss.

Any clues to how I could solve this would be much appreciated.

---

### Post by tbonius on 2006-10-06
Try a portrange.. like 6881, 6882, 6883, 6884, 6885, 6886, 6887, 6888, 6889

(6881-6889) TCP and UDP

T

---

### Post by Mookawaka on 2006-10-07
That was actually the first range of ports that I tried out, as it would appear from searching the forums that those are generally recommended for running Bittornado.  I can get a normal internet connection but still get limited accessibility with any bittorrent application.
Is there something else regarding the NAT on my router that I am missing?  Perhaps something that Windoze would take care of automatically that I am unaware of?

---

### Post by Mookawaka on 2006-10-09
Bumpty bump . . .

Regarding the previous reply from tbonius (thank for the reply by the way), I added the same port range under a UDP heading as well as the previously forwarded TCP.  Nothing has changed from what I can tell.

---

### Post by Mookawaka on 2006-10-10
More bumping . . .

Am I not being specific enough?  Possibly this is posted in the wrong section?

---

