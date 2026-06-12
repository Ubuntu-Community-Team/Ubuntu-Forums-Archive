---
title: "No wifi"
date: 2017-06-29
forum: Networking &amp; Wireless
---

### Post by vasa1 on 2017-06-29
Wifi was working till a couple of days ago. Then my ISP was down. I logged in today and saw a kernel update (and other updates) which I installed. A reboot was suggested. After the reboot, no wifi.

The machine in question is a Dell laptop on which I installed various DEs and deleted a lot of stuff so it's a bit of a mish-mash. It came with Ubuntu 16.04 pre-installed but then I added lubuntu-desktop and kubuntu-desktop.

I'm providing some information below which I hope will let people help solve this issue. (I got the necessary information and am posting from another laptop which is working fine after the same kernel updates).

```
$ inxi -F
System:    Host: aes-3567 Kernel: 4.4.0-83-generic x86_64 (64 bit) Desktop: KDE Plasma 5.8.7
           Distro: Ubuntu 16.04 xenial
Machine:   System: Dell (portable) product: Inspiron 15-3567
           Mobo: Dell model: 0FGN4M v: A00 Bios: Dell v: 01.00.00 date: 09/12/2016
CPU:       Dual core Intel Core i3-6006U (-MCP-) cache: 3072 KB 
           clock speeds: max: 2000 MHz 1: 992 MHz 2: 865 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: radeon,amdgpu) Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 520 (Skylake GT2) GLX Version: 3.0 Mesa 12.0.6
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel Sound: ALSA v: k4.4.0-83-generic
Network:   Card-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter driver: ath9k
           IF: wlp1s0 state: up mac: 28:56:5a:42:3a:89
           Card-2: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller driver: r8169
           IF: enp2s0 state: down mac: 98:40:bb:26:89:7b
           Card-3: Atheros
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 1004.2GB (1.8% used) ID-1: /dev/sda model: TOSHIBA_MQ01ABD1 size: 1000.2GB
           ID-2: USB /dev/sdb model: Transcend_4GB size: 4.0GB
Partition: ID-1: / size: 906G used: 9.6G (2%) fs: ext4 dev: /dev/sda3
           ID-2: swap-1 size: 8.31GB used: 0.00GB (0%) fs: swap dev: /dev/sda4
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 40.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 188 Uptime: 34 min Memory: 1046.0/7852.3MB Client: Shell (bash) inxi: 2.2.35 
$ 
```

