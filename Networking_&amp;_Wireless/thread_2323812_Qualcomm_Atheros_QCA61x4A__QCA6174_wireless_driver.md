---
title: "Qualcomm Atheros QCA61x4A / QCA6174 wireless driver Ubuntu 16.04"
date: 2016-05-08
forum: Networking &amp; Wireless
---

### Post by uli9 on 2016-05-08
Everything I found is compiling something from git, which didn't work for me. Is there an easier way or a procedure that actually works? Machine is ASUS Aspire R.

---

### Post by jeremy31 on 2016-05-08
Try it from my git
```
sudo apt-get install git
git clone https://github.com/jeremyb31/ath10k-firmware.git
sudo cp ath10k-firmware/ /lib/firmware/ath10k/
```

Reboot, if it still doesn't work, see the wireless script link in my signature and use code tags when posting the results from the script

---

### Post by uli9 on 2016-05-08
Please, explain for noob. I am not a developer. I tried several things before, so now:

um@um-Aspire-R5-471T:~$ git clone [https://github.com/jeremyb31/ath10k-firmware.git](https://github.com/jeremyb31/ath10k-firmware.git)
fatal: destination path 'ath10k-firmware' already exists and is not an empty directory.

um@um-Aspire-R5-471T:~$ sudo cp ath10k-firmware/ /lib/firmware/ath10k/
cp: omitting directory 'ath10k-firmware/'

I am not sure how to use your link?

I assume the wifi doesn't work, because clicking on the network icon the entry "Wi-Fi Networks" is greyed out.

---

### Post by jeremy31 on 2016-05-08
I forgot to delete the existing directory, just post results for ```
lspci -nnk | grep -iA2 net; dmesg | ath10k
```.  You probably just need to rename a firmware file you already have

---

### Post by uli9 on 2016-05-08
um@um-Aspire-R5-471T:~$ lspci -nnk | grep -iA2 net; dmesg | ath10k
01:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Foxconn International, Inc. QCA6174 802.11ac Wireless Network Adapter [105b:e09d]
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci
ath10k: command not found

---

### Post by jeremy31 on 2016-05-08
Sorry ```
dmesg | grep ath10k
```

I hope these firmware files get added to Ubuntu's linux-firmware package soon.  Kalle Valo just submitted them upstream 5 days ago

---

### Post by uli9 on 2016-05-08
um@um-Aspire-R5-471T:~$ dmesg | grep ath10k
[    3.326586] ath10k_pci 0000:01:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    3.573037] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    3.573405] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    3.573408] ath10k_pci 0000:01:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    3.638157] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-2.bin failed with error -2
[    5.791477] ath10k_pci 0000:01:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 105b:e09d) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[    5.791481] ath10k_pci 0000:01:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    5.876611] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
[   11.138918] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   17.139054] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   22.467150] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   28.467263] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   33.775354] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   39.775477] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   55.247573] ath10k_pci 0000:01:00.0: failed to set rx-chainmask: -11, req 0x3
[   58.247800] ath10k_pci 0000:01:00.0: failed to set arp ac override parameter: -11
[   64.247925] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   69.556093] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   75.556191] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   90.123824] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   96.107489] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  101.413381] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  107.410086] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  123.096529] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  129.097245] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  134.409711] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  140.410257] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  156.099289] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  162.099601] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  167.407879] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  173.408144] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  189.100474] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  195.100597] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  200.412741] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  206.412921] ath10k_pci 0000:01:00.0: could not suspend target (-11)

---

### Post by jeremy31 on 2016-05-08
The -11 errors are usually caused by board.bin files but you seem to be missing a board-2.bin that Kalle added 2 months ago
```
cd /lib/firmware/ath10k/QCA6174/hw3.0
sudo wget https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/board-2.bin
```

Reboot

---

### Post by uli9 on 2016-05-08
I did that. Now:

um@um-Aspire-R5-471T:~$ dmesg | grep ath10k
[    3.404774] ath10k_pci 0000:01:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    3.652953] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    3.653157] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    3.653160] ath10k_pci 0000:01:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    3.718112] ath10k_pci 0000:01:00.0: found invalid board magic
[    5.873676] ath10k_pci 0000:01:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 105b:e09d) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[    5.873679] ath10k_pci 0000:01:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    8.870550] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[    8.945862] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
[   14.242625] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   20.242681] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   25.722794] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   31.722942] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   37.035123] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   43.035202] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   58.251419] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   64.251486] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   69.559513] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   75.559614] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   91.258626] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   97.258494] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  102.566231] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  108.566380] ath10k_pci 0000:01:00.0: could not suspend target (-11)



