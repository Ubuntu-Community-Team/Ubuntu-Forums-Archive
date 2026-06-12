---
title: "Problem with Bluetooth-Pairing under Xubuntu 8.04.1"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by schlauf on 2008-08-24
Hi everybody,
I own a Sony Ericsson K610i which pairs flawlessly and out of the box with Kubuntu 8.04. When sending an AT-command after creating the rfcomm-connection, Kubuntu pops up a window where I enter a PIN, and entering the same PIN on my mobile results in a bonded pair.
On Xubuntu 8.04.1, it's a different story though. Creating the rfcomm-connection works fine. Sending an AT-command makes my mobile respond and asking for a PIN to enter. Since there is no pop-up on Xubuntu as to enter the equivalent/same PIN here, I tried to create a file /etc/bluetooth/pin, containing just the PIN and nothing else (1234, for example). Nevertheless, linux always throws a "connection refused" error after entering the PIN on my mobile, the same does my cellphone say.
Restarting the bluetooth services and/or the whole system didn't work either.
Any advice?
Thx!

---

