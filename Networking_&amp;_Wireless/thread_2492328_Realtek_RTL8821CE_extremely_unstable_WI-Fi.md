---
title: "Realtek RTL8821CE extremely unstable WI-Fi"
date: 2023-11-07
forum: Networking &amp; Wireless
---

### Post by gonzalo96 on 2023-11-07
Hi.

On Windows I don't have any problems, but on Ubuntu the WI-FI is extremely unstable, with little range and continuous drops.  I turned of Power Management but didn't solved it. The driver is instaled but don't work fine. This is the pastebin to wireless.info.txt report:

[https://pastebin.com/eprSX5LZ](https://pastebin.com/eprSX5LZ)

Regards.

---

### Post by TheFu on 2023-11-08
My LUG used to meet at a specific restaurant. They had a netgear wifi router that wouldn't support connections for more than a few minutes from our Linux systems.  Talked it over with the owner and we replaced the wifi - not the router, just the wifi part - with a higher quality Ubiquiti AP.  Connected that up and everyone could connect and we had better connections.  Netgear makes fine home stuff, but, at least back then, their wifi adherence to standards was a little off.  Ubiquiti used to be unknown, but they make a name for being enterprise capable, but at consumer prices.  Their pricing has risen post-COVID, but they are still on my short list for qualify wifi devices.

Unfortunately, I have nothing good to say about Realtek networking, except they are cheap and generally work under MS-Windows.  Not so much for any other OS. I'm very biased.
[https://askubuntu.com/questions/1427310/ubuntu-22-04-1-lts-wifi-keeps-disconnection-after-2-minutes-of-working-fine](https://askubuntu.com/questions/1427310/ubuntu-22-04-1-lts-wifi-keeps-disconnection-after-2-minutes-of-working-fine)

There are lots of settings (20+) that can impact the ability of wifi devices to communicate.  Channel size, specific channels, the number of devices holding, trying to connect, and power management on both sides and a bunch I've never bothered to look up.  In general, if you reset the wifi settings to the factory defaults on the router, that will be the most compatible, but not the highest performance.  Just something to consider.

The other recommendations I see are to disable that wifi chip in the BIOS and buy a $20 replacement that uses the Intel AX200 chips instead.  IDK.  I haven't used wifi with Linux since pre-covid. Wired the entire house years ago.

---

### Post by morrownr on 2023-11-09
> Unfortunately, I have nothing good to say about Realtek networking, except they are cheap and generally work under MS-Windows. Not so much for any other OS. I'm very biased.

I agree with what TheFu said.

If you are determined to keep the rtl8821ce based card, you could try moving to a later kernel and check the firmware to make sure it is the latest. What kernel are you using?

If you decide to move on to a difference wifi card, you are welcome to stop by my site. It is about USB-WiFi but you can post questions in Issues and likely get some recommendations or you could get a USB wifi adapter:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

---

### Post by gonzalo96 on 2023-11-10
I finally solved it following the instructions of the second post in this thread:

[https://forums.linuxmint.com/viewtopic.php?t=394684#google_vignette](https://forums.linuxmint.com/viewtopic.php?t=394684#google_vignette)

I had the same problem as the OP, the problem was the default driver of the repository.

---

### Post by TheFu on 2023-11-10
> **gonzalo96 said:**
> I finally solved it following the instructions of the second post in this thread:

[https://forums.linuxmint.com/viewtopic.php?t=394684#google_vignette](https://forums.linuxmint.com/viewtopic.php?t=394684#google_vignette)

I had the same problem as the OP, the problem was the default driver of the repository.

I truly hope this solves the problem for you over the long term, but that hasn't been my experience.  Whatever you did, you might need to script doing it again, so after each kernel update, re-doing it isn't hard.  I had a similar issue with nvidia GPU drivers too - so after every kernel update, I re-linked realtek and nvidia drivers for a few years. It was a pain.

---

