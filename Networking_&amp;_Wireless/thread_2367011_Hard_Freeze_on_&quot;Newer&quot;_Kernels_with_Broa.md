---
title: "Hard Freeze on &quot;Newer&quot; Kernels with Broadcom BCM43142 14e4:4365 Wifi Card"
date: 2017-07-24
forum: Networking &amp; Wireless
---

### Post by srxt on 2017-07-24
Hi,

My  system locks up (somewhat unpredictably, but very frequently) when  there is a transition from relatively little wireless activity to a  moderate amount. The image on the screen freezes in place and no further  input is taken (Magic SysRq key doesn't work anymore). Crashes have  occurred using wget, git, Bittorrent clients, curl, and by general web activity. The system can crash if left idly connected to a wireless network, but I can greatly accelerate matters by increasing network activity. I have observed this  behavior on every kernel I have tried to upgrade to (4.4, 4.8, 4.10).

What works:
If I use USB tethering for a connection instead of wifi, the system remains stable regardless of network traffic or kernel used.
If I use kernel 3.16.0-38-generic, the system remains stable even if using the wireless card.

Nothing  useful shows up in the log files. The last lines before a crash are  always UFW allow/audit entries (I have full logging enabled for UFW, as a  consequence of trying to figure this one out), but there is nothing  remarkable about them. I have thought to try comparing UFW log entries  for recreated activity between kernels to determine what the next UFW  entry would be which is not showing up in the logs when the crash  happens, but I suspect it wouldn't be very illuminating.

My  wireless card is a Broadcom BCM43142 802.11b/g/n (chip ID: 14e4:4365)  and uses the "wl" module/driver (which is the only one supported for the  chip at this time) installed via the "bcmwl-kernel-source" package  (version 6.30.223.271+bdcom-0ubuntu1~1.1) in the repositories. I've  deliberately uninstalled/reinstalled it across kernel versions, just in  case, to no avail.

I modified the source code to the wireless card driver (it's a hybrid,  where part is a binary blob, and the rest is Linux-specific C code) to  generate some initially-dormant debugging output. What I determined is  that a function called "wl_sendup" in the driver is always the last  function called (that logs debug statements, anyway) before a crash. This  function can be called as many as hundreds of thousands of times before a  crash, however. Unfortunately, there are no calls to wl_sendup() in any  of the available code, so I assume it's being done within the blob.  Also, the last thing this function does is call netif_rx(skb), which is a  kernel function. I added a statement to generate log output after the  call and I determined that netif_rx() seems to return consistently (the  last thing printed before a crash is the output statement I created). So  the crash is happening elsewhere, either in the driver or in the kernel.

I  also installed linux-crashdump and configured it to reliably recover  from crashes caused by "echo c > /proc/sysrq-trigger" but this wasn't  helpful for my problem. Crashes caused by wireless traffic cause a hard  freeze with skipping audio and the recovery kernel is never booted  into.

My guess is that the driver is in some way  incompatible with the newer kernels, but it seems as though others have  the driver working on these kernels. I'm kind of stumped and not really sure what the proper way to go about debugging this is.

---

### Post by Hadaka on 2017-07-24
Hi, this is interesting..
What works:
"If I use USB tethering for a connection instead of wifi, the system remains stable regardless of network traffic or kernel used.
 If I use kernel 3.16.0-38-generic, the system remains stable even if using the wireless card."

It may be a router configuration issue..Let's try this command first.
```
printf "[device]\nwifi.scan-rand-mac-address=0\n"| sudo tee -a /etc/NetworkManager/*.conf
```
Boot and test...if no improvement, please post the wireless info file..

 Open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt
Thanks.

---

### Post by srxt on 2017-07-24
The additional NetworkManager option didn't fix the problem. I also don't suspect it to be a router configuration issue because I connect to a number of different access points throughout the day and experience the same problem.

For whatever it's worth, the access point I am currently connected to reported the following just as the machine crashed:
```
wlp3s0: STA 14:2d:27:f6:08:2f IEEE 802.11: disconnected due to excessive missing ACKs
wlp3s0: AP-STA-DISCONNECTED 14:2d:27:f6:08:2f
wlp3s0: STA 14:2d:27:f6:08:2f IEEE 802.11: disconnected due to excessive missing ACKs
wlp3s0: STA 14:2d:27:f6:08:2f IEEE 802.11: disconnected due to excessive missing ACKs
wlp3s0: STA 14:2d:27:f6:08:2f IEEE 802.11: disconnected due to excessive missing ACKs
```

Output from the wireless-info script: [http://paste.ubuntu.com/25166696/](http://paste.ubuntu.com/25166696/)

---

### Post by Hadaka on 2017-07-24
Hi, the problem may indeed be a kernel issue, if this happens on other access points.
There are a couple other things that need attention that are compounding the problem.
first let's try this..
```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
This also causes drops and no connects...
#####IWCONFIG#####
#Power Management-on
Please do..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
and lastly..am I correct that you posted this with the tethered connection ??
#llsv  [AC1]>  Infra  11  2462 MHz  54 Mbit/s  95  &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no
#dbsqr [AC3]>  Infra  3  2422 MHz  54 Mbit/s  78 &#9602;&#9604;&#9606;_  WPA2   yes  *
*If yes..then some adjustments need to be made to your  llsv  [AC1 connection..
please verify my assumption.
thanks.

---

### Post by srxt on 2017-07-25
I made the changes, though crashing still occurs. 

I am posting from a separate machine which is stable and serves as the dbsqr access point (and uses the USB tether for internet access). I switched the crashing computer from the llsv network to the dbsqr network before running the wireless-info script, which is why firewall logs refer to llsv despite dbsqr being the active connection. The crashing computer crashes on both of these networks and on all others which it connects to.

Current setup:
<--(usb tether to internet)---> [stable machine / access point / where I am posting from ] <---(wireless connection)---> [unstable machine]

---

### Post by Hadaka on 2017-07-25
Thanks for the info. as you can see the llsv connection is mixed mode...wpa1-wpa2
ubuntu prefers wpa2 aes ccmp and NO tkip..which it currently also has. These changes
should  be done to allow your network to run faster and better. Starting with ubuntu 15.10
the broadcom wl driver became "unhappy" attempting to run 5g or N mode anything. The
less "aggressive" kernels could be adapted to handle the non support issues from broadcom
for unix/linux application. Now it is getting more difficult to get the wl driver to even function
in any mode with the newer kernels. You are probably better off and will suffer less frustration
by replacing your network cards with fully supported intel cards.I have sent a pm to a couple people
that have far more knowledge about the new kernels than i have. My guess is they will suggest the 
same as I have, to replace with fully supported network cards. Sorry I dont have some magic commands
to make it fly. We did atleast clean up some things that needed a minor massage.
Good luck to you.

---

### Post by praseodym on 2017-07-25
Newer kernels need newer driver versions, check here (German forum):

[https://forum.ubuntuusers.de/topic/wlan-probleme-seit-neuer-o2-box-nur-unter-linu/2/#post-8031898](https://forum.ubuntuusers.de/topic/wlan-probleme-seit-neuer-o2-box-nur-unter-linu/2/#post-8031898)

Did you deactivate SecureBoot in your UEFI?

---

### Post by BenginM on 2017-07-25
Salutations!

I past through this thread post last night and noticed Hadaka is troubleshooting the issue with you , so i steped back and he did great so far .. i was going to suggest as he suggested to replace the Broadcom with an Intel PCI or a Wifi usb adapter with an Intel chipset or Qualcomm Atheros, ojust Atheros chipset they're cheap ..  no Brodcam , Ralink , or Realtek chipset! these are troublesome. 

a good recourses for that would be :

[https://wireless.wiki.kernel.org/en/users/drivers](https://wireless.wiki.kernel.org/en/users/drivers)
[https://wikidevi.com/wiki/Main_Page](https://wikidevi.com/wiki/Main_Page)
[https://wikidevi.com/wiki/Intel](https://wikidevi.com/wiki/Intel)
[https://wikidevi.com/wiki/Category:USB_device](https://wikidevi.com/wiki/Category:USB_device)
[https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux](https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux)

that's the best bit and a quick fix that will get you up and running and save you this debug/troubleshooting headaches..

Free software developers won't help in case of a proprietary driver. And Just so you know this is a known and common issue with bcmwl wl driver not only in GNU/linux but also in MacOSX , freebsd,openbsd !

 
feel free to file a bug report about this upstream , report this problem to Broadcom directly following [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Broadcom_STA_Wireless_driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Broadcom_STA_Wireless_driver)

Good luck with that through ..!

---

### Post by srxt on 2017-07-25
Thanks Hadaka.

praseodym, I tried the "broadcom-sta-dkms" package first (which is version -3) and that was a spectacular failure, as the kernel crashed on boot. I purged it, then picked out the latest version I saw (-7) in your link and installed that, next. Stability is comparable to bcmwl-kernel-source driver. The broadcom-sta-dkms package doesn't come with any additional patches, but the bcmwl-kernel-source does, and applies patches such as "0022-add-support-for-Linux-4.8.patch" so it seems to me that both drivers are on par and already the latest versions? SecureBoot is already disabled, yes.

BenginM, thanks for the information. I will try a bug report, I suppose.

---

### Post by praseodym on 2017-07-26
Ok, I see. The versions 3 to 7 do not contain new code but patches to the latest kernels only.

Please run
```
iwconfig
ifconfig -a
iwlist chan
sudo iwlist scan
dmesg | grep wl
```

---

### Post by srxt on 2017-07-26
As requested: [http://paste.ubuntu.com/25175126/](http://paste.ubuntu.com/25175126/)

The dmesg output caused by the driver is more verbose than usual because I (1) enabled debugging output in the driver source code and (2) added my own print statements to functions which didn't have any in an attempt to trace out where exactly the crash is happening. All lines with the phrase "via_debug" were added by me. Most of the rest of the wl lines were already dormant in the code and just needed some tweaking to be enabled.

---

