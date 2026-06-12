---
title: "Ubuntu 14.04 LTS Can't get Broadcom BCM4318 to work"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by shawnerz on 2014-08-24
First off, I will apologize.  I know this has been solved many times.  I've had this laptop since 2007 and I'm sure the people who spend a lot of time in the forums are tired of seeing people make this same post.  
I've read the sticky's, but I still can not get Ubuntu to "see" the Wi-Fi card.  The wi-fi card was working great in Ubunto 10 LTS.  Then, I went to version 12 (for about a week) and then I went to 14.  Ever since I left version 10, I cannot get my WI-FI card to work again.  For this post, I am running Windows.

I have limited Internet access.  When I do have access, I have Wi-Fi only.  No "cord" access.  I have the Ubuntu 14 ISO burned to disc.

I am doing this from memory, so things will not be exactly correct.  

I copied the b43-fwcutter...deb from the /pool/main/b folder and put it in my /home/Downloads folder.
I also copied the /bcm43...deb from the /pool/restricted/b/ folder and put it in my /home/Downloads folder.

I then ran sudo dpkg -i /b43.....deb and then followed by sudo dpkg -i /bcm....deb  The firmware installs without an error.  The driver mostly installs without an error. DPMS (?) says it installed, but I have to hit ctrl-c to get a command prompt.

After several reboots, Ubuntu does not "see" the Wi-Fi card.  
I've also tried the --force-all option with dpkg.  I get the same results.  If I had corded access, it could just use apt-get and download what I need.  But no access makes things difficult.
Any ideas?
Thanks in advance,
-Shawn

---

### Post by Hadaka on 2014-08-24
Hi, since you have no internet let's make this as painless as possible
please copy and paste the following,
```
lspci -n | egrep '0200|0280' | awk '{print$3}'
lsmod |awk '{print$1}'| grep -i "wl"
rfkill list all | grep -i "yes"
```
thanks

---

### Post by Takashi_Kosaka on 2014-12-23
I have tried to clean install 14.04 by CD in my laptop (HP ze2000 BCM4318).
During installing OS, the installation stops at the setting bcmwl-kernel-source (i386).
Detail says that:
Dec xx:xx:xx ubuntu kernel: [10B95.944B07] ACPI: \SB_.PCI0.LPC0.ACAD: APCI_NOTIFY_BUS_CHECK event: unspported 
Dec xx:xx:xx ubuntu kernel: [10B79.073641] ACPI: \SB_.PCI0.LPC0.ACAD: APCI_NOTIFY_BUS_CHECK event: unspported
....

---

### Post by Hadaka on 2014-12-23
@Takashi_Kosaka

Please start your own thread to avoid confusion.
thanks.

---

### Post by praseodym on 2014-12-23
You need this firmware file 
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot. The others lack the files **ucode4/5.fw**

---

### Post by Takashi_Kosaka on 2014-12-23
@hadaka
I am sorry. But I want to say the followings:
I could install firmware and drivers for bcm4318 on 12.04 in early 2014. But when I try clean installation  12.04 and I try 

sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get --reinstall install bcmwl-kernel-source

and then I have the same problem as the 
>  DPMS (?) says it installed, but I have to hit ctrl-c to get a command prompt.

I try to install 14.04 from CD.  My installation still tries to set bcmwl-kernel-source (almost 6 hours) 

I think that the reason of the problem comes from bcmwl-kernel-source in ubuntu site.

---

### Post by praseodym on 2014-12-23
It works with the native driver and the firmware from above. STA is not needed

---

### Post by Hadaka on 2014-12-23
@takahashi
STOP doing this...
```
sudo apt-get --reinstall install bcmwl-kernel-source

```
that is incorrect as is the driver ubuntu offers in additional drivers
IGNORE the offer from additiona driver,
first...do this...
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get --reinstall install firmware-b43-installer
sudo modprobe b43
```
boot
You should have a working wireless. if you do not.
then open a new thread,instead of hijacking someone elses.
thanks

---

### Post by jeremy31 on 2014-12-23
> **Hadaka said:**
> @takahashi
STOP doing this...
```
sudo apt-get --reinstall install bcmwl-kernel-source

```
that is incorrect as is the driver ubuntu offers in additional drivers
IGNORE the offer from additiona driver,
first...do this...
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get --reinstall install firmware-b43-installer
sudo modprobe b43
```
boot
You should have a working wireless. if you do not.
then open a new thread,instead of hijacking someone elses.
thanks

I will try to explain Hadaka's reasoning as it might be difficult for some to understand.  The additional driver bcmwl-kernel-source, when installed will remove a few drivers and blacklist(but not delete) them and that will interfere with any good that may come from installing firmware-b43-installer

There are other names for similar packages to bcmwl-kernel-source such as broadcom-sta-common and broadcom-sta-dkms

---

### Post by Takashi_Kosaka on 2014-12-23
@  praseddym @hadaka
You are right. However, update process and installing process automatically tries to install bcmwl-kernel-source.
In case of 12.04 clean installing and update process,
when the update tries to set bcmwl-kernel-source, the screen is crashed.  Also ubuntu can not become shutting down.
After I shut down power and boot (Because I can not operate normal shut down).
I have tried on 12.04
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get --reinstall install firmware-b43-installer
sudo modprobe b43

It works. 
Thank you.

BTW, in case of the clean installing 14.04 from CD,
the installing process also tries to set bcmwl-kernel-source. And the installation process stops and never finished.

---

