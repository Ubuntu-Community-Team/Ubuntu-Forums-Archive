---
title: "macbook air wifi not working BCM4355"
date: 2024-01-10
forum: Networking &amp; Wireless
---

### Post by coozo on 2024-01-10
Hello, ):P

New to linux - my wifi is not working and sometimes my hardwire does not work. I need to restart the computer a couple time for network to work.  

Broadcom Inc. and subsidiaries BCM4355 802.11ac Wireless LAN SoC [14e4:43dc] (rev 0c)
Kernel modules: brcmfmac
Apple Inc. BCM4355 802.11ac Wireless LAN SoC [106b:0843]

I installed the newest Ubuntu last weekend.  What steps should I do to get my working. I was not able to find the 43dc SoC so I'm reaching for help.  

Thanks!  :P

---

### Post by coozo on 2024-01-10
I did come across this thread but I don't understand what I need to do to execute it.  

[https://forums.linuxmint.com/viewtopic.php?t=396257&sid=f6c85727edbfb4ff8a7f03d466f75a40&start=20](https://forums.linuxmint.com/viewtopic.php?t=396257&sid=f6c85727edbfb4ff8a7f03d466f75a40&start=20)

This macbook air wifi is a bit difficult. I looked via search engine and found firmware [https://github.com/ztybigcat/brcm43xx/b ... rcm.tar.gz]("https://github.com/ztybigcat/brcm43xx/blob/main/brcm.tar.gz")  apparently according to reddit you download that put the files in the  archive to "brcmfmac4355c1" to "/usr/lib/firmware/brcm/", run "sudo  modprobe brcm" and reboot you should be able to use wifi.

---

### Post by coozo on 2024-01-11
Attaching the wireless info script.  

Thank you for your help!

---

### Post by chili555 on 2024-01-12
What does this tell us?

```
sudo dmesg | grep brcm
```Thanks.

---

