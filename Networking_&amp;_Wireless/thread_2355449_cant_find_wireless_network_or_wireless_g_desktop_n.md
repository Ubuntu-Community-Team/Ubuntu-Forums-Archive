---
title: "cant find wireless network or wireless g desktop network card after update"
date: 2017-03-12
forum: Networking &amp; Wireless
---

### Post by Ka Fish on 2017-03-12
I was using [https://ubuntuforums.org/showthread.php?t=2306677&p=13408172#post13408172](https://ubuntuforums.org/showthread.php?t=2306677&p=13408172#post13408172). Last week an update made the wifi disappear again & it gave me this.
```
ka@ka-desktop:~$ sudo apt-get update
[sudo] password for ka: 
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:5 http://security.ubuntu.com/ubuntu xenial-security/main i386 DEP-11 Metadata [54.5 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [42.4 kB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/universe i386 DEP-11 Metadata [32.1 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [479 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 DEP-11 Metadata [289 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [185 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [424 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 DEP-11 Metadata [150 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [175 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 DEP-11 Metadata [2,520 B]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-backports/main i386 DEP-11 Metadata [3,324 B]
Fetched 2,181 kB in 3s (665 kB/s)                                           
Reading package lists... Done
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
ka@ka-desktop:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 7,171 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 263372 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu1~1.1) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu1~1.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
ka@ka-desktop:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version (1:019-2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
ka@ka-desktop:~$ sudo modprobe b43
ka@ka-desktop:~$ lspci -nnk | grep 0280 -A2
ka@ka-desktop:~$ rfkill list all
ka@ka-desktop:~$ sudo modprobe b43
ka@ka-desktop:~$ echo "b43" | sudo tee -a /etc/modules
b43
ka@ka-desktop:~$ ls /etc/modprobe.d/
alsa-base.conf                  blacklist-rare-network.conf
amd64-microcode-blacklist.conf  blacklist-watchdog.conf
blacklist-ath_pci.conf          dkms.conf
blacklist.conf                  fbdev-blacklist.conf
blacklist-firewire.conf         iwlwifi.conf
blacklist-framebuffer.conf      mlx4.conf
blacklist-modem.conf            vmwgfx-fbdev.conf
blacklist-oss.conf
ka@ka-desktop:~$ sudo rm /etc/modprobe.d/broadcom-sta-*.conf
rm: cannot remove '/etc/modprobe.d/broadcom-sta-*.conf': No such file or directory
ka@ka-desktop:~$ 
```
Why did this not work & how do I get wifi back?

---

### Post by wildmanne39 on 2017-03-12
Click on the wireless script in my signature and follow the directions for running it and posting the link to the file it creates here.

---

### Post by Ka Fish on 2017-03-13
ka@ka-desktop:~$ ```
sudo apt-get update[sudo] password for ka: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Fetched 306 kB in 2s (137 kB/s)                                                
Reading package lists... Done
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
ka@ka-desktop:~$ sudo apt dist-upgrade[sudo] password for ka: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
ka@ka-desktop:~$ sudo apt install pastebinitReading package lists... Done
Building dependency tree       
Reading state information... Done
pastebinit is already the newest version (1.5-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
ka@ka-desktop:~$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && chmod +x wireless-info && ./wireless-info
--2017-03-13 15:24:26--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 192.30.253.113, 192.30.253.112
Connecting to github.com (github.com)|192.30.253.113|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2017-03-13 15:24:27--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.32.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.32.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16156 (16K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[===================>]  15.78K  --.-KB/s    in 0.02s   

Last-modified header missing -- time-stamps turned off.
2017-03-13 15:24:27 (665 KB/s) - ‘wireless-info’ saved [16156/16156]


Results saved in "/home/ka/wireless-info.txt".

Results also archived in "/home/ka/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

Do you also want to post them to your default 'pastebinit' provider? [Y/n]: y

Pastebin successful:
```

[http://paste.ubuntu.com/24172272/](http://paste.ubuntu.com/24172272/)

ka@ka-desktop:~$

---

### Post by chili555 on 2017-03-13
It appears that your wireless is back:> wlan0     IEEE 802.11bg  ESSID:"59FYQ"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC '59FYQ' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:58   Missed beacon:0
We do see a few problems that you could address.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by Ka Fish on 2017-03-13
The I.S.P. is Verizon. The security is set to WPA & WPA2 Personal. I can't find the password to get into it. Can't change anything.
```
ka@ka-desktop:~$ sudo iw reg get
[sudo] password for ka: 
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)
ka@ka-desktop:~$ 
```

---

### Post by chili555 on 2017-03-13
>  I can't find the password to get into it. Can't change anything.Did you Google the make and model of the router and try the default password? By the way, leaving your router or other internet appliance set to the default password is a security vulnerability for exactly that reason; the passwords are easily discoverable using no more than Google. If you get in, change the user name and password immediately.> ka@ka-desktop:~$ sudo iw reg get
[sudo] password for ka: 
country 00: DFS-UNSETDid you go ahead and change it as I suggested? 

To your original question, your readings show that your wireless is working and connected. Isn't the wireless working as expected?

---

### Post by Ka Fish on 2017-03-13
I have looked several places including google & bing. None have worked yet. I'm still working on your suggestion. I have little experience in the command prompt. I believe it was Wildmanne39's wireless script link that corrected this issue.

---

### Post by kurt18947 on 2017-03-14
How old is your Verizon router? FiOS? Fios routers have shipped with stickers detailing default router passwords, wifi passwords etc. for some years now. Pushing the reset button will restore to the defaults on the sticker but are specific to each router.

---

### Post by chili555 on 2017-03-14
> I have looked several places including google & bing. None have worked yet. I'm afraid that I don't quite understand. Do you mean that you've searched Google and Bing for a solution and haven't found it? Or do you mean that, although the wireless appears to be connected, you cannot reach either Google or Bing?

Please tell us more.Most of all, tell us if your wireless is now working as expected.

---

### Post by Ka Fish on 2017-03-14
The router is about 2yrs old. It's not fois. The password I can't find is for admin log in to make changes in the router. The wireless is now working. Sorry for the confusion.

---

### Post by chili555 on 2017-03-14
> The wireless is now working.Awesome! Glad it's working.

Please use thread tools at the top of the forum to mark Solved.

---

### Post by Ka Fish on 2017-03-17
It was working fine till this morning when this box popped up, > Failed to add/activate connection (7) The access point /org/freedesktop/NetworkManager/AccessPoint/13 was not in the scan list.

---

### Post by chili555 on 2017-03-17
That may mean that the router is off line. Do other devices see it? Have you tried rebooting the router by unplugging and replugging it?

---

### Post by Ka Fish on 2017-03-17
My tower & the router have been reset, no change. My wife's laptop occasionally resets wifi connection for no apparent reason. All other wifi devices are working. Wifi network option was greyed out erlier, now it's gone.

---

### Post by chili555 on 2017-03-18
Does the wireless still scan?```
sudo iwlist wlan0 scan
```If it does, does it see your own network? If it does not, what are the error or warning messages?

---

### Post by Ka Fish on 2017-03-18
```
ka@ka-desktop:~$ sudo iwlist wlan0 scan
[sudo] password for ka: 
wlan0     Interface doesn't support scanning : Device or resource busy

ka@ka-desktop:~$
```
The wi-fi network in the ethernet pull down tab is back again but it's greyed out.

---

### Post by chili555 on 2017-03-19
Let's see if the logs can tell us why the device or resource is busy. Please run and post:```
rfkill list all
dmesg | grep -e wlan -e b43 | tail -n 10
```

---

### Post by Ka Fish on 2017-03-19
The wi-fi appears to be on today. My download speed is only 2.91 Mbps. The next time it acts up it will tell me a different reason. At least this is what has been doing for the last 2 months. ```
ka@ka-desktop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ka@ka-desktop:~$ dmesg | grep -e wlan -e b43 | tail -n 10
```

---

### Post by chili555 on 2017-03-20
> ka@ka-desktop:~$ dmesg | grep -e wlan -e b43 | tail -n 10No output? I thought that your wireless driver was b43 and your interface was wlan0. No? Please try again.

---

### Post by Ka Fish on 2017-04-01
The wi-fi has been off & on all week. Long story short 2 days ago it went out & nothing I've tried has gotten it back on. This is a different result from today.  ```
ka@ka-desktop:~$ dmesg | grep -e wlan -e b43 | tail -n 10
[    2.289921] b43-pci-bridge 0000:00:0a.0: enabling device (0004 -> 0006)
[    9.602627] b43-phy0: Broadcom 4304 WLAN found (core revision 5)
[    9.612013] b43-phy0: Found PHY: Analog 2, Type 2 (G), Revision 0
[    9.612034] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[    9.624032] b43-phy0 ERROR: Failed to validate the chipaccess

```

---

### Post by chili555 on 2017-04-02
> b43-phy0 ERROR: Failed to validate the chipaccessThis fascinating error appears on the internet but twice; your post here and this: [https://forum.salixos.org/viewtopic.php?p=37720&sid=61eac0d2a2f889270e07dbdefe4eb352](https://forum.salixos.org/viewtopic.php?p=37720&sid=61eac0d2a2f889270e07dbdefe4eb352)

In the link I found, it was solved by the method of blacklisting part of the driver suite that drives your device. In fact, your device needs the drivers b43, ssb, bcma, mac80211 and cfg80211 *PLUS* firmware! Whew! That's a lot of code that all has to go together perfectly to get wireless to work.

I suppose that the key may be that by blacklisting b43, we delay it's inclusion until ssb and bcma load and pull it in as a dependency notwithstanding the blacklist. The only way we'll know if it will work is, of course, to try it. From the terminal:```
sudo -i
echo "blacklist b43"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us hear your report, especially:```
dmesg | grep -e b43 -e ssb
```

---

### Post by Ka Fish on 2017-04-02
The wi-fi option showed up but was greyed out before the reboot. It's not there now. ```
ka@ka-desktop:~$ dmesg | grep -e b43 -e ssb
[    2.275856] b43-pci-bridge 0000:00:0a.0: enabling device (0004 -> 0006)
[    2.288131] ssb: Found chip with id 0x4304, rev 0x03 and package 0x00
[    2.288140] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    2.288145] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    2.288150] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x00, vendor 0x4243)
[    2.288154] ssb: Core 3 found: V90 (cc 0x807, rev 0x00, vendor 0x4243)
[    2.288158] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    2.291572] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0a.0
```

---

### Post by chili555 on 2017-04-02
> **Ka Fish said:**
> The wi-fi option showed up but was greyed out before the reboot. It's not there now. ```
ka@ka-desktop:~$ dmesg | grep -e b43 -e ssb
[    2.275856] b43-pci-bridge 0000:00:0a.0: enabling device (0004 -> 0006)
[    2.288131] ssb: Found chip with id 0x4304, rev 0x03 and package 0x00
[    2.288140] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    2.288145] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    2.288150] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x00, vendor 0x4243)
[    2.288154] ssb: Core 3 found: V90 (cc 0x807, rev 0x00, vendor 0x4243)
[    2.288158] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    2.291572] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0a.0
```Did b43 ultimately load?```
lsmod | grep b43
```Is there any change if you load it manually?```
sudo modprobe b43
dmesg | grep b43
```

---

### Post by Ka Fish on 2017-04-02
I believe the greyed out wi-fi option showed up as a result of ```
echo "blacklist b43"  >>  /etc/modprobe.d/blacklist.conf
``` It appears to be up & running again. ```
ka@ka-desktop:~$ lsmod | grep b43
ka@ka-desktop:~$ sudo modprobe b43
[sudo] password for ka: 
ka@ka-desktop:~$ dmesg | grep b43
[    2.275856] b43-pci-bridge 0000:00:0a.0: enabling device (0004 -> 0006)
[23792.818979] b43-phy0: Broadcom 4304 WLAN found (core revision 5)
[23792.828039] b43-phy0: Found PHY: Analog 2, Type 2 (G), Revision 2
[23792.828063] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[23796.100482] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
ka@ka-desktop:~$ 
``` Hopefully it stays this time. Thanks for your help.

---

### Post by chili555 on 2017-04-03
It appears that the trick of letting ssb, bcma and the other dependencies load in advance and then loading b43 later has been successful. I learn something new every day.

Let's try to automate the process. I suggest that you leave the blacklist in place and then, after a short pause, load b43. Please do:```
sudo gedit /etc/rc.local
```Use nano or kate or leafpad if you don't have the text editor gedit. Currently, the file should read:```
#!/bin/sh -e

exit 0

```...although it may have some explanatory comments:```
#comments
#blah blah

#!/bin/sh -e

exit 0

```Add two lines to the file:```
#!/bin/sh -e

sleep 2
modprobe b43

exit 0

```Proofread carefully, save and close the text editor. Now, we hope that your wireless starts correctly.

---

### Post by Ka Fish on 2017-04-03
A program called rc.local popped up with ```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
``` Do I put the code in like this? ```
#!/bin/sh -e
#sleep 2
#modprobe b43
# rc.local
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```

---

### Post by chili555 on 2017-04-03
> Do I put the code in like this?
```
#!/bin/sh -e
#sleep 2
#modprobe b43
# rc.local
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```No. Like this, please:```

#!/bin/sh -e
# rc.local
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sleep 2
modprobe b43

exit 0
```

---

