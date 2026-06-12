---
title: "Ralink 3290 - Wi-Fi and Bluetooth issues in 13.10"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by Skyflier on 2014-03-12
Hi guys

I've been trying to install Ubuntu 13.10 on my laptop but have run on some obstacles as of now. I have an HP Pavilion G6-2208ep which has the infamous Ralink RT3290 chipset with Wi-Fi and Bluetooth integrated in it.

In Ubuntu 13.10, Wi-Fi works at first, but about 1 minute after connecting the network falls and I can't connect again. Bluetooth doesn't work at all. So I tried to install the STA drivers provided in Mediatek's website but the "make" command does not finish correctly. Here's what the output of the command brings:

```

 make -C toolsmake[1]: Entering directory `/home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/tools'
/home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/tools/bin2h
cp -f os/linux/Makefile.6 /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/Makefile
make -C /lib/modules/3.11.0-18-generic/build SUBDIRS=/home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-18-generic'
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_md5.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wep.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/action.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_data.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_aes.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_sync.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/eeprom.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_info.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_radar.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/spectrum.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rt_channel.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_profile.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_asic.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/ps.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/uapsd.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/assoc.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/auth.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sync.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sanity.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/connect.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/wpa.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rt_os_util.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/ba_action.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rt_led.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_mac_pci.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_rbus_pci_drv.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/ee_prom.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/ee_efuse.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rt_rf.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt30xx.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.o
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-18-generic'

