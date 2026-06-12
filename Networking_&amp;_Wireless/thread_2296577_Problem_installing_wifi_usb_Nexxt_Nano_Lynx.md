---
title: "Problem installing wifi usb Nexxt Nano Lynx"
date: 2015-09-26
forum: Networking &amp; Wireless
---

### Post by fernando55 on 2015-09-26
Hello,

I'm pretty new on linux and I have installed ubuntu 14.04 LTS (64bits) in my laptop, but I'm having a terrible time trying to install my Wifi USB Nexxt Nano Lynx, the cd came with a folder named "linux" containing a "2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2" file, so I was looking through forums how to install it, so I already extract it and tried to run make command ,at the beginning I was obtaining the 127 error but I was able to find in a forum how to remove some space in folder name to make it work, but now I have a new error:

make[2]: *** [/home/gafjubuntu/Documents/Driver_Linux_Nexxt_USB_wifi/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/gafjubuntu/Documents/Driver_Linux_Nexxt_USB_wifi/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.16.0-46-generic'
make: *** [LINUX] Error 2

I tried some threats in other forum posts but did not work for me, I runned this commads trying to solve the problem:

sudo apt-get install linux-headers-generic build-essential git
sudo apt-get install git
git clone [http://github.com/GlassGhost/RT3070STA.git](http://github.com/GlassGhost/RT3070STA.git)

But the error remains equal when i tried to run again make command. I'm not sure if this is enough information but please let me know anything else I could provide to you. 

Thanks a lot in advance for any comments or help!!

BR,

---

