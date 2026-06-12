---
title: "my Broadcom wireless adapter doesn't work :("
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by panganino on 2007-12-06
Hello,
I just installed ubuntu 6.06 (64bits) on my laptop acer Aspire 9302, but the problem is that the system could'nt detect my wireless adapter (model: broadcom) even the Ethernet adapter does not work although it is recognized.4 ur help

---

### Post by kevdog on 2007-12-06
Please type at the terminal and post at the terminal:

lshw -C network

---

### Post by panganino on 2007-12-06
$sudo lshw -C network

[ 390.463213] buffer I/O error on device hdc, logical block 0
[ 390.464697] buffer I/O error on device hdc, logical block 1
[ 390.466191] buffer I/O error on device hdc, logical block 2
[ 390.467703] buffer I/O error on device hdc, logical block 3
[ 390.469186] buffer I/O error on device hdc, logical block 4
[ 390.470681] buffer I/O error on device hdc, logical block 5
[ 390.472192] buffer I/O error on device hdc, logical block 6
[ 390.473685] buffer I/O error on device hdc, logical block 7
[ 390.475190] buffer I/O error on device hdc, logical block 8
[ 390.476603] buffer I/O error on device hdc, logical block 9
  *-network UNCLAIMED
          description: network controller
          product: broadcom coorporation
          vendor: broadcom coorporation
          physical id : 0
          bus info: pci@01: 00.0
         version: 01
         width : 32 bits
        clock: 33Mhz
        capabilities: bus_master cap_list
        ressources: iomemory: c3000000-c3003fff irq:255

---

### Post by kevdog on 2007-12-06
> **panganino said:**
> $sudo lshw -C network

[ 390.463213] buffer I/O error on device hdc, logical block 0
[ 390.464697] buffer I/O error on device hdc, logical block 1
[ 390.466191] buffer I/O error on device hdc, logical block 2
[ 390.467703] buffer I/O error on device hdc, logical block 3
[ 390.469186] buffer I/O error on device hdc, logical block 4
[ 390.470681] buffer I/O error on device hdc, logical block 5
[ 390.472192] buffer I/O error on device hdc, logical block 6
[ 390.473685] buffer I/O error on device hdc, logical block 7
[ 390.475190] buffer I/O error on device hdc, logical block 8
[ 390.476603] buffer I/O error on device hdc, logical block 9
  *-network UNCLAIMED
          description: network controller
          product: broadcom coorporation
          vendor: broadcom coorporation
          physical id : 0
          bus info: pci@01: 00.0
         version: 01
         width : 32 bits
        clock: 33Mhz
        capabilities: bus_master cap_list
        ressources: iomemory: c3000000-c3003fff irq:255


Dont have any ideas about the buffer errors -- looks like a hard drive problem

network UNCLAIMED means you have not installed the driver for your card.

---

### Post by panganino on 2007-12-07
> network UNCLAIMED means you have not installed the driver for your card.
can u help me to install it? knowing that i can't connect to the Internet because i have another probleme with ethernet adapter :(

---

