---
title: "Advent 4213 Hardy"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by thasl on 2009-03-02
Hi all, I'm a Linux newbie, just put it on my Advent 4213 with dual boot with XP. I originally tried intrepid, but when I updated it, my Ethernet started working, so I put hardy back on it, however, there is a problem with the wirelesscard driver. There are lots of intrepid drivers compiled and out there, just trying to find one for Hardy! Hoping some one. Can point me in the right direction.

Thank you!

THASL

---

### Post by Kevbert on 2009-03-02
Welcome to Ubuntu.
We need to find out which wireless chipset you have. Please go to Applications-Accessories-Terrminal and type in
```
lspci
``` (list all pci devices) or
```
lsusb
``` (list USB devices)
Select the output with the mouse and press Ctrl-Shift-C (to copy), open a new post and press Ctrl-C to paste it here.

---

### Post by thasl on 2009-03-02
Hope this is right, thanks for the help :)

thal@THAL-Advent:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02) 
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Unknown device 8199 (rev 22) 
thal@THAL-Advent:~$ 







thal@THAL-Advent:~$ thal@THAL-Advent:~$ lspci 
bash: thal@THAL-Advent:~$: command not found 
thal@THAL-Advent:~$ 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Unknown device 8199 (rev 22) 
bash: syntax error near unexpected token `(' 
thal@THAL-Advent:~$ thal@THAL-Advent:~$  
bash: thal@THAL-Advent:~$: command not found 
thal@THAL-Advent:~$

---

### Post by northern lights on 2009-03-02
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false")

---

### Post by Kevbert on 2009-03-02
[[COLOR="Red"]Here's[/COLOR]]("http://boskastrona.ovh.org/index.php?lang=en") the 32 bit driver for Hardy (go to RTL8187SE - new packages for Hardy). Download it and then double click on the deb file which you've saved on your desktop.

---

### Post by thasl on 2009-03-02
Thanks so much

I've downloaded and installed the file, so I'll check if it works at uni tomorrow and confirm then, but everything should be cool. Do you know if this supports wpa2 professional security?

THASL

---

### Post by Kevbert on 2009-03-02
It should support WPA2 personal and enterprise security, but you'll need to check as there have been problems with this in the past.

---

### Post by thasl on 2009-03-03
Thanks so much, everything is working hunky-dory, so to speak, and, for future reference, wpa2 enterprise works fine :)

Thanks again

THASL

:KS:D

---

