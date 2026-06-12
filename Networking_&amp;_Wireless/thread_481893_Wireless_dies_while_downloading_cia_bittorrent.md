---
title: "Wireless dies while downloading cia bittorrent"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by cactusbin on 2007-06-23
I am using Ubuntu Feisty Fawn 7.04. I am dual booting with windows XP. I attempted download some things with bittorrent. I was getting about 40 kb/s download speed and 20 kb/s upload speed for about 4 minutes, then it all died. I was getting 0 kb/s on both. I tried pinging google and got this message 'ping: sendmsg: No buffer space available'. I couldn't connect to the internet over anything, but the network manager didn't say I had disconnected. I exited Bittorrent and tryed everything again, still doesn't work. I ran dmesg and this is what I got:
[30496.148000] wlan0: starting scan
[30497.464000] wlan0: scan completed
[30617.512000] wlan0: starting scan
==CUT==
[50279.328000] wlan0: scan completed
[50399.376000] wlan0: starting scan
[50400.692000] wlan0: scan completed
[50480.756000] wlan0: No ProbeResp from current AP 00:18:39:d0:48:2d - assume out of range
[50480.928000] wlan0: Initial auth_alg=0
[50480.928000] wlan0: authenticate with AP 00:18:39:d0:48:2d
[50481.128000] wlan0: authenticate with AP 00:18:39:d0:48:2d
[50481.328000] wlan0: authenticate with AP 00:18:39:d0:48:2d
[50481.528000] wlan0: authentication with AP 00:18:39:d0:48:2d timed out
[50485.928000] wlan0: Initial auth_alg=0
[50485.928000] wlan0: authenticate with AP 00:18:39:d0:48:2d
[50486.128000] wlan0: authenticate with AP 00:18:39:d0:48:2d
[50486.328000] wlan0: authenticate with AP 00:18:39:d0:48:2d
[50486.528000] wlan0: authentication with AP 00:18:39:d0:48:2d timed out
[50489.832000] wlan0: Initial auth_alg=0
[50489.832000] wlan0: authenticate with AP 00:18:39:d0:48:2d
[50493.288000] wmaster0: Does not support passive scan, disabled
[50498.528000] wlan0: Initial auth_alg=0
[50498.528000] wlan0: authenticate with AP 00:18:39:d0:48:2d
[50498.532000] wlan0: RX authentication from 00:18:39:d0:48:2d (alg=0 transaction=2 status=0)
[50498.532000] wlan0: authenticated
[50498.532000] wlan0: associate with AP 00:18:39:d0:48:2d
[50498.532000] wlan0: RX AssocResp from 00:18:39:d0:48:2d (capab=0x401 status=0 aid=1)
[50498.532000] wlan0: associated
[50502.452000] wlan0: duplicate address detected!
[50520.768000] wlan0: starting scan
[50522.044000] wlan0: scan completed
[50542.136000] wlan0: starting scan
==CUT==
[51964.104000] wlan0: scan completed
[52084.144000] wlan0: starting scan
[52085.440000] wlan0: scan completed
I had to reboot before my wireless would work again. I booted into Windows and downloaded the torrent fine. I want to get rid of Windows completely, but this is severally impairing me. My router is a WRT54G running DD-WRT v23 SP2. My wireless is the one included on my motherboard: [http://www.newegg.com/Product/Product.asp?item=N82E16813131011](http://www.newegg.com/Product/Product.asp?item=N82E16813131011) I've tried using different clients, Deluge, Azerous, BitComet, and the official client.

Please help, I would really appreciate it.

Thanks,
DJ

---

