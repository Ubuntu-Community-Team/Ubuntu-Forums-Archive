---
title: "bluetooth connection problem"
date: 2015-05-20
forum: Networking &amp; Wireless
---

### Post by Jaladhi_R_Trivedi on 2015-05-20
hi,
  I have compaq 510 laptop running on ubuntu 15.04. after upgrading from zorin 5 to ubuntu 14.04 my laptop's inbuilt bluetooth had stopped working with message of bluetooth adapters not found. after much efforts and help from the community I was able to start the bluetooth and I could pair with my android and send file from my laptop to my android device. there are still following problems though
  (1) I cannot browse files on my android which I was able to with zorin 5 and Nokia devise(s40 I guess)
  (2) I cannot send files from my android to my laptop
  (3) I cannot use internet through bluetooth with my android working as modem
Kindly help me out friends

---

### Post by jeremy31 on 2015-05-20
Can you post ```
lsusb; lsmod | grep bluetooth
```

---

### Post by Jaladhi_R_Trivedi on 2015-05-21
here it is 
```
jaladhi@jaladhi-Compaq-510:~$ lsusb
Bus 002 Device 004: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 002 Device 005: ID 05c6:6001 Qualcomm, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 03f0:231d Hewlett-Packard Broadcom 2070 Bluetooth Combo
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jaladhi@jaladhi-Compaq-510:~$ lsmod | grep bluetooth
bluetooth             491520  22 bnep,btusb,rfcomm
jaladhi@jaladhi-Compaq-510:~$ 
```

---

### Post by Jaladhi_R_Trivedi on 2015-05-21
when I tried to setup my android in connecting there was difficulty in matching passkeys (both device showing different passkeys) and in the step to create network there was notification something like bnep0 failed

---

