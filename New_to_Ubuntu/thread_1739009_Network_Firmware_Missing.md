---
title: "Network Firmware Missing"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by Reddieteddy on 2011-04-25
Hello Ubuntu Forum. 
I'm a Noob to ubuntu and i have recently installed it on my netbook (Acer Aspire one) and i can connect to the internet using a cable but not Wifi, when i try to connect using wifi it's in grey and says (firmware missing) i dont know what to do. is there a driver i need to install and if so which one? 
Also if this helps my :~$ lspci -nn is:


[COLOR=Red]Jordan@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
jordan@ubuntu:~$ [/COLOR]



once again i'm a newbie to this OS and would like to have wifi working, 
Thanks in advanced!

---

### Post by ian dobson on 2011-04-25
Hi,

Maybe have a look here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I imagine you can install the firmware using the firmware cutter.

Regards
Ian Dobson

---

### Post by Reddieteddy on 2011-04-25
Ok I'll give it a shot.
Thank you Ian

---

### Post by josephmills on 2011-04-25
lets see the firmware errors go to applications-->accessories-->terminal and type in ```
dmesg | grep b43
``` then paste that here

---

### Post by Reddieteddy on 2011-04-25
> **josephmills said:**
> lets see the firmware errors go to applications-->accessories-->terminal and type in ```
dmesg | grep b43
``` then paste that here

here you go. 
=]


[    2.042080] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.042111] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[   21.864135] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   22.042524] Registered led device: b43-phy0::tx
[   22.042608] Registered led device: b43-phy0::rx
[   22.042685] Registered led device: b43-phy0::radio
[   26.022290] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   26.022303] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   26.022313] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
jordan@ubuntu:~$

---

### Post by josephmills on 2011-04-25
> **Reddieteddy said:**
> here you go. 
=]


[    2.042080] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.042111] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[   21.864135] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   22.042524] Registered led device: b43-phy0::tx
[   22.042608] Registered led device: b43-phy0::rx
[   22.042685] Registered led device: b43-phy0::radio
[   26.022290] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   26.022303] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   26.022313] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
jordan@ubuntu:~$
looks like the kernel is not seeing the firmware just like you said. ok I have seen this a lot lately. I know the work around the first thing that you have to do is download this tar.gz [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz) then move it to your home folder then right click on your home folder and make a new folder call it wireless then move the down loaded file to the new folder(wireless) then go to system-->admin-->syspatic package manager type in b43 in the search bar now you want to mark all of them there should be 4 but 2 should be active(green box)  after you have marked for removal press the apply button in synaptic then close synaptic  post back here after that and I will give the rest of the workaround.

---

### Post by Reddieteddy on 2011-04-25
> **josephmills said:**
> looks like the kernel is not seeing the firmware just like you said. ok I have seen this a lot lately. I know the work around the first thing that you have to do is download this tar.gz [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz) then move it to your home folder then right click on your home folder and make a new folder call it wireless then move the down loaded file to the new folder(wireless) then go to system-->admin-->syspatic package manager type in b43 in the search bar now you want to mark all of them there should be 4 but 2 should be active(green box)  after you have marked for removal press the apply button in synaptic then close synaptic  post back here after that and I will give the rest of the workaround.
ok i'm also going to update it. since i clicked the youtube link and he had the same problem as me and he said a quick update fixed it som ima give that a go before i get into this. gotta take it bit by bit right =]
i'll tell you if the update works or not.

---

### Post by Reddieteddy on 2011-04-25
> **josephmills said:**
> looks like the kernel is not seeing the firmware just like you said. ok I have seen this a lot lately. I know the work around the first thing that you have to do is download this tar.gz [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz) then move it to your home folder then right click on your home folder and make a new folder call it wireless then move the down loaded file to the new folder(wireless) then go to system-->admin-->syspatic package manager type in b43 in the search bar now you want to mark all of them there should be 4 but 2 should be active(green box)  after you have marked for removal press the apply button in synaptic then close synaptic  post back here after that and I will give the rest of the workaround.

ok i have done what you hace said. i removed them and now they just look like a toolbox with some stuff in it.
what is my next step...
btw the update did nothing =/

---

### Post by josephmills on 2011-04-25
> **Reddieteddy said:**
> ok i have done what you hace said. i removed them and now they just look like a toolbox with some stuff in it.
what is my next step...
btw the update did nothing =/
[b]
to copy and paste things in the terminal press shift+ctrl+c to copy and to paste it is shift+ctrl+v 
[/b]
ok now open your terminal and type in ```
sudo cp -r ~/wireless/* /lib/firmware/
```
then
```

cd /lib/firmware

```
then 
```

sudo -s 

```
then 
```

tar -xzf b43-all-fw.tar_.gz

``` then 
```

exit

```
then 
```

sudo reboot 

```
Tell us what happens

---

### Post by Reddieteddy on 2011-04-25
it rebooted and did nothing.. it stilll says firmware missing =/

---

### Post by josephmills on 2011-04-25
> **Reddieteddy said:**
> it rebooted and did nothing.. it stilll says firmware missing =/

do it again and post what the terminal says you dont have to reboot just show us what the terminal says

---

### Post by Reddieteddy on 2011-04-25
> **josephmills said:**
> do it again and post what the terminal says you dont have to reboot just show us what the terminal says

this is what the terminal says: 
[COLOR=Red]jordan@ubuntu:~$ sudo cp -r ~/wireless/* /lib/firmware/
[sudo] password for jordan: 
Sorry, try again.
[sudo] password for jordan: 
jordan@ubuntu:~$ cd /lib/firmware
jordan@ubuntu:/lib/firmware$ sudo -s
taroot@ubuntu:/lib/firmware# tar -xzf b43-all - fw.tar._.gz
tar (child): b43-all: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
root@ubuntu:/lib/firmware# 
[/COLOR]

---

### Post by Reddieteddy on 2011-04-26
when i  was installing wine it came up with and error so i read it thinking i will try to fix it and came across this.
[COLOR=Red]Setting up gnome-exe-thumbnailer (0.7-0ubuntu1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 firmware-b43-installer 
Setting up firmware-b43-installer (4.150.10.5-4) ... 
Not supported low-power chip with PCI id 14e4:4315! 
Aborting.[/COLOR]

b43 installer and a low power chip (PCI) 
now i believe that has something to do with my wireless problem and i'm hoping this will help me and anyone that wishes to help me further.

---

### Post by Reddieteddy on 2011-04-26
[B]josephmills Thank you so much for the help. i did your steps a few more times and eventually got it to work with the help of a few other terminal codes.
i appreciate  your help and i'm grateful you were so kind. 
thanks again 

Reddieteddy
[/B]

---

