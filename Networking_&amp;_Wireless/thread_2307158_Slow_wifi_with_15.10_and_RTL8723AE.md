---
title: "Slow wifi with 15.10 and RTL8723AE"
date: 2015-12-22
forum: Networking &amp; Wireless
---

### Post by warren3 on 2015-12-22
Hi.

I am getting slow wifi with this adapter (around 1mb) and 15.10.  I also have an Intel AC7260 in the draw but my experience with 14.04 using the 7260 was not pleasant - maybe with the newer kernel things have changed?

But anyway I only want to concentrate on the RTL8723AE at the moment.  I have looked on the web but some guides are a few years old and I don't want to start messing with anything until I've asked you guys.

Thanks.

---

### Post by chili555 on 2015-12-22
Are you sure? I'd rather coax the 7260 to life.> maybe with the newer kernel things have changed?And newer firmware.

---

### Post by warren3 on 2015-12-22
OK I'll put the 7260 in tomorrow when I put my mechanical HD in my machine.  I have just got a dread of spinning loading wheels in Firefox happening again.

---

### Post by chili555 on 2015-12-22
I suggest you install the later driver and firmware. Let's build the 4.3 version of the driver, download the later firmware and see if it helps. First, download these files to your desktop: [https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-25.30.13.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-25.30.13.0.tgz) Also: [https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-15.227938.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-15.227938.0.tgz) Right-click each and select 'Extract Here.' Now, in a terminal:
```
cd ~/Desktp/iwlwifi-7260-ucode-25.30.13.0
sudo cp iwlwifi*  /lib/firmware
cd ~/Desktop/iwlwifi-7260-ucode-15.227938.0
sudo cp iwlwifi*  /lib/firmware
```
Now, let's build the later driver:
```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.3/backports-4.3-1.tar.gz
tar -zxvf backports-4.3-1.tar.gz
cd backports-4.3-1
make defconfig-iwlwifi
make
sudo make install
```
Reboot.

Any improvement? I will probably have one more step.

---

