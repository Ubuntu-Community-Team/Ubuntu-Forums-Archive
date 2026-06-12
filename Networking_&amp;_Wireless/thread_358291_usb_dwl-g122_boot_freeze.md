---
title: "usb dwl-g122 boot freeze"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by peterthewolf on 2007-02-10
I have finally got the usb wireless stick working but when I rebooted the pc froze when the ubuntu progress bar came up. If I remove the usb stick reboot then insert stick all is OK.
I have found that if I append nousb to the grub kernel command then the pc will boot with the stick inserted and the wireless connection still works.
Are there any other ramifications to nousb.

Further test shows that nousb only works if pc completely rebooted if I choose restart on closedown then reboot fails.

---

