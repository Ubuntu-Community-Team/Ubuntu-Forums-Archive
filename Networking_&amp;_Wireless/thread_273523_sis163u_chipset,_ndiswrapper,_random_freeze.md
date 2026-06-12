---
title: "sis163u chipset, ndiswrapper, random freeze"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by plowna on 2006-10-08
Hi,

I also posted [here]("http://ubuntuforums.org/showthread.php?t=271696") but I have a feeling its the wrong forum for it.

Anyway just started playing around with Ubuntu 6.06. Everything works fine, except for my wireless adapter.

Wait, I mean ndiswrapper works fine with my wireless USB adapter (KOB WL550-C, sis163u based), except I get random freezes. Everything locks, mouse, gnome, audio, everything.

This is using 2.6.15-27 kernel package and latest ndiswrapper/utils (1.8 I think is the package).

- I've tried compiling the latest version of ndiswrapper (1.25? Apparently? What is going on with the versioning here?). It installs the windows driver fine, however when I modprobe ndiswrapper it won't apply any changes to wlan0's configuration, and iwlist won't find any networks when it "scans" (its definitely there!). This happens with 1.25 and 1.26RC1.

- Tried updating the windows driver - I already had the latest driver from the company's website (Mercury Wireless) but have now tried the latest driver from SiS' website. Works fine with Windows XP SP2 but same problem under ndiswrapper.

- Next on the list is a new kernel compile (2.6.18) from vanilla sources + kc patch + 1.25 source. Hey! You never know.

- Just in case, tried without ACPI. (acpi=off in grub on boot) Didn't work.

- Its definitely ndiswrapper. Left it running all night without ndiswrapper loaded. With ndiswrapper loaded, the system will last without a hard lock maybe an hour or two at best, sometimes within minutes.

I might as well cross-post this to ndiswrapper forums as well. If I'm lucky they might point me in the direction of my mistakes. (Apart from having a wireless USB that crashes the kernel)

cheers,
Steve

---

