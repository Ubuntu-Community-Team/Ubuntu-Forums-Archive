---
title: "ethernet and wireless at the same time??"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by sicknessjb on 2007-07-23
Ive search for an answer but couldnt find anything related to my question. let me start..

I'm trying to get my younger brother into Ubunutu which he finds interest with the packages that come with the OS. he 's able to make use with the everyday stuff, hardware works, but theres only one problem, i configured his windows with 1 wireless card pci which is intended for internet use, and the ethernet card, being used to connect to his PS2 making him use the online game play. So his nic is setup as a source of internet for whatever is plugged into the other end, also the ethernet cable is a crossover cable.

Question is can Ubuntu manage/config other interfaces at the same time and configure the nic card to work like it did on widnows xp?? or do i need to perform/install packages.

We ran the online that tries to get the dhcp, but stoped their. (knowing it probably wouldnt work)

any help would be great. thanks!

---

### Post by t4thfavor on 2007-07-23
Put the wireless device and the eth0 device into a bridge (research brctl) and then use the wireless device to connect to the wireless router for internet.

then get a dhcp address on the bridge interface, and then anything you plug into eth0 should be allowed to broadcast for dhcp address as well as access the internet.

---

### Post by sicknessjb on 2007-07-23
> **t4thfavor said:**
> Put the wireless device and the eth0 device into a bridge (research brctl) and then use the wireless device to connect to the wireless router for internet.

then get a dhcp address on the bridge interface, and then anything you plug into eth0 should be allowed to broadcast for dhcp address as well as access the internet.

thanks! with the help i searched then found the documents that ubuntu provides 

[https://help.ubuntu.com/community/NetworkConnectionBridge?highlight=%28NetworkConnectionBridge%29](https://help.ubuntu.com/community/NetworkConnectionBridge?highlight=%28NetworkConnectionBridge%29) 

i'm going to try this walkthrough when i get off work. thanks again with quick  reply cheers! :)

---

