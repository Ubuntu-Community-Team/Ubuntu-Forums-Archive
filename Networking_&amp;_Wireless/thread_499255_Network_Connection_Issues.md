---
title: "Network Connection Issues"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by chalka on 2007-07-12
let me start off by saying im new to linux, and im not all that "versed" with computers or networking for that matter. i recently downloaded ubuntu for my dell laptop (which currently runs vista home premium). when i booted ubuntu to test the waters before installing it fully, i noticed  it wasnt picking up my network connection. it was originally set to WPA, then i switched to WEP with a passcode, then i swtiched it to completely open just to see if i could get a connection going. none of which worked and im wondering if its a issues with my router, or if there's an issues with my wireless card. my computer is a dell inspiron 1501 with the dell wireless 1390802.11 minicard. does anyone have any ideas for a remedy?

---

### Post by spd106 on 2007-07-14
I recommend that you read this wiki page for setting up your wireless card.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

This process is best done with a temporary wired connection, just until you have the card working.

After that it should work with any of WPA(2), WEP or even unencrypted. Make sure that you have the AP set to broadcast it's SSID, Network Manager doesn't like it switched off at the moment (should be fixed in the next release).

---

