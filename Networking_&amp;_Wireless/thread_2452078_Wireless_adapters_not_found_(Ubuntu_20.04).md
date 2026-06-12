---
title: "Wireless adapters not found (Ubuntu 20.04)"
date: 2020-10-16
forum: Networking &amp; Wireless
---

### Post by sliwkahax on 2020-10-16
Hello. I tried to connect to wireless network on ubuntu but it says that there are no adapters found.
[ATTACH=CONFIG]287163[/ATTACH]
I used wired connection before and it worked just fine.
Other devices see the wifi network i wanted to connect to.

---

### Post by TheFu on 2020-10-16
There are 5 common, possible, situations:
The wifi card/chips in/used by your system 
[LIST=1]
[*] are not supported and will never be supported.
[*] need a little manual help getting the driver installed and will NOT maintain itself, always needing a manual rebuild after every new kernel is installed
[*] need a little manual help getting the driver installed, but will maintain itself using dkms going forward.
[*] are supported out of the box (fully plug-in-play), but something else has gotten messed up to prevent them working today.
[*] might be soft or hard locked by the system or BIOS. This is usually easy to solve using **rfkill** + some options or going into the BIOS or using an Fn + F2 (or something like that on most laptops) to toggle the enable/disable function for the internal wifi adapter.
[/LIST]

So, what's next?  Gathering information, of course.  There is a sticky thread at the top of this sub-forum that has a **wireless-info** script inside it.  Get that script and run it. It should create an anonymous URL where we can look at the output and provide ideas.

Here's hoping the problem is just that the BIOS has the card disabled and the wifi card is intel-based and fully supported.

---