```
$ inxi -Nn
Network:   Card-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter driver: ath9k
           IF: wlp1s0 state: down mac: 28:56:5a:42:3a:89
           Card-2: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller driver: r8169
           IF: enp2s0 state: down mac: 98:40:bb:26:89:7b
           Card-3: Atheros
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
$
```
and a pastebin link to the wireless-info script posted in the Network sticky: [http://paste.ubuntu.com/24978203/](http://paste.ubuntu.com/24978203/)

I suppose I could do a clean re-install but I'd rather not: I suspect I'd lose some of the Dell stuff.

---

### Post by jeremy31 on 2017-06-29
See if chili555's ideas help [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
The script results show you are using TKIP encryption and haven't set your country code
The following error is showing in dmesg and I haven't seen it before
```
ath: phy0: Unknown AMPDU action 
```

---

### Post by vasa1 on 2017-06-29
Thanks, jeremy31. I'll try chili555's ideas and get back here.

I didn't do anything to use or not use TKIP encryption and I don't know where to set the country code except when choosing the time zone in the Ubiquity screen during installation.

---

### Post by jeremy31 on 2017-06-30
The kernel changelog shows some changes to IPv6 so I would definitely edit the connection settings in Network Manager to disable/ignore IPv6

---

### Post by vasa1 on 2017-06-30
> **jeremy31 said:**
> The kernel changelog shows some changes to IPv6 so I would definitely edit the connection settings in Network Manager to disable/ignore IPv6

I made those changes, including the IPv6 one, except for the router encryption. Still no wifi. I tested with a Kubuntu 16.04 iso. Got wifi. Now, I've installed Kubuntu 16.04 alongside the existing Ubuntu+Lubuntu+Kubuntu mix-up and the wifi is working fine without any need to change any settings. It's working even after a full apt-get dist-upgrade.

I'm veering round to thinking that I deleted something essential which basically broke the wifi in the previous distro.

I could possibly try an ethernet connection but that would require me to visit my ISP because I can have either wifi or ethernet but each time I want to switch I need to visit the ISP office. I prefer wifi because I can easily use my cell phone to access the internet.

Just for comparison, this is the wireless-info with the new system, same machine: [http://paste.ubuntu.com/24989098/](http://paste.ubuntu.com/24989098/)

---

### Post by kc1di on 2017-06-30
What does ```
rfkill list
``` show?

---

### Post by vasa1 on 2017-06-30
> **kc1di said:**
> What does ```
rfkill list
``` show?

```

0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

```is what I see when I rebooted into the distro without wifi.

---

### Post by Hadaka on 2017-06-30
Hi To set your country code..please Copy and paste..
```
sudo iw reg set IN
sudo sed -i 's/=.*/=IN/' /etc/default/crda
```








@kc1di....vasa1 posted his wireless script on post #1
: [URL="http://paste.ubuntu.com/24978203/"]http://paste.ubuntu.com/24978203/




[/URL]

---

### Post by vasa1 on 2017-06-30
@Hadaka, I've set my country default. But it didn't make any difference. BTW, on the laptop I'm currently using successfully with wifi from the same router has```
REGDOMAIN=
```

---

### Post by kc1di on 2017-06-30
Sorry Hadaka  missed that on first post :(

---

### Post by jeremy31 on 2017-06-30
Not sure what happened with that kernel update vasa1 but I installed the same kernel, enabled IPv6 and TKIP and had no issues with my wireless.  It isn't the same chipset but uses the same ath and ath9k modules.  Hopefully it is a small issue as I know there are other users with the same chipset as yours using Linux.  The wireless works with 4.8 and doesn't have the error I noted from the 4.4.0-83 kernel.  I am sure you are aware that the 4.8 kernel will be EOL by August.  If I see someone else with the issue, I will have them file a bug report

---

### Post by vasa1 on 2017-07-06
> **jeremy31 said:**
> Not sure what happened with that kernel update vasa1 but I installed the same kernel, enabled IPv6 and TKIP and had no issues with my wireless.  It isn't the same chipset but uses the same ath and ath9k modules.  Hopefully it is a small issue as I know there are other users with the same chipset as yours using Linux.  The wireless works with 4.8 and doesn't have the error I noted from the 4.4.0-83 kernel.  I am sure you are aware that the 4.8 kernel will be EOL by August.  If I see someone else with the issue, I will have them file a bug report

@jeremy31, thank you for that hint! I booted into an older kernel and wifi is back without my having to do anything about IPv6 or TKIP!

```
4.4.0-81-generic
``` is what *uname -r* shows.

For the record, I ran the wireless script again from the working set-up.

[http://paste.ubuntu.com/25029924/](http://paste.ubuntu.com/25029924/)

I'll try to boot once again with the latest kernel, the one with which I **didn't** get wifi and post back later because, even though there hasn't been any update from 4.4.0.81 (apparently), there were some other updates that may have helped.

If that kernel still doesn't work staying on an older kernel isn't good. In that case, I'll use the other pure Kubuntu distro which has the 4.8 kernel. I understand that with 16.04, there'll be rolling updates so I won't be stuck with 4.8 unsupported.

One other possibility is to upgrade my present kernel to 4.8 by whatever is the required procedure. What do you think?

---

### Post by jeremy31 on 2017-07-06
You could update to 4.8 by installing package linux-generic-hwe-16.04 but it would be nice to have a bug report filed as there have been others with wireless issues with this kernel.

---

### Post by johndough2 on 2017-07-06
Hi

While I don't have an answer, I will mention something that may make a difference...

[https://askubuntu.com/questions/167603/how-do-i-install-the-firmware-on-ubuntu-12-04#489437](https://askubuntu.com/questions/167603/how-do-i-install-the-firmware-on-ubuntu-12-04#489437)

First enable non-free debian packages by editing /etc/apt/sources.list and adding contrib and non-free to the line

deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main

so it becomes

deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free

############

I forgot to do this with Debian 9, assumed all packages would be fulfilled, they weren't.

Reading thru you pastebin, the following look odd...

wlp1s0    IEEE 802.11bgn  ESSID:off/any
wlp1s0    13 channels in total; available frequencies : (usually there is a frequency selected or shown as in use) like this
enp0s10   14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
       
          Channel 14 : 2.484 GHz
          Current Channel:0

So my guess is the WiFi is running, the WiFi card is working and there is no matching config.

Like the SSID to connect to, the passphrase or similar (even the gateway and DNS) details are missing.

---

### Post by vasa1 on 2017-07-06
> **jeremy31 said:**
> You could update to 4.8 by installing package linux-generic-hwe-16.04 but it would be nice to have a bug report filed as there have been others with wireless issues with this kernel.
True! But how could I possibly do that? If I log into that kernel, I won't have connectivity. I can't switch to ethernet. My ISP's allows wifi or ethernet. I have to go to their office and fill up a form asking to switch :(

---

### Post by jeremy31 on 2017-07-06
I was thinking you could save the info gathered, yes [https://help.ubuntu.com/community/ReportingBugs#Filing_bugs_when_offline_or_using_a_headless_setup](https://help.ubuntu.com/community/ReportingBugs#Filing_bugs_when_offline_or_using_a_headless_setup)
Then you can upload the apport info using a kernel that works

---

### Post by vasa1 on 2017-07-06
> **jeremy31 said:**
> I was thinking you could save the info gathered, yes [https://help.ubuntu.com/community/ReportingBugs#Filing_bugs_when_offline_or_using_a_headless_setup](https://help.ubuntu.com/community/ReportingBugs#Filing_bugs_when_offline_or_using_a_headless_setup)
Then you can upload the apport info using a kernel that worksI guess I could try that. What would be appropriate for "package name" in ```
apport-cli -f -p <package name> --save bug.apport
```?

---

### Post by jeremy31 on 2017-07-06
I would use linux for package name as it is likely a kernel issue

---

### Post by vasa1 on 2017-07-06
Okay, I'll start trying!

Please check back in an hour or so. Thanks!

---

### Post by vasa1 on 2017-07-06
I filed it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1702685](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1702685)

@jeremy31, Please take a look. Thanks!

---

### Post by jeremy31 on 2017-07-06
This is strange, from dmesg in bug report
```
  33.368800] audit: type=1400 audit(1499345285.806:39): apparmor="DENIED" operation="open" profile="/sbin/dhclient" name="/etc/ld.so.preload" pid=1377 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   33.390146] ath: phy0: Unknown AMPDU action
