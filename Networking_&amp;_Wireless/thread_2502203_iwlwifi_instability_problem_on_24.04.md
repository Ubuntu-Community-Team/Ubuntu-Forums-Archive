---
title: "iwlwifi instability problem on 24.04"
date: 2024-11-05
forum: Networking &amp; Wireless
---

### Post by karhulitos on 2024-11-05
Hello,

I noticed bad wifi performance after 24.04 upgrade as my radio player dropped out occasionally. Having a closer look to wifi performance revealed following:
- steady 160-170mbps after reboot or laptop startup on a 5 minute test (local nw openspeedtest)
- after a while same test results in much worse results, throughput slows down to a complete halt to start again after few moments
- 24.04.1 did help situation, I think, but didn't resolve it completely
- a test on 20.04 ubuntu studio live-usb revealed same pattern but steadier behavior; first test at 160-170mbps but next ones dropped to steady 100mbps. No complete d/l speed halts.
- (24.04 also had screen stutters/halts which was sorted by disabling wayland - not related to this I guess. Running nvidia proprietary driver.)
- ([edit] Same test on Lenovo X1/Win 11 results in steady 200mbps, Samsung A52s 250mbps)

What could this be?

Device details: [https://termbin.com/9q21]("https://termbin.com/9q21")

[ATTACH=CONFIG]294475[/ATTACH]

---

### Post by karhulitos on 2024-11-11
Appeared to be completely my own fault. I had "fixed" an ip conflict a few times already not understanding I had a setup which produced new conflict every morning. I now get a steady 160mbps after removing the conflict generator.

The "generator" was Tenda Nova Mesh3 "maintenance schedule" i.e. nightly reboot at the same time my router did its nightly reboot. This resulted in dhcp not available by the time the Novas rebooted. What I didn't realize was that the chief-Nova ("gateway"-role) still had its dhcp running even in bridged mode and that gave a conflicting address to one of the secondary Novas in my setup as a backup measure. And as the reboot schedule was nightly one, no matter if I every morning fixed the conflict, it came back again the next day.

I now set the schedule to weekly and offset the router reboot 30mins away from Nova reboots.

Reboots save the world.

[edit] No, ip cnflict did not cause the stalling of download speed. It has done it again several times today and now I certainly do not have a conflict. Also, how stupid of me to suspect the conflict while X1/Windows and A52s/Android was giving 200-300mbps results.

---

