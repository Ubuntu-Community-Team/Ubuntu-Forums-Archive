---
title: "Help booting from flash drive"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by dcboratko on 2011-04-23
Hello,
My netbook is an eeePC 1005HA that came with windows XP.  I installed eeebuntu on it a while ago, but want to switch to ubuntu netbook 10.10 or ubuntu standard 10.10.  I downloaded the iso and followed the instructions on the ubuntu.com website, but I am having trouble getting my netbook to recognize the flash drive as a bootable device.  I have some experience with this before; I used this method to install eeebuntu on my netbook in the first place.  I have tried using unetbootin and universal usb installer to mount the iso on my flash drive and I formatted it to FAT32.  It is an 8gb flash drive and I just bought it today.  Both unetbootin and the universal usb installer complete the process with no errors and say it is ready to boot.  I have also tried using the utility that came with eeebuntu and it also reported no errors.  My desktop running windows 7 also will not recognize the usb as a bootable device.  I have gone into the BIOS on both my 1005HA and my desktop and tried to edit the boot order to no avail.  Can anyone offer me any suggestions?
Thank you

---

### Post by dcboratko on 2011-04-23
Hello,
My netbook is an eeePC 1005HA that came with windows XP. I installed eeebuntu on it a while ago, but want to switch to ubuntu netbook 10.10 or ubuntu standard 10.10. I downloaded the iso and followed the instructions on the ubuntu.com website, but I am having trouble getting my netbook to recognize the flash drive as a bootable device. I have some experience with this before; I used this method to install eeebuntu on my netbook in the first place. I have tried using unetbootin and universal usb installer to mount the iso on my flash drive and I formatted it to FAT32. It is an 8gb flash drive and I just bought it today. Both unetbootin and the universal usb installer complete the process with no errors and say it is ready to boot. I have also tried using the utility that came with eeebuntu and it also reported no errors. My desktop running windows 7 also will not recognize the usb as a bootable device. I have gone into the BIOS on both my 1005HA and my desktop and tried to edit the boot order to no avail. Can anyone offer me any suggestions?
Thank you

---

### Post by wilee-nilee on 2011-04-23
By default the 1005HA has something called 'Boot Booster' enabled which might prevent you from booting using a USB-Stick. To disable this go into the BIOS by repeatedly pressing F2 after turning on the Eee PC. Don't change anything and just press F10 to save and exit from the BIOS. After having exited repeatedly press ESC to get into the boot device selection screen. Once there just select your USB-Stick. When the UNetBootin menu pops up you should choose 'Default' and then wait untill crunchbang has started up. T

The link.
[http://crunchbanglinux.org/forums/topic/3954/asus-eee-pc-1005ha-crunchbang-installation-guide/](http://crunchbanglinux.org/forums/topic/3954/asus-eee-pc-1005ha-crunchbang-installation-guide/)

I was mainly looking for the per session key prompt for the boot from menu outside of the bios it appears, to be esc on the eee on my acer it is f12.

---

### Post by dcboratko on 2011-04-23
Hello,
My netbook is an eeePC 1005HA that came with windows XP. I installed eeebuntu on it a while ago, but want to switch to ubuntu netbook 10.10 or ubuntu standard 10.10. I downloaded the iso and followed the instructions on the ubuntu.com website, but I am having trouble getting my netbook to recognize the flash drive as a bootable device. I have some experience with this before; I used this method to install eeebuntu on my netbook in the first place. I have tried using unetbootin and universal usb installer to mount the iso on my flash drive and I formatted it to FAT32. It is an 8gb flash drive and I just bought it today. Both unetbootin and the universal usb installer complete the process with no errors and say it is ready to boot. I have also tried using the utility that came with eeebuntu and it also reported no errors. My desktop running windows 7 also will not recognize the usb as a bootable device. I have gone into the BIOS on both my 1005HA and my desktop and tried to edit the boot order to no avail. Can anyone offer me any suggestions?
Thank you:confused:

---

### Post by heyandy889 on 2011-04-23
Hi dcboratko. Here are my initial thoughts

-Your "boot order" might be incorrect. Try watching the first splash screen and searching for a boot-order key, like F12 or F2. Pressing the key should take you into a menu-looking screen (inside the computer's BIOS). Your options might be hard disk drive HDD or USB, you will want to choose USB. :-D

-The USB drive might not be correctly formatted as a bootable drive. There is a nice tutorial on installing Ubuntu on ubuntu.com, take a look at "Get Ubuntu Desktop Edition" [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Good luck, dude. :-D

---

### Post by cariboo on 2011-04-23
Please don't create multiple threads on the same subject, I have merged your three threads.

---

