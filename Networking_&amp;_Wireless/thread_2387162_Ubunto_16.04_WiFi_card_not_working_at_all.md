---
title: "Ubunto 16.04 WiFi card not working at all"
date: 2018-03-15
forum: Networking &amp; Wireless
---

### Post by abc-xyz2 on 2018-03-15
I've just put a new PCI WiFi card into my machine. Network Manager is not detecting the card at all. Output from the wireless-info script is on pastebin at: [http://paste.ubuntu.com/p/7CD3cHTdph/](http://paste.ubuntu.com/p/7CD3cHTdph/)

From the (little) I know it looks like the card can be seen but not initialized? Has the card got a hardware problem? - I'm basing that on the "Bad EEPROM checksum" message.


NB. This is a follow on from the situation in this thread ([https://ubuntuforums.org/showthread.php?t=2386072](https://ubuntuforums.org/showthread.php?t=2386072)). I'm now using a new router and new PCI WiFi card so I don't think it's relevant anymore but putting it in just in case.

---

### Post by wildmanne39 on 2018-03-15
Pastebin link is not working.

---

### Post by abc-xyz2 on 2018-03-15
Oops, typo. Fixed now.

---

### Post by wildmanne39 on 2018-03-16
> ath: phy0: Unable to initialize hardware; initialization status: -22
I am not an expert on this error message but I believe it looks like a hardware issue and that is what my research has shown as well, I suggest you try to reset the card or move it to a new slot, if that does not help it is most likely defective.

---

### Post by chili555 on 2018-03-16
> ath: phy0: **Bad EEPROM checksum **0x11e1Possibly related: [http://lists.infradead.org/pipermail/lede-dev/2017-February/005926.html](http://lists.infradead.org/pipermail/lede-dev/2017-February/005926.html)

I suggest that you try the live USB or DVD for Ubuntu 17.10 to see if the error remains.

---

### Post by abc-xyz2 on 2018-03-19
@[**[COLOR=#C61919][B]wildmanne39**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=508533") 
Not sure what you mean by reset the card but I tried taking it out and putting it back in again and also tried a different slot. No difference.

@[**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=35909") 
I tried the LiveUSB version of 17.10 and still nothing.

I'm going to assume it's a problem with the card so I'm returning it. Any recommendations for a WiFi PCI card which should definitely work?

Thanks.

---

### Post by wildmanne39 on 2018-03-19
It was a typo, it should have been re-seat.

---

