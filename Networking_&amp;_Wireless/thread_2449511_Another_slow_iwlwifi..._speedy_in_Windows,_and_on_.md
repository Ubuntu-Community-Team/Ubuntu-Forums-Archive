---
title: "Another slow iwlwifi... speedy in Windows, and on other machine with same card"
date: 2020-08-28
forum: Networking &amp; Wireless
---

### Post by Ascaris_ on 2020-08-28
Ok, I am stumped here.

I've  had the slow iwlwifi issue before, and I even wrote a how-to post on  another site to help novices with turning off the power saving (which  caused a big slowdown at the time I wrote the post). To no avail now,  though. 

I have a Dell G3 (3579) laptop into which I've  transplanted a 7265D (AC+BT) M.2 card. It came with a single stream  version of the same card, which didn't provide the performance I was  looking for. 

In "that other" OS (Windows 10 1809), I can connect to  the FTP server on my home LAN (which is wired to the router) and  download any one of the files at a rate of about 66 MB/s, with the full  wireless connection speed of 867 Mb/s.  It's on the 5 GHz band, and  there are only minor impingements from other access points. The 66MB/s  speed is consistent and reliable in the times I have tested it.

If  I take that same G3 laptop and boot into Linux (Kubuntu 20.04, but the  same issue exists in Fedora 32), downloading the same file, the speed  drops to 20 MB/s throughput at the same 867 Mb/s connect speed. 

In addition to the standard 5.4 Ubunbu kernel, I've  tried mainline kernels 5.7.x and 5.8.x (no change), turned off power  saving, tried the 11n_disable=8 option, and none if it makes a  difference. If I set 11n_disable to 1, it also disables AC mode when using the later kernels, so I'm  stuck at 802.11g speeds, which of course  makes it much slower. In 5.4, it doesn't seem to make any difference.

I've tried disabling fast boot on Windows, as some have suggested, but it didn't change anything when in Linux.

I'm using firmware 29.163394017.0 7265D-29, the last one Intel released for the 7265D.

Here's  the really interesting thing. My Acer Swift laptop, with the same  wireless card (7265D AC+BT), with the same firmware revision, with the  same OS (and configured as much alike as possible), with the same  kernel, connected to the same access point, downloading files from the  same FTP server, gets the same kinds of speeds that Windows does on the  G3. 

I've looked through all of the settings, and I don't see anything that's different between the two Linux laptops. 

I've  tried some live sessions from USB thumb drives, KDE Neon and Mint, with  no settings changed from default except putting in the wifi key (WPA2  PSK).

I have no reason to suspect the wifi card itself, as it  works great in Windows. Iwlwifi, the firmware that goes with it, the  kernel, and the rest of the distro all work with that model of card too,  since the Swift works nicely with that setup.

I've used the script I saw linked here to get some data. I used it also on my Swift, and it all looks the same, yet the Swift works well.

Any input welcome.

---

### Post by praseodym on 2020-08-29
Try
```

sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by Ascaris_ on 2020-08-30
Thanks for your reply.
I already had tried disabling power saving via the 'iwconfig wlp4s0 power off' method, but I tried the method you suggested also, and it's not any better.

[there was a bit in here about it being slow one way in Windows and the other in Linux, but that proved to be something else. I can confirm it is fast in both directions on Windows 10 on the G3 as it is in Linux on the Swift. It's only downloading on the G3 in Linux that is slow.

---

