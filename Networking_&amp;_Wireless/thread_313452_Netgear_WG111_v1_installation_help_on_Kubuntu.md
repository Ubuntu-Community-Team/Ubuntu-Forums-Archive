---
title: "Netgear WG111 v1 installation help on Kubuntu"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by Jamson on 2006-12-06
Hi,

I am desperate to switch to linux (job requires it) and i want to get my Netgear WG111 to work with Kubuntu 6.10! I have had a play around with the Live CD and it's great.

Can i get a step-by-step instructions for it? The easier the better.

Thanks team :-D

---

### Post by FrodoB on 2006-12-06
I retract my previous statement, thinking about the wrong card, see:

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29)
[]("https://help.ubuntu.com/community/WifiDocs")

---

### Post by AAM on 2006-12-06
Hi Jamson,

I am using a Netgear WG111 at this very instant to access my wireless network for broadband. So the first think to say is that it can be done!

You will need to use ndiswrapper to wrap the Win drivers. If WG111 use is you pre-eminent problem, then I would suggest the following process:
[LIST=1]
[*]do a lot of research on setting up the device before you do anything. This will include how to install ndiswrapper, which drivers to use, and how to wrap them and then 'insert' them into the kernel, and then how to activate the access point.
[*]try your new instructions while running the LiveCD, if this works, record all the steps you take and then repeat them after the installation. If it does not work, make a new partition and install Kubuntu, and then get to work trouble shooting. You may wish to re-install Kubuntu over and over until you have the WG111 installation procedure written down completely.
[*]make sure that you have internet access throughout the process to be able to check new issues as they arise.
[*]be prepared to adapt other people's procedures, but record everything you do.
[/LIST]

Here is a list of what I can find about what I did:

[LIST=1]
[*]take the Netgear WG111 out of the USB port
[*]install Kubuntu (first time use the LiveCD, then install if no joy)
[*]copy the Win drivers into a convenient place, like /home/jamson/. Make sure that you have all the files (is there a ndis directory on the driver CD?) including *.inf and *.sys in the same place.
[*]backlist default drivers
```
sudo gedit etc/modprobe.d/blacklist

*add to the bottom of the file the following*
[B]blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb[/B]
```
[*]install ndiswrapper
you will find the ndiswrapper package in the CD directory (**/pool/main/n/ndiswrapper**), install it.
[*]configure ndiswrapper
In a terminal window type the following lines:
```
cd /home/jamson/ (*change to directory where stored the Win drivers*)
sudo ndiswrapper -i netwg111.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```
[*]edit preferences
Open first file
```
sudo gedit /etc/iftab

*add to the bottom of the file*
**wlan0 mac 00:00:AA:BB:CC:DD** 
(substitute the MAC of your dongle, its on the side!)
```
Open the second file
```
sudo gedit /etc/modules

*add to the bottom of the file*
**ndiswrapper**
```
[*]insert WG111
reboot, and the light should be on
[*]configure network, this is where I get a little hazy. I would suggest that you unprotect your wireless network until such time as you are connected reliably, then use WEP or WPA ... but that's a later problem. Hopefully by this time, things will be working.
[/LIST]
I did this configuration some time ago. All 4 PCs here are running WG111s to access the wireless access and have been faultless for the last 6 months.

Good luck! I hope that this is a help,

AAM

---

