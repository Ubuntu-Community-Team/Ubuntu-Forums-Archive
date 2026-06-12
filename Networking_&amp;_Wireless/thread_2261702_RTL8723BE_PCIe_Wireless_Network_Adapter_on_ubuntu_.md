---
title: "RTL8723BE PCIe Wireless Network Adapter on ubuntu 14.04"
date: 2015-01-20
forum: Networking &amp; Wireless
---

### Post by eli_fabrikant on 2015-01-20
Hi there,

my RTL8723BE PCIe Wireless Network Adapter gives me loads of trouble  (disconnects and freezes every few minutes). 

I researched a lot on google and the forum here and at askubuntu, and couldn't find any answer that i could actually decipher (I'm a novice). 

Is there anyone who might be kind enough to quickly guide me through this?

greatly appreciated in advance!
e

---

### Post by Hadaka on 2015-01-20
hi,please open a terminal...ctrl/alt/t then
COPY  and paste one line at a time..
```
sudo modpobe -r rtl8723be
echo "options rtl8723be fwlps=0 swlps=0" sudo tee -a /etc/moprobe.d/rtl8723be.conf
sudo modprobe rtl823be
```
thanks

---

### Post by eli_fabrikant on 2015-01-22
Hi Hadaka,

thank you so much for your reply!

unfortunately I don't think it worked :( I corrected the typos in the lines that you've posted (always made it modprobe rtl8723be), and inserted them by order into the terminal. But nothing happened. The terminal gave no reply, and the wifi keeps disconnecting one minute after reboot. 
Can you go over the second line and tell me if all is correct there? Or is there anything else that I can do?


Thanks so much for your time!
e

---

### Post by Pilot6 on 2015-01-22
It is better to install new driver, which is already megred it ti new kernels.

[https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)

---

### Post by chili555 on 2015-01-22
> **Pilot6 said:**
> It is better to install new driver, which is already megred it ti new kernels.

[https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)Unless you can guide this novice through the process, your answer is useless.

There are four branches of this driver. Which branch to use depends on your kernel version. eli_fabrikant, please tell us from the terminal:```
uname -r
```

---

### Post by eli_fabrikant on 2015-01-22
This is the output:

3.13.0-44-generic

---

### Post by chili555 on 2015-01-22
With an internet connection, ideally ethernet, open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
sudo reboot
```Please tell us if you have any improvement. We will probably have one additional step.

---

### Post by eli_fabrikant on 2015-01-22
Dear chili555,

it looks very good! I'll check it for a coupke more days and then mark it as solved if the problem doesn't appear gain.
Just out of curiousity - can I do the same procedure after upgrading to  13.6 kernel or is it 13.3 specific?  I'm asking because it seems like another driver that I need (touchpad elantech-x551c) is only available in 13.6.


In any case, thanks a thousand times for your help! 
e

---

### Post by Pilot6 on 2015-01-22
I can just add that you will have to reinstall this driver after each kernel update.
Unless I force myself to make a ppa with dkms package.

---

### Post by chili555 on 2015-01-22
> **eli_fabrikant said:**
> Dear chili555,

it looks very good! I'll check it for a coupke more days and then mark it as solved if the problem doesn't appear gain.
Just out of curiousity - can I do the same procedure after upgrading to  13.6 kernel or is it 13.3 specific?  I'm asking because it seems like another driver that I need (touchpad elantech-x551c) is only available in 13.6.


In any case, thanks a thousand times for your help! 
eIt works perfectly well in 3.16. Whether it provides the needed driver for your Elantech depends on the device. What is it?

As Pilot6 notes, after a kernel update and after the required reboot, recompile:```
cd rtlwifi_new
make clean
make
sudo make install
sudo reboot
```Glad it's working!

---

### Post by eli_fabrikant on 2015-01-25
Hi Chili555,


I though the device IS touchpad elantech-x551c. or am I missing something?

I'm afraid I have new problems :( I tried to upgrade to the new Kernel using the instructions here:
[http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/](http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/)
but I think I am suffering now from kernel panic, because Ubuntu won't load the new kernel. What can i do to over-come this problem?

Thanks so much for your time and sorry for piling up new problems :(
e

---

### Post by chili555 on 2015-01-25
> **eli_fabrikant said:**
> Hi Chili555,


I though the device IS touchpad elantech-x551c. or am I missing something?

I'm afraid I have new problems :( I tried to upgrade to the new Kernel using the instructions here:
[http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/](http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/)
but I think I am suffering now from kernel panic, because Ubuntu won't load the new kernel. What can i do to over-come this problem?

Thanks so much for your time and sorry for piling up new problems :(
eWhich debs did you download and install? Is your current system 32- or 64-bit?```
arch
```What driver do you need that is only available in 3.16? The driver for the touchpad?

---

### Post by m4tiasr on 2016-01-17
Thanks a lot! this worked perfectly for my HP Pavilion 15 pl006.

---

### Post by Estefa_RG on 2016-05-02
It works perfectly, gratitud!!!!

---

### Post by vasa1 on 2016-05-02
This thread is more than a year old. If you have a related issue, please start a new thread and link to this one if necessary.

---

