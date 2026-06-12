---
title: "Asus laptop disabled WiFi (hard blocked)"
date: 2019-12-16
forum: Networking &amp; Wireless
---

### Post by rikyepoveri on 2019-12-16
Hi everyone,

I really hope someone could help me because I have been looking for a solution for months in this forum and elsewhere but I haven't come up with anything.
I have a ASUS K550J laptop with Xubuntu 18.04 installed. The problem is WiFi doesn't work, the physical switch fn+F2 does nothing and from *rfkill *it appears that *phy0: Wireless LAN* is hard blocked.

I tried performing a clean installation of Xubuntu 18.04, i tried to install a previous version (14.04), I tried to install Ubuntu as well to be sure that the problem isn't related to the Xubuntu distro but the issue still occurs. Xubuntu is installed on an external HDD, while on the internal HDD I have Windows 10 installed, on which WiFi works like a charm.

All relevant information related to my wireless configuration can be found attached below.

[ATTACH]284616[/ATTACH]

I'd really need your help because I don't know what to do ](*,)

Thanks in advance

---

### Post by chili555 on 2019-12-16
Please check here: [https://askubuntu.com/questions/880700/cant-connect-to-wifi-with-intel-7265ac-on-ubuntu-16-04-lst/880821#880821](https://askubuntu.com/questions/880700/cant-connect-to-wifi-with-intel-7265ac-on-ubuntu-16-04-lst/880821#880821)

As per Pilot6 comment, I would suggest that you start with =4.

---

### Post by rikyepoveri on 2019-12-16
First thing, thanks for your reply.

I've tried one after another all options from =0 to =4, rebooting after each change, but the fn+F2 shortcut doesn't work.
I don't really know whether the asus_nb_wmi module is loaded or not, but the output of the *grep *command is:

```
asus_nb_wmi            28672  0 
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
asus_wireless          20480  0
wmi                    28672  3 asus_wmi,mxm_wmi,nouveau
video                  49152  3 asus_wmi,i915,nouveau
```

---

### Post by chili555 on 2019-12-16
May we please proofread your file?

```
cat /etc/modprobe.d/asus.conf
```

---

### Post by rikyepoveri on 2019-12-17
Of course, I'll attach the *asus.conf *file. Its content is the same of the *asus_nb_wmi.conf *file.

---

### Post by rikyepoveri on 2019-12-19
Any idea?

---

### Post by SeijiSensei on 2019-12-19
Perhaps you inadvertently hit the airplane mode key combination: Fn+F2?  Is the little icon that looks like a radio tower lit?

[https://dlcdnets.asus.com/pub/ASUS/nb/X550JD/0409.pdf](https://dlcdnets.asus.com/pub/ASUS/nb/X550JD/0409.pdf)

On my HP laptop I have a key that turns Bluetooth+wifi off and on. I accidentally turn off wifi all the time.

---

### Post by praseodym on 2019-12-19
Try to change the driver

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/06/23/5641297-RT3290_u16_v3.tar.gz
tar xvf 5641297-RT3290_u16_v3.tar.gz
cd RT3290_u16
tar xvf src.tar.gz
./compile.sh
sudo ./install.sh
sudo cp firmware/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf  
```
For Bluetooth

```
sudo add-apt-repository ppa:blaze/rtbth-dkms
sudo apt-get update
sudo apt install dkms rtbth-dkms blueman
sudo modprobe -v rtbth 
```
Reboot and show
```

iwconfig
lsmod
sudo iwlist scan
rfkill list
```

---

### Post by rikyepoveri on 2019-12-19
> **praseodym said:**
> Try to change the driver

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/06/23/5641297-RT3290_u16_v3.tar.gz
tar xvf 5641297-RT3290_u16_v3.tar.gz
cd RT3290_u16
tar xvf src.tar.gz
./compile.sh
sudo ./install.sh
sudo cp firmware/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf  
```


When it comes to compiling the driver, I get an error and the process fails. I'm a novice with Ubuntu, therefore I can't tell what the problem is. Attached is the output.

---

### Post by rikyepoveri on 2019-12-19
> **SeijiSensei said:**
> Perhaps you inadvertently hit the airplane mode key combination: Fn+F2?  Is the little icon that looks like a radio tower lit?

[https://dlcdnets.asus.com/pub/ASUS/nb/X550JD/0409.pdf](https://dlcdnets.asus.com/pub/ASUS/nb/X550JD/0409.pdf)

On my HP laptop I have a key that turns Bluetooth+wifi off and on. I accidentally turn off wifi all the time.

I do have the same key combination: this combo works like a charm on Windows, but not on Ubuntu. I've found out that Fn+F2 on Ubuntu turns on/off the *Soft Blocked* state of the wireless card, but not the *Hard Blocked* one, which is permanently set to *yes*.

---

### Post by praseodym on 2019-12-20
Try hitting that combo permanently or repeatedly during boot-up. Any chance to check the BIOS settings?

---

### Post by rikyepoveri on 2019-12-20
Just tried, but I've gained no results. I've entered the BIOS countless times but it appears to me that everything is fine: the wireless card is enabled at boot.

---

### Post by praseodym on 2019-12-20
If its a BIOS, try resetting it to default values, but not with an UEFI!

Try also

```
sudo rfkill unblock all
rfkill list
```

---

### Post by rikyepoveri on 2019-12-21
Already tried but the phy0 wireless LAN is still hard blocked.

> [COLOR=#000000]If its a BIOS, try resetting it to default values, but not with an UEFI![/COLOR]

What does it mean? How can I reset the BIOS without an UEFI?

---

### Post by praseodym on 2019-12-22
Please show the output of

```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS 
```

---

### Post by rikyepoveri on 2019-12-23
It just says
```
UEFI
```

---

### Post by praseodym on 2019-12-23
Ok, please check all options available there for activating wireless

---

### Post by rikyepoveri on 2019-12-26
During Christmas holidays I've tried to install Xubuntu 14.04, 16.04 and 18.04 just to discover that the WiFi card doesn't work with any of these versions. I'm assuming therefore that my issue doesn't depend neither on the Ubuntu version nor on the kernel, although I've found out that installing the RT3290 drivers [as suggested by praseodym]("https://ubuntuforums.org/showthread.php?t=2433264&p=13918244#post13918244") returns an error due to some changes between kernel 4.4 and the following ones.

For all Xubuntu versions the WiFi card is hard blocked and wireless connection is consequently disabled. However, it works without any problem on Windows. For this reason I've checked my BIOS configuration but I haven't found any option that turns the WiFi off.

Options in my BIOS are (except for date and time settings):

[U]Advanced section
[/U]Internal Pointing Device: Enabled
Wake On Lid Open: Enabled
Power Off Energy Saving: Enabled
Intel Virtualization Technology: Enabled
Intel AES-NI: Enabled
VT-d: Enabled
Sata Mode Selection (IDE/AHCI): AHCI
DVMT Pre-Allocated: 64M
Legacy USB Support: Enabled
HXCI Pre-Boot Mode: Enabled
Network Stack: Disabled

_Boot section_
Fast Boot: Enabled
Launch CSM: Disabled
(boot options: ubuntu, windows, ...)

_Security section_
Administrator password: Not Installed
LAN Network/CardReader Interface: Unlock
Wireless Network and Bluetooth I/F: Unlock
HD Audio Interface: Unlock
SATA ODD Interface: Unlock
USB Interface: Unlock
External Ports: Unlock
CMOS Camera: Unlock

_Secure Boot Variables section_
Platform Key (PK)
Key Exchange Key Database (KEK)
Authorized Signature Database (DB)
Forbidden Signature Database (DBX)

I'm really discouraged because I've tried like hell but still I haven't got any result, and I'd really need the WiFi connection to work on Ubuntu for job purposes.

---

### Post by chili555 on 2019-12-26
> I'm really discouraged because I've tried like hell but still I haven't got any result, and I'd really need the WiFi connection to work on Ubuntu for job purposes.Please check here: [https://ubuntuforums.org/showthread.php?t=2150597](https://ubuntuforums.org/showthread.php?t=2150597)

---

### Post by tea for one on 2019-12-27
> **rikyepoveri said:**
> 

_Boot section_
Fast Boot: Enabled
Launch CSM: Disabled
(boot options: ubuntu, windows, ...)

I'm really discouraged because I've tried like hell but still I haven't got any result, and I'd really need the WiFi connection to work on Ubuntu for job purposes.

Is there a chance that leaving **Fast Boot enabled** has allowed Windows to somehow control/lock the wireless device and prevent any fix working correctly?

I have no idea if Windows would be able to do this but I would not be too surprised if it were possible?

The general advice for dual-booting is to disable Fastboot

@OP - I reckon that you are in good hands with praseodym, chili555 together with jeremy31

---

### Post by praseodym on 2019-12-27
Check, if Windows shuts down the card when shutting down

---

### Post by rikyepoveri on 2019-12-28
First thing, thank you all for your interest. It's very important to me that I manage to turn on WiFi on Ubuntu.
I've tried everything but I haven't been able to turn it on yet. In a nutshell, WiFi works flawlessly on Windows 10 installed on an internal SSD, but doesn't work on Xubuntu (14.04, 16.04, 18.04) installed on an external HDD. The green light is off, there's no external switch and the hardware switch Fn+F2 does nothing.

In the latest days I tried the following:
- I disabled fast boot and secure boot from BIOS. Nothing changed.
- I updated the BIOS. Nothing changed.
- I performed a fresh installation of Xubuntu 14.04, 16.04, 18.04. Still got anything.
- I tried to install the rt3290 driver instead of the in-built rt2800, but it looks like that this driver isn't supported by kernels following 4.8.

I could try to remove the WiFi card but it would imply disassembling my laptop since it's not accessible from its trapdoor, and I doubt this way would be effective since on Windows it does work.

> [COLOR=#000000]Check, if Windows shuts down the card when shutting down[/COLOR]

How could I check it?

---

### Post by rikyepoveri on 2019-12-28
This may be useful: when I boot into the Ubuntu live USB (for installation or testing purposes) WiFi is disabled as well. I'm convincing myself that, for this reason, it's the BIOS that's causing it all, but I think I've checked everything I could and I don't know where to look further.

---

### Post by praseodym on 2019-12-28
[https://richarddouglasdenton.wordpress.com/2011/05/11/how-to-bypass-a-laptop-wireless-switch/](https://richarddouglasdenton.wordpress.com/2011/05/11/how-to-bypass-a-laptop-wireless-switch/)

Try bypassing the switch

---

### Post by rikyepoveri on 2019-12-29
> **praseodym said:**
> [https://richarddouglasdenton.wordpress.com/2011/05/11/how-to-bypass-a-laptop-wireless-switch/](https://richarddouglasdenton.wordpress.com/2011/05/11/how-to-bypass-a-laptop-wireless-switch/)

Try bypassing the switch

I'd really wish there was another way, apart from acting on the wireless card, because it requires completely disassembling my laptop (something I've never done), but I'm afraid I'll have to give up and take a chance disassembling it.

I've bought a wireless USB adapter so as to plug it in the USB port when I need to connect to WiFi, but after having compiled its driver and installed the device I can't connect to WiFi because the network manager says "Wi-Fi disabled by hardware switch". How is it possible? I'm not even relying on the wireless card!

---

### Post by rikyepoveri on 2019-12-29
I apologize for  spamming.
Update: I installed Xubuntu 14.04 LTS and after installing the RT3290 driver as suggested by praseodym [here]("https://ubuntuforums.org/showthread.php?t=2433264&p=13918244#post13918244") (which wasn't possible on Xubuntu 18.04 and 16.04 due to the different  kernel - or this is what I think) I can connect to WiFi through the USB adapter, but not through the wireless card since the latter doesn't find any available network (on the contrary, the USB adapter do!)

---

