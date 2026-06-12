---
title: "Netgear WNA3100(v1)"
date: 2015-02-04
forum: Networking &amp; Wireless
---

### Post by chili555 on 2015-02-04
This device has been the subjuct of many long threads on this forum and at askubuntu.com. First, some details from lsusb:```
ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
```Searching for this device shows that there is no native Linux driver. The only way to get this working (badly) is ndiswrapper. Here is a long thread that shows the process. [http://ubuntuforums.org/showthread.php?t=1695036&highlight=WNA3100](http://ubuntuforums.org/showthread.php?t=1695036&highlight=WNA3100) Only 249 replies!

My colleague jeremy31 mailed me his WNA3100 to try to get working properly. Here I will outline the process I followed. First, I installed ndiswrapper:```
sudo apt-get install ndiswrapper-common ndiswrapper-dkms ndiswrapper-utils-1.9

```Then I downloaded the files from post #89 at the thread I linked. I installed the appropriate inf file. As mine is a 64-bit system, I did:```
cd ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2_amended
sudo ndiswrapper -i bcmn43xx64.inf
sudo ndiswrapper -ma
sudo modprobe ndiswrapper
```The balloon at Network Manager notified me that I had available networks and I tried to connect. After a couple of tries, I connected and even at N speeds! After about an hour, it slowed and stopped. Even though it appeared to be connected, pings to my router or to the DNS nameserver 8.8.8.8 went unanswered.

I disconnected it, unloaded ndiswrapper, reloaded the driver for my internal wireless and all was well, albeit frustrating.```
sudo modprobe -r ndiswrapper
sudo modprobe iwlwifi
```Next, I wondered if the problem was my 3.16.0-xx kernel in Ubuntu 14.10. I therefor installed a 3.13 kernel and headers from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.11.11-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.11.11-trusty/) I rebooted into 3.13 and repeated the experiment with the same result. After about an hour, it slowed and stopped.

I then tried to compile the hopefully latest ndiswrapper version from here:  [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) As you can see, it was last updated June 8, 2014. It won't compile without error in kernel versions 3.13 nor 3.16.

Next, I tried a later version of the XP inf and sys files from here: [http://downloadcenter.netgear.com/en/product/WNA3100#searchResults](http://downloadcenter.netgear.com/en/product/WNA3100#searchResults) I used Wine to extract the files. I installed bcmwlhigh5.inf and connected. dmesg is full of: ```
ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900226e4e00, 16000, 5
ndiswrapper (ndis_encode_setting:383): unknown type: 3 
```Again, in about an hour, it stalled and passed no traffic.

I removed the device and unloaded ndiswrapper. ```
sudo modprobe -r ndiswrapper
```I added a driver parameter to /etc/modprobe.d/ndiswrapper.conf:```
options ndiswrapper hangcheck_interval=3
```After a reboot, in about an hour, it stalled again.

When the device stalled, I had the sense that it was very hot. Checking with my multimeter thermal probe, I never saw a temperature above 101 F or 38 C. I don't believe that's excessively hot.

As of now, unless someone has another driver or process to try, I don't believe this device can be made to work correctly in Ubuntu 14.04 and later. Please don't ask me to help. I've tried everything I know of and it doesn't work.

SLIGHTLY OFF-TOPIC EDITORIAL

Linux will, indeed, always have driver issues, but for several reasons that may not be apparent to all of us. First, new devices are developed and released every day. The manufacturers are in a constant arms race to have a better device with more features and, often, cheaper. In almost every case, they have no concern for the 1-2% of Linux users and therefor don't provide a working driver.

Second, most new Linux users come to the party with what they have now that they bought with working Windows drivers. That device may work well or not at all in Linux. Experienced Linux users always check the forums and are sure the device works in Linux. Mrs. Chili hates it when we walk through the store and I make remarks about items in the computer department; "Those Netgears are tricky even in ndiswrapper." Now I can tell her they are impossible.

---

