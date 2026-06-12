---
title: "wirless on HP laptop MEDIATEK MT7630e"
date: 2014-05-20
forum: Networking &amp; Wireless
---

### Post by brick2 on 2014-05-20
MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter

My friend just got an HP laptop: HP PROBOOK 450 G1

I pretty much have the same problems as with my own laptop but I managed to fix it all on my laptop with relative ease jsut took me some time and people on this forum help me out.

Can get wirless to work at all, even the wirless button is not responsive. If somebody could direct me in the right dirrection of the proper drivers or give me any other advice.
I ve installed Ubuntu 14.04 LTS.

---

### Post by dim4 on 2014-05-22
I'm with same [COLOR=#000000]HP laptop: HP PROBOOK 450 G1 - same problem with wifi Mediatek [/COLOR]MT7630e...I didn't find working solution. Maybe it's new card and not enough supported yet. Anyway - I think this is a big trouble with new laptop...

PS: Here are some drivers working with kernel 3.5 -  [https://github.com/anthonywong/mt7630](https://github.com/anthonywong/mt7630) (may be "working" - I have not tried them yet)

---

### Post by brick2 on 2014-05-22
Does anyone else have any further information on the matter?

---

### Post by varunendra on 2014-05-22
> **brick2 said:**
> Does anyone else have any further information on the matter?

Only that no Linux driver for this chip seems to exist yet. At least not to my knowledge, or wikidevi's : [https://wikidevi.com/wiki/MediaTek_MT7630E_Reference_Design](https://wikidevi.com/wiki/MediaTek_MT7630E_Reference_Design)

What dim4 suggested is clearly an experimental driver, and would run only on an outdated kernel. So it seems (to me) that a windows driver with 'ndiswrapper' may be your only hope for now.

I can't promise any specific help on ndiswrapper (don't have much experience with it, and won't have much time since tomorrow), but here is a comprehensive guide : [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If your Ubuntu installation is 32 bit, you'll need 32bit version of windows driver to use with ndiswrapper, for 64bit installation the driver should also be 64 bit version.

---

### Post by dim4 on 2014-05-28
[COLOR=#000000]varunendra, 
[/COLOR]I didn't know this 'ndiswrapper'. It was a very good idea but unfortunately not work for me...I will buy WiFi USB adapter.

---

### Post by cqfd93 on 2014-09-01
Hi,

Check out comment #161 (and if it doesn't work for you, comment #125) of bug #1220146

[https://bugs.launchpad.net/ubuntu/+s...6/comments/161]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/161")
[https://bugs.launchpad.net/ubuntu/+s...6/comments/125]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/125")

Hope this helps

---

