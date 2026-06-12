---
title: "[SOLVED] Success with Madwifi &amp;amp; Atheros AR5007EG"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by mfdc1969 on 2008-09-08
Last night I successfully got the Atheros AR5007EG working in my Acer Aspire 5610Z with Madwifi. I was previously using ndiswrapper but after following the instructions on the Madwifi site I changed the drivers

    [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

It wasn't working immediately but then I found additional information on this page:

    [http://home.nyc.rr.com/computertaiju...less.html#5007](http://home.nyc.rr.com/computertaiju...less.html#5007)

My main issue was that after installing Madwifi I had not fully disabled/removed ndiswrapper - a few tips on that are mentioned in the second link above.

So far it is working well although connection speed varies from 24/48/54 Mb/s - even though my computer has remained in the exact same room/position only 15' from my wireless router.

I hope this helps others as the Atheros AR5007EG is something I have struggled with too. 
__________________

---

### Post by aquaroot on 2008-10-20
x

---

### Post by mfdc1969 on 2008-11-26
Follow up ...

I did a clean install of Intrepid and installed the module **linux-backports-modules-intrepid** as per:

[INDENT][https://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")[/INDENT]

Everything worked on the wireless side but I had to further apply **intrepid-proposed** updates in Synaptic to resolve an issue that knocked out my Broadcom ethernet connection - described at LaunchPad:

[INDENT][/INDENT][LaunchPad Bug Report #287450]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/287450")


Atheros Wireless is much easier in Intrepid!

My thanks to all those who have worked so hard to make it so!

---

