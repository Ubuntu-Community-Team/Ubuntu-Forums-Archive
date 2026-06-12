---
title: "ipw3945 and ieee80211 - incompatibilities between versions"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by Kiril on 2007-07-28
Hello everybody,

after spending days of looking through the Ubuntu forums and trying out every possible solution, I decided my experience should at least be shared:

I have a new HP Compaq nx7400 laptop with a Intel/Pro 3945 wireless card. Normally, this is one of the best supported cards for Linux, or so I have heared. And indeed, the Live CD for Ubuntu Feisty also automatically recognized the hardware and immediately offered me a connection to the wireless network which worked out fine.

But for some reason I don't quite understand, after I installed Ubuntu Feisty the restricted drivers for the card were already preinstalled (fine), some ieee80211 drivers were also a part of the kernel (fine), but the ipw3945 drivers were missing... So I got version ipw3945-1.2.1. I won't go into detail with the troubles I had, but eventually I had to install ieee80211 myself. I installed the latest release - ieee.80211-1.2.18, and did (make install and) "make patch_kernel".  Then I compiled ipw3945-1.2.1 with that.

The wireless network was suddenly there, but immediately after typing the password for cryptography, the computer froze. dmesg gave a message like "ieee80211_crypt: registered algorithm 'NULL'" before giving up. So I am thinking some problem with the cryptogtaphy of the newest ieee80211 version. Nothing helped. I did the complete install again, same result.

After many many retries (and hangups, poor new laptop :(), I finally got everything to work with an older version - ieee80211-1.2.16 AND the newest  ipw3945-1.2.1.

So, these two are the ones that work for me, anything else MIGHT be a problem ...  FYI

So, an obvious compatibility issue with a severe result. A real shame, I thought it was really hard to bring Ubuntu to hang up :)

---

### Post by noob12 on 2007-07-29
The Feisty install should have given you ipw3945 OOB, well almost --you may have had to enable it in **System | Administration| Restricted Driver Manager**.  Ive used it successfully but not extensively on one Dell that had a 3945 chipset.

---

