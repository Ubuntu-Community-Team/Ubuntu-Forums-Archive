---
title: "Shoutcast stream constantly buffering"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by DigitalGunfire.com on 2007-05-12
I've been streaming my Shoutcast station from a Linux box for about 4 years now, and I've recently converted the box to Ubuntu. Since the minute of this conversion, I've been experiencing very poor Shoutcast performance to some overseas relays.

My setup is that I run sc_serv on a local box and stream content to it using sc_trans_linux from the same box. Three relays then connect to sc_serv and relay the service out to listeners. One server is inside the US and two are in Sweden.

The box previously ran Redhat ES and this setup performed wonderfully - all servers were smooth with no buffering or skips.

The box recently became compromised and I thought it was a good opportunity to switch the box to my new favorite server OS, Ubuntu. Since the change, my Shoutcast performance has been abysmal to Sweden and I can't figure out why.

The server configs have not changed at all. I copied my old .conf files over to the new box and I'm using those. The US server seems to be fine but the two Swedish servers work for 30 seconds or so and then buffer constantly.

I've tried everything I can think of to troubleshoot this. It really seems to be like some low level networking difference between the kernel I was running on the RH box and this Ubuntu box, but I have tried changing everything I can think of to no avail. Has anyone run into any kind of similar problem and been able to resolve it? I'm close to going back to RH and I really don't want to.

---

