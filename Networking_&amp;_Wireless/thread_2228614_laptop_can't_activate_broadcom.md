---
title: "laptop can't activate broadcom"
date: 2014-06-08
forum: Networking &amp; Wireless
---

### Post by chicoharv on 2014-06-08
After being digusted with my new windows 8 computer I have gone back to linux on my old pc and laptop I installed Lubunto 14.04 on both boxes as Ubunto 14.04 would not load up on my older machines. PC is fine, I have it on a KLM with audio switch with the horrible Win8. My lap top works fine on ethernet but can't activate broadcom wireless. Also when I shut down laptop it shuts down Lbuntu but leaves the logo on the screen without shutting down the box.I have downloaded fwcutter, b43, and even ndiswrapper to no avail. What can I do to fix?

---

### Post by praseodym on 2014-06-08
Please check
```

lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig
```
Does LAN work?

---

### Post by chicoharv on 2014-06-08
Lan works wireless printer works, I wish I knew how to print terminal readout but newbie to using terminal. 
When I queiry the term. I can see :
Command 1 shows broadcombcm4318 and kernal driver in use.
Command 2 shows long list ,I recognize pcmcia only
Command 3 no killlist
Command 4 shows: lo no wireless extension; etho no wireless extension.
Hope this helps. Tell me how to print the results to this form thread and I would be appreciate.

---

### Post by praseodym on 2014-06-08
You need this firmware:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

### Post by chicoharv on 2014-06-09
I have downloaded the above and sudo complete. Still not able to activate wifi. 
when I go to network tools and supply the key 'save ' is not highlighted to install? also when I restart or shut down all my lap does is disconnects Lubuntu to opening screen. I can not do anything until I manually shut down using the on/off switch. Looks like I need more help.

---

### Post by praseodym on 2014-06-09
Start the NM via
```

gksudo nm-connection-editor
```

---

### Post by chicoharv on 2014-06-09
That gives me the network manager file which I already can get too, I just can't enter my key and highlight the save button. If I go to install windows drivers it reports not a good driver for inf file.

---

### Post by praseodym on 2014-06-09
You dont need Windows drivers for this device. Check
```

lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```

---

### Post by chicoharv on 2014-06-09
my lap now turns on and off and restarts ok My wifi light and switch now comes on. I still can't get on line wireless. 
cat /etc/resolv.conf = nameservor 127.0.1.1    and gateway pace.com
I think I am having trouble getting through the gateway. Any suggestions? When I go to network connections I still only have 3 windows, no connections window as is shown in the help menu

---

### Post by chicoharv on 2014-06-09
After further probing my lap top see the gateway but can't connect. My gateway sees the laptop on Ethernet only. When I last used Linux it was on Ubuntu 8 and if I remember right I could scan the laptop for available wireless connections. I don't see any way to do this now. Maybe I can't use Lubuntu but seems to me I should be able to see what wireless networks are available. I want to use this laptop when I travel and need to find wifi access everywhere.

---

### Post by praseodym on 2014-06-10
Pleas show the outputs of the commands

---

### Post by chicoharv on 2014-06-10
What commands do you want the outputs of. Is there a way to copy the commands and paste them to a reply?

---

### Post by jeremy31 on 2014-06-10
Use terminal and not xterm then you can left click/drag to select and right click to copy/paste

---

### Post by chicoharv on 2014-06-10
harv@harv-Aspire-3000:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.
yenta_socket           40201  0 
cfg80211              409394  2 b43,mac80211
snd                    60871  10 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
pcmcia_rsrc            18319  1 yenta_socket
joydev                 17101  0 
k8temp                 12842  0 
serio_raw              13230  0 
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
soundcore              12600  1 snd
i2c_sis96x             13006  0 
mac_hid                13037  0 
parport_pc             31981  0 
shpchp                 32128  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
psmouse                91033  0 
sis900                 26518  0 
mii                    13654  1 sis900
ssb                    51854  1 b43
harv@harv-Aspire-3000:~$ lspci -nnk | grep -iA2 net
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
	Subsystem: Acer Incorporated [ALI] Device [1025:0083]
	Kernel driver in use: sis900
--
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
	Kernel driver in use: b43-pci-bridge
harv@harv-Aspire-3000:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by jeremy31 on 2014-06-10
> **chicoharv said:**
> harv@harv-Aspire-3000:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.
yenta_socket           40201  0 
cfg80211              409394  2 b43,mac80211
snd                    60871  10 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
pcmcia_rsrc            18319  1 yenta_socket
joydev                 17101  0 
k8temp                 12842  0 
serio_raw              13230  0 
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
soundcore              12600  1 snd
i2c_sis96x             13006  0 
mac_hid                13037  0 
parport_pc             31981  0 
shpchp                 32128  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
psmouse                91033  0 
sis900                 26518  0 
mii                    13654  1 sis900
ssb                    51854  1 b43
harv@harv-Aspire-3000:~$ lspci -nnk | grep -iA2 net
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
    Subsystem: Acer Incorporated [ALI] Device [1025:0083]
    Kernel driver in use: sis900
--
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
    Kernel driver in use: b43-pci-bridge
harv@harv-Aspire-3000:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
And please use code tags around info like this, in advanced reply, it is a # symbol or you could just put [ c o d e ] before the info without spaces and [ / code ] after because some of your iwconfig info turned into smilies

---

### Post by chicoharv on 2014-06-10
Iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chicoharv on 2014-06-10
#wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chicoharv on 2014-06-10
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by praseodym on 2014-06-11
[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Install this file by double click with the software-center and reboot

---

### Post by chicoharv on 2014-06-11
no change already in . I think the network manager is missing something per [http://www.webupd8.org/2014/04/fix-lubuntu-1404-net](http://www.webupd8.org/2014/04/fix-lubuntu-1404-net)

---

### Post by chicoharv on 2014-06-12
Have not heard from anybody since yesterday. It looks like other users are having simular problem  Do not get a networks available except for ethernet. Network manager shows wireless never used. Broadcom 4318 turns on on start, but nothing after that . Have to use ethernet to go on line. This laptop will b e used out in a wifi area only. Is there another Distro than lubuntu 14.04 that might work better? This laptop last worked on Ubuntu 8 wireless okay then.

---