[   33.466780] audit: type=1400 audit(1499345285.906:40): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/etc/ld.so.preload" pid=1378 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
```

---

### Post by vasa1 on 2017-07-06
I haven't done anything to Apparmor. So whatever that message shows seems to be set by the system :)

---

### Post by jeremy31 on 2017-07-06
Does it show the Denied message in a kernel where wifi works?
I am keeping this short as my phone gets me logged out often

---

### Post by vasa1 on 2017-07-06
> **jeremy31 said:**
> Does it show the Denied message in a kernel where wifi works?
I am keeping this short as my phone gets me logged out often
Yes! Here's the latest from */var/log/syslog*:
```
Jul  6 23:21:46 aes-Inspiron-15-3567 kernel: [   29.283683] audit: type=1400 audit(1499363506.546:23): apparmor="DENIED" operation="open" profile="/sbin/dhclient" name="/etc/ld.so.preload" pid=1115 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jul  6 23:21:46 aes-Inspiron-15-3567 kernel: [   29.361064] audit: type=1400 audit(1499363506.626:24): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/etc/ld.so.preload" pid=1116 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

```And this is from Kubuntu 16.04 with the 4.8 kernel and wifi working fine.

It's late in my part of the world and so g'night!

---

### Post by jeremy31 on 2017-07-06
Where did this ath9k-msi dkms package come from?  I haven't heard of it

I saw it from the log when you attempted to install the 4.12 kernel

After further review I think it may have come from Dell if your computer had Ubuntu installed when you bought it as I know Dell has their own repo for Ubuntu and there is a lot I haven't looked at, try
```
sudo dkms remove -m ath9k-msi -v 1.0 -k 4.4.0-83-generic
```

Post if there are any errors, if no errors reboot into the 4.4.0-83 kernel

I suspect the dkms failed to build for the 4.8 kernel also but went unnoticed

---

### Post by vasa1 on 2017-07-06
> **jeremy31 said:**
> Where did this ath9k-msi dkms package come from?  I haven't heard of it

I saw it from the log when you attempted to install the 4.12 kernel

After further review I think it may have come from Dell if your computer had Ubuntu installed when you bought it as I know Dell has their own repo for Ubuntu and there is a lot I haven't looked at, try
```
sudo dkms remove -m ath9k-msi -v 1.0 -k 4.4.0-83-generic
```

Post if there are any errors, if no errors reboot into the 4.4.0-83 kernel

I suspect the dkms failed to build for the 4.8 kernel also but went unnoticed

Can you explain what that command does and the context for me to run that command? 

That is, should I run it with the 4.4.0-81 kernel which has wifi and then reboot into the 4.4.0-83 kernel to see if that works?

Yes, this laptop came with Ubuntu 16.04 pre-installed by Dell.

I'm including a pastebin of today's kern.log with the 4.8 kernel: /home/vasa1/Dropbox/Mainline/kernlog-7-7-17.txt

There are a lot of DENIED lines even though wifi is working fine.

---

### Post by jeremy31 on 2017-07-06
The command should remove this ath9k-msi for the 4.4.0-83 kernel and only that kernel.  You can run that command from any kernel then just reboot into the 4.4.0-83
You should also check ```
dkms status
```
It may show some info about the 4.8 and 4.12 kernel

---

### Post by vasa1 on 2017-07-07
Thanks. Here is the output of *dkms status*

```
09:38 AM ~ $ dkms status
ath9k-msi, 1.0, 4.4.0-81-generic, x86_64: installed
ath9k-msi, 1.0, 4.4.0-83-generic, x86_64: installed
intel-hid, 3.1, 4.4.0-81-generic, x86_64: installed
intel-hid, 3.1, 4.4.0-83-generic, x86_64: installed
oem-audio-hda-daily, 0.201612080732~ubuntu16.04.1, 4.4.0-81-generic, x86_64: installed
radeon-si, 1a, 4.4.0-38-generic, x86_64: built
radeon-si, 1a, 4.4.0-81-generic, x86_64: installed
radeon-si, 1a, 4.4.0-83-generic, x86_64: installed
09:41 AM ~ $ 
```

And then I ran```
09:41 AM ~ $ sudo dkms remove -m ath9k-msi -v 1.0 -k 4.4.0-83-generic

