---
title: "Xubuntu 22.04 Error trying to Install driver for UGREEN USB WiFi Adapter AC650"
date: 2024-04-18
forum: Networking &amp; Wireless
---

### Post by abielv on 2024-04-18
Hi everyone, 

I bought this [UGREEN WiFi]("https://www.amazon.com/UGREEN-Adapter-Desktop-Wireless-Computer/dp/B08M9FX4G3/ref=sr_1_5?crid=1TD1OYLEJY3IH&dib=eyJ2IjoiMSJ9.7f2pf4ceOjm5u5tWnmGOU-f2MlTAFqtEiDE3jeMoBo-8SKYscBF-HjWkkMtaS2PVYvb0MU2dECrjWd8r6ussGoVzXaLBOGqSUyx5a_MvBaI53WwWzG1ggitU4LhzEyFSD4MZRQiovF82z2c6aq68fyxVPwf_5i8nXiNt9cpSi92UeVEs-FqGJF-a3E_q80HMk-pVlw9zsDBpTNyLFdDHtlByEYhJIOqE2J5HFDhFvHE.Xy3Q1O0_t0H1zdLcBhf3o5igzaLUavJ6i02odODDa0Q&dib_tag=se&keywords=ugreen+wifi+adapter&qid=1713486685&sprefix=ugreem+wifi%2Caps%2C342&sr=8-5") adapter from amazon and I'm having issues connecting to a network, the system detects the adapter and in the network options the list of available networks options but when I try to connect to any it does not establish the connection. I also tried to install the driver that is on their [site]("https://www.ugreen.com/pages/download") but it gives me this error when running the install.sh:
```

/home/abielv/Downloads/RTL8811CUDriver/Linux/driver/rtl8821CU_rtl8731AU_WiFi_linux_v5.8.1.5_36625.20200416_COEX20200321-4141/core/rtw_br_ext.c:20:18: fatal error: net/ipx.h: No such file or directory
   20 |         #include <net/ipx.h>

```

I don't have experience with make or gcc, so I don't know what else to do :(. 
I'm running **Xubuntu** and this is my lsb_release print:
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy

And the linux kernel version is 6.5.0-27-generic

Thank you in advance.

---

### Post by praseodym on 2024-04-20
Please run the Wireless Script from the sticky thread and show the outputs

---

### Post by morrownr on 2024-04-24
Hi abielv

Go to: [https://github.com/morrownr/8821cu-20210916](https://github.com/morrownr/8821cu-20210916)

It would be good if you can clean out the old driver you tried but if you don't know how, the installation script at the above site will likely handle it.

For what it is worth, there are some of us at the repo above that have been working to improve the in-kernel driver and as of kernel 6.9, it should work much better in client mode. That in-kernel driver does mean there has to be a deconflict but the installation script at the repo listed above handles that for you. When you get to the repo, carefully follow the instructions. They are written for real people, not programmers but if you need to ask a question, use Issues.

You also welcomed to stop by the site Main Menu:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Menu items 1 and 2 can be very informative.

Regards

---

