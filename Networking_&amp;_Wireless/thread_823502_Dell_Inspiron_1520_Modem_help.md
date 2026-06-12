---
title: "Dell Inspiron 1520 Modem help"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by qbox on 2008-06-09
Hi to all
I have Dell Inspiron 1520
Using Ubuntu 8.04
How to install My modem. I have no idea what modem is.
Please help.
Thank you.

---

### Post by nixscripter on 2008-06-09
I believe they use a Coaxant modem with a proprietary driver.

Unfortunately, I've never configured one of those. Hopefully, it will set up a serial line, like ttyS0. In a terminal, do:

```
ls /dev/ttyS*
```

It should list at least one. If it does, then try using:
```

sudo pppconfig

```

to set it up. If it can't find the command, install it with Synaptic package manager.

---

### Post by qbox on 2008-06-09
I receive this
qbox@qbox:~$ ls /dev/ttyS*
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3
qbox@qbox:~$ 
What I need to chose?

---

### Post by nixscripter on 2008-06-09
Whoops.

I did some research, and it turns out this is a proprietary driver, which does different things with serial lines.

First, make sure you have the driver loaded: ```
lspci | grep hsf
```

I am still trying to figure out which driver the softmodem uses.

In any case, it turns out you should use /dev/ttySHSF0 instead of /dev/ttyS0. Set it up using pppconfig.

I'm still looking into it. Perhaps I can give you more specific information in the future.

---

### Post by qbox on 2008-06-10
lspci | grep hsf
didnt return me anything.
What this mean?
p.s. thank for your help man I have no idea how to make this work...

---

### Post by nixscripter on 2008-06-10
Doh, typo:

```
lsmod | grep hsf
```

I was looking for the kernel module, which is done in the above.

If you don't have a PCI driver, perhaps it's USB. I have a 1420n myself, and I can't find the device either.

Try this command to see if the software can find anything:

```
sudo hsfconfig
```

If it asks you about wanting to keep the existing modules, say yes.

---

### Post by qbox on 2008-06-11
I receive this

qbox@qbox:~$ lsmod | grep hsf
qbox@qbox:~$ sudo hsfconfig
[sudo] password for qbox: 
sudo: hsfconfig: command not found
qbox@qbox:~$ 

If I install the winXP drivers with ndiswrapper, they will work or not?

---

### Post by nixscripter on 2008-06-11
Hmm. Maybe the 1520n doesn't have the HSF modem as I thought.

Go to the Restricted Drivers Manager (Ubuntu Menu -> System Administration -> Restricted Drivers), and see if you have "Connexant Modem Driver" or something like that in the list. I probably should have checked that earlier.

I don't know whether the windows drivers will work or not for a modem. It depends on if they use the NDISwrapper interface, and I don't know.

---

### Post by qbox on 2008-06-11
I didn't find Restricted Driver. I don't have that any where in the menu.
The command lspci give me this

qbox@qbox:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
qbox@qbox:~$ 

I didn't see nothing that look like a modem...:confused:

---

### Post by nixscripter on 2008-06-13
Hmm.

Looks like I was mistaken. I just assumed that the 1520n was like the 1420n. I've done all the research I can, and there appears to be very little information out there about either one.

Sorry not to be more help. :neutral:

---

### Post by taqkavar on 2008-08-03
To get the Conexant modem for inspiron 1520 work in gutsy 8.04:

1- Follow this page: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry)
(I don't exactly know what this is, but it is necessary to get it working, It also fixes the Wi-Fi light! yay )

2- Get the linuxant alsa driver from  [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) in DEB Format and install it.
( You need this, otherwise after the next step sound will not work anymore )

3- Download [http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb)
then:
```
sudo dpkg -i hsfmodem_7.68.00.09oem_i386.deb
```
Now reboot
( This is an OEM version of the linuxant's HSFmodem driver, unlike the one that you can get for free directly from linuxant this driver allows for full modem speed. linuxant is a 3rd party developer and is not supported by Conexant itself, hence they sell their drivers at about 25$ which either Conexant (doubt it) or Dell has provided for us for free)

4- Find a place with internet connection and: 
```
sudo apt-get install gnome-ppp
```
Right click on the applications menu, select "Edit Menus". Under "Applications" click on "Internet" then Under "Items:" make sure "GNOME PPP" is checked. Right click on "GNOME PPP", click "Properties" and change the "command" field to:
```
gksudo gnome-ppp
```
( You need to run gnome-ppp as root, otherwise it can't access the modem )

5- Run Gnome ppp then click "Setup", click "Detect". Now the modem should be detected properly if everything is alright. On the "Options" tab under "Connection" make sure "Ignore terminal strings ( stupid mode )" is selected. Now enter your ISP's phone# , user and password and click connect and it should start dialing. Sometimes you have to try 2 or 3 times before you get any dial tone. If it didn't work no matter what, run gnome-ppp in terminal as root, watch the terminal output and if it got stuck on one of the steps interrupt it by pressing ctrl+c. Then run gnome-ppp again. This time it should start dialing.
Also, make sure that you aren't playing any music while trying to dial. After it is connected to the internet, you can resume listening to music.

I guess this is all.
Sorry, I'm really bad at writing tutorials so if this is a bit awkward, you now know why.
To get the modem working has been a real headache for me. It is quite simple, but there were no straight forward guides around which pointed out what is needed in order to get this modem working. Worse than that, most of them where greatly misleading and complicated! I came across this topic the first time I tried to get it working a month ago.

Later

PS: Almost forgot, for me firefox stays off-line mode with dialup. Go to Edit and take the check mark off for "Work Offline". Same problem with evolution, you have to click the little link button on left-down corner of the page.

---

