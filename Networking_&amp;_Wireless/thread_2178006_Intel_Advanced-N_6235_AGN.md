---
title: "Intel Advanced-N 6235 AGN"
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by sharathcshekhar on 2013-10-01
Hi All,
I am using a Dell XPS 14 Ultrabook with Intel Advanced-N 6235 AGN Wifi card. My firmware version is 18.168.6.1 and Kernel version is 3.8.
My wifi driver keeps crashing with "Unable to load microcode" error. This seems to be common problem and it is reported in many places including the mainline kernel bug tracking system. I keep seeing traces like this when the wifi driver crashes:
```

[  977.571861] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  977.628124] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[  983.292777] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[  983.292793] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[  983.292805] iwlwifi 0000:02:00.0: Failed to start RT ucode: -110
[  983.666070] iwlwifi 0000:02:00.0: Unable to initialize device.
[  983.669138] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  983.725054] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[  989.392508] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[  989.392523] iwlwifi 0000:02:00.0: Could not load the [0] uCode section

```

None of the often suggested solutions like disabling 802.11n, power save option etc., has worked. I also tried the latest mainline RC kernel and it is not fixed. According to intel site,
[http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm]("http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm") I am already using the latest firmware version for my model.
As a last resort, I wanted to try out the previous version of the firmaware. I am not even sure if this is a good idea. Can someone advice me on this? Also five me pointers to install older firmware versions? Or any better solutions I can try out. If you need any more logs/test results I will be happy to do it.

Thanks and Regards,
Sharath

---

### Post by chili555 on 2013-10-01
The boys in the back room think I am the resident Intel go-to guy. I think it's more like they think your problem looks too hard and they are in a mood to nap today! OK, let's give it a try. Happy, guys??

What firmware does the card want?```
modinfo iwlwifi
```On my machine, it's:> firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
[COLOR="#FF0000"]firmware:       iwlwifi-6000g2b-6.ucode[/COLOR]
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
What firmware does Intel offer? [http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi) > Intel® Centrino® Advanced-N 6235
	

iwlwifi-6000g2b-ucode-18.168.6.1.tgz So far, so good.

Do you have the proper firmware and the correct permissions?```
ls -al /lib/firmware | grep iwlwifi
```I have, among others:> -rw-r--r--  1 root root  679436 Nov  8  2012 iwlwifi-6000g2b-6.ucodeThose little r's say it's readable.

Before we take stronger measures, does everything on your system match?

---

### Post by sharathcshekhar on 2013-10-02
Hi chili555,
Thank you (and the backroom guys :) ) so much for your reply!
modeinfo:
```

 modinfo iwlwifi
filename:       /lib/modules/3.5.0-40-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
alias:          iwlagn
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
srcversion:     D1BB8599EF9DF793A499F9E

```

Yes, I think I have the latest firmware intel offers. Here is my output:
```

ls -al /lib/firmware | grep iwlwifi
-rw-r--r--  1 root root 330K Nov  8  2012 iwlwifi-1000-5.ucode
-rw-r--r--  1 root root 330K Nov  8  2012 iwlwifi-100-5.ucode
-rw-r--r--  1 root root 674K Nov  8  2012 iwlwifi-105-6.ucode
-rw-r--r--  1 root root 685K Nov  8  2012 iwlwifi-135-6.ucode
-rw-r--r--  1 root root 680K Nov  8  2012 iwlwifi-2000-6.ucode
-rw-r--r--  1 root root 691K Nov  8  2012 iwlwifi-2030-6.ucode
-rw-r--r--  1 root root 147K Nov  8  2012 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root 184K Nov  8  2012 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root 333K Nov  8  2012 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root 330K Nov  8  2012 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root 444K Nov  8  2012 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root 434K Nov  8  2012 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root 662K Nov  8  2012 iwlwifi-6000g2a-6.ucode
-rw-r--r--  1 root root 664K Nov  8  2012 iwlwifi-6000g2b-6.ucode
-rw-r--r--  1 root root 459K Nov  8  2012 iwlwifi-6050-5.ucode

```


Thanks again, and please let me know if you need more information to narrow down on the problem.

---

