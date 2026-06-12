---
title: "Need help with my MA111 network adapter"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by RinMin on 2006-11-27
Hey, (I'm a newbie so bear with me)
I installed the newest version of Ubuntu 6.10 edgy eft
I did not do anything yet, am trying to get my internet to work. Here's what I tried:

I tried to set up my Netgear MA111 usb network adapter using [this site]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111?highlight=%28ma111%29") at ubuntu. 

I am using the v1 version of the adapter

I type in $ lsmod | grep prism and get:
prism2_usb   79236 0
usbcore 134912 7 prism2_usb, usb_storage, usbhid, libusual, ehci_hcd, uhci_hcd

the site says I should also have 
ieee80211 xxxxx 1 prism2_usb but I don't

it tells me to manually load the driver by using 
sudo modprobe prism2_usb
there is no text displayed so I don't know if anything happened or not

it tells me to add 
alias wlan0 prism2_usb to /etc/modprobe.d/wlan
but I have no such file

then I successfully installed the linux-wlan-ng package from the cd

it told me to edit the interfaces file which I did do successfully

I type in sudo ifup wlan0 and it states:
ifup: interface wlan0 already configured

Note: I typed in lsusb and the device is detected:
Bus 002 Device 003: ID 0846:4110 NetGear, Inc. MA111 WiFi (v1)

Help... I don't know why I'm having problems when it seems Ubuntu should support this adapter rather easily

---

### Post by az on 2006-11-27
Boot your computer without the device plugged in and run

tail -f /var/log/messages

Then, plug in the device and post the output.

---

### Post by RinMin on 2006-11-28
Alright... here's the output:

Nov 28 11:46:19 aaron-desktop kernel: [17179631.392000] NTFS volume version 3.1.
Nov 28 11:46:24 aaron-desktop kernel: [17179635.756000]   Vendor: Kingston  Model: DataTraveler 2.0  Rev: 1.00
Nov 28 11:46:24 aaron-desktop kernel: [17179635.756000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Nov 28 11:46:24 aaron-desktop kernel: [17179636.048000] SCSI device sdc: 492544 512-byte hdwr sectors (252 MB)
Nov 28 11:46:24 aaron-desktop kernel: [17179636.048000] sdc: Write Protect is off
Nov 28 11:46:24 aaron-desktop kernel: [17179636.052000] SCSI device sdc: 492544 512-byte hdwr sectors (252 MB)
Nov 28 11:46:24 aaron-desktop kernel: [17179636.052000] sdc: Write Protect is off
Nov 28 11:46:24 aaron-desktop kernel: [17179636.052000]  sdc: sdc1
Nov 28 11:46:24 aaron-desktop kernel: [17179636.052000] sd 3:0:0:0: Attached scsi removable disk sdc
Nov 28 11:46:24 aaron-desktop kernel: [17179636.052000] sd 3:0:0:0: Attached scsi generic sg2 type 0

(Here's where I plugged it in)
Nov 28 11:47:28 aaron-desktop kernel: [17179699.824000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Nov 28 11:47:28 aaron-desktop kernel: [17179699.988000] usb 2-1: configuration #1 chosen from 1 choice
Nov 28 11:47:28 aaron-desktop kernel: [17179700.104000] prism2usb_init: prism2_usb.o: 0.2.5 Loaded
Nov 28 11:47:28 aaron-desktop kernel: [17179700.104000] prism2usb_init: dev_info is: prism2_usb
Nov 28 11:47:28 aaron-desktop kernel: [17179700.104000] usbcore: registered new driver prism2_usb
Nov 28 11:47:28 aaron-desktop kernel: [17179700.388000] ident: nic h/w: id=0x8026 1.0.0
Nov 28 11:47:28 aaron-desktop kernel: [17179700.392000] ident: pri f/w: id=0x15 1.1.3
Nov 28 11:47:28 aaron-desktop kernel: [17179700.392000] ident: sta f/w: id=0x1f 1.7.0
Nov 28 11:47:28 aaron-desktop kernel: [17179700.392000] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
Nov 28 11:47:28 aaron-desktop kernel: [17179700.392000] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
Nov 28 11:47:28 aaron-desktop kernel: [17179700.396000] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
Nov 28 11:47:28 aaron-desktop kernel: [17179700.396000] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/12
Nov 28 11:47:28 aaron-desktop kernel: [17179700.396000] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
Nov 28 11:47:28 aaron-desktop kernel: [17179700.396000] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
Nov 28 11:47:28 aaron-desktop kernel: [17179700.400000] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
Nov 28 11:47:28 aaron-desktop kernel: [17179700.400000] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00
Nov 28 11:47:28 aaron-desktop kernel: [17179700.456000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by az on 2006-11-28
> **RinMin said:**
> it told me to edit the interfaces file which I did do successfully

Are you sure?

The driver is loading properly (as per the text you posted).  The link says that it is not ready.  Did you type in the WEP in the proper format?  This driver is very finnicky.

You should not need to bring the link up - it should come up as you plug the thing in and it should come down when you remove it.

---

### Post by RinMin on 2006-11-28
Are you saying that the hardware is working correctly, but not connecting to my network? I'll try removing the WEP key and seeing if I can connect.

---

### Post by RinMin on 2006-11-28
Alright, I still can't connect to the network.
i tried removing the WEP key and that didn't work.
I also tried using a 64bit instead of a 128bit WEP key... nope.
I tried to ping the router but it said connect: Network is uncreachable
I tried enabling the wired connection under network settings and then disabling it... nothing.
I am sure everything is labeled correctly. 

Is there anyway to see what wireless networks are detected?

---

### Post by az on 2006-11-29
> **RinMin said:**
> Alright, I still can't connect to the network.
i tried removing the WEP key and that didn't work.
I also tried using a 64bit instead of a 128bit WEP key... nope.
I tried to ping the router but it said connect: Network is uncreachable
I tried enabling the wired connection under network settings and then disabling it... nothing.
I am sure everything is labeled correctly. 


Did you unplug and then plug back the device every time you made changes?  I dunno why it's not working.  There is a firmware package available for the prism2 devices, but I don't really think it's necessary, though.

---

### Post by FrodoB on 2006-11-29
Can you try a Dapper live CD to check this. There is a bug in Edgy for prism2 devices using the PCI bus, and maybe that also applies to this one as well?

Any way, sorry to but in here, but this is a serious issue with the ma311 on PCI, and I thought it might be applicable here as well.

---

### Post by RinMin on 2006-12-01
Not quite sure what you mean. Do you mean the desktop cd or the alternative install cd? Also, are you saying I should try to install it or just reload the linux-wlan-ng package? A while ago I tried using the adapter with a 6.06 version and it didn't work then either.

---

### Post by FrodoB on 2006-12-01
Alright, just hoping. I will defer to you folks now. Thanks for trying my hunch, sorry that it did not help you.

---

### Post by peril blue on 2006-12-13
i got the same problem. no faq i have read has successfully told me how to configure the wireless and keep it running. i was able to get my ma111 running fine after 2 bootups, but required so much work i forgot how it was configured in the first place. any help would be much appreciate.

this sucks after all the hell i went through for me to get compiz running, i have to get rid of ubuntu because of something so simple.

---

