---
title: "Someone please help broadband problems"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-04-07
I have been scouring the forums, and can not find anything that helps. My last 3 posts I got no responses. I really need to get this working. 

I have a new T-mobile Hauwei UMG181 Broadband USB dongle. It doesn't seem to want to connect. I was using my friends Cricket one, and it was just plug and play, worked great. I got a deal at T-mobile cause I was already a customer, so I really don't want to return it.

PLEASE CAN SOMEONE HELP ME ON THIS??????

---

### Post by AndyP79 on 2009-04-07
Okay, I found in a post to run this; lspci

This is the output I got, does this help anyone?


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by dmizer on 2009-04-07
> **AndyP79 said:**
> I have been scouring the forums, and can not find anything that helps. My last 3 posts I got no responses. I really need to get this working. 

I have a new T-mobile Hauwei UMG181 Broadband USB dongle. It doesn't seem to want to connect. I was using my friends Cricket one, and it was just plug and play, worked great. I got a deal at T-mobile cause I was already a customer, so I really don't want to return it.

PLEASE CAN SOMEONE HELP ME ON THIS??????

With this information, I was able to use google to find this thread: [http://georgia.ubuntuforums.org/showthread.php?t=1107634](http://georgia.ubuntuforums.org/showthread.php?t=1107634)

Here's my google search parameters:
[Hauwei UMG181 8.10 site:ubuntuforums.org](http://www.google.com/search?source=ig&hl=en&rlz=1G1GGLQ_ENUS269&=&q=Hauwei+UMG181+8.10+site%3Aubuntuforums.org&btnG=Google+Search&aq=f&oq=)

For future reference, the most important thing to do is determine your hardware's identification. Once you have that, then you can perform a search and find your answer.

---

### Post by GeorgeVita on 2009-04-09
Hi **AndyP79**,
as I have not used the Huawei UMG 181 we are going to find how the system recognizes the modem and then try to connect with one method (possibly wvdial).

Please do the following:
Boot without the modem, wait for the system to stabilize, attach the modem, wait 20 seconds, open a terminal window and try:
[B]
dmesg
lsusb
ls /dev/ttyU*
[/B]

Post here the last 10-15 lines of **dmesg** (concerning /dev/ttyUSBx and usbserial) and also the output of the other two commands.

The **dmesg** command will show all system activity after inserting the modem, **lsusb** will show all USB peripherals attached and their vendor/product IDs and **ls /dev/ttyU*** will list any configured serial communication ports.

Regards,
George

EDIT:** See also another similar case at [http://ubuntuforums.org/showthread.php?t=1107634](http://ubuntuforums.org/showthread.php?t=1107634)**

---

### Post by AndyP79 on 2009-04-09
> **GeorgeVita said:**
> Hi **AndyP79**,
as I have not used the Huawei UMG 181 we are going to find how the system recognizes the modem and then try to connect with one method (possibly wvdial).

Please do the following:
Boot without the modem, wait for the system to stabilize, attach the modem, wait 20 seconds, open a terminal window and try:
[B]
dmesg
lsusb
ls /dev/ttyU*
[/B]

Post here the last 10-15 lines of **dmesg** (concerning /dev/ttyUSBx and usbserial) and also the output of the other two commands.

The **dmesg** command will show all system activity after inserting the modem, **lsusb** will show all USB peripherals attached and their vendor/product IDs and **ls /dev/ttyU*** will list any configured serial communication ports.

Regards,
George

EDIT: now my local time is 03:57 (GMT+2), logging out! **[COLOR="DarkGreen"]Returning online 09:30 (GMT 07:30)[/COLOR]**


Hi George,
 Thanks for the pickup of my thread. I did what you asked, and I that all this starts to explain what I need to do. Below is the outputs;


[  123.664074] usb 4-1: new high speed USB device using ehci_hcd and address 4
[  123.822768] usb 4-1: configuration #1 chosen from 1 choice
[  123.850467] scsi7 : SCSI emulation for USB Mass Storage devices
[  123.866372] usb 4-1: USB disconnect, address 4
[  123.866773] usb-storage: device found at 4
[  123.866780] usb-storage: waiting for device to settle before scanning
[  130.332056] usb 4-1: new high speed USB device using ehci_hcd and address 5
[  130.475317] usb 4-1: configuration #1 chosen from 1 choice
[  130.486699] usb-storage: probe of 4-1:1.0 failed with error -5
[  130.499425] usb-storage: probe of 4-1:1.1 failed with error -5
[  130.500091] usb-storage: probe of 4-1:1.2 failed with error -5
[  134.508185] scsi11 : SCSI emulation for USB Mass Storage devices
[  134.527756] usb-storage: device found at 5
[  134.527763] usb-storage: waiting for device to settle before scanning
[  138.528187] scsi12 : SCSI emulation for USB Mass Storage devices
[  138.550071] usb-storage: device found at 5
[  138.550079] usb-storage: waiting for device to settle before scanning
[  138.555076] usb-storage: probe of 4-1:1.5 failed with error -5
[  138.555660] usbcore: registered new interface driver usbserial
[  138.555880] usbserial: USB Serial support registered for generic
[  138.556160] usbcore: registered new interface driver usbserial_generic
[  138.556170] usbserial: USB Serial Driver core
[  138.580207] usbserial: USB Serial support registered for GSM modem (1-port)
[  138.581910] option 4-1:1.0: GSM modem (1-port) converter detected
[  138.583159] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[  138.584508] option 4-1:1.1: GSM modem (1-port) converter detected
[  138.585955] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[  138.587087] option 4-1:1.2: GSM modem (1-port) converter detected
[  138.588207] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[  138.589800] option 4-1:1.5: GSM modem (1-port) converter detected
[  138.590875] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB3
[  138.591981] usbcore: registered new interface driver option
[  138.591988] option: USB Driver for GSM modems: v0.7.2
[  139.525321] usb-storage: device scan complete
[  139.527414] scsi 11:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  139.581655] sr1: scsi-1 drive
[  139.582032] sr 11:0:0:0: Attached scsi CD-ROM sr1
[  139.582388] sr 11:0:0:0: Attached scsi generic sg3 type 5
[  143.549325] usb-storage: device scan complete
[  143.551288] scsi 12:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[  143.579303] sd 12:0:0:0: [sdc] Attached SCSI removable disk
[  143.579767] sd 12:0:0:0: Attached scsi generic sg4 type 0
[  146.860548] usb 4-4: USB disconnect, address 2
[  152.420774] ISO 9660 Extensions: Microsoft Joliet Level 1
[  152.424067] ISOFS: changing to secondary root

andrew@TravelingMonkeyBox ~ $ lsusb
Bus 004 Device 005: ID 12d1:1414 Huawei Technologies Co., Ltd. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

andrew@TravelingMonkeyBox ~ $ ls/dev/ttyU*
bash: ls/dev/ttyU*: No such file or directory

---

### Post by GeorgeVita on 2009-04-10
EDITED to reserve space as first try did not work and all data writen in more detail into post#9

The tested **/etc/wvdial.conf** file for **t-mobile** is the following:
([http://ubuntuforums.org/showthread.php?t=1107634](http://ubuntuforums.org/showthread.php?t=1107634))

[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = pass
Phone = *99#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 =AT+CGDCONT=1,"IP","internet2.voicestream.com"

Notes:
We are using the port /dev/ttyUSB0 to communicate with an Analog Modem which is not ISDN(?), setting for an initial communication speed of 115200 Bauds. This provider does not need a specific Username or Password (others may do). Dial *99# (usual for GPRS/3G connection) and start pppd immediately (stupid mode = 1).
When initializing the modem: Do a soft reset (ATZ), restore factory settings (AT&F), echo the commands (E1) in verbal mode (V1), don't remember (X1), use h/w handshakes (&D2 &C1) and finally do not auto answer to an incoming call (S0=0).
**Sometimes Init3 is very important**. This sets the type of service we want for this connection. Most providers mean internet BUT some have very different charges if you choose the wrong one!** If you are not sure ask your provider checking also the dial no., username and password.**

References: from terminal read the manual pages **man wvdial** and **man wvdial.conf**
After reading the manual pages press **:** (colon) and then **q** to **exit!**

---

### Post by AndyP79 on 2009-04-10
Hi George,
 I understand the command about the terminal. BUT.... I do not understand what the rest of what you said was? Sorry, I am only learning this stuff as I go, as before Linux, I just checked email on my old computer, and that was about it. There is a lot I am learning on the fly.

---

### Post by AndyP79 on 2009-04-10
Hi George, i copy and pasted exactly what you posted into what I am assuming was gedit, cause it opened when I ran the terminal, this is what I got;

--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory


I was looking at the stuff, and was wondering if the username/password is something I should have for my dongle? Can I just call T-mobile and aquire it from them?

---

### Post by GeorgeVita on 2009-04-10
> **AndyP79 said:**
> ... I do not understand what the rest of what you said was? Sorry, I am only learning this stuff as I go, as before Linux, I just checked email on my old computer, and that was about it. There is a lot I am learning on the fly.

Ok, lets Add some "icons" to the top panel:

1. From **Applications**, **Accessories**, right click **Terminal** and click to **Add this launcher to panel**.
2. From **Applications**, **Accessories**, right click **Text Editor** and click to **Add this launcher to panel**.
3. From **System**, **Administration**, right click **System Monitor** and click to **Add this launcher to panel**.

Now you can just click the terminal icon to open it, or later it will be more convenient to know the 3G data traffic from system monitor.

For connecting with the **wvdial** program we have to set some parameters to the configuration file **wvdial.conf**
Open a terminal window (by clicking the terminal icon created before) type:
**sudo gedit /etc/wvdial.conf** and press <ENTER>
give your password if asked (not shown while you type it) and press <ENTER> again.

A window will open with the title **wvdial.conf (/etc) - gedit**
There you should delete any existing line (use the mouse to select and DEL to delete).
Copy and paste the following lines (shown in bold) into that window:

[B][Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = pass
Phone = *99#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 =AT+CGDCONT=1,"IP","internet2.voicestream.com"
[/B]
Click on **SAVE icon** and close this (gedit) window.

Boot the system without the modem, wait for the system to stabilize (till all panels and icons appear), attach your modem, wait 20 seconds, open a terminal window, type:
**sudo wvdial** and press <ENTER>

If all are OK you will see some text lines including:
CONNECT xxxxxxx
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at ...
--> Pid of pppd: ...
...
--> local IP address ...
...
--> primary DNS address 66.94.25.120
...
**The connection done!** Click on **Firefox** icon, remove **Work Offline** mode with **ALT+F W** and browse.

To **disconnect** press **CTRL+C** at the window you got connected.

In case of any error copy & post here **ALL** terminal messages starting from your sudo wvdial command till the final terminal prompt.

Regards,
George

---

### Post by AndyP79 on 2009-04-10
Hi George!
 Okay, soooo.... it appears to be working. Does this mean I can just plug it in each time, or do I have to reconnect? i am sending this via the T-mobile connection, and the speed is quite nice. 

Oh, new question, the intenet icon in my panel, with everything else, it usally shows a choice of connection choices, but this time it shows nothing(except for the wireless in the neighbourhood) and it shows as not connected. Is the wvdial a different thing all together?

Anyways though, it appears to work, and I am very grateful for your help. Thank You many times over.
Andrew

---

### Post by GeorgeVita on 2009-04-10
Well done!
To connect with **wvdial** method, you have to open a terminal window, type **sudo wvdial**, press <ENTER>, give your password if asked, press <ENTER>. Disconnect by pressing **CTRL+C** at the same window.
...> in brief: **sudo wvdial**

wvdial and system (Firefox, Network Manager, etc) are not cooperating very well so it seems to be disconnected!

Hardcopy post#9, wvdial works ALWAYS! It is your BACKUP!

**And now lets try Network Manager!** (We own ourselves a try for a better User Interface)
We must edit HAL info to see HUAWEI UMG181. Open a terminal window and run:
**sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi**
(copy above line and paste it to the terminal window, press <ENTER>)
A window of text editor (gedit) will open and you will see all data of the 10-modem.fdi file.

**Now watch your steps! Be careful in what you type!**

**Search** by pressing **CTRL+F** for **12d1** (this is the HUAWEI ID#).
Move cursor 2 lines below and edit line **<match key="...product_id" int_outof="0x1001;0x1406">**
to **<match key="...product_id" int_outof="0x1001;0x1406;0x1414">**
(insert text **;0x1414** which is the product# of UMG181). **Save** and **exit** from gedit.

NOTE: this edit must be done again if an Ubuntu update restores the file 10-modem.fdi to defaults!

**Setup Network Manager & connect!**
Remove modem from USB port, reboot, wait for the system to stabilize, plug in the modem. After a while a message will appear over the **Network Manager** icon (2 PC screens up right) and help you create a **Mobile Broadband** connection. After created, click to Network Manager icon, and click to your provider. You must be connected!

If the wizard does not appear right click Network Manager icon, **Edit Connections**, **Mobile Broadband**, **Add**, check **Country** and select **provider**.
In any problem check from **Edit Connections**, **Mobile Broadband**, **Edit** the phone number and the APN (for **t-mobile** is **internet2.voicestream.com**).

Hope we finished!

---

### Post by AndyP79 on 2009-04-11
Hi George,
 Okay, so I tried the above post, and I got nothing. I added the line of text after searching it, and after there was still no connection through the network manager. A wierd thing though, my network manager icon has dissapeared, but if I mouse over it acts like it is with the left and right click options. I tried going to the various country choice, and choose my area. Nothing. This is a fresh install of my OS as of last night, with a fresh set of updates from last night, so...... should be nice and clean?

I will be away until late tonight, or tomorrow afternoon, as I have to go earn my living on the sea, so I can keep paying the bill for my internet! HAHA! 

Thanks again, and looking forward to continuing the network manager set up.

Andrew

---

### Post by HeavyHaulTrucker on 2009-12-24
> **AndyP79 said:**
> I have been scouring the forums, and can not find anything that helps. My last 3 posts I got no responses. I really need to get this working. 

I have a new T-mobile Hauwei UMG181 Broadband USB dongle. It doesn't seem to want to connect. I was using my friends Cricket one, and it was just plug and play, worked great. I got a deal at T-mobile cause I was already a customer, so I really don't want to return it.

PLEASE CAN SOMEONE HELP ME ON THIS??????

Check out my complete instructions at this post:  [Hauwei UMG-181 Installation Instructions]("http://ubuntuforums.org/showthread.php?t=1079344&page=2") -- scroll down to post #12.

I bought one last night and had it working within 15 minutes -- still using it this morning, too!

John

---

### Post by AndyP79 on 2009-12-24
Hey John,
 Saw this posted on here, on the new releases, it just works. Plug and play, choose broad band or mobile broadband and presto chango, it works. This was a year ago, and we have had two releases since then. 
Happy Holidays

---

