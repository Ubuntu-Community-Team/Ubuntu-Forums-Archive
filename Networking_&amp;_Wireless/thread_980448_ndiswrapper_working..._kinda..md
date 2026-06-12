---
title: "ndiswrapper working... kinda."
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by monoxide0184 on 2008-11-12
Well, I have a USB wireless adapter, so I was cautiously optimistic about trying to get Ubuntu running. Anyway, I managed to find a copy of the full Windows drivers for it, put them on a USB pen drive and rebooted into the live cd to see if I could get it working before taking the leap and installing Ubuntu over Windows.

I'm testing with Kubuntu 8.04 with KDE4, X86_64. After installing ndiswrapper from the cd, I browsed to the USB drive and installed the drivers with:

```

ndiswrapper -i netmw226.inf
modprobe ndiswrapper

```

Voila, my wireless card showed up in the network manager. So I tried to connect to my network. No go, it didn't find any networks in range, and when I tried to connect anyway, the connecting bubble popped up and hang at 0%.

I have a feeling that this is a driver error more than anything, it certainly doesn't run 100% on windows either (though it's usually pretty good). Does ndiswrapper support Vista drivers? Perhaps I should try the Vista64 drivers? I really have no ideas about how to go about diagnosing/fixing this issue.

The adapter itself is a Wiretek WTWL54U, which is a piece of crud, but it's running on a Marvell chipset.

---

