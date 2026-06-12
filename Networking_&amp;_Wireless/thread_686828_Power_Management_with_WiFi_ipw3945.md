---
title: "Power Management with WiFi ipw3945"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by Daniao on 2008-02-03
Dear all, 
I have an IBM Thinkpad T43 with the ipw3954 wireless drivers. I would like to ask if anyone has information about the power management modes implemented in this card. This is what you can find in the README.ipw3945:

"Power management works by powering down the radio after a certain 
interval of time has passed where no packets are passed through the 
radio.  Once powered down, the radio remains in that state for a given 
period of time.  For higher power savings, the interval between last 
packet processed to sleep is shorter and the sleep period is longer."

Basically you can configure the timeout after which the radio goes to sleep state and the awake period in that state. But the sentence that confuses me is: "after a certain 
interval of time has passed where no packets are passed through the 
radio".

Does this mean that the card does not have to detect any packet at all in the radio ? Even if these packets are from other WLAN cells with a different SSID in the same channel ? Or it refers to packets addressed to me? I am asking because I am testing the power save mode but I do not see my card going to sleep.

Anyway this power save mode seems to be different than the one detailed in the 802.11 standard.

Regards

Daniel

---

