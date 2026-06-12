---
title: "Belkin Wireless G USB Network Adapter"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by tompickles on 2007-06-13
I am currently on Win 2k happily browsing the net attached to my Router with WPA encryption. Even though the box in my hand with teh specs to the Wireless adapter says it only support WEP. When I booted up the Live CD of Feisty, I could see my network fter a few minutes in the Network Manager drop down box thing from the top right of screen, but it says hardwre did not support security of network. Meaning, can't support WPA, though it clearly does as I'm attached to a WPA network!

Confused!

---

### Post by spd106 on 2007-06-14
Most wireless devices can support WPA, if not in hardware then in software via wpa_supplicant. There are some drivers that do not work well with wpa_supplicant because they implement their own authentication stack. I am a little hazy on which ones as I haven't researched this much, though I think one of the Ralink card drivers does this.

Just out of interest which supplicant are you using on Win 2K? I have had a bad experience with the McAfee (WSC) one, though I rarely boot into Windows any more. I can't believe Belkin don't provide one. There's no way I'm ever buying a Windows upgrade just to use WPA.

---

