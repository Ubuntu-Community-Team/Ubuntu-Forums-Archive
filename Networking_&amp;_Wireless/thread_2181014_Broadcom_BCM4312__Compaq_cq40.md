---
title: "Broadcom BCM4312 / Compaq cq40"
date: 2013-10-15
forum: Networking &amp; Wireless
---

### Post by Taimur_Saleem on 2013-10-15
I am having a wifi issue with my laptop running ubuntu 12.04. The wifi works fine when booted into windows 7 but ubuntu shows the wifi to be undetected. Rfkill list all reports only bluetooth being soft blocked since I have purposely disabled bluetooth but the wireless LAN shows both soft and hard blocked as "No".

Here are a list specs.
   00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)  
 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)  
 00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)  
 00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)  
 00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)  
 00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)  
 00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)  
 00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)  
 00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)  

 00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)  
 00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)  
 00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)  
 00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)  
 00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)  
 00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)  
 00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)  
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)  
 00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)  
 00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)  
 00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)  
 02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)  
 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)  
 04:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]  
 04:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]  
 04:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]  
 04:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]

---

### Post by chili555 on 2013-10-15
Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe -r b43 && sudo modprobe b43
```Detach the ethernet and your wireless should now be working.

---

### Post by Taimur_Saleem on 2013-10-17
I ran this command and it says "E: Unable to locate package firmware-b43-lpphy-installer" and the second line of the command you gave does nothing. It returns the command line.

> **chili555 said:**
> Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe -r b43 && sudo modprobe b43
```Detach the ethernet and your wireless should now be working.

---

### Post by Bucky Ball on 2013-10-17
> **chili555 said:**
> Please get a temporary wired ethernet connection ...

You were online with an ethernet cable when you tried the commands that chilli555 gave you? You need to be online or not much will happen.

---

### Post by chili555 on 2013-10-17
> **Taimur_Saleem said:**
> I ran this command and it says "E: Unable to locate package firmware-b43-lpphy-installer" Do you have a working internet connection at the time you ran this command? When you open Software & Updates, do you have the usual sources selected? See attached. Please try again:```
sudo apt-get update
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe -r b43 && sudo modprobe b43
```

---

### Post by Taimur_Saleem on 2013-10-18
Yes i had a wired internet connection and my software sources does look like the one in your screen shots. Only download from was different so I changed it. 

> **chili555 said:**
> Do you have a working internet connection at the time you ran this command? When you open Software & Updates, do you have the usual sources selected? See attached. Please try again:```
sudo apt-get update
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe -r b43 && sudo modprobe b43
```

---

### Post by Bucky Ball on 2013-10-18
? That's odd. While online with a cable, open Software Centre or Synaptics and search for:

firmware-b43-lpphy-installer

Is it there? If so install, then issue chilli's other command in a terminal:

```
sudo modprobe -r b43 && sudo modprobe b43
```

Make sure you only have one package manager open when you're trying this.

---

### Post by Taimur_Saleem on 2013-10-18
It worked after I changed the download from, it was set to my own country so now its running fine after setting USA, also the wifi has started to work and I just cant believe ubuntu loaded all the drivers for touchpad and other things on its own. 
> **chili555 said:**
> Do you have a working internet connection at the time you ran this command? When you open Software & Updates, do you have the usual sources selected? See attached. Please try again:```
sudo apt-get update sudo apt-get install firmware-b43-lpphy-installer sudo modprobe -r b43 && sudo modprobe b43
```

---

### Post by Taimur_Saleem on 2013-10-18
Ok the wifi turns off everytime the computer restarts and I have to go to the terminal and write the  "sudo modprobe -r b43 && sudo modprobe b43" command everytime to turn it on again. Also it doesnt auto detect my wifi, instead I have to use connect to a hidden network and then add my wifi settings manually.

---

### Post by Taimur_Saleem on 2013-10-18
Now if I search the driver updates it gives me 1 update for broadcom STA wireless drivers but when I press activate it gives an error saying check jockey.log file and there is another issue, I wrote that in the previous reply.

> **Bucky Ball said:**
> ? That's odd. While online with a cable, open Software Centre or Synaptics and search for:

firmware-b43-lpphy-installer

Is it there? If so install, then issue chilli's other command in a terminal:

```
sudo modprobe -r b43 && sudo modprobe b43
```

Make sure you only have one package manager open when you're trying this.

