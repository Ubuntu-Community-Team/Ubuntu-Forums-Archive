---
title: "Unable to detect WiFi - Broadcom 4352"
date: 2017-05-03
forum: Networking &amp; Wireless
---

### Post by agonsalves on 2017-05-03
[COLOR=#000000][FONT=sans-serif]Hey Ubuntu Family,[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]So I've recently just made made the switch from Windows 10 to Kubuntu 16.04.02 LTS. For clarity, I'm an adolescent linux user - fresh and new to linux. [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]The issues is that I do not seem to have the wifi icon, rather just an airplane mode icon. Thus, I can't even scan for wifi. [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]I am using a Dell XPS 13 laptop with Intel Broadwell Core i5-5200U CPU, 4GB RAM, 256GB SSD. I am not able to access the internet on my system - obv. due to no wifi, and my laptop does not have an Ethernet port.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Through the Konsole command: [/FONT][/COLOR][COLOR=#333333][FONT=sans-serif][FONT=UbuntuMono]lspci -vvnn | grep -A 9 Network 
[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]I found that I am using a Broadcom Corporation [/FONT][/COLOR]_BCM4352_[COLOR=#000000][FONT=sans-serif] 802.11ac Wireless Network Adapter [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]My PCI-ID is 14e4:43b1 [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]The Kernel driver in use: bcma-pci-bridge[/FONT][/COLOR][COLOR=#333333][FONT=sans-serif][FONT=UbuntuMono]
[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]The current Kernel I am using is 4.8.0-36-generic[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]I would genuinely appreciate any help I can get to resolve this issue and get my beloved Wifi working again. 

2. I saw a post somewhere, which I now am unable to find saying that if i could get the b43-fwcutter-installer downloaded elsewhere and working on my laptop, it would update/manage the drivers for me and allow my wifi to work, however i don't fully understand firstly if this will work, and secondly how to do it. - The post also mentioned getting the STA ones but stated they were terrible, but beats nothing.

[/FONT][/COLOR][FONT=arial]3. Also as a side note i'd like to know if this issue would be a problem on all distros,[/FONT][FONT=arial] since it's the driver installer missing from the repositories - due to them not being openly available by broadcom or something similar was mentioned on the b43 post. Or if it's[/FONT][FONT=arial] just Kubuntu/my laptop(since it's my wireless adapter issue).[/FONT]
[COLOR=#000000][FONT=sans-serif]Thank you[/FONT][/COLOR]

---

### Post by agonsalves on 2017-05-03
I'm not sure, but would this article be of any benefit to me? [https://wiki.gentoo.org/wiki/Dell_XPS_13_9343](https://wiki.gentoo.org/wiki/Dell_XPS_13_9343)

---

### Post by wildmanne39 on 2017-05-03
Do you have a usb port and a cell phone? you can tether your cell for a connection to install the driver, if so I will post the direction to do so, if not I will find the directions to do it without a connection but that will take a lot more time.
Thanks

---

### Post by wildmanne39 on 2017-05-03
*Thread moved to **Networking & Wireless**.*

---

### Post by agonsalves on 2017-05-03
Yes I have a USB port and a cell phone! Would appreciate direction as to what to do

---

### Post by wildmanne39 on 2017-05-03
You need to go into the settings on your phone and turn on tethering it may be under hotspot settings, then connect your phone to the usb port and you should have internet. then open a terminal in Ubuntu and copy and paste the following command:
```
sudo apt install bcmwl-kernel-source
```
Watch for errors while the driver is installing.

Reboot and wifi should work.

---

### Post by agonsalves on 2017-05-03
Done. Last line i got is "E: Unable to locate package bcmwl-kernel-source"

Should i still reboot it?

---

### Post by wildmanne39 on 2017-05-03
Sounds like your internet connection did not work, can you see if you have a connection with tethering?

No will not do any good to reboot.

---

### Post by agonsalves on 2017-05-03
Did it again, got the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  dkms fakeroot libfakeroot
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot libfakeroot
0 upgraded, 4 newly installed, 0 to remove and 184 not upgraded.
Need to get 1,698 kB of archives.
After this operation, 8,765 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 dkms all 2.2.0.3-2ubuntu11.3 [66.1 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted amd64 bcmwl-kernel-source amd64 6.30.223.271+bdcom-0ubuntu1~1.1 [1,544 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 libfakeroot amd64 1.20.2-1ubuntu1 [25.5 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 fakeroot amd64 1.20.2-1ubuntu1 [61.8 kB]
Fetched 1,698 kB in 1s (1,396 kB/s)
Selecting previously unselected package dkms.
(Reading database ... 158754 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11.3_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11.3) ...
Selecting previously unselected package bcmwl-kernel-source.
Preparing to unpack .../bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu1~1.1_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu1~1.1) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20.2-1ubuntu1_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20.2-1ubuntu1) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20.2-1ubuntu1_amd64.deb ...
Unpacking fakeroot (1.20.2-1ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up dkms (2.2.0.3-2ubuntu11.3) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu1~1.1) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 4.8.0-36-generic
Building for architecture x86_64
Building initial module for 4.8.0-36-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.8.0-36-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up libfakeroot:amd64 (1.20.2-1ubuntu1) ...
Setting up fakeroot (1.20.2-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Processing triggers for shim-signed (1.19~16.04.1+0.8-0ubuntu2) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.8.0-36-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915

---

### Post by jeremy31 on 2017-05-03
agonsalves,  I think you may need to ```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```
Then reboot

---

### Post by wildmanne39 on 2017-05-03
The good news is your connection is working and jeremy31 is probably right if you have never connected to the internet and received updates before then you need to then you can run the command again.

---

### Post by agonsalves on 2017-05-03
SOLVED! Thank you very much Jeremy31

---

### Post by agonsalves on 2017-05-04
Slight problem,  it shows all the connections,  but once I put in all the info it says 'for accessing the WiFi network you need to provide a password'  and two little popups come up saying wifi deactivated and no secrets were provided. I tried my WiFi and laptop password and neither work here. 

Am I missing something really simple or is there another issue? 

Thanks again :)

---

### Post by wildmanne39 on 2017-05-04
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by agonsalves on 2017-05-04
heres the link: [http://paste.ubuntu.com/24512444/](http://paste.ubuntu.com/24512444/)

---

### Post by wildmanne39 on 2017-05-04
I just started working with another person with the same device and driver and you both have the same driver error, let's try to reinstall the driver and see if that works if it does not we will install a different driver.

Please do:
> sudo apt install --reinstall bcmwl-kernel-source
Reboot

---

### Post by agonsalves on 2017-05-05
[COLOR=#000000][FONT=Noto Sans]This is what I get:
DKMS: install completed.[/FONT][/COLOR]

 [COLOR=#000000][FONT=Noto Sans]update-initramfs: deferring update (trigger activated)[/FONT][/COLOR]

 [COLOR=#000000][FONT=Noto Sans]Processing triggers for shim-signed (1.27~16.04.1+0.9+1474479173.6c180c6-1ubuntu1) ...[/FONT][/COLOR]
 [COLOR=#000000][FONT=Noto Sans]Secure Boot not enabled on this system.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Noto Sans]Processing triggers for initramfs-tools (0.122ubuntu8.8) ...                                                                         [/FONT][/COLOR]
 [COLOR=#000000][FONT=Noto Sans]update-initramfs: Generating /boot/initrd.img-4.8.0-51-generic                                                                       [/FONT][/COLOR]
 [COLOR=#000000][FONT=Noto Sans]W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915  [/FONT][/COLOR]

Still asking for the password (which i entered again correctly) after reboot. 

Guess I'd have to install the next driver.

---

### Post by Hadaka on 2017-05-05
Hi, try this..
Click  the    wifi icon   upper right corner  
Click          Edit Connections
Click          Wireless    tab
                 Delete Your SSID
                 and your SSID 1 if it exists
                 Boot then add your SSID

---

### Post by agonsalves on 2017-05-06
@Hadaka Ive tried it, but I get the same error.

---

