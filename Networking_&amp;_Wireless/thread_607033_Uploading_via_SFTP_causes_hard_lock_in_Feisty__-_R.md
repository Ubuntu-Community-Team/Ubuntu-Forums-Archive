---
title: "Uploading via SFTP causes hard lock in Feisty  - RTL 8185 wireless card"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by justinflavin on 2007-11-08
I have Feisty Fawn instlled with all the latest updates, and yet when i try to upload a file via sftp i get a complete system lock that i can only get out of by hitting the reset button

Gateway Laptop, with an RTL-8185 wireless card.
Model: ML 3108B

>uname -r
2.6.20-16-generic

>lspci | grep "Ethernet"
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

i get the same hard lock if i try to rsync from my laptop to my desktop, so its possibly something to do with the RTL-8185 drivers in the kernel.  

Anyone else come across this problem before and is there a solution or update i can apply?


by the way i can't migrate to Gutsy - tried the live CD and it doesnt even get beyond the boot splash screen. 

thanks.

---

