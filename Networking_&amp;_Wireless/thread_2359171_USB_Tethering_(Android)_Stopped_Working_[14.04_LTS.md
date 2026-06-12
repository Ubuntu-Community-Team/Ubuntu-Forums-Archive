---
title: "USB Tethering (Android) Stopped Working [14.04 LTS]"
date: 2017-04-21
forum: Networking &amp; Wireless
---

### Post by Biltron on 2017-04-21
Hello all,

So, I had _*USB tethering stop working out of nowhere*_ for my Samsung Galaxy and my Lenovo Thinkpad.  
Background you will probably want:  Ubuntu 14.04.5 LTS, Lenovo T430s laptop, Core i5-3320m (64 bit, obviously), Dual-boot with Windows and Ubuntu on different partitions.

Let me emphasize that USB tethering IS ENABLED ON MY PHONE.

USB tethering worked fine before, and I haven't made any major changes (I recently installed apache2, see my addendum at the bottom of this post regarding the 2 things I tried in case that somehow affected the tethering issue).  Let me start with the things I HAVE tried, to eliminate some of the obvious suggestions.

1- I enabled "USB Tethering" under Settings -> Mobile Hotspot and Tethering.  I DID connect the phone to the laptop with a USB cable.
2 - I have tried using different USB ports. (I have a port that sometimes doesn't work in MTP mode for some reason, I think the connectors are getting loose)
3 - I tried rolling back **libnl-3-200**, **libnl-genl-3-200**, and **libnl-route-3-200** as per Hadaka's suggestion in this post: [https://ubuntuforums.org/showthread.php?t=2312192](https://ubuntuforums.org/showthread.php?t=2312192)
    (I downloaded the three files from here: [http://packages.ubuntu.com/source/trusty/libnl3](http://packages.ubuntu.com/source/trusty/libnl3), then put them in their own directory and ran **sudo dkpg -i *.deb**.  It claimed to have successfully downgraded each one.)  Below is the output of that:
[ATTACH=CONFIG]274690[/ATTACH]

4 - I checked to see if my phone shows up with **lsusb**.  This entry is in there (a good sign):

[B]Bus 003 Device 005: ID 04e8:6863 Samsung Electronics Co., Ltd GT-I9500 [Galaxy S4] / GT-I9250 [Galaxy Nexus] (network tethering)

[/B]5 - I ran lspci for funzies, and assumed I should only see USB controllers or any other device that is actually connected to the motherboard.  Here is the output:

[B]00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
04:00.0 System peripheral: Ricoh Co Ltd MMC/SD Host Controller (rev 07)


[/B]I DO NOT see usb0 as a network device when running **ifconfig**.  It lists **eth0**, **lo**, and **wlan0**.  Under the network dropdown menu (in the notification area) I see my wireless network, and my neighbors' networks (as usual), and at the top (when I have my phone connected, and USB tethering ENABLED on the phone) is this entry, greyed out:

[B]Ethernet Network (SAMSUNG Android)
disconnected[/B]

As I said, this option is THERE, but greyed out.  :confused:  I'm not sure what else to include, but feel free to ask for anything else that might help you make sense of this nonsense!

Thank you for your time, if you got through this post!  I look forward to, and appreciate, any help!

-internick

[ADDENDUM]

I forgot when I first wrote this, *that I did recently install apache2* and set it up to let me access my web page (that I am currently playing around with) via localhost.  I tried commenting out the **127.0.0.1 <virtual-host-domainname>** entry in **/etc/hosts**, as well as disabling apache2 on startup with **update-rc.d -f apache2 remove** (Not that these should really affect the usb0 network adapter), but this did not change the situation.

---

### Post by Biltron on 2017-04-21
Here is the output of **dmesg **immediately after connecting the phone and turning on "USB Tethering" from the menu in Android.

[   30.765481] usb 3-1: new high-speed USB device number 3 using xhci_hcd
[   30.896193] usb 3-1: New USB device found, idVendor=04e8, idProduct=6860
[   30.896197] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   30.896198] usb 3-1: Product: SAMSUNG_Android
[   30.896200] usb 3-1: Manufacturer: SAMSUNG
[   30.896201] usb 3-1: SerialNumber: 7241ec52
[   32.043865] systemd-hostnamed[2908]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[   33.918777] usb 3-1: USB disconnect, device number 3
[   34.225722] usb 3-1: new high-speed USB device number 4 using xhci_hcd
[   34.414113] usb 3-1: New USB device found, idVendor=04e8, idProduct=6860
[   34.414120] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   34.414124] usb 3-1: Product: SAMSUNG_Android
[   34.414127] usb 3-1: Manufacturer: SAMSUNG
[   34.414130] usb 3-1: SerialNumber: 7241ec52
[   37.397500] usb 3-1: USB disconnect, device number 4
[   37.733907] usb 3-1: new high-speed USB device number 5 using xhci_hcd
[   37.863779] usb 3-1: New USB device found, idVendor=04e8, idProduct=6863
[   37.863788] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   37.863792] usb 3-1: Product: SAMSUNG_Android
[   37.863795] usb 3-1: Manufacturer: SAMSUNG
[   37.863798] usb 3-1: SerialNumber: 7241ec52
[   37.866066] rndis_host 3-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, 00:00:00:00:00:00
[   38.327762] audit_printk_skb: 54 callbacks suppressed
[   38.327764] audit: type=1400 audit(1492787620.520:30): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2991 comm="apparmor_parser"
[   38.327769] audit: type=1400 audit(1492787620.520:31): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2991 comm="apparmor_parser"
[ 1130.094781] usb 3-1: USB disconnect, device number 5
[ 1130.094854] rndis_host 3-1:1.0 eth1: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device
[ 1130.382554] usb 3-1: new high-speed USB device number 6 using xhci_hcd
[ 1130.514264] usb 3-1: New USB device found, idVendor=04e8, idProduct=6860
[ 1130.514271] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1130.514275] usb 3-1: Product: SAMSUNG_Android
[ 1130.514278] usb 3-1: Manufacturer: SAMSUNG
[ 1130.514281] usb 3-1: SerialNumber: 7241ec52
[ 1131.454017] systemd-hostnamed[8248]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 1138.858082] usb 3-1: USB disconnect, device number 6
[ 1139.163110] usb 3-1: new high-speed USB device number 7 using xhci_hcd
[ 1139.351594] usb 3-1: New USB device found, idVendor=04e8, idProduct=6860
[ 1139.351601] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1139.351605] usb 3-1: Product: SAMSUNG_Android
[ 1139.351608] usb 3-1: Manufacturer: SAMSUNG
[ 1139.351611] usb 3-1: SerialNumber: 7241ec52
[ 1149.260111] usb 3-1: USB disconnect, device number 7
[ 1149.595841] usb 3-1: new high-speed USB device number 8 using xhci_hcd
[ 1149.726604] usb 3-1: New USB device found, idVendor=04e8, idProduct=6863
[ 1149.726611] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1149.726615] usb 3-1: Product: SAMSUNG_Android
[ 1149.726618] usb 3-1: Manufacturer: SAMSUNG
[ 1149.726621] usb 3-1: SerialNumber: 7241ec52
[ 1149.729322] rndis_host 3-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, 00:00:00:00:00:00


