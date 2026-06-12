---
title: "Internet drops on Ubuntu 16.04 running on Acer E15"
date: 2016-10-21
forum: Networking &amp; Wireless
---

### Post by Siddharth_Kulshres on 2016-10-21
[COLOR=#111111][FONT=Ubuntu]I'm facing this issue where the internet through the wifi drops randomly for 2 - 3 minutes while on Ubuntu. The wifi signal is always full and connected but the internet in my browser says no internet. Now this works perfectly on Windows and there are no drops at all which leads me to believe this is a driver issue.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]lscpi Output -
```

[FONT=Consolas]00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers[/FONT][/FONT][/COLOR]
        (rev 08) 00:02.0 VGA compatible controller: Intel Corporation Sky Lake
        Integrated Graphics (rev 07) 
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0
        xHCI Controller (rev 21) 
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP
        Thermal subsystem (rev 21) 
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP
        Serial IO I2C Controller (rev 21) 
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP
        CSME HECI (rev 21) 
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller 
        [AHCI mode] (rev 21) 
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1) 
00:1d.0 PCI bridge: Intel Corporation Device 9d18 (rev f1) 
00:1d.2 PCI bridge: Intel Corporation Device 9d1a (rev f1) 
00:1d.3 PCI bridge: Intel Corporation Device 9d1b (rev f1) 
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21) 
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21) 
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21) 
01:00.0 3D controller: NVIDIA Corporation Device 179c (rev a2) 
03:00.0 Network controller: Qualcomm Atheros Device 0042 (rev 31) 
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01) 
04:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. [COLOR=#111111][FONT=Ubuntu][FONT=Consolas]        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)[/FONT]
```

[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]What could be the problem and how do I solve it?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]NW Diagnostics during outage - [http://paste.ubuntu.com/23358150/](http://paste.ubuntu.com/23358150/)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]NW Outage after outage - [http://paste.ubuntu.com/23358156/](http://paste.ubuntu.com/23358156/)[/FONT][/COLOR]

---

### Post by Zero_Bytes on 2016-10-21
Have you tried restarting the networking service?

```
 sudo systemctl restart networking 
```

or restarting the wifi applet

```
 nm-applet start 
```

Have you tried using a static IP?

---

### Post by Siddharth_Kulshres on 2016-10-22
> **Zero_Bytes said:**
> Have you tried restarting the networking service?

```
 sudo systemctl restart networking 
```

or restarting the wifi applet

```
 nm-applet start 
```

Have you tried using a static IP?

Tried Both. Unfortunately, the problem still exists :(

---

### Post by jeremy31 on 2016-10-22
Post results for ```
iwconfig
```

---

### Post by Siddharth_Kulshres on 2016-10-22
> **jeremy31 said:**
> Post results for ```
iwconfig
```

Hey Jeremy,

Here it is - 

```
wlp3s0    IEEE 802.11abgn  ESSID:"mav"            Mode:Managed  Frequency:2.432 GHz  Access Point: 0C:D2:B6:3B:46:30   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:19   Missed beacon:0


lo        no wireless extensions.


enp4s0f1  no wireless extensions.
```

Heres the on during outage 

```

wlp3s0    IEEE 802.11abgn  ESSID:"mav"            Mode:Managed  Frequency:2.432 GHz  Access Point: 0C:D2:B6:3B:46:30   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2314  Invalid misc:241   Missed beacon:0



```

---

### Post by Siddharth_Kulshres on 2016-10-23
Would appreciate some help as Im really unable to work :(

---

### Post by cariboo on 2016-10-23
It looks like you have a DNS problem. I'd suggest you add Google to the IPV4 settings in Network Manager. I normally use:

```
8.8.8.8 and 8.8.4.4
```

---

### Post by jeremy31 on 2016-10-24
And lets see if we can keep power management for wifi off
```
sudo -H gedit /lib/systemd/system/wifi-power-management-off.service
```
Enter the following
```
[Unit]
Description=Disable power management for wlp3s0
Requires=sys-subsystem-net-devices-wlp3s0.device
After=network.target


[Service]
Type=oneshot
ExecStartPre= /bin/sleep 25
ExecStart=/sbin/iwconfig wlp3s0 power off



[Install]
WantedBy=multi-user.target
```

Save file, exit gedit and then
```
systemctl enable wifi-power-management-off.service
```
This may prompt for your password twice, Reboot

If you have issues after suspend/sleep then you also need to

```
sudo -H gedit /etc/systemd/system/root-resume.service
```
Enter
```
[Unit]
Description=Turn off wlan power management
After=suspend.target


[Service]
Type=simple
ExecStartPre= /bin/sleep 25
ExecStart= /sbin/iwconfig wlp3s0 power off



[Install]
WantedBy=suspend.target
```

And activate with

```
sudo systemctl enable root-resume
```
Source of the sleep/suspend fix is [http://askubuntu.com/a/614245/300665](http://askubuntu.com/a/614245/300665)

Reboot

---

### Post by Siddharth_Kulshres on 2016-10-24
Help!! I tried all these steps and it completely removed my wifi! I cant see any nearby wifi networks or connect to any!! I tried deleting the services and disabling them but nothing works. How do I reconnect again :(

---

### Post by jeremy31 on 2016-10-24
If it was from disabling power management it can be undone with ```
systemctl disable wifi-power-management-off.service
sudo systemctl disable root-resume

```
Reboot

---

### Post by Siddharth_Kulshres on 2016-10-24
Thanks for the reply but it seems this has disabled my wifi. I have tried both steps and my wifi is still gone.

Also I cant see my wifi device when I use iwconfig anymore. There is no trace of [COLOR=#000000][FONT=&quot]wlp3s0.[/FONT][/COLOR]

---

### Post by jeremy31 on 2016-10-24
Let's see ```
dmesg | grep ath
```

---

### Post by Siddharth_Kulshres on 2016-10-24
```
[    2.194772] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.440803] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    2.442374] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-5.bin failed with error -2
[    2.442387] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-5.bin': -2
[    2.442422] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-4.bin failed with error -2
[    2.442431] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-4.bin': -2
[    2.442447] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-3.bin failed with error -2
[    2.442453] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-3.bin': -2
[    2.442469] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-2.bin failed with error -2
[    2.442475] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-2.bin': -2
[    2.442491] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware.bin failed with error -2
[    2.442497] ath10k_pci 0000:03:00.0: could not fetch firmware (-2)
[    2.442503] ath10k_pci 0000:03:00.0: could not fetch firmware files (-2)
[    2.442505] ath10k_pci 0000:03:00.0: could not probe fw (-2)
```

---

### Post by jeremy31 on 2016-10-24
```
sudo apt-get install linux-firmware
```
Reboot
Did you ask this same question somewhere else?  The commands posted here would not have deleted firmware files

---

### Post by Siddharth_Kulshres on 2016-10-26
Hey,

Firstly, yes that was my fault, I messed up the drivers.

Secondly, I tried the steps you asked me earlier. The internet still stops randomly for 2 -3 minutes at a time :(

---

### Post by jeremy31 on 2016-10-26
Does iwconfig still show power management on?

---

### Post by Siddharth_Kulshres on 2016-10-26
yes. Power Management:on but I have tried earlier to turn off manually, power management seems to have no effect on the internet.

---

### Post by jeremy31 on 2016-10-26
Please do:```
gksudo gedit  /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf 
 
```Change:```
[connection]
wifi.powersave = 3
```To read:```
[connection]
wifi.powersave = 0
```Proofread carefully, save and close the text editor.

Then ```
gksudo gedit /etc/NetworkManager/system-connections/mav
```
Go to the section [wifi] add a line below that with
```
powersave=0
```
Save, close the editor and reboot.  Then we see if power management stays disabled.  Do you have the same issue if you use the install media with "Try without installing"

---

### Post by Siddharth_Kulshres on 2016-10-27
[COLOR=#000000][INDENT]It still stays on :( Tried all the steps. I'm not sure what that means = " install media with "Try without installing" :([/INDENT]
[/COLOR]

---

### Post by jeremy31 on 2016-10-27
It might not work using the install media as I remember the ISO having an older version of linux-firmware and some of the newer Atheros cards didn't work out of the box

Using a different Network Manager may help
```
sudo apt-get install wicd
```

Then we can disable network manager from Ubuntu with
```
sudo systemctl disable NetworkManager.service
```

And we could set the country code and it appears you are in India
```

sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda

```

Reboot and see if wicd keeps power management off.  If you find power management is enabled use ```
sudo iwconfig wlp3s0 power off
```
As wicd should not re enable power management like the Network Manager does.

If problems arise from this, you can uninstall wicd with
```
sudo apt-get remove wicd
```

And enable Network Manager with ```
sudo systemctl enable NetworkManager.service
```

Reboot

---

### Post by jeremy31 on 2016-10-28
Found some new info about the Network Manager powersave
Please do:```
gksudo gedit  /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf 
 
```Change:```
[connection]
wifi.powersave = 3
```To read:```
[connection]
wifi.powersave = 2
```

Save and reboot

Thanks to the link in this post [https://ubuntuforums.org/showthread.php?t=2339242&p=13562842#post13562842](https://ubuntuforums.org/showthread.php?t=2339242&p=13562842#post13562842)

---

### Post by Siddharth_Kulshres on 2016-10-30
The last one worked!Thanks a lot  for the help :)

---