---

### Post by varunendra on 2013-10-18
> **Taimur_Saleem said:**
> Now if I search the driver updates it gives me 1 update for broadcom STA wireless drivers but when I press activate it gives an error saying check jockey.log file and there is another issue, I wrote that in the previous reply.

The sta driver will blacklist the b43 driver as soon as you attempt to install it, and usually doesn't work as good as the native b43 with your card. Now that you have attempted to install it, I'm sure it must have blacklisted b43, even though itself failed to install.

Please do this, and ONLY this -
```
sudo apt-get purge bcmwl-kernel-source
```
This will get rid of the sta driver and its configurations including the blacklisting. Don't try installing it again, just ignore it (I think you can set in the software sources or jockey to let it not prompt you again).

Now if the wifi still can't start automatically on next boot, you may try this -
```
sudo sed -i "s:^exit 0:sleep 20 \&\& iwlist wlan0 scan\n&:" /etc/rc.local
```
This will insert a line "**sleep 20 && iwlist wlan0 scan**" in your /etc/rc.local file above the line "exit 0" in it. You can use the above command without the "-i" option to see its effect on the screen without changing the file (recommended to test this).

This has been a workaround recently reported by some users using the same card and driver. Otherwise, it won't detect any networks until you manually do almost the same thing (scan or try connecting to hidden networks).

I'm sure Dr. chili can offer you more decent workarounds or fixes if there exist any.

---

### Post by Taimur_Saleem on 2013-10-18
This fix worked and now it auto scans to connect to my preferred network. On a side note whenever I run "su" command in terminal and I input my password it says authentication failed even though I typed my password correctly. Is this normal? 

I am glad that ubuntu has good support. :D

> **varunendra said:**
> The sta driver will blacklist the b43 driver as soon as you attempt to install it, and usually doesn't work as good as the native b43 with your card. Now that you have attempted to install it, I'm sure it must have blacklisted b43, even though itself failed to install.

Please do this, and ONLY this -
```
sudo apt-get purge bcmwl-kernel-source
```
This will get rid of the sta driver and its configurations including the blacklisting. Don't try installing it again, just ignore it (I think you can set in the software sources or jockey to let it not prompt you again).

Now if the wifi still can't start automatically on next boot, you may try this -
```
sudo sed -i "s:^exit 0:sleep 20 \&\& iwlist wlan0 scan\n&:" /etc/rc.local
```
This will insert a line "**sleep 20 && iwlist wlan0 scan**" in your /etc/rc.local file above the line "exit 0" in it. You can use the above command without the "-i" option to see its effect on the screen without changing the file (recommended to test this).

This has been a workaround recently reported by some users using the same card and driver. Otherwise, it won't detect any networks until you manually do almost the same thing (scan or try connecting to hidden networks).

I'm sure Dr. chili can offer you more decent workarounds or fixes if there exist any.

---

### Post by Bucky Ball on 2013-10-18
> **Taimur_Saleem said:**
> I am glad that ubuntu has good support. :D

So are we! To help others, please mark thread as 'solved' from Thread Tools at the top right. 

Incidentally, it is 'sudo su' then you are root. You might want to avoid doing that unless there is a very specific reason. Sticking to 'sudo' is best and fine for most situations. ;)

---

### Post by chili555 on 2013-10-18
>  update for broadcom STA wireless driversThe STA driver is *incorrect* for your device! Please remove all remnants of it and let's seee if the wireless now works correctly:```
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot and tell us if it's working correctly.

Please ignore Additional Drivers as it offers to install the *wrong *driver and wreck your wireless.

---

### Post by Bucky Ball on 2013-10-18
> **chili555 said:**
> The STA driver is *incorrect* for your device! Please remove all remnants of it ...

I think varunendra has worked through this and all seems okay now with correct driver (B43 - see post #12). Correct me if I'm wrong. ;)

---

### Post by Taimur_Saleem on 2013-10-18
Yeah its working fine now, and I did run the command to remove the STA driver, I will mark the thread solved. Thanks alot guys, having a really good experience with ubuntu so far. :D

> **chili555 said:**
> The STA driver is *incorrect* for your device! Please remove all remnants of it and let's seee if the wireless now works correctly:```
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot and tell us if it's working correctly.

Please ignore Additional Drivers as it offers to install the *wrong *driver and wreck your wireless.

---

