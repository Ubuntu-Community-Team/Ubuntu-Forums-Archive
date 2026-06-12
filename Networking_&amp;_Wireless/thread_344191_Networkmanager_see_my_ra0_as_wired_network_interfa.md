---
title: "Networkmanager see my ra0 as wired network interface"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by macozz on 2007-01-22
Hi all,
I just partially resolved a problem of scan wifi network with rt2400 driver (see thread [http://www.ubuntuforums.org/showthread.php?t=341862](http://www.ubuntuforums.org/showthread.php?t=341862)) and now experienced another problem.
Once again I try to use NetworkManager. Previous times I tried it I desisted because normally  it doesn't detect the networks. Now, to vary, it detected interfaces, but surprisingly lits my ra0 (rt2400 driver, PCMCIA) as a wired interface, and the network as a wired network. Since I am writing  this with only this net connection, I know it work, but, besides not recognizing it as wireless NM list a wrong IP address when I click on "Connection Information".
To test that, I installed the rt2400 utility, RutilT, which give me the correct IP, but does not show the link quality and signal level (they are just empty). Netaplet also recognize correctly ra0 as wireless and give the correct ip info, but also does not show any intensity signal indication.
I I install a wired PCMCIA card along with the wifi one, both them are listed as wired by NM.
Someone has idea about the reason for this behavior of NM?

Thanks allot!

Mario

---

