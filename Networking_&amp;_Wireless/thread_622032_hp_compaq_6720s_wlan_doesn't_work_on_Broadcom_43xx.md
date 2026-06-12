---
title: "hp compaq 6720s wlan doesn't work on Broadcom 43xx card"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by deguz on 2007-11-24
Hi!

lspci says this:
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
iwconfig says this:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
so it seems alright, but it isn't working.
I tried bcm43xx and ndiswrapper too, but the result is the same. The wlan button on the laptop isn't working either. When i do iwlist wlan0 scan, the result: No scan results.
But it isn't correct, when i used windows on this laptop, it worked fine, it saw wlan networks, so there are networks here. I tried thousands of howto-s, but they didn't help.
Please help me! I love linux, and i hate windows, but if i can't use wlan on linux, i will need to use windows, and i would hate that. Please help me!

---

### Post by jmauler on 2007-11-24
What is your ubuntu version?
I was having some problems with my wireless driver bcm43xx when I installed ubuntu 7.10. My sys log said "bcm43xx IRQ timeout". I search for a solutions and tried a lot, but didn't work. So I've installed ubuntu 7.04 and at the first try it worked. The linux kernel that ubuntu 7.10 uses conflicts with bcm43xx driver implementation... 
Don't loose your time trying to fix that if you are using ubuntu 7.10.

J.Marcelo Auler

---

### Post by deguz on 2007-11-24
i'm using Kubuntu 7.10, well thanks the hint, i'm gonna try 7.04 on a live cd. Do you think it's enough or should i install permanently?

---

### Post by kevdog on 2007-11-24
Use ndiswrapper instead of the bcm43xx firmware and you will be OK

---

### Post by deguz on 2007-11-24
i tried them both (ndiswrapper and bcm43xx too)

where can i download Kubuntu 7.04? google is full of links, but they don't work :(

---

### Post by kevdog on 2007-11-24
Thats a good question.  If you use ndiswrapper I dont think you will need Feisty.

---

### Post by deguz on 2007-11-25
i found Kubuntu 7.04, but it didn't work with it either.

---

### Post by deguz on 2007-11-28
please help me!!!!!

---

### Post by deguz on 2007-12-18
i figured out how to solve it. I installed windows. First, it didn't work on it either. But installed the driver which handles the button and the card, and i enabled the wlan, and after  that i rebooted in linux (and first reinstalled GRUB), and it worked in linux too.

---

### Post by rhellvis on 2008-01-26
I have a 6720s and the WLAN is working perfectly. Just follow this guide (i uses ndiswrapper)

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

The guide it a little over the top at times, but still very useful.

---

