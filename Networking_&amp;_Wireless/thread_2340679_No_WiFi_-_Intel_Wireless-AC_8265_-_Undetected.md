---
title: "No WiFi - Intel Wireless-AC 8265 - Undetected"
date: 2016-10-20
forum: Networking &amp; Wireless
---

### Post by bridgman on 2016-10-20
Hi all,

I'm relatively new to Linux and this is my first post here. I just purchased the new HP Spectre x360 today and installed Ubuntu with no issues except for the lack of internet connectivity. The laptop has a new model network card (Intel wireless-ac 8265) with no Ethernet port. I tried searching this forum and others and I can't find it mentioned anywhere - there's hardly even any information on Google.

I tested 4 different distros all of which were unable to detect the wireless card.

Any help would be greatly appreciated. Thanks!

---

### Post by jeremy31 on 2016-10-21
Welcome to the forums

Are you using 16.04?  And please post results for ```
lspci -nnk | grep -iA2 net; rfkill list all
```

---

### Post by bridgman on 2016-10-21
Thanks Jeremy - I am using 16.04
I've attached a photo of the results. Let me know if there's a better method.

---

### Post by jeremy31 on 2016-10-21
Post results for ```
modinfo iwlwifi | grep 1010
```
What kernel are you using ```
uname -r
```

---

### Post by bridgman on 2016-10-21
results attached

---