```

At the end of the output in the terminal, which is not shown here, there are some errors depicted:
```
cc1: some warnings being treated as errors
make[2]: *** [/home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.o] Error 1
make[1]: *** [_module_/home/goncalo/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-18-generic'
make: *** [LINUX] Error 2

```


Before running "make", I ran these commands to install some required packages first

```
sudo apt-get update
sudo apt-get install build-essential linux-headers-generic
```
So I assume the problem is related to the kernel version in Ubuntu 13.10 being incompatible with the drivers. 
I tested this in Ubuntu 12.04 with a downgraded kernel and the drivers compiled and installed correctly.

I would like to know if there is some way to compile drivers in 13.10 or if I will have to use 12.04 at the expense of having a much older kernel version.

---

### Post by chili555 on 2014-03-12
> So I assume the problem is related to the kernel version in Ubuntu 13.10 being incompatible with the drivers. Exactly correct.

Finding and installing a different driver would be on my list of things to try, but it would be pretty far down my todo list. Installing an *older* driver than what I have wouldn't be anywhere on my list! First, I'd do a bit of troubleshooting. 

If the connection drops after a few moments, I'd turn off power saving and see if it helps:```
sudo iwconfig wlan0 power off
```I might also try a driver parameter:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```I'd also try to isolate the reason for the drops:```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```If and only if none of these worked, I'd read this: [https://bugzilla.kernel.org/show_bug.cgi?id=61621](https://bugzilla.kernel.org/show_bug.cgi?id=61621) Some reports suggest that this is fixed in kernel 3.12 et seq. We can install the 3.13 backported driver or kernel packages if all the above suggestions are ineffective.

------------------

Possible reference: [http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working)  <--kernel debs

---

### Post by Skyflier on 2014-03-12
Well, many thanks for yout help.

None of the commands worked, I also tried to grab the log on the last command but for some dumb reason I did not copy it to the pen drive to bring it to Windows. But for what I read on it, the wireless manager dropped the connection because it said the SSID where it was connected did not exist any more. It must be a kernel bug for sure as you already noted.

So I have two options here, and I don't know which one I should go. 
1 - Install Ubuntu 13.10 even without Wi-Fi and Bluetooth and try the next step to install the 3.13 kernel (NOTE: I already tested the 3.13 kenrel in Ubuntu 14.04 and wireless was working out of the box BUT no Bluetooth).
2 - Install Ubuntu 12.04 and downgrade kernel to 3.2 and use [this guide]("http://lifeindwarka.blogspot.in/2013/08/setting-up-hp-pavilion-g6-2313ax-on.html") where he gets the Wi-Fi, Bluetooth and switch button with led working which is something really impressive. But I will be using older kernel following this way,

It would be good to know if some users with Ralink RT3290 got these three components working in 13.10.

I just don't want to install Ubuntu on my PC and then having a broken system that I can't fix.

---

### Post by chili555 on 2014-03-12
You can copy the log into a text file:```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20 > wifi.txt
```And then transfer it on a USB.

Frankly, if it were me, I'd just grab the 3.13 kernel debs and install them and reboot. Get these on a USB drive: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/) Get the files appropriate to your architecture; either 32- or 64-bit:```
arch
```If, for example, you have a 64-bit system, get linux-image amd64, linux-headers amd64 and linux-headers all. Drag and drop them to your desktop and install:```
cd ~/Desktop
sudo dpkg -i linux*.deb
sudo update-grub
sudo reboot
```And then tell us if it is working as expected.

---

### Post by praseodym on 2014-03-12
Alternatively, try this patch:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466/comments/116](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466/comments/116)

---

### Post by Skyflier on 2014-03-12
> **praseodym said:**
> Alternatively, try this patch:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466/comments/116](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466/comments/116)
I'm trying this procedure but I'm doing something wrong (or noob in other words).

Which file should I untar to /usr/src ? I untared the folder inside with name "rt3290sta" and copied it to the folder. Then when I run dkms it tells me there is no module in the folder. What am I doing wrong?

---

### Post by Skyflier on 2014-03-13
Well I am still having trouble trying to install that AUR patch in Ubuntu. Either way I grabbed the network manager log to check the cause of the connection drop.

```
Mar 13 18:44:50 ubuntu NetworkManager[1697]: <info> (wlan0): roamed from BSSID 78:8D:F7:07:32:B8 (ZON-32B0) to (none) ((none))
Mar 13 18:44:50 ubuntu NetworkManager[1697]: <info> (wlan0): supplicant interface state: completed -> disconnected
Mar 13 18:44:50 ubuntu NetworkManager[1697]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 13 18:44:50 ubuntu NetworkManager[1697]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 13 18:44:50 ubuntu NetworkManager[1697]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Mar 13 18:44:50 ubuntu NetworkManager[1697]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 13 18:44:56 ubuntu NetworkManager[1697]: <info> (wlan0): IP6 addrconf timed out or failed.
Mar 13 18:44:56 ubuntu NetworkManager[1697]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 13 18:44:56 ubuntu NetworkManager[1697]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 13 18:44:56 ubuntu NetworkManager[1697]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar 13 18:45:06 ubuntu NetworkManager[1697]: <warn> (wlan0): link timed out.
Mar 13 18:45:06 ubuntu NetworkManager[1697]: <info> (wlan0): device state change: activated -> failed (reason 'SSID not found') [100 120 53]
Mar 13 18:45:06 ubuntu NetworkManager[1697]: <warn> Activation (wlan0) failed for connection 'ZON-32B0'
Mar 13 18:45:06 ubuntu NetworkManager[1697]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 13 18:45:06 ubuntu NetworkManager[1697]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar 13 18:45:06 ubuntu NetworkManager[1697]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 3356
Mar 13 18:45:06 ubuntu kernel: [  207.477151] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 13 18:45:06 ubuntu NetworkManager[1697]: <warn> DNS: plugin dnsmasq update failed
Mar 13 18:45:06 ubuntu NetworkManager[1697]: <info> Removing DNS information from /sbin/resolvconf
Mar 13 18:45:06 ubuntu NetworkManager[1697]: <info> (wlan0): supplicant interface state: scanning -> disconnected

```

---

### Post by praseodym on 2014-03-14
> ```
Mar 13 18:45:06 ubuntu NetworkManager[1697]: <info> Removing DNS information from /sbin/resolvconf
```
Check:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by Skyflier on 2014-03-14
> **praseodym said:**
> Check:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```
It didn't work at all. After running the commands it can't connect to the Wireless.

Here´s a log after running the commands:
```
Mar 14 17:06:19 ubuntu kernel: [  633.218764] wlan0: authentication with 78:8d:f7:07:32:b8 timed out
Mar 14 17:06:19 ubuntu NetworkManager[3789]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Mar 14 17:06:19 ubuntu NetworkManager[3789]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 14 17:06:20 ubuntu wpa_supplicant[2128]: wlan0: SME: Trying to authenticate with 78:8d:f7:07:32:b8 (SSID='ZON-32B0' freq=2417 MHz)
Mar 14 17:06:20 ubuntu kernel: [  634.388828] wlan0: authenticate with 78:8d:f7:07:32:b8
Mar 14 17:06:20 ubuntu kernel: [  634.388846] wlan0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
Mar 14 17:06:20 ubuntu NetworkManager[3789]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 14 17:06:20 ubuntu kernel: [  634.404190] wlan0: direct probe to 78:8d:f7:07:32:b8 (try 1/3)
Mar 14 17:06:20 ubuntu kernel: [  634.608293] wlan0: direct probe to 78:8d:f7:07:32:b8 (try 2/3)
Mar 14 17:06:20 ubuntu kernel: [  634.812504] wlan0: direct probe to 78:8d:f7:07:32:b8 (try 3/3)
Mar 14 17:06:21 ubuntu kernel: [  635.016715] wlan0: authentication with 78:8d:f7:07:32:b8 timed out
Mar 14 17:06:21 ubuntu NetworkManager[3789]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Mar 14 17:06:21 ubuntu NetworkManager[3789]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 14 17:06:25 ubuntu NetworkManager[3789]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Mar 14 17:06:25 ubuntu NetworkManager[3789]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Mar 14 17:06:25 ubuntu NetworkManager[3789]: <warn> Activation (wlan0) failed for connection 'ZON-32B0'
Mar 14 17:06:25 ubuntu NetworkManager[3789]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 14 17:06:25 ubuntu NetworkManager[3789]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar 14 17:06:25 ubuntu NetworkManager[3789]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Mar 14 17:06:25 ubuntu NetworkManager[3789]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.

```

---

### Post by firesock on 2014-04-24
Hi!!
If you want to solve the wifi problem, go to the last post at:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)

For bluetooth go to:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721)

Cheers!!

---

