---
title: "Wireless not working with Dell Inspiron 1764."
date: 2011-05-16
forum: New to Ubuntu
---

### Post by bobbrock on 2011-05-16
After installing Ubuntu 11.04 with windows7 my wireless is not working
with ubuntu i use my ethernet connection to update ubuntu when doing 
the install. I also checked  Additional Drivers and it shows "Broadcom STA 
Wireless Driver." This driver is activated and currently in use.
But i still dont have a wireless connection. 
Its showing my SSID i enter my password correctly too but still not working.
I deleted my wireless connection and rebooted and enter my SSID password
but no luck there. When i click on my network icon it Shows my SSID and underneath
it says "disconnect" and my icon looks like is trying to find a signal or something
From time to time when trying to open firefox and clicking my network icon
a window pops up  "Wireless Network Authentication required" so i click 
connect but still "NADA" and my network icon again looks like its trying to find a 
signal. 
Does this mean tha ubuntu11.04 is not compatible with my wireless driver.
Because windows7 works fine wirelessly.  :confused:

Dell Inspiron 1764

Thanks

---

### Post by TBABill on 2011-05-16
Hmmmm....I use the same driver and it works fine for my BCM4312. Which device do you have? You can find out with a terminal command of ```
lspci
``` and look for network devices.
 
Can you run the command ```
sudo rfkill list all
``` and if soft blocked says "YES" then ```
sudo rfkill unblock all
```
 
Did you try any other drivers first? Did you install anything manually? Did you enable the driver upon installation or after updates?

---

### Post by bobbrock on 2011-05-16
Im New to ubuntu i was looking for a way to run the terminal command "1spci"
but i have not figure tha one out yet.
And no i didn't try any other drivers first.Im not sure if i enable the drivers .

---

### Post by astex on 2011-05-16
This doesn't sound like a driver problem.  Rather, DHCP detection would not work if the driver was not configured correctly.  Are you perhaps entering the wireless password using the wrong encryption (WEP,AES, etc)?

Also, the command is 'lspci' with a lower case L.  To get a terminal in ubuntu 11.04, hit the windows key and type terminal.  The icon form terminal should pop up.

---

### Post by bobbrock on 2011-05-16
Thanks ASTEX
 TBABILL my is BCM4312 too.
Astex im using WPA&WPA@personal

---

### Post by josephmills on 2011-05-16
hi there could you please open your terminal and type in ```
lspci -vnn | grep 14e4 
``` and paste here , thanks**edit** could we also see a ```
 dmesg | grep -i broadcom
```

---

### Post by bobbrock on 2011-05-16
TBABILL i ran sudo rfkill list all 

0:dell-wifi:wireless lan
          soft blocked: no

---

### Post by bobbrock on 2011-05-16
Hi JOSEPHMILLS
ubuntu@ubuntu-Inspiron-1764:~$ lspci -vnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
here is the 2nd one
ubuntu@ubuntu-Inspiron-1764:~$ dmesg | grep -i broadcom
[   13.732881] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38

---

### Post by josephmills on 2011-05-16
please see post number 44 [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5) let us know if you have any troubles

---

### Post by bobbrock on 2011-05-16
Thanks 
Quick question which version of adobe do i need for ubuntu

---

### Post by josephmills on 2011-05-16
> **bobbrock said:**
> Thanks 
Quick question which version of adobe do i need for ubuntu

go to ubuntu software center and enter flash into the search box or adobe and it will give you a list of what ones you should install hope that helps

---

### Post by kswitch on 2011-05-16
Hi... I too am having the exact same problem. I just installed ubuntu 11.04 some weeks back and everything seems to be working fine except for the wireless. The wired network and bluetooth are working fine but when you click on the network icon on the taskbar and look under the wireless, the wireless says 'firmware missing'. The thing is that I installed it alongside windows 7 and the wireless works fine when I log on to windows 7 but when i go to ubuntu, i doesn'work. Pls any solution. I use a HP Compaq compaq 615. And the wireless adapter i use is Broadcom 802.11g

P.S: I haven't installed anything on the ubuntu. I only connected to the internet via cable and bluetooth and they both work fine. I don't even have flashplayer installed. I am totally clueless when it comes to Ubuntu.

Thanks for your help.

---

### Post by josephmills on 2011-05-16
> **kswitch said:**
> Hi... I too am having the exact same problem. I just installed ubuntu 11.04 some weeks back and everything seems to be working fine except for the wireless. The wired network and bluetooth are working fine but when you click on the network icon on the taskbar and look under the wireless, the wireless says 'firmware missing'. The thing is that I installed it alongside windows 7 and the wireless works fine when I log on to windows 7 but when i go to ubuntu, i doesn'work. Pls any solution. I use a HP Compaq compaq 615. And the wireless adapter i use is Broadcom 802.11g

P.S: I haven't installed anything on the ubuntu. I only connected to the internet via cable and bluetooth and they both work fine. I don't even have flashplayer installed. I am totally clueless when it comes to Ubuntu.

Thanks for your help.

hi there could you please open your terminal and type in ```
dmesg | grep b43
``` if anything comes back cool post here if not just say so thanks

---

### Post by josephmills on 2011-05-16
> **kswitch said:**
>  i use is Broadcom 802.11g

P.S: I haven't installed anything on the ubuntu. I only connected to the internet via cable and bluetooth and they both work fine. I don't even have flashplayer installed. I am totally clueless when it comes to Ubuntu.

Thanks for your help.

