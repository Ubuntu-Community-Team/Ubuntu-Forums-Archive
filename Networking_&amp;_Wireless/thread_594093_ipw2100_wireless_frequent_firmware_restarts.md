---
title: "ipw2100 wireless frequent firmware restarts"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by matgates on 2007-10-27
I have seen this before, but it is happening a lot more in gutsy than it did in Feisty.

When under heavy load, my wireless networking throughput drops to 0 for five to ten seconds every 15-30 seconds.  This isn't just over the intarwebs - it also happens when doing local file transfers between machines on my local net.

I see these messages in the dmesg output when it happens:

```
[48054.688000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[48064.436000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[48080.412000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[48092.592000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[48102.936000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[48128.128000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[48136.964000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[48146.220000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[48157.696000] ipw2100: Fatal interrupt. Scheduling firmware restart.
```

I would like to know if other people have the same problem, and if there are any suggests to fix it?  I tried disabling ipv6, but no dice.

---

### Post by matgates on 2007-10-27
I think I have managed to solve the problem.  My wireless router has an option which is describes as "Turbo Mode", which I turned off... no more firmware restarts.

This makes me think there is some bug in the driver which makes it vulnerable to a DOS attack, but at least I have better performance now.

The more detailed description of this "turbo mode" reads like this:

> Selecting "Frame Bursting" will result in all devices capable of Frame Bursting to function in frame bursting mode, and all clients not capable to operate in normal 802.11g modes. Frame Bursting mode supports both Frame Bursting enabled devices and non Frame Bursting enabled devices simultaneously. Frame Bursting mode is based on the unreleased 802.11e specification.

The Router is a Belkin F5D7230-4 with firmware version 4.05.03.

---

