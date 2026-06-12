---
title: "wireless - iwlist scan - what are cell"
date: 2024-08-25
forum: Networking &amp; Wireless
---

### Post by mos6502mos on 2024-08-25
I using the 'iwlist' tool to get details about the wifi landscape at my location; however, I noticed items called 'cell'. Some of these cells have bogus mac addresses, and do not show SSIDs. Are these cells the radios from my router? For example: My ssid shows up as 'cell 01'; however, 'cell 02' and 'cell 03' are on the same channel as my SSID and signal strength and SNR are the same, but there is not listed SSID.

Just not sure how to read the iwlist output. Thank you

---

### Post by currentshaft on 2024-08-25
They could be multiple radio bands (2.4 Ghz and 5Ghz) or they could simply be APs which do not broadcast SSIDs.

Try this command instead: " nmcli -f all dev wifi "

---

