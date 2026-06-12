---
title: "OpenVPN (client) connection issues with certain LAN setup (home)"
date: 2017-06-10
forum: Networking &amp; Wireless
---

### Post by JV_Roig on 2017-06-10
(This is a problem I've encountered in Ubuntu 17.04 and also Fedora 25; I'm laying out all the tests I've done, which includes references to F25. In general, though, this seems more like a Linux network stack issue than just Ubuntu/Fedora)

I've done a lot of testing and I've identified and cleared up a lot of factors in this problem, so I hope it helps you guys to figure this out.

**Problem:** OpenVPN (client, through "sudp openvpn --config client.ovpn" command) connects, but after initialization completes, it behaves as if I have no internet connection. Adapter is on, tray icon is ok, but trying to browse to anything (even just google) either gets an error or tries (and fails) to load forever (throbber icon in browser tabs just keep spinning to no avail).

**When/Where does this happen:**
1.) In my main desktop ("Computer A" from here on), running Fedora 25, at my home LAN.
2.) In my main laptop ("Computer B" from here on), running Fedora 25, at my home LAN
3.) In my secondary laptop ("Computer C" from here on) running Ubuntu 17.04 at my home LAN.

**Scenarios tested when/where this does NOT happen (i.e., OpenVPN client works perfectly fine):**
1.) Computer A, at home LAN, when I boot into Windows 7.
2.) Computer B, running Fedora 25, at my friend's house (different LAN)
3.) Android smartphone, running the official OpenVPN app, on any LAN I've tested so far.

(Note: all of these tests connect to the same VPN server at work)

**From all the test cases above, these are some sticky factors we gathered:**
a.) The Android client and Windows client don't seem to have a problem.
b.) Linux distros (Fedora and Ubuntu) encounter the problem, but only at my home LAN, since they work at my friend's house / LAN.

**What's the difference between my LAN at home and at my friend's house? **
My friend has only 1 network device at his house - his ISP's wifi-router. His computer and our laptops/phones connect to it directly.
At my home, I connect to a wifi network switch in my room, which is just an extension of the main wifi swtich in the living room (signal issues), which in turn is connected to my ISP-provided router. It doesn't matter which switch I am connected to (my room switch or the living room switch), openvpn client just doesn't work.

If I emulate my friend's LAN setup (by plugging my laptop directly to the ISP-provided router), *voila*! OpenVPN works as expected.


**Concluding take-aways, so far:**
It seems to me like a NetworkManager problem, or at least something in the network stack of current linux distros, that don't play well with my LAN setup / network devices. On the same network, the Android and Windows clients work fine, only the Fedora/Ubuntu distros don't (haven't tested any other distros). But when plugged directly to the ISP-router, they are fine.

At this point, I don't even know what to check anymore. Making this thread to get suggestions of what to try.

---

