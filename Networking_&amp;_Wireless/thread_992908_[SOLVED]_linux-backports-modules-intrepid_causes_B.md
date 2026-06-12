---
title: "[SOLVED] linux-backports-modules-intrepid causes Broadcom Wired Connection to Fail"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by mfdc1969 on 2008-11-25
Just did a fresh install of Intrepid and followed instructions on [Community Page]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") to get my Atheros wifi going.

The Atheros chipset is working perfectly but using *linux-backports-modules-intrepid* causes my Broadcom wired network to fail 100% of the time. I can't get a wired connection to my router.

I'm not alone and there is already a [LaunchPad Bug Report #287450]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/287450").

I have updated my Synaptic Repositories but there is no update apparent for this module as of the time of writing this.

So, I'm wondering - if I un-install *linux-backports-modules-intrepid* and then go get the source for Ath5k and build it as per Madwifi Project instructions will this eliminate my problem?

---

### Post by Ayuthia on 2008-11-25
> **mfdc1969 said:**
> Just did a fresh install of Intrepid and followed instructions on [Community Page]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") to get my Atheros wifi going.

The Atheros chipset is working perfectly but using *linux-backports-modules-intrepid* causes my Broadcom wired network to fail 100% of the time. I can't get a wired connection to my router.

I'm not alone and there is already a [LaunchPad Bug Report #287450]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/287450").

I have updated my Synaptic Repositories but there is no update apparent for this module as of the time of writing this.

So, I'm wondering - if I un-install *linux-backports-modules-intrepid* and then go get the source for Ath5k and build it as per Madwifi Project instructions will this eliminate my problem?

According to the bug report, it says that intrepid-proposed needs to be added to the list of repositories.  Have you already done this?

---

### Post by mfdc1969 on 2008-11-25
I'm feeling a little silly right now ... I had mistakenly subscribed to *intrepid-backports* instead of *intrepid-proposed*!

After the updates and a shutdown it all works beautifully!

:oops:

Thanks.

Michael

---

