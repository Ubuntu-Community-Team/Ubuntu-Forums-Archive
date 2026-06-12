---
title: "HP Stream 11 wireless card not enabled"
date: 2016-10-19
forum: Networking &amp; Wireless
---

### Post by Leon A on 2016-10-19
I have deployed HP Stream 11 netbooks in a dozen school labs in Liberia running Lubuntu 15.10.  Originally they were equipped with either Realtek rtl8723be or Broadcom bcm43142 OEM wireless network adapters. We've battled the ubiquitous intermittent network connection/lost packet problems on these laptops even though I followed suggestions on this forum for disabling power saving, changing buffer size, changing default drivers, etc. I was able to slightly improve the RTL cards but BCM still have problems, often requiring disabling of network or reboot to restore connections.  I've also tried Lubuntu 14.04LTS and Lubunto 16.04LTS (even worse). They still drop connections after a few minutes and long PINGS show up to 50% packet loss at times, but sometimes will run clean for 5 minutes then suddenly drop out (note this is in jungle of Liberia far from any other RF sources except for our battery access point server!).  
In an attempt to find an alternate solution, I researched other wireless adapters and selected Intel Centrino Wireless N + WiMax 6150 half-mini PCI adapter card due to good reviews and supposedly superior processing power and buffer than the Broadcom and RTL units.  I installed the new card in my test notebook that formerly had a bcm card, and Lubuntu shows it is installed, but the Network Manager does not even show "Enable Wireless" checkbox and it doesn't show any available wireless networks.  (and no, there is not a hardware WiFi on/off switch. I have read that some manufacturers "white list" certain wireless adapters in BIOS, but since Lubuntu lspci and other utilities does "see" and properly ID the card, I hope that is not the case here).
I'm attaching the wireless-info.txt output in the hopes that someone can spot what may be preventing this card from working.  Thanks.
[ATTACH]271683[/ATTACH]

---

### Post by chili555 on 2016-10-19
> [   15.578994] iwlwifi 0000:01:00.0: Uncorrectable OTP ECC error, abort OTP read
[   15.578998] iwlwifi 0000:01:00.0: Unable to init EEPROMI am very concerned about this. Aside from seeing the error in the driver code, such as here: [https://git.congatec.com/arm/imx6_kernel_3.14/blob/507cadf262fe67cd71e02247b240706be12f1042/drivers/net/wireless/iwlwifi/iwl-eeprom-read.c](https://git.congatec.com/arm/imx6_kernel_3.14/blob/507cadf262fe67cd71e02247b240706be12f1042/drivers/net/wireless/iwlwifi/iwl-eeprom-read.c)

We only see references to this error here: [http://www.linuxquestions.org/questions/linux-networking-3/iwlagn-eeprom-for-intel-wifi-link-1000-help-884670/](http://www.linuxquestions.org/questions/linux-networking-3/iwlagn-eeprom-for-intel-wifi-link-1000-help-884670/) This was a question in 2011 and there was no reply.

I wonder if the card is faulty, a pre-production sample or the like. 

We can certainly try to update the firmware and remove the unnecessary Broadcom driver to see if it helps:```
sudo apt-get purge bcmwl-kernel source
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb
sudo dpkg -i linux*.deb
```Reboot and check again:```
dmesg | grep iwl
```If the problem remains, I'd suggest returning the card.

---

### Post by Leon A on 2016-11-29
Thanks for response.  I'm back in USA and catching up on this project again. The Intel Centrino WiFi card works fine in a Windows laptop.  In the HP Stream11 with Lubuntu 15.10, it still won't connect to our AP.
Running the sudo apt-get purge bcmwl-kernel source returns "unable to locate package" error, and I can't run the wget http: . . .  command since there is no connection to internet (this machine does not have a wired ethernet port).
The dmesg | grep iwl does show that it recognized the Intel Wifi card with model number and reports some setttings, but there are a lot of errors "failed to init" or failed to load firmware chunk. 
Using this alternate card is not ideal as it would involve purchasing replacement wifi cards en masse and modifying all the existing laptops in school labs, but since we have been unable to achieve stable operation with the original BCM43142 or Realtek rlt8723be cards, we thought it was worth a try.  What we'd really like is a solution for the original cards with updated drivers or whatever it takes to make Lubuntu 15 or 16 work on the HP Stream 11 laptops.  I've tried the swapping antenna cable, increasing wireless buffer sizes, and many other suggestions, but they still sporadically drop connection and lose packets.

---

### Post by chili555 on 2016-11-30
> wget http: . . . command since there is no connection to internet (this machine does not have a wired ethernet port).You can certainly download the file on any other machine and transfer it on a USB key to the desktop and then install:```
cd Desktop
sudo dpkg -i linux*.deb
```

---

