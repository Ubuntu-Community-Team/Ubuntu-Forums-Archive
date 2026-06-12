---
title: "How to install WiFi ?"
date: 2021-04-27
forum: Networking &amp; Wireless
---

### Post by loover1 on 2021-04-27
[h=2][FONT=sans-serif]Hello,[/FONT][/h][COLOR=#000000][FONT=sans-serif][INDENT]
I installed last LTS version of Kubuntu on my PC (dual-boot with Windows 10 Pro 20H2).
What to do to have WiFI with the [COLOR=#BC2A4D]TP[/COLOR]-[COLOR=#BC2A4D]LINK[/COLOR] AC 1300 USB Adapter "Archer T4U" Ver. 2.0 ?

Thanks in advance for your reply.

Best regards.[/INDENT]
[/FONT][/COLOR]

---

### Post by CelticWarrior on 2021-04-27
Welcome.

This should work (but please confirm yours have the Realtek 8812u chipset): [https://askubuntu.com/a/1203576/1210606](https://askubuntu.com/a/1203576/1210606)

---

### Post by chili555 on 2021-04-27
In the terminal, please run the command: ```
lsusb
``` and then post the result.

---

### Post by morrownr on 2021-04-27
chili555,

I don't know if you are aware of this but I added a text file showing the supported Device IDs to the repos I maintain for each Realtek driver. Here is the one for the likely chipset:

[https://github.com/morrownr/8812au/blob/5.9.3.2/supported-device-IDs](https://github.com/morrownr/8812au/blob/5.9.3.2/supported-device-IDs)

I say likely but we will see.

---