-------- Uninstall Beginning --------
Module:  ath9k-msi
Version: 1.0
Kernel:  4.4.0-83-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

ath.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ath9k.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ath9k_common.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ath9k_htc.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ath9k_hw.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

Backing up initrd.img-4.4.0-83-generic to /boot/initrd.img-4.4.0-83-generic.old-dkms
Making new initrd.img-4.4.0-83-generic
(If next boot fails, revert to initrd.img-4.4.0-83-generic.old-dkms image)
update-initramfs...............

DKMS: uninstall completed.
09:43 AM ~ $ 
```

I'll reboot now and try to choose the problematic kernel.

---

### Post by vasa1 on 2017-07-07
Rebooted. WiFi works! Thank you very much for your patient and clear guidance :)

What should I post in the bug now?```
09:51 AM ~ $ dkms status
ath9k-msi, 1.0, 4.4.0-81-generic, x86_64: installed
intel-hid, 3.1, 4.4.0-81-generic, x86_64: installed
intel-hid, 3.1, 4.4.0-83-generic, x86_64: installed
oem-audio-hda-daily, 0.201612080732~ubuntu16.04.1, 4.4.0-81-generic, x86_64: installed
radeon-si, 1a, 4.4.0-38-generic, x86_64: built
radeon-si, 1a, 4.4.0-81-generic, x86_64: installed
radeon-si, 1a, 4.4.0-83-generic, x86_64: installed
09:53 AM ~ $ 
```

---

### Post by vasa1 on 2017-07-07
```
Changed in oem-priority:
status:	New &#8594; Confirmed
importance:	Undecided &#8594; High
assignee:	nobody &#8594; Shih-Yuan Lee (fourdollars)

```Yay!

---

### Post by jeremy31 on 2017-07-07
I would just comment that it is a computer that came with Ubuntu installed

---

### Post by vasa1 on 2017-07-07
> **jeremy31 said:**
> I would just comment that it is a computer that came with Ubuntu installed
Between comments #7 and #8 someone has tagged it "added: inspiron-15-3567" and it's also "oem-priority". So I think they figured it out although I should have mentioned what you suggested in the first post itself.

---