During the install I could not install the 3rd party software (did not have ethernet and UEFI, secure boot, no supervisor password issues etc.). Anyways, I might be missing some proprietary packages?

---

### Post by jeremy31 on 2016-05-08
This might be the one odd one
```
sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/board.bin /lib/firmware/ath10k/QCA6174/hw3.0/board.bin.bak
sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/board-2.bin /lib/firmware/ath10k/QCA6174/hw3.0/board.bin
```

reboot

There are no proprietary packages for Qualcomm devices as they are nice enough to help create open source modules that are in the kernel

---

### Post by uli9 on 2016-05-08
I did that. Now there is no wireless networks entry when I click on the network symbol.

um@um-Aspire-R5-471T:~$ dmesg | grep ath10k
[    3.417024] ath10k_pci 0000:01:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    3.657434] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    3.657630] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    3.657632] ath10k_pci 0000:01:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    3.722223] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-2.bin failed with error -2
[    5.890698] ath10k_pci 0000:01:00.0: firmware crashed! (uuid 5ce5c952-d597-4358-8fcf-4e4c3950935c)
[    5.890710] ath10k_pci 0000:01:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 105b:e09d) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[    5.890713] ath10k_pci 0000:01:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    5.892729] ath10k_pci 0000:01:00.0: firmware register dump:
[    5.892732] ath10k_pci 0000:01:00.0: [00]: 0x05030000 0x00000000 0x809FE363 0x00032E30
[    5.892734] ath10k_pci 0000:01:00.0: [04]: 0x809FE363 0x0040E6C8 0x00032E30 0x20302030
[    5.892735] ath10k_pci 0000:01:00.0: [08]: 0x00000002 0x00000002 0x00407CC8 0x00407E84
[    5.892737] ath10k_pci 0000:01:00.0: [12]: 0x000007FF 0x0040E738 0x000197FF 0x00408484
[    5.892739] ath10k_pci 0000:01:00.0: [16]: 0x00023FFF 0x00000E00 0x0041F400 0x00407E84
[    5.892758] ath10k_pci 0000:01:00.0: [20]: 0x809CF15E 0x0040E708 0x000FFFFF 0x00000000
[    5.892760] ath10k_pci 0000:01:00.0: [24]: 0x00000006 0x00000006 0x00403CCC 0x0001A2C4
[    5.892761] ath10k_pci 0000:01:00.0: [28]: 0x80A05C2B 0x0040E6E8 0x00032E30 0x20302030
[    5.892763] ath10k_pci 0000:01:00.0: [32]: 0x00000002 0x00000003 0x00403CE4 0x0000000D
[    5.892765] ath10k_pci 0000:01:00.0: [36]: 0x00000000 0x00000000 0x00000000 0x00000000
[    5.892768] ath10k_pci 0000:01:00.0: [40]: 0x00000000 0x00000000 0x00000000 0x00000000
[    5.892770] ath10k_pci 0000:01:00.0: [44]: 0x00000000 0x00000000 0x00000000 0x00000000
[    5.892771] ath10k_pci 0000:01:00.0: [48]: 0x00000000 0x00000000 0x00000000 0x00000000
[    5.892773] ath10k_pci 0000:01:00.0: [52]: 0x00000000 0x00000000 0x00000000 0x00000000
[    5.892788] ath10k_pci 0000:01:00.0: [56]: 0x00000000 0x00000000 0x00000000 0x00000000
[   10.875541] ath10k_pci 0000:01:00.0: wmi unified ready event not received
[   10.918017] ath10k_pci 0000:01:00.0: device has crashed during init
[   10.942403] ath10k_pci 0000:01:00.0: device has crashed during init
[   10.942406] ath10k_pci 0000:01:00.0: failed to wait for target init: -70
[   10.943058] ath10k_pci 0000:01:00.0: could not init core (-110)
[   10.943099] ath10k_pci 0000:01:00.0: could not probe fw (-110)
[   10.951528] ath10k_pci 0000:01:00.0: cannot restart a device that hasn't been started

---

