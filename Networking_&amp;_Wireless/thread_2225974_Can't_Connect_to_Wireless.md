---
title: "Can't Connect to Wireless"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by al1n4 on 2014-05-24
Okay, so I recently installed Lubuntu onto my new laptop, an Acer Aspire E1-510-2500. All went well, but right now I am sitting on the floor in a corner connected to LAN because I cannot connect to any wireless connections. I am guessing it is a driver issue, because all of the available connections show, with signal strength as well, but then it immediately shows me a dialog for the password into the network. My PC isn't dirt, but the fact that it skipped scanning and whatnot and immediately presented a password confirmation window for the network is a little unusual. That tells me it is skipping a huge step. After inserting the password, it appears to have done nothing, as I am still not connected. I have also tried unsecured networks. Also a no-go. Any help would be greatly appreciated.

EDIT: I also tried installing ath9k wireless drivers, and that was a failure, too.

Specs:
Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
Lubuntu 14.04

Useless but maybe helpful specs:
Intel N2820 CPU @ 2.13 GHz, 2.13 GHz
4.00 GB DDR3 RAM (2 cards? Haven't checked.)
500 GB HDD

---

### Post by tgalati4 on 2014-05-24
Is the card reachable from the underside?  If so, with the computer off, try reseating the wireless card.  Be careful with the antenna connections, they are delicate.  

This is an old link, but some of the basic steps may be helpful:  [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Here's a detailed procedure for capturing data for your card:  [http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385)

Some more suggestions:  [http://askubuntu.com/questions/461149/wireless-network-card-is-dectected-but-not-working/461177#461177](http://askubuntu.com/questions/461149/wireless-network-card-is-dectected-but-not-working/461177#461177)

More suggestions:  [http://ubuntuforums.org/showthread.php?t=2217096&highlight=AR9565](http://ubuntuforums.org/showthread.php?t=2217096&highlight=AR9565)

These were found using *AR9565* in the Advanced Search box in the upper right corner of the ubuntuforums page.

Take careful notes of what you have installed or uninstalled while troubleshooting.  It takes patience, but ultimately it is fixable.

---

