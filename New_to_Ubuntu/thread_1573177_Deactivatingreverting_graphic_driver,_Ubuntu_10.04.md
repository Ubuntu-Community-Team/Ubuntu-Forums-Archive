---
title: "Deactivating/reverting graphic driver, Ubuntu 10.04"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by altblirgrusomt on 2010-09-12
First of all, I am running Ubuntu 10.04, 64 bit, on an Aspire 5810TG, intel core 2 solo processor with Ati Mobility Radeon HD 4330. 

I activated the ATI/AMD proprietary FGLRX graphic drivers, and restarted my computer.
On reboot, I only got a black screen and had to boot with the LIVE CD.

Im a returning fairly newbie Linux user and not familiar with the new way of reconfiguring Xconf.
So I had to no such luck restoring the X conf with 
> sudo dpkg-reconfigure -p high xserver-xorgI tried deleting the Ati Radeon driver, hoping it would automatically load the default graphic driver -- no such luck! 

There must be an easy solution to this problem, without needing to reinstall Ubuntu. 
I would be very happy if anyone could help me.

---

### Post by sandyd on 2010-09-12
> **altblirgrusomt said:**
> First of all, I am running Ubuntu 10.04, 64 bit, on an Aspire 5810TG, intel core 2 solo processor with Ati Mobility Radeon HD 4330. 

I activated the ATI/AMD proprietary FGLRX graphic drivers, and restarted my computer.
On reboot, I only got a black screen and had to boot with the LIVE CD.

Im a returning fairly newbie Linux user and not familiar with the new way of reconfiguring Xconf.
So I had to no such luck restoring the X conf with 
I tried deleting the Ati Radeon driver, hoping it would automatically load the default graphic driver -- no such luck! 

There must be an easy solution to this problem, without needing to reinstall Ubuntu. 
I would be very happy if anyone could help me.
```

sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```This will nuke fglrx and get your OSS (radeon) drivers back

cheers

---