### Post by chili555 on 2013-10-03
In your original post, you said:>  My firmware version is 18.168.6.1 and Kernel version is[COLOR="#FF0000"] 3.8[/COLOR].However, the evidence is:> filename:       /lib/modules/[COLOR="#FF0000"]3.5[/COLOR].0-40-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.koYou might, in fact, have a better result with a 3.8 kernel. I suggest you do so. If you need some guidance, please let me know.

---

### Post by sharathcshekhar on 2013-10-03
Hi chili555,
I am sorry for the confusion. I recently reverted backt o 3.5 to check if it solves my problem. I use 3.8 as my main kernel. I raised this bug in Launchpad and people there suggested me to test with the latest mainline kernel (3.12RC when I tested) which I did and reproduced the issue there too. So in short, I have seen this issues with various kernels - 3.5-x, 3.8-x and 3.12-RC.
Only thing I am sure is, I had not faced this issue with before upgrading to 13.04 (or I had not noticed it). But downgrading and testing seems too much of pain now :( 
What do you think are the chances of this actually being a HW issue? Unfortunately (or fortunately, you can say) I completely removed windows from my system and cannot test it there.
Thanks!

---

### Post by chili555 on 2013-10-03
> Only thing I am sure is, I had not faced this issue with before upgrading to 13.04 You could easily download and test the live CD (or DVD) for 12.04 LTS or even earlier to find out for sure. [http://releases.ubuntu.com/](http://releases.ubuntu.com/) > What do you think are the chances of this actually being a HW issue?I think the chances are very high, actually. A Google of the errors; "...Failed to load firmware chunk!" ...often ends with the report that there is a hardware issue.

---

### Post by sharathcshekhar on 2013-10-03
Thanks again! I will probably tryout some older version, but the only problem is the issue is very erratic. Sometime I go without crahes for 2-3 days. Sometimes I crash twice within half an hour.
But, I hope it is a hardware issue so I can get a new card or a simple USB wifi adaptor and be happy rather than desperately hoping for a kernel patch. I am hoping this guy does the trick for me for 10 bucks.
[Edimax-EW-7811Un-Wireless-Adapter-Wizard]("http://www.amazon.com/Edimax-EW-7811Un-Wireless-Adapter-Wizard/dp/B003MTTJOY/ref=sr_1_1?ie=UTF8&qid=1380856885&sr=8-1&keywords=wireless+adapter")

---

### Post by sharathcshekhar on 2013-10-05
Chili555,
I just observed something.. Everytime my wifi driver crashes, I have this log just before the crash
```
usb 2-1.5: USB disconnect, device number 3
```
Is there any connection betwee this and the wifi driver crashing? I dont know why I am getting this log because I never use any USB IO device and rarely use a USB Pen Drive.
And these are the logs I get when I enable or disable WIFI. 

```
[   26.354633] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[   26.587504] usb 2-1.5: new full-speed USB device number 4 using ehci_hcd
[   26.787949] usb 2-1.5: New USB device found, idVendor=8087, idProduct=07da
[   26.787960] usb 2-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
```

Can you please explain why I am getting USB logs when I enable WIFI? My Wireless card is a normal PCI card and not a internal USB (is there even anything like that?). This is the o/p of my lscpi/lshw:
```
*-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 memory:c0600000-c06fffff
           *-network
                description: Wireless interface
                product: Centrino Advanced-N 6235
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 24
                serial: c4:85:08:b4:11:e9
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-40-generic firmware=18.168.6.1 ip=192.168.1.17 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:46 memory:c0600000-c0601fff

```
I have also attached the failed logs I had captured a few days back and the link to the launchpad bug I have reported:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1226728]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1226728")

Thanks.

---

### Post by chili555 on 2013-10-06
I believe that this:> usb 2-1.5: New USB device found, idVendor=[COLOR="#FF0000"]8087[/COLOR], idProduct=[COLOR="#FF0000"]07da[/COLOR]...is the bluetooth part of your Intel wireless card. Often, internal devices are attached to a USB bus and not necessarily PCI. It is therefor natural that as you enable the combination card, both the wireless and the bluetooth start or expire together.

I suggest you try:```
sudi -i
echo "options iwlwifi bt_coex_active=N" >> /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and see if there is any change. 

I still feel this is a hardware issue.

---

