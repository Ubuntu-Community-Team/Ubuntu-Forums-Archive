---
title: "Problems with Ubuntu and Wi-Fi"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Murderuption on 2009-03-06
Hello.  Long time lurker, first time poster.

I've yet to install Ubuntu on my laptop because just like the GOP, I'm afraid of change.  I installed it on my girlfriend's Compaq Presario C300 and the wi-fi won't work.  Now she won't stfu about how I screwed up her laptop and I can't figure out how to get the damned thing working.  If any of you can help a brother out, it would be greatly appreciated.

Anyway, I'm running Windows7 and windows sucks, as we all know, and I'd like to install Ubuntu on my laptop but I'm afraid I'll encounter the same problem as my unfortunate girlfriend.  I have a Gateway M-6823.  Will Ubuntu work out da box on my machine?

If any of you can help me with my Ubuntu problems, please, I shall award thee with 1,000 internets.  

Thanks a lot, fellers.

---

### Post by avtolle on 2009-03-06
We need to know the wireless card for the computers (both yours and the gf's). Run```
lspci
```from the terminal (Applications>Accessories>Terminal).

---

### Post by Murderuption on 2009-03-06
It says a lot of stuff.  Not sure what you need exactly.  The last few lines read as follows:

Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139
C+ (rev 10)

I don't know what mine is, as I'm still running Windows7 on it and have yet to install Ubuntu.

---

### Post by avtolle on 2009-03-06
OK, the gf's computer has a Broadcom wireless card. There are a number of threads on the forum about getting that card to work. I need to go back to work for a bit, but will see what I can find (and I encourage you to do so as well).

---

### Post by Murderuption on 2009-03-06
On my laptop, the following are listed under network adapters:

Intel(R) PRO/Wireless 3945ABG Network Connection
Realtek RTL8101E Family PCI-E Fast Ethernet NIC (NDIS 6.2)

---

### Post by avtolle on 2009-03-06
On yours, as it is an Intel, it should work without any other issues. Re: your gf's situation, which release of Ubuntu is installed (8,10; 8.04)? If 8.10, if the system is updated, it is my recollection that there should be a driver for the wireless card under Hardware Drivers found under System>Administration; the drivers will need to be activated (which may well require downloading, so a wired connection is desirable), and after installation, a restart of the system should get the job done.

---

### Post by st33med on 2009-03-06
On GF's lappy
```
sudo apt-get install b43-fwcutter
sudo b43-fwcutter
sudo modprobe -r b43 && sudo modprobe b43
```

BAM

---

### Post by Murderuption on 2009-03-06
works perfectly on hers.  thanks a lot.  so i can just install it on mine and it'll work right off the bat???

---

### Post by st33med on 2009-03-06
Pretty much, yeah.  Intel has really good driver support for Linux.

---

