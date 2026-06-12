---
title: "Setup wireless Intel 3945"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by 1/0 on 2007-10-05
Ok, I'm stuck and feeling like a real noob here. I've just bought a laptop (HP dv8289) and the first thing was to get rid of that thing called OS they had put on it. One of the issues that are left to deal with is the wireless connection. The regular way works fine. 

The NIC is a Intel 3945 one. I've got Kubuntu 7.10 on it with knetworkmanager and wpasupplicant installed. The modules are loaded (ipw3945 and iwl3945) but the only thing iwconfig gives me is:

```
lo no wireless extensions.

eth0 no wireless extensions.

```

My /etc/network/interfaces:

```

auto lo
iface lo inet loopback

```

I just don't know how to configure the wireless... I've tried wicd, same same. No firewall. I must have missed something really easy but I just can't seem to figure out what and there are tonnes of threads about this, yet I can't figure it out so help is much appreciated!

---

### Post by Trance Gemini on 2007-10-05
check if your wireless device is determined by OS with no problems.
(and also check if your wi-fi button on the laptop case is turned on. I know it sounds stupid, but that could be the reason also) :)

---

### Post by 1/0 on 2007-10-05
> **Trance Gemini said:**
> (and also check if your wi-fi button on the laptop case is turned on. I know it sounds stupid, but that could be the reason also) :)

I knew it was something easy... Now the router at least shows in the list. Now I only have to figure out how to actually get connected but I will probably solve that now by fiddling around a bit with the security settings. Anyway, thanks for the help!

---

### Post by 1/0 on 2007-10-05
I got it working now but I just realized one thing. The maximum speed I can reach via wireless or wire is about 340kb/s, even between two computers on my lan where the others do it at about 2000kb/s. What might be causing that?

---

