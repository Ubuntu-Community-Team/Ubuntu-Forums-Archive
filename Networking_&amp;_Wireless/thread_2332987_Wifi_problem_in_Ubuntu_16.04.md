---
title: "Wifi problem in Ubuntu 16.04"
date: 2016-08-06
forum: Networking &amp; Wireless
---

### Post by hal-2 on 2016-08-06
Hello,

I have installed Ubuntu 16.04 on my Lenovo U31 and having slow connection issues in Ubuntu. Windows is also installed on the same laptop and works fine. I would really appreciate any suggestion.

Some details:
After I installed Ubuntu, the wifi driver was not recognized. It started to work after I downloaded firmware files for the driver from [this website]("https://github.com/kvalo/ath10k-firmware"). However, the speed is very slow and the signal is very weak. Very often the connection drops and asks for wifi password. Everything is fine if I connect with a cable.

EDIT: results of the wireless script is attached.
EDIT: previous attachment replaced with the new results of the wireless script after disabling power management and setting the router channel to 9.

iwconfig:
```
wlp3s0    IEEE 802.11abgn  ESSID:"Kuci"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 90:0D:CB:98:D7:E0   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:42  Invalid misc:18   Missed beacon:0


enp2s0    no wireless extensions.


lo        no wireless extensions.


```
rfkill list all:
```

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



```

cat iwlwifi.conf:
```
options iwlwifi swcrypto=1# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
```

cat ath10k.conf:
```
options ath10k nohwcrypt=1

```

Thank you!

---

### Post by jeremy31 on 2016-08-06
*Thread moved to **Networking & Wireless**.*

Please see the wireless script link in my signature and post results

Welcome to the forums

---

### Post by Geoffrey_Arndt on 2016-08-06
Well, if you compiled the driver from that github page, that's the Unix driver and not the linux driver.

The linux driver is at:   [https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/  ]("https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/")

