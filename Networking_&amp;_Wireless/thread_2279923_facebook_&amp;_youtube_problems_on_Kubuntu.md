---
title: "facebook &amp; youtube problems on Kubuntu"
date: 2015-05-26
forum: Networking &amp; Wireless
---

### Post by Telxonator on 2015-05-26
Hello all,

I recently got my AT&T Uverse upgraded, and I have trouble navigating youtube and FB, YT vids will take forever to decide to load, and FB won't load all the pictures. After searching, I found several articles on DNS issues, so I changed my DNS on the kubuntu machine to freeDNS servers with instructions on their site. Still no go on the Kubuntu PC, but the Fedora one and the other one running Win 7 work fine, as do the Android devices, which leads me to believe it's on the Kubuntu box alone, and probably a misconfigured setting or some such. Yahoo mail seems to not work with the new DNS settings.

All other sites seem to be fine, and I am running Firefox on all 3 machines, and it's all the same versions of FF, with the same add ons on each, so likely not FF.

What do I need to look into/change? Running 14.04 LTS, fwiw

---

### Post by Telxonator on 2015-05-27
Would really like an answer to this, surely someone knows what I should do. using Google DNS in my network settings, but that really hasn't solved anything.

---

### Post by Telxonator on 2015-06-02
curious why no one has a clue about this, is it because I'm new, or because no one knows?

---

### Post by wildmanne39 on 2015-06-02
No it is not because you are new, you have a very strange issue and no one that has seen your post knows or they would have posted I am sure.

---

### Post by Telxonator on 2015-06-02
Wild Man, was kind of wondering if that was it, and yes it is strange. Thanks for the input.

---

### Post by NoWayWin8 on 2015-06-02
Maybe your upgrade included ipv6 internet in addition to ipv4. Check with your ISP to find out. When ipv4 and ipv6 are both active it can cause DNS resolution issues, and in my own situation, I, too, noticed the problem being particularly apparent when connecting to Facebook and Youtube,.. perhaps it has something to do with their use of Flash?

For me, I had to change Ubuntu WiFi Connection settings for ipv4 to "Automatic DHCP Addresses Only" and leave0 ipv6 on "Automatic". But only try this if you know your Internet uses ipv6.

---

### Post by Telxonator on 2015-06-03
> **NoWayWin8 said:**
> Maybe your upgrade included ipv6 internet in addition to ipv4. Check with your ISP to find out. When ipv4 and ipv6 are both active it can cause DNS resolution issues, and in my own situation, I, too, noticed the problem being particularly apparent when connecting to Facebook and Youtube,.. perhaps it has something to do with their use of Flash?

For me, I had to change Ubuntu WiFi Connection settings for ipv4 to "Automatic DHCP Addresses Only" and leave0 ipv6 on "Automatic". But only try this if you know your Internet uses ipv6.

This worked, read about it on a Uverse site, went in and disabled ipv6 on the router and it fixed it. Hopefully it stays fixed. Thanks for the info, I'll also check the net settings on this machine.

---

