---
title: "Atheros AR5007EG doesn't always show up on lspci"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by thunderbunny on 2007-11-26
Hi:

I bought a Sony Vaio laptop (VGN-NR120E) about a month ago. I got the installed Atheros 5007EG card working (using ndiswrapper) with the help of these forums, and for that I'm eternally grateful.

But my problem now is that the card seems to be working only when it wants to. When I execute a lspci command after a reboot, the device doesn't always show up. Sometimes, the device shows up under lspci, but still bringing up wicd results in "No Wireless Networks Found" (when I'm sitting ten feet away from my router). And sometimes the device will just randomly stop working after the machine has been up for a while. And sometimes...the device works, but those times are starting to get scarce enough to make me wonder, and I bought a USB wireless adapter just to use as a backup (though I'd prefer the installed card).

Are there any suggestions as to how I could go about debugging this? Any interesting dmesg output that would point me to the problem? Or is the fact that the device isn't always showing up under lspci a clear-cut hint of a hardware problem?

---

### Post by overdrank on 2007-11-27
> **thunderbunny said:**
> Hi:

I bought a Sony Vaio laptop (VGN-NR120E) about a month ago. I got the installed Atheros 5007EG card working (using ndiswrapper) with the help of these forums, and for that I'm eternally grateful.

But my problem now is that the card seems to be working only when it wants to. When I execute a lspci command after a reboot, the device doesn't always show up. Sometimes, the device shows up under lspci, but still bringing up wicd results in "No Wireless Networks Found" (when I'm sitting ten feet away from my router). And sometimes the device will just randomly stop working after the machine has been up for a while. And sometimes...the device works, but those times are starting to get scarce enough to make me wonder, and I bought a USB wireless adapter just to use as a backup (though I'd prefer the installed card).

Are there any suggestions as to how I could go about debugging this? Any interesting dmesg output that would point me to the problem? Or is the fact that the device isn't always showing up under lspci a clear-cut hint of a hardware problem?

Hi and do you have another slot to try the card in? I had a dell that one slot worked and the other would do what you are describing.

---

### Post by thunderbunny on 2007-11-27
I think the card is integrated into the laptop. I can't easily get to it and move it to another slot.

---

