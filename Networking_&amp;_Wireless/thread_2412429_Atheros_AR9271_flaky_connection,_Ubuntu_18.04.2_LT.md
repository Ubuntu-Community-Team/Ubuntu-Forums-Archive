---
title: "Atheros AR9271 flaky connection, Ubuntu 18.04.2 LTS"
date: 2019-02-12
forum: Networking &amp; Wireless
---

### Post by malcolmw2 on 2019-02-12
Hi,

I am running Ubuntu 18.04.2 LTS on a Dell Optiplex 9020 with a Wireless N USB Adapter w/ External Antenna (Model: TPE-N150USBL from ThinkPenguin.com), and my wireless connection is very flaky. The connection is fast when it works, but frequently, suddenly--and seemingly randomly--drops out. When it drops out, sometimes I will get a '?' tray icon in place of the wifi signal strength indicator at top-right and other times I will still have a few bars of signal strength but no connectivity.

My MacBook is sitting right beside the antenna of my wifi adapter and has no connectivity issues; it always has a strong signal strength and never disconnects.

The output from wireless-info script is here [http://paste.ubuntu.com/p/DyTDXMvq95/](http://paste.ubuntu.com/p/DyTDXMvq95/) and is also attached as a tarball.

Any suggestions on how I can troubleshoot this issue?

Thanks in advance,
Malcolm

[ATTACH]282494[/ATTACH]

---

### Post by lonehades on 2019-02-13
Same happens with me, it just drops sometimes and might come back few minutes later on its own. Top bar icon gets lost and goes to "turn off" drop down menu (with no signal indicator on it)

---

### Post by malcolmw2 on 2019-02-20
It is too early to confirm with confidence, but upgrading to Ubuntu 19.04 seems to have resolved this issue.

---

### Post by malcolmw2 on 2019-02-27
After one week using Ubuntu 19.04 Disco Dingo, I have had very few problems with my wifi; my problem is effectively resolved. A great improvement over my experience with 18.04.2 LTS.

---

