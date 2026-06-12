---
title: "install rt2870 stuck on make"
date: 2015-03-24
forum: Networking &amp; Wireless
---

### Post by orugari on 2015-03-24
Hello,

After long hour searching around, I still cannot find a solution to my problem.

I am following this tutorial [http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html](http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html) 
But at the $ sudo make install, I have a problem :

```
make -C /tmp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux -f Makefile.6 install
make[1]: Entering directory `/tmp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /tmp/2010_0709_RT2870_Linux_STA_v2.4.0.1/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.16.0-33-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.32-24-generic-pae/kernel/drivers/net/wireless/
cannot stat 'rt2870sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/tmp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
make[1]: *** [install] Error 2


``` 
I download the driver [here]("http://www.mediatek.com/jp/downloads/")

I have absolutly no clue how to make it works and will love for some help. Taking hours on this forum to find similar problems, but none of them worked... Or I may do bad.. ?
Thank you so much !

---

### Post by SeijiSensei on 2015-03-24
Did you run "make" by itself first?  Look at the page you linked to.  Did you see all those lines that begin with "CC"?

> make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
  CC [M]  /tmp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_md5.o
  CC [M]  /tmp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_sha2.o
  CC [M]  /tmp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_hmac.o
  CC [M]  /tmp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.o


This article is also over four years old, and the platform is RedHat/CentOS, not Debian/Ubuntu.  You can tell because it is using kernel 2.6.32.  Maybe you should try the suggestions in this thread: [http://ubuntuforums.org/showthread.php?t=2210930](http://ubuntuforums.org/showthread.php?t=2210930).

---

### Post by wildmanne39 on 2015-03-24
That driver is very old it will never compile own a newer version of ubuntu, what version are you using? newer version should already have the driver installed.
I suggest you run the wireless script in my signature and post the results here.
Thansk

---

### Post by orugari on 2015-03-24
Hum, not working.
Yup I did run $ make then $ sudo make install to get this 

I am using Xubuntu 14.04
Well here is what I do, step by step

lsusb:
 ```
Bus 001 Device 002: ID 0789:0166 Logitec Corp. LAN-W300N/u2 Wireless LAN Adapter
```

I download [rt2870]("http://www.mediatek.com/en/downloads/rt2870usbrt2870rt2770/") from [mediatek]("http://www.mediatek.com/en/downloads/")

I extract and then go to the folder

```

$ make clean
$ make

[...]
/home/yuko/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevDetach&#8217;:
/home/yuko/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c:1694:38: warning: initialization discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
  struct net_device_ops *pNetDevOps = pNetDev->netdev_ops;
                                      ^
/home/yuko/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
/home/yuko/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c:1731:38: warning: initialization discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
  struct net_device_ops *pNetDevOps = pNetDev->netdev_ops;
                                      ^
make[2]: *** [/home/yuko/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/yuko/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.16.0-33-generic'
make: *** [LINUX] Error 2

$ sudo make install

make -C /home/yuko/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux -f Makefile.6 install
mkdir: cannot create directory &#8216;/etc/Wireless&#8217;: File exists
make[1]: Entering directory `/home/yuko/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
rm -rf /etc/Wireless/RT2870STA
rm: cannot remove &#8216;/etc/Wireless/RT2870STA/RT2870STA.dat&#8217;: Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/yuko/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
make: *** [install] Error 2
```


Here is where I am stuck.

According to [this thread ]("http://ubuntuforums.org/showthread.php?t=2210930")I may refer on lsusb, but I cannot find a link on mediatek.

Thanks again for your help !

Edit : I did like that too [http://askubuntu.com/questions/577941/installing-the-driver-for-tp-link-tl-wn727n-on-ubuntu-14-04/578017#578017](http://askubuntu.com/questions/577941/installing-the-driver-for-tp-link-tl-wn727n-on-ubuntu-14-04/578017#578017)
I got no error but still not working :/

---

### Post by wildmanne39 on 2015-03-24
I believe it is not working because it is not the correct driver for your device, I believe you need rt2800usb and it comes with the kernel so it should be installed but since you did not post the results of the script I can not know for sure. I am very busy so I am not able to help much right now but I will heck back when I can to see if you posted the file.
Thanks

---

### Post by orugari on 2015-03-24
Thanks to take the time.
Do you need the whole $ make script? I am not sure about what you mean by script, sorry (>_<)

I will try with this drivers and post again

Edit : After few try, I just back to the basics. You said that it must be already install so I just format and reinstall Xubuntu (Nothing to loose) and... It works... I am not sure what was the problem on the first try.

I am really sorry for that topics, but thanks for your help anyway, you push me to find it !
Thanks !

---

### Post by praseodym on 2015-03-25
This is the right one for kernels up to 3.13:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/13/16/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5370sta -v 2.5.0.3
sudo dkms build -m Ralink_5370sta -v 2.5.0.3
sudo dkms install -m Ralink_5370sta -v 2.5.0.3 
sudo mkdir -p /etc/Wireless/RT2870STA
sudo cp /usr/src/Ralink_5370sta-2.5.0.3/src/RT2870STA.dat /etc/Wireless/RT2870STA 

```
Supported chipsets include:

	0789:0166 Edimax 

Check the grey boxes here:

[http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/#post-4365112](http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/#post-4365112)

---

