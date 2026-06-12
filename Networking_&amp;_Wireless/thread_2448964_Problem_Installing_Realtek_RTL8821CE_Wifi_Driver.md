---
title: "Problem Installing Realtek RTL8821CE Wifi Driver"
date: 2020-08-17
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2020-08-17
Help - I have a hp 14s-dq1xxx laptop where I've just install ubuntu-mate 20.04.  Researching it appears ubuntu does not have the realtek driver in the repros.  So although it sees the hardware the driver is not installed and so I have no wifi networking options.  I have come across a number of sites that show me what to do but there are comments like:  step 1 - establish a temporary internet connection by some means.   Hmm.. this is OK but this laptop does not have an Ethernet port so I have no means of getting a connection.  Any help most appreciated - I'm assuming I'm going to have to do this the long/manual way, if it can be done, but so far I have not got anywhere in terms of instructions.  I have access to other machines so can download s/w but I do not know what to do at this stage.  (I have downloaded rtl8821ce from git hub - if I follow the readme file will it work for 20.04?)

---

### Post by Quarkrad on 2020-08-17
I have established a network connection via a wifi usb stick but I cannot get wifi networking to work (without using the usb stick).  lshw shows the realtek 8821 hardware and in Additional Drivers I am using DKMS source for the Realtek 8821C PCIe Wifi driver from rtl8821ce-dkms (open Source).  Having been a ubuntu user since 8.04 without any wifi problems - I now see why people have issues getting ubuntu to work.  It appears with this wifi h/w it is a challenge to get ubuntu 20.04 working. Apologies - rant over.

---

### Post by slickymaster on 2020-08-17
*Thread moved to **Networking & Wireless**.*

---

### Post by nadrojsl on 2020-08-17
> **Quarkrad said:**
> Help - I have a hp 14s-dq1xxx laptop where I've just install ubuntu-mate 20.04.  Researching it appears ubuntu does not have the realtek driver in the repros.  So although it sees the hardware the driver is not installed and so I have no wifi networking options.  I have come across a number of sites that show me what to do but there are comments like:  step 1 - establish a temporary internet connection by some means.   Hmm.. this is OK but this laptop does not have an Ethernet port so I have no means of getting a connection.  Any help most appreciated - I'm assuming I'm going to have to do this the long/manual way, if it can be done, but so far I have not got anywhere in terms of instructions.  I have access to other machines so can download s/w but I do not know what to do at this stage.  (I have downloaded rtl8821ce from git hub - if I follow the readme file will it work for 20.04?)

Are you not able to use a USB cable to your phone and share the internet?

---

### Post by Quarkrad on 2020-08-17
At the moment I have internet connectivity using a wifi usb stick. So my problem is getting ubuntu to use the rtl8821ce hardware that is can see via **lshw -C Network**

---

### Post by nadrojsl on 2020-08-17
> **Quarkrad said:**
> At the moment I have internet connectivity using a wifi usb stick. So my problem is getting ubuntu to use the rtl8821ce hardware that is can see via **lshw -C Network**


I having issue with RTL8125 2.5GbE Controller 

It shows below

network UNCLAIMED       
       description: Ethernet controller
       product: RTL8125 2.5GbE Controller
       vendor: Realtek Semiconductor Co., Ltd.

---

### Post by chili555 on 2020-08-17
> **nadrojsl said:**
> I having issue with RTL8125 2.5GbE Controller 

It shows below

network UNCLAIMED       
       description: Ethernet controller
       product: RTL8125 2.5GbE Controller
       vendor: Realtek Semiconductor Co., Ltd.This is not the same device. I recommend that you try the steps I referred to in your own thread on the subject.

---

### Post by chili555 on 2020-08-17
> **Quarkrad said:**
> At the moment I have internet connectivity using a wifi usb stick. So my problem is getting ubuntu to use the rtl8821ce hardware that is can see via **lshw -C Network**Please show us:

```
lspci -nnk | grep 0280 -A3
sudo dkms status
dmesg | grep 8821

```

---

### Post by Quarkrad on 2020-08-18
I have it sorted now thanks.  I was under pressure because this was not my machine and had limited time to fix it.  In the end I re installed and followed the many suggestions to install 8821ce e.g. [https://www.youtube.com/watch?v=vPfLVsyQU_A](https://www.youtube.com/watch?v=vPfLVsyQU_A)  I'm guessing there was a/some conflicts due to my many attempts first time round.

---

