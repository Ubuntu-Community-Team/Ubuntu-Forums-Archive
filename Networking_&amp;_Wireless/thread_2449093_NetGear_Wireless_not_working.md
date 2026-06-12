---
title: "NetGear Wireless not working"
date: 2020-08-20
forum: Networking &amp; Wireless
---

### Post by ivan-pong-1 on 2020-08-20
[Hi, I used the second answer on this page to try to get my netgear wifi adapter working with ubuntu.]("https://askubuntu.com/questions/1027094/netgear-a6100-ac600-wifi-adapter-driver")




The hardware match was exact, and I used 4.2.2 instead. I am using Ubuntu 20.04. Additional Drivers verifies that I am using the dkms source,
however I cannot find anyway to display wifi sources to connect to. 


Thanks for any suggestions you might have. I cannot regress to 18.xx, since my graphics drivers are a bit finnicky.

---

### Post by chili555 on 2020-08-20
Let's have a look at the result of these terminal commands;

```
sudo modprobe 8812au
sudo dkms status
dmesg | grep -i rtl
dmesg | grep 8812

```
Thanks.

---

### Post by kurt18947 on 2020-08-20
> **chili555 said:**
> Let's have a look at the result of these terminal commands;

```
sudo modrobe 8812au
sudo dkms status
dmesg | grep -i rtl
dmesg | grep 8812

```
Thanks.

Possible typo? Should sudo modrobe 8812au be sudo mod**p**robe 8812au? I've never made a typo - not me - not ever - and my nose is so long it makes Pinochio's nose looks dainty:biggrin:.

---

### Post by chili555 on 2020-08-20
Yikes! Sorry. Edited as needed.

Now I will wipe a layer of grime off of these old spectacles!

---

