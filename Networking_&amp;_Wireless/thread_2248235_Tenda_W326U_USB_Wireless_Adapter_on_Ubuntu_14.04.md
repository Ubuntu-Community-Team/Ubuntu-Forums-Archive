---
title: "Tenda W326U USB Wireless Adapter on Ubuntu 14.04"
date: 2014-10-13
forum: Networking &amp; Wireless
---

### Post by Antonache_Emanuel_ on 2014-10-13
Hello,

 Recently I have acquired this USB adapter ([http://www.tenda.cn/tendacn/downloads/show.aspx?productid=360)]("http://www.tenda.cn/tendacn/downloads/show.aspx?productid=360"), wanting to replace my older USB adapter. I have inserted the instalation disk, and inside the Linux folder, I found an archive of the folder 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO which would be the driver for this USB adapter. I have unpacked it, and then I looked at readme and followed the steps. Except of a problem caused by the structures kgid_t and kuid_t, which in the newer kernels aren't an int anymore, which I solved it in the folder mentioned previously in /os/linux/rt_linux.c on lines 1126 and 1127 by adding .val at the end, everything went fine. I used "make", then "make install". In the end, I removed my older USB, rebooted, but didn't work (looked like I didn't even insert the new USB adapter). After that, I installed "sudo apt-get install linux-formware-nonfree", but it still didn't work after that. The links to the important files are [http://www.mediafire.com/download/23ab45rkrbh259c/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.tar.gz](http://www.mediafire.com/download/23ab45rkrbh259c/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.tar.gz) and [http://www.mediafire.com/download/ad65cfy6c2dr44q/wireless-info.txt.tar.gz](http://www.mediafire.com/download/ad65cfy6c2dr44q/wireless-info.txt.tar.gz).
Thanks for your help!

Yours, Emanuel

---

### Post by george-bungarzescu on 2015-06-14
> **Antonache_Emanuel_ said:**
> Hello,

 Recently I have acquired this USB adapter ([http://www.tenda.cn/tendacn/downloads/show.aspx?productid=360)]("http://www.tenda.cn/tendacn/downloads/show.aspx?productid=360"), wanting to replace my older USB adapter. I have inserted the instalation disk, and inside the Linux folder, I found an archive of the folder 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO which would be the driver for this USB adapter. I have unpacked it, and then I looked at readme and followed the steps. Except of a problem caused by the structures kgid_t and kuid_t, which in the newer kernels aren't an int anymore, which I solved it in the folder mentioned previously in /os/linux/rt_linux.c on lines 1126 and 1127 by adding .val at the end, everything went fine. I used "make", then "make install". In the end, I removed my older USB, rebooted, but didn't work (looked like I didn't even insert the new USB adapter). After that, I installed "sudo apt-get install linux-formware-nonfree", but it still didn't work after that. The links to the important files are [http://www.mediafire.com/download/23ab45rkrbh259c/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.tar.gz](http://www.mediafire.com/download/23ab45rkrbh259c/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.tar.gz) and [http://www.mediafire.com/download/ad65cfy6c2dr44q/wireless-info.txt.tar.gz](http://www.mediafire.com/download/ad65cfy6c2dr44q/wireless-info.txt.tar.gz).
Thanks for your help!

Yours, Emanuel

It is Is working in Ubuntu , Linux  3.19.0-20-generic #20-Ubuntu SMP Fri May 29 10:10:47 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux ,DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu Wily Werewolf (development branch)"
with stock kernel rt2800usb module.   

modprobe rt2800usb nohwencrypt ( just press tab after modprobe rt2800usb part )
For some obscure reason you need to do also after line above, 
modprobe rt2800pci

---

### Post by george-bungarzescu on 2015-08-05
this solution does not work anymore after update

---

