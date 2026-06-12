---
title: "Intermittent TCP/IP function - Wifi Connection Shows Good Throughout"
date: 2024-04-26
forum: Networking &amp; Wireless
---

### Post by eagle3312 on 2024-04-26
[ATTACH]293698[/ATTACH]

Hello, 

I am running an older Asus GL552VW that I'm trying to breathe new life into. I have installed 24.04 and have a new AX210/1675 intel wireless card in it. 

I'm getting an unstable connection of some kind. The wifi shows a strong signal, but when I download a large file, like an ubuntu ISO, the DL peters off and then stops. If I hit the resume button it will start up and run at about 15MB/s or so for a little bit and then fade out again. 

This is impacting connection to services like my unraid servers in the house as well, as I am connected to those over SMB and unable to drag the iso down to the file share, since my connection errors out at some point (which is the message I get with the file copy[via GUI.])

I'm unable to find a good anwser on what to do. I have tried the following:
Disable power save

Manually download this firmware package : [https://mirrors.edge.kernel.org/ubuntu/pool/main/l/linux-firmware/nic-firmware_1.187.39_all.udeb](https://mirrors.edge.kernel.org/ubuntu/pool/main/l/linux-firmware/nic-firmware_1.187.39_all.udeb)
Then I found he device and followed these instructions to swap it: [https://www.dell.com/support/kbdoc/en-ca/000144425/killer-wireless-firmware-update-guide-for-ubuntu-systems#ANCHOR-TAG-NAME-1](https://www.dell.com/support/kbdoc/en-ca/000144425/killer-wireless-firmware-update-guide-for-ubuntu-systems#ANCHOR-TAG-NAME-1)

This did nothing, so I did a reboot and I still have the issue. 

I am unsure what to do now as I can find nothing helpful, except, hopefully your reply. Thank you in advance.

---

### Post by praseodym on 2024-04-27
Overlooked tar.gz.

Can you c/p the content?

---

