---
title: "QCA9337 on ASUS TP200S (ubuntu-15.10-desktop-amd64)"
date: 2015-12-25
forum: Networking &amp; Wireless
---

### Post by Benjamin_Brand on 2015-12-25
Hello,

I'm a completly new user of ubuntu. I never worked with it before, but I wanted to try it and so i decided to install it on my ASUS T200S. The installation went smoothly, but now my wireless module does not seem to work. Because I don't have any ethernet port, I have to install everything manually. So I found this thread :

[http://ubuntuforums.org/showthread.php?t=2300861&page=11](http://ubuntuforums.org/showthread.php?t=2300861&page=11)

downloaded the QCA9337 lib from the link, copied it to the ath10k folder, loaded the linux-headers-generic and these backports:
[https://www.dropbox.com/s/6hl52r0krq3wpxf/backports-20150903b.tar.gz](https://www.dropbox.com/s/6hl52r0krq3wpxf/backports-20150903b.tar.gz)

Then I manually did this :

sudo apt-get install build-essential linux-headers-$(uname -r) git
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
wget [https://www.dropbox.com/s/6hl52r0krq3wpxf/backports-20150903b.tar.gz](https://www.dropbox.com/s/6hl52r0krq3wpxf/backports-20150903b.tar.gz)
tar -zxvf backports-20150903b.tar.gz
cd backports-20150903
make defconfig-ath10k
make
sudo make install
git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/





and renamed the firmware file to firmware-5.bin.

lshw -C network Now gives the correct information, where before it would say UNCLAIMED.

BUT

dmesg | grep ath10k says :

device 0042 with chip_id 003820ff isn't supported.

Can I do something? Or is this chip just not supported yet and i have to wait?

Thanks in advance

bjt

edit : just found [http://askubuntu.com/questions/701350/qualcomm-atheros-qca9377-wireless-not-working-on-lenovo-with-14-04-3](http://askubuntu.com/questions/701350/qualcomm-atheros-qca9377-wireless-not-working-on-lenovo-with-14-04-3) gonna try it real quick

edit2: alright nevermind, the last link did the trick. Im sorry to have bothered you

---

### Post by nhm on 2016-11-02
Are there any updates to this pls?  I need to install ubuntu badly on my Asus TP200S and trying to gather all the data that I'll need for the adventure. Pls help.

---

