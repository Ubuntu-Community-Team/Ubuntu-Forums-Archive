---
title: "OpenVPN, Android, Shorewall - with a side of confusion!!!!"
date: 2016-11-23
forum: Networking &amp; Wireless
---

### Post by sparky-steve on 2016-11-23
Good day all!

I like to think of myself as pretty linux savvy, both desktop and server (I have multiples of both at home), but I am having issues with setting up OpenVPN; This has eluded me for almost a year now (on & off!)

So first of all, here's my setup.

ISP Modem, connected (ethernet) to my kubuntu router (16.10), connected (ethernet) to my home network.

Kubuntu router is running shorewall and various customized scripts I've written over the years; Also on the server are squid, dansguardian, bind etc etc

What I'd like to do is connect to my home network on my Android phone using "OpenVPN Connect" which requires an .ovpn config file.

I have installed and configured OpenVPN on my server using this guide: [https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html)

It gives me 3 files, ca.crt, client1.crt & client1.key but no .ovpn file.

I found this script to create the .ovpn file [https://gist.github.com/trovao/18e428b5a758df24455b](https://gist.github.com/trovao/18e428b5a758df24455b) - but that talks about a TLS key

I guess my initial question would be.... Is there an 'easy' interface (I use webmin, and have 'OpenVPN + CA' installed, but as yet no idea how to use it) to get this all working seamlessly

Failing that easy option, what am I missing, and can anyone point me to a complete a-through-z guide on setup - all I have found are fragments from here and there, and trying to put them together with little success.

Thanks!
SS

---