So, since it seems to be trying to connect as **eth1**, rather than **usb0** as it previously did, I tried **sudo ifconfig eth1 up**.  I get the following response:
[B]SIOCSIFFLAGS: Cannot assign requested address

[/B]From another thread I had found whilst scouring the interwebs, I found a person with a similar problem, and they suggested installing and using **macchanger** to change the MAC address of the tethered phone, since apparently that person's system (and maybe mine?) has an issue with the MAC of **HWaddr 00:00:00:00:00:00**.  So, I tried the following:

**me@mycomputer:~$ sudo macchanger -r eth1**
[B]Current MAC:   00:00:00:00:00:00 (XEROX CORPORATION)
Permanent MAC: 00:00:00:00:00:00 (XEROX CORPORATION)
[ERROR] Could not change MAC: interface up or insufficient permissions: Cannot assign requested address
[/B]

So, the device seems to be recognized, and the system seems to be trying to set it up on **eth1**.  As far as the MAC of all 0's, I'm sort of puzzled.

---

### Post by Biltron on 2017-04-21
Another noteworthy item:  

I just looked in **/etc/udev/rules.d**, and the last time I had looked in there (maybe a week or two ago) there were at least 20 or 30 rules.  Now I only have 6.  This is all I have now:

[B]52-xilinx-digilent-usb.rules          
52-xilinx-pcusb.rules         
70-persistent-net.rules       
99-jlink.rules 
README
z011_mchp_jlink.rules
z010_mchp_tools.rules[/B]

I remember there being an "android rules" file starting with a number in the 50's, since I looked in that file to make sure my Samsung device was listed in it.  That is gone now, along with many other rules.  NO CLUE why they are gone.  I certainly didn't go in there and type **rm -f *.***.

---

### Post by Biltron on 2017-04-23
Any ideas?  Or did I cover everything that anyone would have suggested?  I've seen this problem in plenty of posts, so I know it's not just me.

---

### Post by jeremy31 on 2017-04-23
If you have a lot of USB devices connected, see if the phone tether will work with some other USB devices disconnected

---

### Post by Biltron on 2017-04-30
I don't normally have any USB devices connected.  I tried connecting an external HDD and then tried tethering again but no go.  I'm fairly certain this is a driver/software issue.  I know others have had this problem but no one is chiming in.

---

### Post by Biltron on 2017-04-30
Luckily I was able to fix Bluetooth tethering, because nothing I have tried fixes the USB tether issue.  Downgrading/Upgrading libnl components does not seem to do anything, although supposedly this is what enables that particular interface.  Hopefully someone out there knows how it works, and I posted extremely detailed information, including a dmesg output showing what it's attempting to do.  So many people just post "my <whatever> broke help!" with no information whatsoever!

---

### Post by jeremy31 on 2017-04-30
I haven't used 14.04 since 16.04 was released but I wonder if you didn't get an Android update that requires you to have USB debugging enabled in developers options.  I did some testing with my old Note 2 a while back and I couldn't access the file system without having the USB debugging on

---

### Post by Biltron on 2017-04-30
I did try enabling USB debugging, btw, that had no effect.  But good call, some things do require that I've noticed.



I got it to work, finally.

So the issue was mostly that the phone was showing up as a network interface but reporting a MAC address of 00:00:00:00:00:00.  And I guess NM/Ubuntu does not like this.  I downloaded **macchanger**, and I tried using the **-r** option to set a random MAC, but that never worked, it said device up or insufficient permissions (I ran it with sudo, and the device was down, I made sure of that with **sudo ifconfig eth1 down**).

So, after some more reading, I tried using **macchanger** again, but with different options.  I ran the following:
[B]sudo ifconfig eth1 down
sudo macchanger -b -a eth1
sudo ifconfig eth1 up
[/B]
and lo and behold, it worked.  The -b option mimics a "burned in" MAC address, and -a mimics a MAC of a same or similar vendor.  It successfully set a non-zeroed MAC to my Samsung Galaxy, and after putting the interface back up, I get the connection option in the network dropdown menu.

So, maybe I can help someone else who has this issue, and spare them a week of research.

---

