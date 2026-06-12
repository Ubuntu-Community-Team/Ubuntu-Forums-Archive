---
title: "Acer Aspire 5100 Wifi"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by RyanGamerGoneGrazy on 2007-11-10
Hi All,


I've been running Ubuntu on several desktops for the past few years, however, I recently installed it on my Acer Aspire 5100. It works quite well except for the wifi


Wired connections work fine, however, wifi does not, Its using the atheros chipset

I've tried ndiswrapper, and madwifi, with no luck.....I'm not exactly skilled at terminal and what not though

Can/Does someone have some help to get wifi working?

Cheers

Ryan

---

### Post by nae5 on 2007-11-11
i would search the forum for the lspci output for your wireless card. i got nuthin else..

---

### Post by beeper on 2007-11-13
Works for me on my Acer 5100.....Atheros AR5006EG......AMD64

First obtain the 64bit WinXP driver for Atheros AR5007......
Then install it using the 'Windows Driver Install (ndiswrapper)' Applet

System -> Administration -> Windows Wireless Drivers

Once you have the driver installed...then you should be able to go to the 'Network Manager' applet and set up your wireless connection.

After doing updates and rebooting....it disappeared. So I uninstalled and then reinstalled it and now its there after reboot and power down.

Some of the features don't work in 'Network Manager' due to ndiswrapper limitations but the connection works just fine for me.

I have the wireless connection working on WinXP, VIsta, and Gutsy Gibbon all on the same Acer Aspire 5100-5300

Good Luck

---

### Post by RyanGamerGoneGrazy on 2007-11-18
Thanks guys!


It works now, but only on un-secured connections. WEP and WPA, and it wont seem to connect....


Any ideas?



Ryan

---

### Post by sporkubus on 2007-12-12
I installed ndiswrapper using Synaptic but I can't find it under System > Administration. How do I use it?

---

### Post by sporkubus on 2007-12-12
Oh, nevermind, I reinstalled it using Add/Remove and there it is. But now where do I find this driver? I thought I had it but I have an EXE file and ndiswrapper needs an INF file...

---

### Post by sporkubus on 2007-12-12
So I finally got this driver from Acer's site.

I opened up Windows Wireless Drivers, clicked Install, selected the .inf file for the 64 bit XP driver and... nothing. The dialog box just disappears, nohting shows up in the Installed Drivers list, and the wifi still doesn't show up.

Please, somebody help!

---