### Post by jeremy31 on 2016-05-08
```
sudo rm /lib/firmware/ath10k/QCA6174/hw3.0/*

sudo wget -O /lib/firmware/ath10k/QCA6174/hw3.0/board.bin https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/board.bin?raw=true

sudo wget -O /lib/firmware/ath10k/QCA6174/hw3.0/board-2.bin https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/board-2.bin?raw=true

sudo wget -O /lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1?raw=true
```

This should make sure the latest versions are there and see if there are any results for ```
cat /etc/modprobe.d/ath10k_core.conf
```

---

### Post by uli9 on 2016-05-08
It looks like not:

um@um-Aspire-R5-471T:~$ cat /etc/modprobe.d/ath10k_core.conf
cat: /etc/modprobe.d/ath10k_core.conf: No such file or directory

---

### Post by uli9 on 2016-05-08
um@um-Aspire-R5-471T:/etc/modprobe.d$ ls -a
.   alsa-base.conf          blacklist.conf           blacklist-framebuffer.conf  blacklist-oss.conf           blacklist-watchdog.conf  intel-microcode-blacklist.conf  mlx4.conf
..  blacklist-ath_pci.conf  blacklist-firewire.conf  blacklist-modem.conf        blacklist-rare-network.conf  fbdev-blacklist.conf     iwlwifi.conf                    vmwgfx-fbdev.conf

---

### Post by jeremy31 on 2016-05-08
Forgot to say reboot.  I don't know if the ath10k_core.conf could actually cause any issue as the ignore_otp must be set in the firmware now, it used to have to be set manually

---

### Post by uli9 on 2016-05-08
Yes Sir! It works! So what did we actually do?

---

### Post by jeremy31 on 2016-05-08
We basically replaced some older files you had with the latest from kvalo's github site.  I imagine you had 15.10 before and just updated?

Since it work, please use the forums tools menu at the top of the page to mark as solved

---

### Post by uli9 on 2016-05-08
Thank you for your help jeremy31!

---

### Post by sonicking on 2017-04-01
Hi, I just came across this thread and I have experienced similar issue (same wireless device and same machine).  I also had tried to install driver, but the result is not too satisfying.  <br>
<br>
If I want to try&nbsp;<strong>jeremy31</strong>'s file, what exactly are the steps I need to take? &nbsp;I am a novice and please be clear in your explanation. &nbsp;Thanks in advance!

---

### Post by jeremy31 on 2017-04-01
Now they work the best they can with the module in the kernel and the firmware in the package linux-firmware.  Sometimes they don't work at all with older wireless routers

---

### Post by sonicking on 2017-04-01
Can I at least try it?   Do I just follow post#12 (and make sure the Ethernet cable is connected)?

---

### Post by jeremy31 on 2017-04-01
Or with an ethernet connection do ```
sudo apt-get install linux-firmware
```
It is the same or newer firmware from the same person as Kalle Valo also commits the firmware to linux-firmware

---

### Post by sonicking on 2017-04-01
Do I need to remove anything beforehand?

---

### Post by jeremy31 on 2017-04-01
It should replace the files when installed but you could remove the ath10k directory before installing by ```
sudo rm -r /lib/firmware/ath10k/
```
Then run the command to reinstall linux-firmware

---

### Post by Stazzy on 2017-05-20
Hallelujah! 

I have a brand new Acer Aspire S13 (S5-371T), and I'm fighting with the Linux Mint 18 (Sarah).
The wifi was the second problem after I made the Windows 10 [dualboot work]("https://askubuntu.com/a/630662"). This laptop doesn't have any place for ethernet cable, so luckily I have another computer to use too. 

Jeremy's [solution in msg #12]("https://ubuntuforums.org/showthread.php?t=2323812&page=2&p=13485882#post13485882") worked for me. 

I downloaded those three files on Jeremy's links on an USB pen drive. 
Then I opened /lib/firmware/ath10k/QCA6174/hw3.0 as administrator (right click, no command line this time for me). I copied the files from the pen drive to the hw3.0 folder.
Reboot. Worked. 

Thank you.

---

### Post by Nattydread69 on 2017-10-12
[QUOTE=jeremy31;13485869]This might be the one odd one
```
sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/board.bin /lib/firmware/ath10k/QCA6174/hw3.0/board.bin.bak
sudo mv /lib/firmware/ath10k/QCA6174/hw3.0/board-2.bin /lib/firmware/ath10k/QCA6174/hw3.0/board.bin
```


