---
title: "Wireless: Giving back to the community"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by jeffblacktn on 2007-01-04
Hello everyone,

Laptop: Dell Latitude D505
Built-in Wireless card:  Broadcom bcm4309
Ubuntu Version: Edgy Eft upgraded from Dapper Drake

After initial installation of Dapper Drake Broadcom wireless did not function.  Followed instructions on this forum to utilize ndiswrapper without success.

Upgraded Ubuntu to Edgy Eft from Dapper Drake.

Broadcom wireless still did not function.

Happened upon a D-Link AirXpert PCMCIA wireless card (DWL-AG650) that I had purchased several years past for an old laptop I once used.  Card maybe cost approximately $30.00 several years ago.

Inserted card into PCMCIA slot then restarted Ubuntu.  Card was recognized and configured without issue.

Configured card to access my AP which is WEP enabled.

All is well.

Best,

jb

---

### Post by spd106 on 2007-01-04
Thanks for the info. 

You were unlucky having Broadcom card built-in rather than the Intel 2200, since it doesn't have the same level of support. But as you discovered the Atheros based D-Link card has better support than the Broadcom card, while it's not the best solution due to non-free kernel modules.

If you want to contribute further maybe you could help update the wiki page [https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD505](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD505). Go read [this]("https://wiki.ubuntu.com/LaptopTesting") to get started

---