Further, IF you want a simpler, and better solution, just get a linux certified usb wifi adapter.   Panda has several that are 100% plug & play on Ubuntu . . [http://www.pandawireless.com/](http://www.pandawireless.com/)
[URL="https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/"]


[/URL]

---

### Post by jeremy31 on 2016-08-06
> **Geoffrey_Arndt said:**
> Well, if you compiled the driver from that github page, that's the Unix driver and not the linux driver.

The linux driver is at:   [https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/  ]("https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/")

Further, IF you want a simpler, and better solution, just get a linux certified usb wifi adapter.   Panda has several that are 100% plug & play on Ubuntu . . [http://www.pandawireless.com/](http://www.pandawireless.com/)
[URL="https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/"]


[/URL]

Actually it is just firmware on the github site.  It just happens the github site is that of Kalle Valo, the one who submitted the ath10k firmware to the git.kernel.org site
[http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/log/ath10k](http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/log/ath10k)

---

### Post by Geoffrey_Arndt on 2016-08-06
Hmm, after looking closer, you're right.    Guess the next step is for OP to run the script.

---

### Post by hal-2 on 2016-08-07
Thank you! I have edited my first post and attached the results.

---

### Post by kurt18947 on 2016-08-08
No expert here but I see entries for iwlwifi (Intel) and ath10k (Atheros). Do you have two wifi adapters? Or does the 'cat' command return results even if a piece of hardware is not installed or in use?

---

### Post by hal-2 on 2016-08-08
I was thinking that I have only Qualcomm Atheros. Interestingly, after your question I had a look on Lenovo website with my laptop model and saw that there are two drivers listed for download (windows only). Now, I am confused if I have both Qualcomm and Intel.

---

### Post by Geoffrey_Arndt on 2016-08-08
The wireless should be qualcomm/atheros.   The wired network chipset is Realtek 8168/8111 series.   BTW, did you try the Ubuntu process for obtaining/installing "additional drivers" . .?

---

### Post by jeremy31 on 2016-08-08
> **hal-2 said:**
> I was thinking that I have only Qualcomm Atheros. Interestingly, after your question I had a look on Lenovo website with my laptop model and saw that there are two drivers listed for download (windows only). Now, I am confused if I have both Qualcomm and Intel.

The Lenovo's usually have 3 or 4 different wifi cards that might be in a certain model.  I looked at the maintenance manual for my G710 and it listed the Atheros AR9485, an Intel, a Broadcom, and a Realtek for possible wifi cards

I would change the Kuci wifi router to channel 9 as it is on a channel with quite a few other routers

And we should disable power management for the wifi
```
sudo -H gedit /etc/systemd/system/root-resume.service
```
Insert the following
```
[Unit]
Description=Turn off wlan power management
After=suspend.target

[Service]
Type=simple
ExecStartPre= /bin/sleep 10
ExecStart= /sbin/iwconfig wlp3s0 power off

[Install]
WantedBy=suspend.target
```

Save and exit gedit, then
```
sudo systemctl enable root-resume
```

Reboot and see if it is better, actually run the wireless script again after the reboot ```
./wireless-info
```

---

### Post by hal-2 on 2016-08-08
No, I haven't. I will have a look how it is done and let you know regarding the results. Thanks.

---

### Post by hal-2 on 2016-08-08
I have tried to disable power management according to your message but it is still not disabled (I can see that power management is on if I type iwconfig). Can it be something to do with the following error that I received while creating the file.
> 
** (gedit:5086): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported


Note: I have changed the router channel to 9 as suggested but can't see any improvement for now.

---

### Post by jeremy31 on 2016-08-09
Try ```
sudo iwconfig wlp3s0 power off
```
That should disable power management

---

### Post by hal-2 on 2016-08-10
Thanks. This code disabled the power management. However, I haven't noticed any improvement. I ran the wireless script once more and attached the results to my first post.

---

### Post by hal-2 on 2016-08-24
After changing the wifi router channel and disabling power management there is a slight improvement. However, the speed is still very slow compared to my other devices or the same device while operating on windows. This problem occurs also in other networks. I have attached a new result of wireless script, I would be happy to receive any suggestions. 

I also want to mention that I have to manually disable power management every time. Unfortunately the method to make the change permanent did not work for me.

Now I am considering using newer backports although I am not so sure what it is. Shall I try it?

Thanks,

---

### Post by jeremy31 on 2016-08-25
You might be able to disable power management with
```
sudo -H gedit /etc/rc.local
```

Then make changes to the bottom of the file so it look like
```
sleep 10
/sbin/iwconfig wlp3s0 power off
exit 0
```
Save, exit program and reboot

What version of linux-firmware do you have now? ```
dpkg -l | grep linux-firmware
```

---

### Post by hal-2 on 2016-08-26
Thank you.

However, the power management is still on after the reboot. That code didn't work for me.

Here is the linux firmware

> ii  linux-firmware                              1.157.3                                                     all          Firmware for Linux kernel drivers



---

### Post by jeremy31 on 2016-08-26
Found something on an Intel linux page
```
sudo -H gedit /lib/systemd/system/wifi-power-management-off.service
```

Paste the following into the file
```
[Unit]
Description=Disable power management for wlp3s0
Requires=sys-subsystem-net-devices-wlp3s0.device
After=network.target

[Service]
Type=oneshot
ExecStartPre= /bin/sleep 10
ExecStart=/sbin/iwconfig wlp3s0 power off

[Install]
WantedBy=multi-user.target
```

Save, exit gedit, then
```
systemctl enable wifi-power-management-off.service
```

Reboot and see if power management is off

---

### Post by hal-2 on 2016-08-27
Thanks. I just tried it but the power management is still on.

Since my internet speed is still slow even when the power management is off, do you think that it may be of help to try newer backports? And is it a safe method? I just saw the following method in another forum.

> Try a newer backports first

```
wget [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gztar](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gztar) -zxvf backports-4.4.4-1.tar.gz
cd backports-20151120

sudo make uninstall
```[COLOR=#333333][FONT=&amp]

[/FONT][/COLOR]Reboot

```
cd backports-4.4.2-1make defconfig-ath10k
make
sudo make install
```[COLOR=#333333][FONT=&amp]



[/FONT][/COLOR]

---

### Post by jeremy31 on 2016-08-27
The newest backports now is [https://www.kernel.org/pub/linux/kernel/projects/backports/2016/03/24/backports-20160324.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2016/03/24/backports-20160324.tar.gz)
It may look like March 24 of this year but the last update was in July where the 4.4.2 backports was from back in February

Strange that power management wasn't disabled at boot with that as it worked on a machine of mine.  Backports are safe and we have used them here before, the downside is that they have to be reinstalled after every kernel update
```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2016/03/24/backports-20160324.tar.gz
tar -zxvf backports-20160324.tar.gz
cd backports-20160324
make defconfig-ath10k
make
sudo make install
```

Reboot and see if it is better

After a kernel update you will need to 
```
cd backports-20160324
make clean
make defconfig-ath10k
make
sudo make install
```
Reboot

---

### Post by hal-2 on 2016-08-27
I tried it and the speed really increased to 10 Mbps (still not as high as 25 Mbps as in windows or other devices) immediately. However, after a few minutes it decreased to 3-5 Mbps. I don't know if it is related but I got the following errors while installing the backports.

```
Building modules, stage 2.  MODPOST 6 modules
  INSTALL /home/halil/backports-20160324/compat/compat.ko
At main.c:222:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/halil/backports-20160324/drivers/net/wireless/ath/ath.ko
At main.c:222:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/halil/backports-20160324/drivers/net/wireless/ath/ath10k/ath10k_core.ko
At main.c:222:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/halil/backports-20160324/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
At main.c:222:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/halil/backports-20160324/net/mac80211/mac80211.ko
At main.c:222:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/halil/backports-20160324/net/wireless/cfg80211.ko
At main.c:222:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  DEPMOD  4.4.0-34-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.


Your backported driver modules should be installed now.
Reboot.
```

---

### Post by jeremy31 on 2016-08-28
I secure boot enabled in BIOS?

We could also increase the sleep time in the systemd file
```
sudo sed -i 's/sleep 10/sleep 20/' /lib/systemd/system/wifi-power-management-off.service
```

---

