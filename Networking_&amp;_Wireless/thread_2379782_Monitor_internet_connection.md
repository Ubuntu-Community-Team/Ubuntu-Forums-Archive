---
title: "Monitor internet connection?"
date: 2017-12-09
forum: Networking &amp; Wireless
---

### Post by amanchesterman on 2017-12-09
We have a domestic internet connection provided to our home by Virgin Media. The service is via an underground cable which connects directly to a Virgin Media 'hub' which functions as a combined modem, router and wifi access point. We have various devices connected to our network: my laptop (Xubuntu 17.04), two mobile phones (Android) and my wife's iPad. My laptop has a wired connection, the others are wireless.
Most of the time our connection to the internet is fine and data downloads and uploads swiftly. But occasionally - apparently at random - the service seems to 'freeze' for a short period, up to a couple of minutes. During these 'freezes' the devices remain connected to the network, so I don't think that's the problem: rather, I suspect that our incoming and outgoing traffic via the cable is interrupted.
Naturally I'd like to take this up with Virgin Media. I guess that when I call them they will ask when and how often this occurs, so I'm wondering if there is a Linux utility to monitor our internet connection (not just the network connection) while my laptop is running. Does anyone know of one?
I should add that I have tried turning off the 'hub' (unplugging the power, waiting 30 secs, plugging it in again) which is the first troubleshooting step advised by Virgin Media. Of course that resets the network and everything then works fine for a while. But it doesn't prevent future intermittent freezes!
Thank you for any help you can give.

---

### Post by Darth4212 on 2017-12-14
You can monitor your connections with Nmap.

You can install Nmap by opening a terminal window and typing
```
sudo apt install nmap
```

---

