---
title: "No wifi"
date: 2016-07-18
forum: Networking &amp; Wireless
---

### Post by acomoon on 2016-07-18
Hello,

 After an update and reboot, my laptop doesn't recognize any wireless conection, only wired. I've tried some solutions found on internet, but no succeed. I use Ubuntu 14.04LTS

Here are some hardware specifications:

[INDENT]01:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
	Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8470]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Dell Device [1028:06b2]
	Kernel driver in use: r8169[/INDENT]

After running "nm-tool" ( my laptop wasn't connect to internet, when terminal was used)

[INDENT]&#65279;alejandra@alejandra-Inspiron-5459:~$ nm-tool[/INDENT]
[INDENT]
[/INDENT]
[INDENT]NetworkManager Tool[/INDENT]
[INDENT]
[/INDENT]
[INDENT]State: disconnected[/INDENT]
[INDENT]
[/INDENT]
[INDENT]- Device: eth0 -----------------------------------------------------------------[/INDENT]
[INDENT]  Type:              Wired[/INDENT]
[INDENT]  Driver:            r8169[/INDENT]
[INDENT]  State:             unavailable[/INDENT]
[INDENT]  Default:           no[/INDENT]
[INDENT]  HW Address:        F8:CA:B8:3C:99:D9[/INDENT]
[INDENT]
[/INDENT]
[INDENT]  Capabilities:[/INDENT]
[INDENT]    Carrier Detect:  yes[/INDENT]
[INDENT]
[/INDENT]
[INDENT]  Wired Properties[/INDENT]
[INDENT]    Carrier:         off[/INDENT]



I really hope someone can help me. I'm a new Linux user and totally clueless.

Thanks for reading,
Alejandra.-

---

### Post by wildmanne39 on 2016-07-18
Need to keep thread to one issue one thread! Please edit this thread to just one issue and create another thread for your second issue.
Thanks

---

