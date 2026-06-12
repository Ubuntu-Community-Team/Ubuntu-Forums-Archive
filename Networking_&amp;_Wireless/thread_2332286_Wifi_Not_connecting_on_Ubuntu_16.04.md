---
title: "Wifi Not connecting on Ubuntu 16.04"
date: 2016-07-30
forum: Networking &amp; Wireless
---

### Post by ganesh3 on 2016-07-30
Hi,

The Wifi is not enabled at all suddenly whereas it was working couple of days back. Not sure what is the issue.

I am on Ubuntu 16.04 with kernel version 4.4.0-31.

lspci output:```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 7310]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 1)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 05)
```

iwconfig output:

iwconfiglo        no wireless extensions.
enx00a0c60690e0  no wireless extensions.
eno1      no wireless extensions.

ifconfig -a output file
```
eno1      Link encap:Ethernet  HWaddr 28:92:4a:43:f7:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enx00a0c60690e0 Link encap:Ethernet  HWaddr 00:a0:c6:06:90:e0  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::77fe:8cb:89cb:56ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16590466 (16.5 MB)  TX bytes:2837267 (2.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:265533 (265.5 KB)  TX bytes:265533 (265.5 KB)

```



I tried installing a driver from as per this site: [http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working/253660#253660](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working/253660#253660) but was getting a compile/make error even after making changes to the config and the .C file.

Can someone please help on this issue?



Thanks

Ganesh

---

### Post by kyrithis on 2016-07-30
Well, the obvious issue *appears* to be a simple lack of a driver for the device. The system is not detecting/able to use a Wireless Device. Let's see what we can do here, shall we?

First off, I'd like to take another try at installing the driver. Here's a much simpler guide to installing the RT3290 driver:

 
[LIST]
[*]Download the source code of the driver:
  wget [http://dl.dropbox.com/u/11876059/DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz](http://dl.dropbox.com/u/11876059/DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz)

[*]then extract the file from tar file
  tar -xvf DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz

[*]after that enter to this dir 
  cd ~/DPO_RT3290_LinuxSTA_V2600_20120508
make    
# compile the make file
sudo make install
# install the make file
[*]After that activate the wireless driver
  sudo modprobe rt3290sta
[/LIST]

---

### Post by ganesh3 on 2016-07-30
[ATTACH=CONFIG]270444[/ATTACH]


Attaching screenshot of the error

---

### Post by kyrithis on 2016-07-30
Try putting it on a pastebin and linking it here, or use CODE tags.

---

### Post by jeremy31 on 2016-07-30
Please see the wireless script link in my signature and post your results.

---

### Post by ganesh3 on 2016-07-30
wireless info txt file added as attachment.

The Code tags are not working for sharing the error and hence have shared screenshot.

---

### Post by jeremy31 on 2016-07-30
I would check in BIOS and see if the WLAN is enabled as the script results show no wireless device connected with the exception of the cellular dongle.  If you can't find any setting to enable wireless in BIOS, I would remove the wifi card from the laptop after the laptop is powered down and power cable and battery removed.  The reinstall the wifi card and boot as it may be an issue with the wifi cards connection to the motherboard

---

### Post by ganesh3 on 2016-08-06
Hi, 

Now the ethernet is also disabled. 

What do I do? 


Thanks 

Ganesh Bhat

---

### Post by jeremy31 on 2016-08-06
Can you run the script again with ```
./wireless-info
``` and post new results

Did you make any changes in BIOS?

---

### Post by ganesh3 on 2016-08-18
No Changes in BIOS.

Attaching wireless info file.[ATTACH]270731[/ATTACH]

---

### Post by jeremy31 on 2016-08-21
Reboot and press the SHIFT key until the GRUB menu appears, scroll to advanced options for Ubuntu and select an older kernel to boot to and see if networking is restored

---

### Post by ganesh3 on 2016-08-21
Tried with older kernel also.... Didn't work.

---

### Post by jeremy31 on 2016-08-22
You could try removing and reinserting the wifi card to see if it works but if that doesn't work, it is likely a hardware failure

---

### Post by ganesh3 on 2016-09-12
So I did a complete re-install of Ubuntu 16.04 and the Wifi started  working but the Ethernet still did not work (Ethernet Network  disconnected) in the nm-applet. So I opened my laptop to check if  everything is fine with the Hardware and it did look fine but the  Ethernet still did not work.

So I decided to buy a new Laptop as  my current laptop was more than 4 years old. But guess what the new  laptop also has the Ethernet issue. The Ethernet Network is disconnect  in the nm-applet. I am sharing the wireless-info for the new laptop.

Please let me know how can I resolve it now. Its a Lenovo Ideapad 100 14-inch with Intel i3.

There  is also an issue with the Wifi as it disconnects with the existing  connection yet the nm-applet shows connected and I have to disconnect  manually and connect again. Everytime I connect with the same Wifi it  asks me for password everytime. You will see that in the wireless info  files with "Wifi Name (masked) 1", " Wifi Name (masked) 2)".... 


Thanks

Ganesh Bhat


[ATTACH]271099[/ATTACH]

lspci output for new laptop

```
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 08)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
```

---

### Post by ganesh3 on 2016-09-15
Dear All,

Since there has been no response. Can this thread be marked unsolved?

I will like to open a new thread for my new laptop by referencing to this thread since I do not see any respond to this thread.

Please let me know.


Regards,
Ganesh

---

### Post by howefield on 2016-09-15
> **ganesh3 said:**
> Since there has been no response. Can this thread be marked unsolved?

I will like to open a new thread for my new laptop by referencing to this thread since I do not see any respond to this thread.

The thread hasn't been marked solved, so it cannot be unmarked.

If you have a separate issue, ie on a different laptop, feel free to create a new thread and reference this one if needs be. 

Just don't continue this one in a new thread.

---

### Post by jeremy31 on 2016-09-15
For the new laptop try ```
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Then reboot

---

### Post by ganesh3 on 2016-09-16
Ok. Will keep this open and will open a new thread for the new laptop with reference to this.

Thanks Jeremy!!!

---

