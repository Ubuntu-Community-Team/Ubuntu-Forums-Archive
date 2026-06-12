---
title: "problem with wifi on ubuntu 22"
date: 2022-11-13
forum: Networking &amp; Wireless
---

### Post by adrianrt on 2022-11-13
[SIZE=2][FONT=arial]My Wifi driver is not loaded anymore, please see the following error:
[/FONT][/SIZE][B][SIZE=2][FONT=arial]adrian@adrian-XPS-15-9570:~$ sudo dmesg | grep -i ath10k[/FONT][/SIZE]
[SIZE=2][FONT=arial][   30.799576] ath10k_pci 0000:3b:00.0: enabling device (0000 -> 0002)[/FONT][/SIZE]
[SIZE=2][FONT=arial][   30.804907] ath10k_pci 0000:3b:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0[/FONT][/SIZE]
[SIZE=2][FONT=arial][   31.091149] ath10k_pci 0000:3b:00.0: loading /lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin failed with error -22[/FONT][/SIZE]
[SIZE=2][FONT=arial][   31.091183] ath10k_pci 0000:3b:00.0: Failed to find firmware-N.bin (N between 2 and 6) from ath10k/QCA6174/hw3.0: -2[/FONT][/SIZE]
[SIZE=2][FONT=arial][   31.091188] ath10k_pci 0000:3b:00.0: could not fetch firmware files (-2)[/FONT][/SIZE]
[SIZE=2][FONT=arial][   31.091190] ath10k_pci 0000:3b:00.0: could not probe fw (-2)[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]Any tips on how to fix this?[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]Many thanks.[/FONT][/SIZE]
[/B]

---

### Post by adrianrt on 2022-11-15
any ideas here please?

---

### Post by jeremy31 on 2022-11-15
```
sudo apt install --reinstall linux-firmware
```
Reboot

---

