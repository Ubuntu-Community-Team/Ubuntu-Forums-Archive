---
title: "Wireless connection not working"
date: 2016-04-27
forum: Networking &amp; Wireless
---

### Post by Finn_Francis on 2016-04-27
Hi guys, 

I'm completely new to linux and I've been having some trouble connecting to the internet, I can connect  via  ethernet cable but I'm having some trouble getting a wireless  connection.

So far I've checked for additional drivers in my software updates but it says no new drivers available.  I'm not really sure where to go from here so some advice would be very much appreciated!

---

### Post by jeremy31 on 2016-04-27
Welcome to the forums Finn_Francis, please see [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Please use code tags when posting the wireless script results [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by RobGoss on 2016-04-27
> [COLOR=#000000]So far I've checked for additional drivers in my software updates but it says no new drivers available.[/COLOR]

This is because it can not scan for the necessary drivers needed because you have no internet connection, the easier way is to connect with a wired connection and allow your system to scan for the drivers that is needed to get you on line. You should always use a wired connection when you are doing a new installation this way you will avoid theses issues.

---

### Post by chili555 on 2016-04-27
> **RobGoss said:**
> > [COLOR=#000000]So far I've checked for additional drivers in my software updates but it says no new drivers available.[/COLOR]This is because it can not scan for the necessary drivers needed because you have no internet connection,Doesn't the OP say:>  I can connect via ethernet cableThe more likely reason is that Additional Drivers only offers Broadcom drivers and the OP probably hasn't any Broadcom device.

---

### Post by RobGoss on 2016-04-27
> **chili555 said:**
> Doesn't the OP say:The more likely reason is that Additional Drivers only offers Broadcom drivers and the OP probably hasn't any Broadcom device.

Yep I'm aware what the **OP** says about not having any **internet connection **but you would think most if not every machine that I know has a [COLOR=#000000]***Ethernet cable **connection on that machine. *All you would need is a cable which you get just about anywhere it makes life a lot easier.[/COLOR]

---

### Post by chili555 on 2016-04-27
> **RobGoss said:**
> Yep I'm aware what the **OP** says about not having any **internet connection **but you would think most if not every machine that I know has a [COLOR=#000000]***Ethernet cable **connection on that machine. *All you would need is a cable which you get just about anywhere it makes life a lot easier.[/COLOR]He says:>  I can connect via ethernet cableThat seems very clear to me that he CAN connect.

You said that:>  it can not scan for the necessary drivers needed because you have no internet connection,I think it is quite clear that he DOES have an internet connection. I think it did scan for the necessary drivers but found no Broadcom device.

---

### Post by RobGoss on 2016-04-27
> **chili555 said:**
> He says:That seems very clear to me that he CAN connect.

You said that:I think it is quite clear that he DOES have an internet connection. I think it did scan for the necessary drivers but found no Broadcom device.

Got ya I was reading it in correctly I thought we stated he could not connect...

---

### Post by chili555 on 2016-04-27
> **Finn_Francis said:**
> Hi guys, 

I'm completely new to linux and I've been having some trouble connecting to the internet, I can connect  via  ethernet cable but I'm having some trouble getting a wireless  connection.

So far I've checked for additional drivers in my software updates but it says no new drivers available.  I'm not really sure where to go from here so some advice would be very much appreciated!Let's identify your device and then propose a solution. Please open a terminal and run and post:```
lspci -nnk | grep 0280 -A2
```Thanks.

---

### Post by Finn_Francis on 2016-04-28
Thanks for all the replies everyone.  Sorry if I was a little unclear in my original post, I can confirm that I am currently connected to the internet via ethernet cable.

When I run: 
```
lspci -nnk | grep 0280 -A2
```

I get this:
```
03:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 81)
    Subsystem: Intel Corporation Dual Band Wireless AC 3165 [8086:4010]
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
```

I've also attached my wireless-info file.

---

### Post by chili555 on 2016-04-28
> [   32.409527] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-3165-12.ucode failed with error -2
[   32.410677] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-3165-11.ucode failed with error -2
[   32.410688] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-3165-10.ucode failed with error -2
[   32.410690] iwlwifi 0000:03:00.0: request for firmware file 'iwlwifi-3165-10.ucode' failed.
[   32.410698] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-3165-9.ucode failed with error -2
[   32.410700] iwlwifi 0000:03:00.0: request for firmware file 'iwlwifi-3165-9.ucode' failed.
[   32.410701] iwlwifi 0000:03:00.0: no suitable firmware found!Let's install the correct firmware. Please download this file to your desktop: [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157_all.deb) Now open a terminal and do:```
cd ~/Desktop
sudo dpkg -i linux*.deb
cd /lib/firmware
sudo cp iwlwifi-7265D-13.ucode  iwlwifi-3165-9.ucode
sudo cp iwlwifi-7265-13.ucode  iwlwifi-3165-13.ucode
```Reboot and tell us if the wireless is working.

---

### Post by Finn_Francis on 2016-04-28
It's still saying no suitable firmware found, I've attached an updated wireless info file.

---

### Post by chili555 on 2016-04-28
Please try:```
sudo cp /lib/firmware/iwlwifi-7265D-12.ucode /lib/firmware/iwlwifi-3165-12.ucode

```
Reboot.

---

### Post by Finn_Francis on 2016-04-28
That's done it.

Thanks very much for your help!

---

