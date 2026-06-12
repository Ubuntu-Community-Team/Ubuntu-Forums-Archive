---
title: "Broadcom wireless"
date: 2005-10-02
forum: Networking &amp; Wireless
---

### Post by celluloid on 2005-10-02
Hey. I've installed a Belkin wifi card via Ndiswrapper as it's not recognised by Hoary.

The card is recognised in ndiswrapper and iwconfig and ifconfig however I cannot get the card to see the accesspoint? I can switch it to active in the Network tool but it still does nothing. 
iwconfig wlan0 essid belkin54g does nothing either.. when i type iwconfig wlan0 I still see ESSID: Off/Any

Can anyone help me. It's on my brothers computer, trying to convert him :)

---

### Post by dcraven on 2005-10-02
In my experience, the version of ndiswrapper in Hoary does not work with the Broadcom chipset. It appears to work fine, but cannot connect, just as you describe. The good news is that it can be made to work. The bad news is that either you need to compile a newer version of ndiswrapper yourself, or you need to upgrade to Breezy. Either way works. To compile your own newer version, see the instructions at the [SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto) wiki page. To upgrade to breezy, which is in preview stages, you can follow the normal upgrade procedure and use the ndiswrapper module in the repositories.

HTH,
~djc

---

