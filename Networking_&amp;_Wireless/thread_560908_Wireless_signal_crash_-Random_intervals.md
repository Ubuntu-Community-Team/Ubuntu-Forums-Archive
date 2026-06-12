---
title: "Wireless signal crash -Random intervals"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by multifaceted on 2007-09-26
I use a Linksys 2.4GHz wireless adapter to receive a signal from the Linksys router with a direct connection. There is another Xubuntu machine connected and never has problems with a direct line. I always get the internet when I start up and it works fine. However, at least once a session,  I will lose signal and will have to reset.

Note: reseting the signal is pretty simple --(I just open network manager, un-check and then re-check "wireless connection")-- and it works fine. It's a rather quick fix but, it is just a huge annoyance.

If it's any significance at all: My signal strength jumps wildly. Averaging around 11% percent and ranges to about 40% with occasional and brief spikes. Does anyone think it may be the driver?

---

### Post by str8line on 2007-09-27
Check Wireless channel in the Linksys router.  Using Channel 1, 6 or 11 can dramatically increase the connected signal as these are the only 3 channels that are not shared with each other in the North Americal spectrum.

---

### Post by multifaceted on 2007-09-28
> **str8line said:**
> Check Wireless channel in the Linksys router.  Using Channel 1, 6 or 11 can dramatically increase the connected signal as these are the only 3 channels that are not shared with each other in the North Americal spectrum.

I'm trying to think of how I can configure that........? There is said Xubuntu machine with a direct Ethernet to the router. (that's where it gets it's connection) I can't see too much other than the fact that I am getting a signal from that vantage point.

The network manager on my main wireless machine doesn't give me many options for selecting which channels to use as far I can tell.... but then again, I am no expert. Is there something I am overlooking?

---

### Post by str8line on 2007-09-28
Set it in the router.  The card is set to scan as a general rule.  The 3 channels listed are the three strongest in the North American Spectrum.

---

### Post by multifaceted on 2007-09-29
Ahhh.... I actually feel kind of stupid now, lol. I am going to try that out now, I'll tell you how it goes, thanks!

---

### Post by tgalati4 on 2007-09-29
It could be interference or it could be a faulty antenna.  If signal strength jumps around on channels 1, 6, or 11, then that increases the likelyhood of an antenna connection problem.

I'm assuming this is a pcmcia card that sticks out the side.  If the card is flexed too much, then that will weaken the solder connections.  It's also possible that the card is defective.  Do a google search on your card model and see if others are having issues.

I've experenced heat issues with some laptops.  The pcmcia slot is sometimes over the hard disk and the heat from the hard disk causes the card to act funny.  Pull the card out after a loss of signal and feel how warm it is.

---

### Post by specker on 2007-09-29
I have recently started getting the same problem under Gutsy.  When copying large files over NFS the connection drops.

---

### Post by multifaceted on 2007-09-29
> **tgalati4 said:**
> It could be interference or it could be a faulty antenna.  If signal strength jumps around on channels 1, 6, or 11, then that increases the likelyhood of an antenna connection problem.

I'm assuming this is a pcmcia card that sticks out the side.  If the card is flexed too much, then that will weaken the solder connections.  It's also possible that the card is defective.  Do a google search on your card model and see if others are having issues.

I've experenced heat issues with some laptops.  The pcmcia slot is sometimes over the hard disk and the heat from the hard disk causes the card to act funny.  Pull the card out after a loss of signal and feel how warm it is.

Actually, the machine I am experiencing this on is a desktop. The wireless adapter is USB fed and the antenna appears to be fine. It's been mounted to the wall and untouched since I bought it.

---

### Post by tgalati4 on 2007-09-29
Use WiFi Radar or Kismet or some other sniffer program.  "There's a new network in town and there ain't room enough for the both of us."

You might have a neighbor who just set up a router that's causing interference.  Or it could be a neighbor's 2.4 GHz telephone.

---