hi again lets make sure ```
lspci | grep 14e4 
``` please post here
**EDIT Kswitch Welcome to Ubuntu Forums **

---

### Post by kswitch on 2011-05-16
> **josephmills said:**
> hi there could you please open your terminal and type in ```
dmesg | grep b43
``` if anything comes back cool post here if not just say so thanks



Yeah the code above shows this
```
 [    2.685629] b43-pci-bridge 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.685733] b43-pci-bridge 0000:06:00.0: setting latency timer to 64
[   18.857090] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   19.084726] Registered led device: b43-phy0::tx
[   19.084749] Registered led device: b43-phy0::rx
[   19.084775] Registered led device: b43-phy0::radio
[   21.801994] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   21.802001] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   21.802005] b43-phy0 ERROR: You must go to http : / / wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
```

the next one shows nothing

---

### Post by kswitch on 2011-05-16
This is the full message the terminal shows




[    2.685629] b43-pci-bridge 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.685733] b43-pci-bridge 0000:06:00.0: setting latency timer to 64
[   18.857090] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   19.084726] Registered led device: b43-phy0::tx
[   19.084749] Registered led device: b43-phy0::rx
[   19.084775] Registered led device: b43-phy0::radio
[   21.801994] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   21.802001] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   21.802005] b43-phy0 ERROR: You must go to http : / / wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

---

### Post by josephmills on 2011-05-16
> **kswitch said:**
> Yeah the code above shows this
```
 [    2.685629] b43-pci-bridge 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.685733] b43-pci-bridge 0000:06:00.0: setting latency timer to 64
[   18.857090] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   19.084726] Registered led device: b43-phy0::tx
[   19.084749] Registered led device: b43-phy0::rx
[   19.084775] Registered led device: b43-phy0::radio
[   [b]21.801994] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   21.802001] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   21.802005] b43-phy0 ERROR: You must go to http : / / wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
```
[/b]
the next one shows nothing

Looks like the firmware is missing please see post number 44 you need the b43 fwcutter the firmware-b43-installer the bcmwl-kernel-source hope that this helps [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

---

### Post by kswitch on 2011-05-16
> **josephmills said:**
> Looks like the firmware is missing please see post number 44 you need the b43 fwcutter the firmware-b43-installer the bcmwl-kernel-source hope that this helps [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

ok i will try it and give u feedback. 

Pls are you on gtalk or y!messenger or ovi. Pls if u are on any one pls send me ur id to

<removed email>

i can understand if you do not wnt to post it here. I have so many questions to ask and so many things i want to learn.

Thanks a lot

---

### Post by bobbrock on 2011-05-16
I did this first"First before installing we need to remove anything that is there right  now so open up synaptic package manager and type in bcm into the search  bar then click on the green box's and mark for removal then press the  apply"
This is my model number  [B]14e4:4315
I installed this [/B] [B]broadcom-sta-source + broadcom-sta-common
And this [/B]bcmwl-kerrnel-source
But still wireless not working .
Im going to try the second part.

---

### Post by bobbrock on 2011-05-16
After trying the second part im still not able to connect to the internet wirelessly.

---

### Post by TBABill on 2011-05-16
bobbrock, the BCM4312 normally uses the wl driver (also called the STA). SOME of the models can use the b43, but all should be able to use the wl. Here's what I'd recommend. 

Make sure you are connected via ethernet and open a terminal, then type in ```
sudo apt-get install --reinstall bcmwl-kernel-source
``` then immediately go to Additional Drivers and enable the STA driver. To see if it worked without clicking restart....it will tell you the system has to be restarted, but there's a way around that. To test immediately, just do this in a terminal then go try to connect ```
sudo modprobe wl
```

---

### Post by bobbrock on 2011-05-16
ubuntu@ubuntu-Inspiron-1764:~$ lsmod | grep b43
ubuntu@ubuntu-Inspiron-1764:~$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,202 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 130132 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up firmware-b43-installer (4.150.10.5-5) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 2.6.38-8-generic
Building for architecture i686
Building initial module for 2.6.38-8-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-8-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
 This is what i got back

---

### Post by bobbrock on 2011-05-16
My STA driver was allready enable

---

### Post by bobbrock on 2011-05-16
I though i mention this 
A windows keeps poping up saying 
Wireless Network Authentication Required

---

### Post by josephmills on 2011-05-16
> **bobbrock said:**
> I did this first"First before installing we need to remove anything that is there right  now so open up synaptic package manager and type in bcm into the search  bar then click on the green box's and mark for removal then press the  apply"
This is my model number  [B]14e4:4315
I installed this [/B] [B]broadcom-sta-source + broadcom-sta-common
And this [/B]bcmwl-kerrnel-source
But still wireless not working .
Im going to try the second part.

You also need the firmware-b43-installer hope this helps also try to hard reset your router

---

### Post by bobbrock on 2011-05-17
I did a fresh install deleted ubuntu and reinstalled again .
I install the [B]broadcom-sta-source + broadcom-sta-common
And the [/B]firmware-b43-installer.
And the bcmwl-kerrnel-source.

And i restarted my router .But tha didnt help.
Now im getting the this pop up "Package Problem"
Sorry the package "firmware-b43-installer4.150.10.5-5."failed to install
or upgrade.

---

### Post by wildmanne39 on 2011-05-17
> **bobbrock said:**
> I though i mention this 
A windows keeps poping up saying 
Wireless Network Authentication Required
Hi at this point it sounded like it just wanted your password so it could connect to you wireless network.

---