### Post by jeremy31 on 2016-10-21
I compiled patched modules, you will need to download and transfer to your Ubuntu desktop.  You can not have Secure Boot enabled in BIOS or this will not work
[https://www.dropbox.com/s/eexh84dofahgig2/iwlmvm.ko?dl=0](https://www.dropbox.com/s/eexh84dofahgig2/iwlmvm.ko?dl=0)
[https://www.dropbox.com/s/1bvc5vqw4429w21/iwlwifi.ko?dl=0](https://www.dropbox.com/s/1bvc5vqw4429w21/iwlwifi.ko?dl=0)

Then in terminal
```
cd Desktop
sudo cp iwlmvm.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/iwlwifi/mvm/
sudo cp iwlwifi.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/iwlwifi/
sudo depmod -a
```
Reboot and with any luck wifi will work

With wifi working, file a [bug report](https://ubuntuforums.org/showthread.php?t=1011078) against package linux Do not install updates as you will not have wireless once again after rebooting.  Also do ```
sudo apt-get update && sudo apt-get install linux-headers-generic build-essential
```
This will likely trigger the Update Manager to prompt to install updates but ignore for now and download [https://www.dropbox.com/s/frw4h1y1lp3cfsf/iwlwifi.tar.gz?dl=0](https://www.dropbox.com/s/frw4h1y1lp3cfsf/iwlwifi.tar.gz?dl=0) which is the source code for what I did
Right click and choose extract and extract to desktop
Then when you install updates and reboot
```
cd Desktop/iwlwifi
cp /usr/src/linux-headers-$(uname -r)/Module.symvers ./
cp /usr/src/linux-headers-`uname -r`/.config ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp iwlmvm.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/iwlwifi/mvm/
sudo cp iwlwifi.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/iwlwifi/
sudo depmod -a
```

Reboot

---

### Post by bridgman on 2016-10-21
No luck getting WiFi after rebooting. Any other suggestions?

---

### Post by jeremy31 on 2016-10-21
what does ```
modinfo iwlwifi | grep 1010
``` show now?

---

### Post by bridgman on 2016-10-21
[ATTACH=CONFIG]271716[/ATTACH]

---

### Post by chili555 on 2016-10-21
I believe my colleague Jeremy also wants to see:```
sudo modprobe iwlwifi
dmesg | grep iwl
```Firmware?

---

### Post by bridgman on 2016-10-21
[ATTACH=CONFIG]271718[/ATTACH]

---

### Post by jeremy31 on 2016-10-22
I did some major patching on the modules so they can use the correct firmware, download
[https://www.dropbox.com/s/1bvc5vqw4429w21/iwlwifi.ko?dl=0](https://www.dropbox.com/s/1bvc5vqw4429w21/iwlwifi.ko?dl=0)
[https://www.dropbox.com/s/eexh84dofahgig2/iwlmvm.ko?dl=0](https://www.dropbox.com/s/eexh84dofahgig2/iwlmvm.ko?dl=0)
[http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-8265-21.ucode](http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-8265-21.ucode)

Transfer them to your Ubuntu desktop after deleting the older iwlwifi.ko and iwlmvm.ko
Then you can ```
cd Desktop
sudo cp iwlmvm.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/iwlwifi/mvm/
sudo cp iwlwifi.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/iwlwifi/
sudo depmod -a
sudo cp iwlwifi-8265-21.ucode /lib/firmware/
```

Reboot

Redownload the source code as that was changed [https://www.dropbox.com/s/frw4h1y1lp3cfsf/iwlwifi.tar.gz?dl=0](https://www.dropbox.com/s/frw4h1y1lp3cfsf/iwlwifi.tar.gz?dl=0)

---

### Post by bridgman on 2016-10-22
Thanks Jeremy. Unfortunately, I didn't have any luck. For those who also run into this problem - Ubuntu 16.10 works fine with this wireless card.

---

### Post by luisfe124 on 2017-02-24
Hi,

I have the same Intel card and am having the same connectivity problems on 16.04. The kernel version is 4.4.0-64-generic. Before trying out the solution proposed I want to ask if the issue has been solved, or if I should update to 16.10?

Cheers,

Luis

---

### Post by chili555 on 2017-02-24
> if I should update to 16.10?Yes, please.

[http://askubuntu.com/questions/854858/new-hp-spectre-x360-wifi-not-working-using-intel-8265-card](http://askubuntu.com/questions/854858/new-hp-spectre-x360-wifi-not-working-using-intel-8265-card)

---

### Post by thehaguefreek on 2017-04-01
The following solution is NOT recommended but it was the only way I got it to work (Tested on Ubuntu 16.04.2 kernel 4.8):

[LIST]
[*]Download the linux driver from the intel site and extract package: [http://www.intel.nl/content/www/nl/nl/support/network-and-i-o/wireless-networking/000005511.html](http://www.intel.nl/content/www/nl/nl/support/network-and-i-o/wireless-networking/000005511.html)
[*]Open terminal and type: gksudo nautilus
[*]Go to: lib/firmware
[*]Delete all files that start with "iwlwifi"
[*]Copy/paste the *.ucode file from the intel package into the lib/firmware folder
[*]Reboot the computer
[/LIST]
Cheers and good luck!

---

### Post by chili555 on 2017-04-01
> **thehaguefreek said:**
> [TABLE]
[TR]
[TD="class: votecell"][CENTER]down vote[/CENTER]
[/TD]
[TD="class: answercell"]The following very simple (GUI) solution worked for me:

[LIST]
[*]Download the linux driver from the intel site and extract package: [http://www.intel.nl/content/www/nl/nl/support/network-and-i-o/wireless-networking/000005511.html](http://www.intel.nl/content/www/nl/nl/support/network-and-i-o/wireless-networking/000005511.html)
[*]Open terminal and type: sudo nautilus
[*]Go to: lib/firmware
[*]Delete all files that start with "iwlwifi"
[*]Copy/paste the *.ucode file from the intel package into the lib/firmware folder
[*]Reboot the computer
[/LIST]
Cheers and good luck!

[/TD]
[/TR]
[/TABLE]What you have proposed here is installing the firmware; not the driver. However, if the vendor, device *and subsystem* identifiers are not included in the default driver iwlwifi, then installing the 8265 firmware will not help at all. 

As well, the needed firmware is already included in later versions of the package linux-firmware. 

We only see problems when users install an older Ubuntu version where the driver was written before the introduction of the 8265 and therefore doesn't include its vendor, device *and subsystem* identifiers.

---

### Post by thehaguefreek on 2017-04-01
What do you consider an "older Ubuntu version". I'm using 16.04.

---

### Post by jeremy31 on 2017-04-01
> **thehaguefreek said:**
> What do you consider an "older Ubuntu version". I'm using 16.04.

Post the results for ```
lspci -nnk | grep -iA3 net; uname -a
```

Some newer Intel cards were not supported by the 4.4 kernel and your method of fixing the issue is not recommended

Deleting all the iwlwifi firmware is not needed as the kernel will load the newest version found and only use the firmware appropriate for your chipset.  Using sudo to open a graphical interface with root permissions is not advised, use gksudo instead

---

### Post by chili555 on 2017-04-01
> **thehaguefreek said:**
> What do you consider an "older Ubuntu version". I'm using 16.04.Your reply to the thread suggests, with no qualification, that the unsophisticated searcher can get his 8265 working with your method. It will not work in 14.04 LTS.

---

### Post by thehaguefreek on 2017-04-02
> **jeremy31 said:**
> Post the results for ```
lspci -nnk | grep -iA3 net; uname -a
```

Some newer Intel cards were not supported by the 4.4 kernel and your method of fixing the issue is not recommended

Deleting all the iwlwifi firmware is not needed as the kernel will load the newest version found and only use the firmware appropriate for your chipset.  Using sudo to open a graphical interface with root permissions is not advised, use gksudo instead

Thank you for the information. I changed my post. In my case the kernel would only load the correct firmware after deleting all others... Non of the other fixes that I'd found worked.

---

### Post by dragon-788 on 2018-03-08
I see there were some suggestions to upgrade to 16.10 or a newer release, but this isn't required to get the wireless card working, and isn't recommended if you actually want to take advantage of a manufacturer's Linux support (if it exists, Dell for example officially supports Ubuntu on some of their systems). The other reason I wouldn't upgrade anything other than the kernel is those releases between LTS versions are where Canonical (Ubuntu) tends to go a little crazy trying out new features and versions of software packages that might end up getting rolled back by the next LTS (see Upstart going away and systemd coming in between 14.04 and 16.04, and Unity going away and Gnome becoming default between 16.04 and 18.04).

You can install officially supported newer kernels on an LTS release of Ubuntu (16.04 is one, 14.04 was well, but it's kernel is capped at 4.4, the one that is default on 16.04). [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)

In order to install the newer kernel you can `sudo apt-get update && sudo apt-get install linux-image-generic-hwe-16.04` per the instructions on their wiki. [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_16.04_LTS_-_Xenial_Xerus](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_16.04_LTS_-_Xenial_Xerus)

---

