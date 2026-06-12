---
title: "Ralink RT3290 not installing in Lubuntu 16.04 on HP Pavilan G6 laptop"
date: 2017-03-16
forum: Networking &amp; Wireless
---

### Post by Boyntonstu on 2017-03-16
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit]stu@stu-HP-Pavilion-g7-Notebook-PC://home/stu/Downloads/RT3290_u16$ ip link show[/FONT]
[FONT=inherit]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1[/FONT]
[FONT=inherit]link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/FONT][/FONT][/COLOR][COLOR=#1D2129][FONT=Helvetica][FONT=inherit]
[FONT=inherit]2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000[/FONT]
[FONT=inherit]link/ether 28:92:4a:52:6b:37 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=inherit]3: wlo1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000[/FONT]
[FONT=inherit]link/ether 68:94:23:2c:87:9b brd ff:ff:ff:ff:ff:ff

Also:  [/FONT][/FONT][/FONT][/COLOR][COLOR=#1D2129][FONT=Helvetica]I got: SIOCSIFFLAGS: Input/output error after the ./activate-net-rt[/FONT][/COLOR]

---

### Post by Boyntonstu on 2017-03-26
Installed 14.0 LTS, problem, solved.

---