I can confirm this procedure of copying the firmware and this rename of board-2.bin fixes the wireless issues on the Samsung galaxy book 12 (SM-W720NZKBXAR).

Thanks so much!

---

### Post by technerd88 on 2018-01-24
Did you get your sound working? I cant seem to figure mine out quite yet. I love ubuntu on this galaxy book 12. Its WAY faster than windows. I just need to get LTE working and brightness controls and sound.

---

### Post by wildmanne39 on 2018-01-24
Hi technerd88, this thread is about a wireless issue if you need help with a sound issue please start your own thread so you can get the help you need and this thread can stay on topic. It is always best to start your own thread even if you have the same issue.

---

### Post by jrec on 2018-01-27
> **jeremy31 said:**
> Try it from my git
```
sudo apt-get install git
git clone https://github.com/jeremyb31/ath10k-firmware.git
sudo cp ath10k-firmware/ /lib/firmware/ath10k/
```

Reboot, if it still doesn't work, see the wireless script link in my signature and use code tags when posting the results from the script


Hi, I just try to clone repository but it is not found ((
I have the same problem on my laptop ( lenovo legion y520)

When I connect my iPhone to laptop I can use Internet. Also I can use LAN but not WiFi

lspci:

03:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)

inxi -Fxz:

Network:   Card-1: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter driver: ath10k_pci bus-ID: 03:00.0
           IF: wlp3s0 state: down mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 3000 bus-ID: 04:00.0
           IF: enp4s0 state: down mac: <filter>
           Card-3: Atheros usb-ID: 001-005
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A


iwconfig: 
lo        no wireless extensions.

enp4s0    no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
enp0s20f0u2c4i2  no wireless extensions.

---

### Post by jrec on 2018-01-27
I've solved my problem.

[https://askubuntu.com/questions/893384/wifi-doesnt-work-on-fresh-ubuntu-16-04](https://askubuntu.com/questions/893384/wifi-doesnt-work-on-fresh-ubuntu-16-04)

 Run in a terminal

  sudo tee /etc/modprobe.d/blacklist-ideapad.conf <<< "blacklist ideapad_laptop"
  and rebooted. This unblocked my Wi-Fi.

---

### Post by ashu2 on 2018-05-22
**I will advise - just don't do this.** I screwed up my Dell XPS 15-950 Wifi adaptor following the above steps. It doesn't have the LAN ports. There seems to be no easy way to get the wifi adaptor back now.

---

### Post by HankB on 2018-06-21
> **ashu2 said:**
> **I will advise - just don't do this.** I screwed up my Dell XPS 15-950 Wifi adaptor following the above steps. It doesn't have the LAN ports. There seems to be no easy way to get the wifi adaptor back now.

There are a lot of instructions in this thread. It would be really helpful if you quoted the instructions that "screwed up my Dell XPS 15-950 Wifi adaptor." It would also be helpful to fix the model designation. 9560? 9570? Other?

---

### Post by jeremy31 on 2018-06-21
> **HankB said:**
> There are a lot of instructions in this thread. It would be really helpful if you quoted the instructions that "screwed up my Dell XPS 15-950 Wifi adaptor." It would also be helpful to fix the model designation. 9560? 9570? Other?

I would say that downloading firmware from github now might be a waste of time

---

### Post by HankB on 2018-06-22
> **jeremy31 said:**
> I would say that downloading firmware from github now might be a waste of time

Can you recommend a place to get better firmware? 

FWIW I'm presently running Debian Buster (testing) upgraded from Debian Stretch (stable.) This WiFi chip did not work with Stretch but seems to work with Buster out of the box. (I have experienced at least one drop that was fixed by stopping and restarting WiFi using NetworkManager.)

If things go according to plan I should be able to test with 10.04 LTS as well.

thanks,
hank

---

### Post by jeremy31 on 2018-06-22
Ubuntu 10.04 has been unsupported for some time now.  The preferred place for firmware would be [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/ath10k](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/ath10k)
These also need newer kernels, 4.2 or 4.4 would be minimum depending on what Atheros card

---

### Post by HankB on 2018-06-22
Doh! I meant to type "18.04" 

Thanks for the further information. The card I'm using identifies as
```
hbarta@rocinante:~$ lspci|grep Atheros
02:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
hbarta@rocinante:~$
```

Windows identifies it as a Killer <something or other>

Should I be looking for information on getting Killer WiFi working?

Thanks!

---

