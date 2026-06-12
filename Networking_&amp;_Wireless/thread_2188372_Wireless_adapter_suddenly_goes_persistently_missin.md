---
title: "Wireless adapter suddenly goes persistently missing in Ubuntu"
date: 2013-11-16
forum: Networking &amp; Wireless
---

### Post by anlag on 2013-11-16
On my EeePC 1000HE ASUS netbook, I've had a strange issue lately. A couple of weeks ago, I noticed it had disconnected from the wifi, and could see no networks, so I thought I'd try and disable and reenable it in case that jolted it. I never got a chance to reenable it; the adapter was quite gone. I rebooted, and it stayed gone. I was running Lubuntu 13.10 at the time. After hassling for a while, I just reinstalled it, switching to Xubuntu 13.10 for variation.

Now, after about a week, I've run into the same issue again, and made sure to better document it. Like last time, it's happened while the netbook's been running, that the wireless has disconnected and the wireless adapter doesn't seem to be there anymore. Looking into dmesg, I could see things like this, with a lot of repetitions:

> 55571.294552] wlan0: authenticate with f8:1a:67:3e:3a:be
[55571.312707] wlan0: send auth to f8:1a:67:3e:3a:be (try 1/3)
[55571.365287] wlan0: send auth to f8:1a:67:3e:3a:be (try 2/3)
[55571.405415] wlan0: send auth to f8:1a:67:3e:3a:be (try 3/3)
[55571.432088] wlan0: authentication with f8:1a:67:3e:3a:be timed out
[55586.663425] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[66770.275240] wlan0: authenticate with f8:1a:67:3e:3a:be
[66770.288538] wlan0: send auth to f8:1a:67:3e:3a:be (try 1/3)
[66770.292065] wlan0: authenticated
[66770.296133] wlan0: associate with f8:1a:67:3e:3a:be (try 1/3)
[66770.299832] wlan0: RX AssocResp from f8:1a:67:3e:3a:be (capab=0x431 status=0 aid=2)
[66770.300291] wlan0: associated
[66770.300366] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

Sometimes the "send auth" would go through on first attempt, sometimes it would fail all three. This seems to have been going for a while. I have the full dmesg on file, in case. Now, after rebooting, I looked into dmesg again and there is nothing whatsoever about wlan0 or the above MAC address. Rebooting again, I check into BIOS and find that "Onboard WLAN" is disabled. I reenable it and boot into Xubuntu again; still no adapter visible. I reboot again, check BIOS and notice it's once more been disabled. I enable and boot into my cobweb draped dual installation of Windows XP, and there the wireless works. Rebooting again into Xubuntu, it's the same story - it doesn't show up because once again it has been disabled in the BIOS.

I guess it's not far off to think of intermittent hardware error, like the network adapter being about to give in. Perhaps it went up and down too much, so Xubuntu (like Lubuntu the week before) somehow blacklisted it and from there on automatically disables it on BIOS level every chance it gets? I didn't know the OS could actually do that, but it definitely gets shut down in BIOS every time I boot into Ubuntu. Whereas in the 15 mins I spent in Windows it worked fine, without getting disabled, but that's of course also a very short time compared to how long I've had it running in Ubuntu.

The only alternative idea I have is that it's somehow a stability issue with my particular hardware and some change in Ubuntu 13.10. The problems started shortly after I upgraded from 13.04, but I can't say that I've ever seen anything like it. As a side note, I noticed today the sound had gone too, which did not happen at the same time as the network card gave up. I haven't looked into that much, it may not be related. Probably isn't.

Anyhow, I'm posting to hear if anyone has any ideas or suggestions for 1) what might be causing this, and 2) how to resolve it. If it's indeed dying hardware then fair enough, but can I somehow get it back to work with my current installation of Xubuntu without having to reinstall another time? Clearly the adapter isn't entirely dead since it works in Windows, and since it started working again after I reinstalled Ubuntu last time, so if I could squeeze a bit more time out of it and perhaps monitor it or whatever, that'd be nice. And if it's whatever else, that I can fix permanently, then all the better.

---

### Post by anlag on 2013-11-16
Well, this might be one of the fastest selv-solved threads for a while, but of course I find the problem within a couple of minutes after finally coming here to post. Turns out the wifi switch was flipped off in Ubuntu, which I'm sure I haven't done myself, but I guess there's always the chance that one of our cats successfully managed to press Fn+F2. I'm not sure it explains the dmesg entries, unless one of said cats was laying on both keys for a considerable time making it go up and down... I'm not convinced, but since it's now back to working, the good people of Ubuntuforums can probably better spend their time on other people's problems. Must say I'm a bit surprised the in-OS off switch went and changed the BIOS without restoring it, but you learn new things every day I guess. 

I'll post back if it dies on me again, when I can rule out feline interference. Cheers!

---

