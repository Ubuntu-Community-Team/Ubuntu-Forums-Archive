---
title: "Lost wifi card..."
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by Kobalt on 2007-04-25
Hello everyone,

I'm facing something that really puzzles me now : It seems I've lost my wifi card. After a casual boot yesterday my wifi led was orange instead of blue (wifi deactivated instead of activated). I run *ifdown wlan0* and get this : *"interface wlan0 not configured"*
:confused: 
I check *ifconfig* : my card isn't there any more. I check *lspci*, not here either. 
Since I compiled ndiswrapper 1.42 and used windows drivers (that worked for a couple of months now, since Feisty Herd4) I recompile it and reinstall the drivers : *modprobe ndiswrapper* doesn't change anything, nor a reboot. 
I total despair I boot on Windows and guess what, the card isn't there either... 

I check in the bios and there is no option do deactivate de wireless. I've checked my wifi switch, it's set to be on (and it's not producing any effect both on Win or Ubuntu). 

I'm now using the ethernet connection as a fall-back. 

Any help would be really appreciated. 
Thank a lot guys.

---

### Post by chili555 on 2007-04-25
We can't have notre ami Kobalt without wireless! The symptoms you describe suggest a hardware problem. Perhaps some integrated circuit somewhere has died.

I gather this is a Mini-PCI in a laptop? These are actually pretty easy to replace and cheap to buy, if you trust Ebay.

---

### Post by sdide on 2007-04-25
What does  (as root or with sudo)

~# lshw -C network

output?

---

### Post by Kobalt on 2007-04-25
I didn't mention that : my laptop is a HP dv6120eu, and the wifi card is a Broadcom 4311.
Thanks for your concern Chili, but the laptop is still on warranty (6 months old) so I won't buy a new card but lose my laptop for a month and eventually get this card replaced. If indeed it's a hardware problem.
*lshw -C network* doesn't return anything sdide...

Updates : the card works if I activate the "boot on Network" option in BIOS and if I turn completely down the computer and finally reboot. I thought it was ok, turns out it's not : after I suspended my laptop to go eat (what a bad habit !) the card is gone again.

---

### Post by RodneyLee on 2007-04-25
Same Here, Broadcom 4311, on Del 1505, after try all the posts here on the forum to get Wireless connection, I seem to have lost the Wireless card completely....

MAy end up reinstalling and staring from Scratch

---

### Post by sdide on 2007-04-25
> **Kobalt said:**
> I didn't mention that : my laptop is a HP dv6120eu, and the wifi card is a Broadcom 4311.

*lshw -C network* doesn't return anything sdide....

That sounds a bit odd..

Does lshw return anything?

---

### Post by Kobalt on 2007-04-25
I can see my ethernet card but not my wifi card...

---

### Post by Kobalt on 2007-04-26
bumpity-bump ...

---

