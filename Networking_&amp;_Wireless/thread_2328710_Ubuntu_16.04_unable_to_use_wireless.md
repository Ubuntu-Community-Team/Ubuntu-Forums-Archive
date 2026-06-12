---
title: "Ubuntu 16.04 unable to use wireless"
date: 2016-06-23
forum: Networking &amp; Wireless
---

### Post by ken poy on 2016-06-23
I updated my Ubuntu 14.04 to 16.04 on my Dell Latitude E6420. Wireless function at 14.04 as does my Windows 7 system. wireless is turned on and Networking recognizes my Modem wireless as excellent signal strength.  i enter my password and connect and nothing happens.  i suspect i need a driver and have found multiple such problems with multiple answers so am confused.  in  "additional drivers" i find only "using processor microcode firmware for INTEL CPU.  nothing about a wireless driver.  i found a thread "how to install a driver for Broadcom series of PCI wireless cards". This sounds like what i need so i followed the instructions.  first issuer LSPCI -nn -d 14e4:  command to determine which driver i need. the command displays nothing and returns to the prompt??  it is not connected to  the internet via ethernet.  i hope i explained my situation and would appreciate any help thanks. ken
thanks for the reply will try
i did the LSPCI cmd no parms  listed was
Communication Controller Intel Corp 6series/c200 series chipset family nei controller #1 (rev04) do not know what it means but may help.    thanks  ken

i tried  lspci -n | awk '/0280/{print $3}'     and the reply was > on next line??

---

### Post by Hadaka on 2016-06-23
Hi, please Copy,paste and then post the output of..
```
lspci -n | awk '/0280/{print $3}'
```
thanks

---

