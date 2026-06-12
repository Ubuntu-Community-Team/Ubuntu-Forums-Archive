---
title: "Offline activation of r8125 for Ethernet connection failts"
date: 2021-02-21
forum: Networking &amp; Wireless
---

### Post by 216ann on 2021-02-21
Hi, tried posting my question on another forum ([https://askubuntu.com/questions/1317814/trying-to-fresh-install-ubuntu-20-04-lts-on-new-computer-without-os-but-cant-in](https://askubuntu.com/questions/1317814/trying-to-fresh-install-ubuntu-20-04-lts-on-new-computer-without-os-but-cant-in)) but have not found an answer.
Apparently many have been in a similar boat (eg, [https://forum.manjaro.org/t/no-ethernet-with-rtl8125/37122/24](https://forum.manjaro.org/t/no-ethernet-with-rtl8125/37122/24)).

Briefly, I am a noob who is trying to activate r8125 driver offline to get Ethernet internet on my "Try Ubuntu" Live USB (Ubuntu 20.04.1 LTS) so that during installation on a new computer, it will auto update and add all the necessary 3rd party stuff.
My kernel is: 5.4.0-42-generic
Both the opensource r8169 & nouveau drivers have chip errors recognizing my Ethernet and Nvidia Graphics.
My ethernet is "UNCLAIMED"

I tried several methods such as:
a) using bluetooth tethering to my phone and tried activating USB Wifi adaptor

b) to blacklist r8169 and ./autorun.sh r8125 according to instructions such as here: [https://askubuntu.com/questions/1259947/cant-get-rtl8125b-working-on-20-04](https://askubuntu.com/questions/1259947/cant-get-rtl8125b-working-on-20-04)   
and [https://forum.manjaro.org/t/no-ethernet-with-rtl8125/37122/4](https://forum.manjaro.org/t/no-ethernet-with-rtl8125/37122/4)  
And [https://www.reddit.com/r/linux/comments/jm3us1/msi_x570_tomahawk_motherboard_ethernet_issues/](https://www.reddit.com/r/linux/comments/jm3us1/msi_x570_tomahawk_motherboard_ethernet_issues/)
Although I did NOT change my kernel at all.  
I grabbed the driver from: [https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software](https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software)
But using the README instructions, such as extracting the tar.bz2 contents resulted in: 
```
sudo: ./autorun.sh: command not found
```

b) to unzip & load a dkms package, such as described here: [https://bbs.archlinux.org/viewtopic.php?id=262120](https://bbs.archlinux.org/viewtopic.php?id=262120)
sudo cp -R /path.to/source/ /usr/src/r8125-9.003.05
It also says command not found 

I tried using the command in each parent/child dir as well as manually using the paths of each.  
I am not sure if I can't do this with a "Try Ubuntu" Live USB...perhaps it may be easier to install the Ubuntu on the new computer offline then try to load the r8125???
For example, if doing a process above requires rebooting, wouldn't the Live USB "lose" all the modifications?

I am thinking that the answer may be here:
[https://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline](https://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline)
But it is awfully confusing and I don't want to screw up
Please help.  Thank you.

---

### Post by howefield on 2021-02-21
Thread moved to the "*Networking & Wireless*" forum, probably a better fit.

---

### Post by 216ann on 2021-03-04
Say @howefield, I am wondering how I could help with my issue.  Did I do something wrong?  Why is noone replying?

---

### Post by mikewhatever on 2021-03-05
To extract the archive, you need to run <tar -xf filename.tar.bz2>. If successful, it should produce a folder, let's say, r8125. 
Then you'd change to that folder with <cd r8125>, and check if "autorun.sh" is there with the <ls> command.
If "autorun.sh" is there, try to run <sudo: ./autorun.sh>.

---

### Post by CelticWarrior on 2021-03-05
As above, but keep in mind that third-party drivers installed in a live session won't be in thew installed system.
As it's also strongly suggested to disable Secure Boot in UEFI as that is probably what is preventing many proprietary (and unsigned) drivers to load properly.

---

### Post by praseodym on 2021-03-06
[https://media-cdn.ubuntu-de.org/forum/attachments/27/49/9210307-r8125-dkms_9.004.01.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/27/49/9210307-r8125-dkms_9.004.01.tar.gz)

Download this one, save in /home, open a new terminal and run

```
sudo tar xvf 9210307-r8125-dkms_9.004.01.tar.gz -C /usr/src
sudo dkms add -m r8125 -v 9.004.01
sudo dkms build -m r8125 -v 9.004.01
sudo dkms install -m r8125 -v 9.004.01 
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee /etc/modprobe.d/blacklist_r8169.conf 
sudo modprobe -v r8125 
```

---

