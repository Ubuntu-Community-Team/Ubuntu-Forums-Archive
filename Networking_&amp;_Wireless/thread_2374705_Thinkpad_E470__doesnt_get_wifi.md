---
title: "Thinkpad E470  doesnt get wifi"
date: 2017-10-18
forum: Networking &amp; Wireless
---

### Post by joheker on 2017-10-18
Hello. I just bought a Thinkpad E470 but i cant seem to get the wifi working at all.
lspci says : 
```
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device c82 
```
but iwconfig says: 
```
no wireless extensions
```
lshw says :
```
f1100000-f1103fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:c000(size=256) memory:f1000000-f100ffff
```
I have read some posts about ppl having some troubles but i cant get any smarter on what i should do to fix this problem.

Best Regards Johannes

---

### Post by slickymaster on 2017-10-18
Thread moved to **Networking & Wireless**

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz".

If you prefer, you can post the file directly to [pastebin]("http://pastebin.com/") yourself.

---

### Post by joheker on 2017-10-18
[https://pastebin.com/kJRVv2Z9](https://pastebin.com/kJRVv2Z9)

I ran the script and uploaded the .txt to this paste.

---

### Post by Hadaka on 2017-10-18
Hi, please refer to this link..
[https://bbs.archlinux.org/viewtopic.php?id=229651](https://bbs.archlinux.org/viewtopic.php?id=229651)
Post # 5

also your country code is missing and will cause issues when you 
purchase a usb to access wifi. To correct the country code please copy and paste..
```
sudo iw reg set SE
sudo sed -i 's/=.*/=SE/' /etc/default/crda
```
Thanks.

---

### Post by joheker on 2017-10-18
> **Hadaka said:**
> Hi, please refer to this link..
[https://bbs.archlinux.org/viewtopic.php?id=229651](https://bbs.archlinux.org/viewtopic.php?id=229651)
Post # 5

also your country code is missing and will cause issues when you 
purchase a usb to access wifi. To correct the country code please copy and paste..
```
sudo iw reg set SE
sudo sed -i 's/=.*/=SE/' /etc/default/crda
```
Thanks.

Thanks for info. Do when know when we will see drivers and ootb support for this card? Will it take 2 weeks or 6 months? In the later case i will just switch computer to smth else.

---

### Post by Hadaka on 2017-10-19
Hi, You ask...
"Do when know when we will see drivers and ootb support for this card?"

My guess is never. ~or possibly when and *IF~
A..Lenovo replaces the RTL8821CE with a Linux compatible card.
B..Realtek provides a Linux  compatible driver.
C..A Linux user builds a fix to make it fly.
 Sorry that is the best I can offer.

Please mark your thread solved by logging in to your thread and clicking..
Thread Tools [upper right area] and choose Solved.

This will help searchers that are in the same situation.
Thanks.

---

