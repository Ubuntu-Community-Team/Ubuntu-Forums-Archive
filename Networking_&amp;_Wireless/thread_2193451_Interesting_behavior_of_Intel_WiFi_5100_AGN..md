---
title: "Interesting behavior of Intel WiFi 5100 AGN."
date: 2013-12-12
forum: Networking &amp; Wireless
---

### Post by an-vain on 2013-12-12
Hello everybody, here is the situation I can't figure out.

I have ubuntu 12.04 for a while and everything was fine with it, wireless worked. Recently, I installed Windows 7 as a second boot system (couldn't flash blackberry os through vmware) and wireless driver there. Wireless worked in Windows. I rebooted from flash drive to Ubuntu and fixed the GRUB. Wireless worked in Ubuntu from USB stick. Rebooted to main system and.... that's it.

Now, I don't have wireless in neither Ubuntu: stationary (HDD boot) **or even flash drive.** I even tried to boot to 13.10 from USB stick - same result. Wireless not working. But when I boot to Windows - wireless works.

Maybe someone can give me a tip WHAT COULD THAT BE  and how to make it back to normal. Any help will be greatly appreciated :confused:

Here are some additional info:
[SIZE=3][FONT=arial][FONT=verdana][SIZE=2]```

$ uname -a
Linux arhatt-pc 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
    Subsystem: Lenovo Device [17aa:3d7e]
    Kernel driver in use: tg3
--
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
    Kernel driver in use: iwlwifi
```
```

$ rfkill list all 
0: ideapad_wlan: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
1: ideapad_bluetooth: Bluetooth 
    Soft blocked: yes 
    Hard blocked: no 
5: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no
```

```
$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ARHNET"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 58:6D:8F:26:C4:C3   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:54   Missed beacon:0

eth0      no wireless extensions.
```

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.0.1      0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
172.16.0.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0
```

```
$ sudo modprobe -l iwlwifi
kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
```

```
$ lsmod | grep iwl
iwlwifi               401148  0 
mac80211              506862  1 iwlwifi
cfg80211              205774  2 iwlwifi,mac80211

$ modinfo iwlwifi | grep -e 0888 -e version -e lib 
filename:       /lib/modules/3.2.0-57-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
version:        in-tree: 
srcversion:     290AB40BBD26BABA465648D 
alias:          pci:v00008086d00000888sv*sd00004266bc*sc*i* 
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i* 
vermagic:       3.2.0-57-generic SMP mod_unload modversions 
```

```
$ modinfo iwlwifi | grep -e 0888 -e version -e lib -e firmware
filename:       /lib/modules/3.2.0-57-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
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
srcversion:     290AB40BBD26BABA465648D
alias:          pci:v00008086d00000888sv*sd00004266bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
vermagic:       3.2.0-57-generic SMP mod_unload modversions 
parm:           fw_restart:restart firmware in case of error (int)
```[/SIZE][/FONT]
[/FONT][/SIZE]
Thanks.

---

### Post by mikewhatever on 2013-12-13
And what makes you think it doesn't work? The output of iwconfig shows it's connected to ESSID:"ARHNET", and route -n says there is an ip address. 
Intel's PRO/Wireless 5100 AGN is known to be pretty horrible for some, but I am not sure that's your case too.

Can you ping your gateway and post the output: ping -c5 172.16.0.1.

How about google: ping -c5 google.com or ping -c5 213.57.24.16.

---

### Post by an-vain on 2013-12-13
Yes, it shows that it's connected ONLY when ethernet cable pluged in:
[ATTACH=CONFIG]248576[/ATTACH][ATTACH=CONFIG]248575[/ATTACH]

But with cable out wireless does NOT work. I can see in tray panel that it's constantly tring to connect. 

Here is what I have with cable pluged out:

```
arhatt@arhatt-pc:~$ ping -c5 172.16.0.1
connect: Network is unreachable
arhatt@arhatt-pc:~$ ping -c5 8.8.8.8
connect: Network is unreachable
arhatt@arhatt-pc:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ARHNET"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 58:6D:8F:26:C4:C3   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

arhatt@arhatt-pc:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

---

### Post by an-vain on 2013-12-14
The situation resolved. It was a router's fault... It finally died today. :( :( :(

---

