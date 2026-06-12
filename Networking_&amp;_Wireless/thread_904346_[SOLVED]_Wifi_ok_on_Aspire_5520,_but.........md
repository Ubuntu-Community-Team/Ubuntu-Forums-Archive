---
title: "[SOLVED] Wifi ok on Aspire 5520, but........"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by papold on 2008-08-29
Hi all from an Italian Linux user.
First of all I ask you to forgive my poor English :)
I'll go to the question:

I followed the instructions to make Hardy recognize the wireless card on my Aspire 5520, the infamous Atheros, using ndiswrapper and XP driver.
lspci calls it AR242x (maybe it's a AR5007EG).

iwconfig let me see my wlan0, so it's recognized.

I edited /etc/network/interfaces manually, with wlan0 auto and dhcp, and also with the right wep key.

The problem is that sometimes the interfaces is able to scan and connect to my AP, and sometimes not.

For example: this morning i booted my laptop and iwconfig showed wlan0 connected to my network and with the right IP got from the router. I tried to surf and everything was ok

I rebooted and iwconfig showed wlan0 trying to connect to the network and, after a couple of minutes, nothing at all. "Scan" don't see any network, and nothing works anymore. (Edit: wlan0, at that point, gets a random IP and that's all...)

It seems to work "randomly", one time yes and the other no...

Vista goes always well.

Can someone please give me a hint?

Thanks in advance

Papold (Linux noob since Slack 4.x)


PS: Since I tried (before ndiswrapper) to get it working also with Hardy drivers and then with madwifi compilation, what must I do to be sure that it is not a conflict with them, a part from unchecking the 2 checkboxes in restricted driver management?)
EDIT: I just saw the sticky post about conflicts with other drivers...)

:confused:

---

### Post by papold on 2008-08-31
It works!
For who needs help:

Changed from ndiswrapper to madwifi (madwifi-hal-0.10.5.6-r3835-20080801) and all was simple.

My machine: laptop Acer Aspire 5520
Athlon 64x2 TK57 1.9 ghz
3gb ddr - 160 hd

downloaded madwifi
simply compiled it (make clean - make - sudo make install)

modprobe ath_pci

...and my ath0 is up and running.

Then with the Gnome network manager I connected very well.

hope this helps...

---

