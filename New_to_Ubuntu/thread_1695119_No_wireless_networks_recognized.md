---
title: "No wireless networks recognized"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by vanoost9 on 2011-02-25
I have a Toshiba Mini Netbook NB505, and just made the switch from Windows 7 to Ubuntu 10.10. I was able to connect to the internet via my wireless modem through Windows 7, but Ubuntu doesn't seem to recognize any wireless networks (none are listed in "Network Connections"). I am able to connect via ethernet cable in Ubuntu, however. I've read a number of threads regarding similar problems, but the solutions seem to be above my technical capacity (quite limited). Thus far, I've attempted to enable my wireless card via a button on my keyboard, but this seems to have no effect. Another thread suggested the code "rfkill unblock all," but when I type it in Terminal, it also seems to have no effect.

Yet another thread suggested "ifconfig eth0 up," but when I type this in, Terminal lists "Permission denied." Another thread suggested "sudo ifconfig eth0 up," and I get a password prompt, but when I attempt to type, nothing works.

When I open "Additional Drivers," it says no proprietary drives recognized.

I'm truly at a loss. I'm sure a solution is out there, but I can't seem to find it. Any help would be greatly appreciated.

---

### Post by migs73 on 2011-02-25
> **vanoost9 said:**
> 

Yet another thread suggested "ifconfig eth0 up," but when I type this in, Terminal lists "Permission denied." Another thread suggested "sudo ifconfig eth0 up," and I get a password prompt, but when I attempt to type, nothing works.

When I open "Additional Drivers," it says no proprietary drives recognized.

When you password is requested in terminal, there is nothing that appears as you type. Try again and type your password and press enter.

The 'Additional Drivers' will only work if you are connected to the internet (it would need to be wired in your case!) I would try this first.

If you are still having problems, open a terminal and type;
```
lspci
```

This will show us some of your hardware, most importantly your wireless. Cut and paste the results back here in code tags (click on the # at the top of the Reply to Thread box) that makes it easier for us to see (it'll end up in a nice box with scroll bars, like the one I have above for 'lspci')


Mike

---

### Post by vanoost9 on 2011-02-25
Mike,

Thanks very much for your quick reply. Even after typing my password, the commands I mentioned in the above post seem to have no effect. I am currently connected via ethernet, and Additional Drivers still finds no proprietary drivers. Here is the hardware rundown you requested:

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

Again, thanks for your help, and I look forward to your reply.

Aaron

---

### Post by vivek.pandey on 2011-02-25
type this command on terminal 
lsusb

and check whether your modem is listed there

(your modem should be a usb modem though which is in most cases)

---

### Post by vanoost9 on 2011-02-25
When I typed in "lsusb," the following came up:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Aaron

---

### Post by vivek.pandey on 2011-02-26
> **vanoost9 said:**
> When I typed in "lsusb," the following came up:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Aaron

there is something chicony electronics in you output you posted.. is it you modem or some other usb device... you can check this by taking out your modem and again typing lsusb and comparing the results

---

### Post by vanoost9 on 2011-02-27
I'm sorry, neo-aryan, I misunderstood your first request. I don't have a USB modem (i.e., one that attaches externally via a USB port, yes?). I presume my modem is internal.

---

### Post by grahammechanical on 2011-02-27
First, the command sudo ifconfig eth0 up will switch on the first ethernet adapter. You may have two. They will be called eth0 and eth1. Do you understand? The wireless adapter is not an ethernet device. The command you could have used is sudo ifconfig wlan0 up.

But do you need to? You say:

> Ubuntu doesn't seem to recognize any wireless networks (none are listed in "Network Connections")

Is this when you left click the network icon? What do you see when you right click the icon? Do you see Enable Wireless? Is there a tick mark against it? If not, then put one there. This will switch on the wireless adapter. With a bit of luck!

Oh, by the way, that button on the keyboard - it does have an effect. It switches off the wireless adapter on the motherboard. You must switch it on before the OS loads otherwise the OS will not know that you have any hardware capable of using a wireless connection. It will not make it possible to set up a wireless connection.

This could be the reason that Additional Drivers does not recommend activating a driver and also why there are no wireless networks listed as available.

Regards.

---

### Post by vanoost9 on 2011-03-01
Sorry for the delayed response. I had read in another forum that computers with Realtek wireless cards typically needed a new driver upon making the switch from Windows 7 to Ubuntu 10.10. So, I contacted Realtek directly, and they sent me the driver RTL8192CE. I found the installation instructions a bit impenetrable, however, and gave up that avenue.

I then looked through other threads regarding this driver, and found one here: [http://ubuntuforums.org/showthread.php?t=1604101&page=3](http://ubuntuforums.org/showthread.php?t=1604101&page=3)

Specifically, I followed this user's instructions:

"canucked:

I just created a thread about a laptop I configured which used the Realtek RTL8188CE wireless adapter.

[http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

Most solutions I found involved compiling the Realtek driver, downloaded  from Realtek's website.  However, this would have to be done each time a  new kernel is installed.

Fortunately, someone has created a PPA which automagically installs the  Realtek driver when a new kernel is installed.  (Since you are new to  Ubuntu, I would suggest reading about PPAs, and understand that they are  not officially supported by Canonical.)

To install support for the Realtek RTL8188CE, run the following in Terminal:
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms

Note that the RTL8192CE driver is installed.  Reboot, and see if wireless now works!

I hope this works for you!"

So, I typed the above three commands in Terminal. It seemed to freeze up Terminal, so, after roughly 10 minutes of waiting, I shut Terminal down and rebooted. Following the reboot, I could see all available wireless networks when I left-clicked the internet connection icon at the top right of the screen. I was able to sign into my network, and access the internet. After roughly 10 seconds, however, my connection was dropped. Any suggestions?

---

### Post by vanoost9 on 2011-03-29
After I had published the previous post, I attempted to wirelessly connect to the Internet on my local university campus, and was able to do so quickly and without being periodically dropped. At first, I attributed this to the fact my campus network assigns an IP address. Soon after, however, I took a research trip to Mexico where, surprisingly, I had virtually no wireless complications (i.e., I was able to connect to various wireless networks, both commercial and private, quickly and without being periodically dropped) even without being assigned an IP address to my knowledge. It seems the problems lies solely with my home wireless network. It's not a matter of physical distance from the wireless modem, as I lose my connection in roughly the same intervals regardless of where I sit. Perhaps interference from other, nearby networks?

Regardless, I'm willing to label this thread "solved," as I'm able to connect wirelessly without difficulty in most places. For the solution I found helpful, see my previous post. Thanks to all for your help.

---

