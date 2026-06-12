---
title: "Wireless networking problems.  Asus P5B / Realtek 8187"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by Cloudane on 2007-02-16
I'm trying to get wireless networking going on an Asus P5B.  I already had to recompile the kernel with a patch (and the default ubuntu kernel config) to get wired networking up and running for the 1Gb network socket.

It will happily *see* the wireless access points, but won't consider connecting to them.  DHCP fails.  It did this from the moment of a clean install (before any kernel compilation or anything)

The wireless on this board consists of an Asus WiFi-AP Solo... better known as a Realtek RTL8187... plugged directly into one of the motherboard USB headers.

I've tried disabling the kernel drivers by adding r8187 to the module blacklist and then running the Win98 drivers via ndiswrapper.  It does exactly the same thing!

I know the wireless adapter works, as it was working fine in Windows.

I have two wireless access points - one WEP secured and one open (different networks and internet lines), one's a Draytek (WEP) and the other's a D-Link (open).  It does the same on both, so I know it's nothing to do with the make of router or whether WEP is used or not.

Here's the output of *sudo iwlist wlan0 scanning*:

```
          Cell 01 - Address: 00:13:46:9A:31:73
                    ESSID:"D-Link"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-48 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


           Cell 02 - Address: 00:0C:76:C9:48:8E
                    ESSID:"vigor2600g"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-51 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 54 Mb/s; 9 Mb/s; 18 Mb/s
                              36 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

I find the **Quality:0/100** bit interesting.  I'm sat right next to both routers.  Maybe this is the root of the problem?

Here's the content of /etc/network/interfaces (before I changed it back to wired for this post)

```
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid D-Link
wireless-channel 6
wireless-mode managed
auto wlan0

```

I'm now officially out of ideas.  Any ideas much appreciated!

---

### Post by Floppyjoe on 2007-02-16
Take a look at this post. It is for another card but this guy says that the native drivers were still somehow getting involved after blacklisting them. He searched for and deleted each occurance of them on his system.

[http://ubuntuforums.org/showthread.php?t=329299](http://ubuntuforums.org/showthread.php?t=329299)

This is what he wrote:
> After finishing the tutorial, sometimes my hardware still doesn't work. I find that the use of the ndiswrapper driver is still preempted by the rt*818* drivers - even though they've been blacklisted. I use locate rt*8187* to find the modules, and then I delete every occurrence. This resolves the problem. The way to test for this is by running dmesg, and scanning the output for an indication that the rt*818* were loaded.


---

### Post by Cloudane on 2007-02-16
Thanks for the suggestion!

Well, I tried manually eradicating all of the modules mentioned in that tutorial (and rebooting), but sadly it didn't help.

---

### Post by Cloudane on 2007-02-16
Well I've done a lot of fiddling around and still no luck.  Rant time.

The 3 most important things to me, and how Linux handles them....

a) My photos.
It doesn't do these properly. Even with the best of support from Bibble Labs, I've gone through several of my landscape shots and the BBpro/DPP shots are miles better.

b) Games.
Okay, I was willing to 'put up' with just WoW and whatever's available for Linux, but first off... ugh, what a sacrifice to begin with. Secondly... I've yet to get WoW actually going. Haven't tried as much as the other issues, but it's far from click-n-go.

c) My hardware.
I don't care if I only use something once or twice in its lifetime, I want it to work. No workie = no deal. RTL8187 support, I'm looking at you.

These are the 3 most important things to me in my computing experience, and it doesn't do ANY of them well.

My "running Ubuntu" experiment was mostly carried out to satisfy the Linux evangelists who were insisting that Linux is perfect for everyone and that anyone who doesn't think so didn't give it a fair enough try. I've been pissing about with it since 1996, but it seemed fair to try and modern and very popular distro.

I think I've given it a fair trial. I'm sorry but I don't think it's for me. There are many many things that I love about it, but unfortunately so many things let it down too. I acknowledge that it's mostly the fault of the hardware and software manufacturers not being open enough, but that's not my problem. Maybe I'll buy a "Linux Box" one day, if it ever gets a real killer feature, but as things stand I can't ever see it being a primary OS.

We all say Microsoft are greedy blah blah but I've come to realise... the £70ish for the OEM version is a bargain for an OS that is fully supported, has all the features in place and just works. Should I spend half my waking life struggling, or just hand over £70 and have everything working? Hmm. In terms of money I'd already be paying £35-40 for Bibble, another tenner for Transgaming, so Linux ain't free (as in beer). At least for people who want the best.

That's the gist of it - I want the best. I'm that kind of computer user. I don't consider "well, you can't have x, y or z but we've got something half working" as an acceptable answer. Stuff the half working. I want the best, and am willing to pay for it.

I wouldn't even consider the Mac as a primary desktop because that's lacking support too, even though it's otherwise an awesome platform. I don't make compromises.

---

