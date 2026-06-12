---
title: "dvd trouble"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by jwftm17 on 2010-03-23
I need some help i installed unbuntu 9.10 on my sony vaio pcg-k35 and when i try and play a dvd with movie player i get the message an error occurred could not read from resource. I am not sure if i have a bad dvd player or if its due to 9.10. If anyone knows a good optical drive tester i can use or a site that i can maybe download the lastest driver., or any help u could give me it would be appreciated. :D

---

### Post by sandyd on 2010-03-23
[http://ubuntuforums.org/showthread.php?t=1428930&p=8961358](http://ubuntuforums.org/showthread.php?t=1428930&p=8961358)

---

### Post by 3rdalbum on 2010-03-23
Rather than give you a set of commands and then not explaining them (no offence), I'll explain a bit.

Commercial DVDs are encrypted in a now-useless attempt at stopping people from copying them. In some parts of the world it's illegal to decrypt DVDs without actually paying for a decryption license. Ubuntu is free to distribute and open-source, so Canonical cannot buy a license to include DVD decryption with Ubuntu; and it cannot ship unlicensed DVD decryption for fear of legal action.

However, you can install unlicensed DVD decryption if you know that your country does not prohibit this action. The easiest way is to go to [www.medibuntu.org](www.medibuntu.org) and use the "Repository Howto" to add the Medibuntu repository to your software sources. Then you can install the "libdvdcss2" package using Synaptic Package Manager, to gain DVD decryption and playback.

I'd also highly recommend downloading the VLC program from Synaptic, it is far superior to the included Totem Movie Player.

---

