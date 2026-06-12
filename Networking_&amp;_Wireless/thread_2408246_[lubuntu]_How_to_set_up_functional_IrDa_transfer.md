---
title: "[lubuntu] How to set up functional IrDa transfer?"
date: 2018-12-16
forum: Networking &amp; Wireless
---

### Post by 2a2t4s on 2018-12-16
Hi,
I have an 9710:7780 MosChip Semiconductor MCS7780 4Mbps Fast USB IrDA Adapter, which if fully functional under 14.04 and 16.04 (with irda-utils and ircp-tray). After running 18.04, there is no power to run it. I followed this guide [https://help.ubuntu.com/community/IrdaHowto]("https://help.ubuntu.com/community/IrdaHowto") but after running ircp-tray I am not able to make any data transfer. USB dongle "sees" the phone, but every data transfer attempt fails. Sometimes I am able to make ping ```
sudo irdaping 0x000005be
IrDA ping (0x000005be on irda0): 32 bytes
32 bytes from 0x000005be: irda_seq=0 time=1044.01 ms.
32 bytes from 0x000005be: irda_seq=1 time=1043.90 ms.
32 bytes from 0x000005be: irda_seq=2 time=1044.00 ms.
32 bytes from 0x000005be: irda_seq=3 time=1043.90 ms.
32 bytes from 0x000005be: irda_seq=4 time=1044.22 ms.

```

Is here any way, how I can run this dongle under 18.04 for data tranferr?

---

