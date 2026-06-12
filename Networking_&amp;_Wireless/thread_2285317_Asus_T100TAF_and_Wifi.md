---
title: "Asus T100TAF and Wifi"
date: 2015-07-04
forum: Networking &amp; Wireless
---

### Post by delmalki on 2015-07-04
Hello,

I need your help guys.
[LIST=1]
[*]I installed ubuntu on my Asus T100 TAF using the magic stick [http://forum.xda-developers.com/windows-8-rt/win-8-development/live-asus-t100-ta-magic-stick-t3091481](http://forum.xda-developers.com/windows-8-rt/win-8-development/live-asus-t100-ta-magic-stick-t3091481)
[*]Grub and all the booting stuff is ok however.
[*]Wifi is not Working !!!
[*]After looking through this google+ community [https://plus.google.com/communities/117853703024346186936](https://plus.google.com/communities/117853703024346186936)
[*]Kernel 4.1 was posted through the community and I installed it hoping my Wifi would work. Nothing. Not working
[*]After, I saw that someone with the same computer than mine posted a Kernel version that would make wifi work.
[*]Here's the link to the github: [https://github.com/pinkflozd/T100TAF_kernel/](https://github.com/pinkflozd/T100TAF_kernel/)
[*]The thing is that I have absolutely no clue how to install this. It's an uncompiled kernel.
[*]Could you please assist me on the subject ?!
[/LIST]
More info:
[LIST=1]
[*]Before arriving to that point, I tried installing brcmfmac43241b4-sdio.txt and brcmfmac43241b4-sdio.bin according to [https://linuxnorth.wordpress.com/2014/08/28/establishing-wi-fi-connectivity-on-the-t100/](https://linuxnorth.wordpress.com/2014/08/28/establishing-wi-fi-connectivity-on-the-t100/)
[*]But, no sign of wifi connection
[*]According to someone on the google+ community, the right driver for my computer is brcmfmac43340.bin, but I have no clue on how to find the .txt(nvram file)
[*]Also, sound is not working but the previously posted uncompiled kernel apparently fixes all the previously mentioned problems.
[*]Heres the actual Google+ Posting of the kernel version for my asus t100taf, its the second post.[https://plus.google.com/112460475763080321634/posts](https://plus.google.com/112460475763080321634/posts)
[/LIST]

All help would be appreciated. thank you very much !!

---

### Post by Niels1974 on 2015-08-14
Hi I am having a similar issue and I am wondering if you managed to get this resolved. Thanks!

---

### Post by arkax on 2016-07-12
Use this for Wifi on ASUS TF100AT
sudo cp /sys/firmware/efi/efivars/nvram-XXXXXX
/lib/firmware/brcm/brcmfmac43340-sdio.txt

---

### Post by slickymaster on 2016-07-12
*Thread moved to **Networking & Wireless**.*

---

