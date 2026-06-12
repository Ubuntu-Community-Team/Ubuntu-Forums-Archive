---
title: "Option USB GPRS/EDGE thingey"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by ThorRune on 2008-06-08
Hullo! I've just put Ubuntu on a Aspire and am now officially impressed with so much working from-the-box. However!

This computer mainly connects to the internet with a Option GlobeTrotter USB-device, over GPRS/3G/Edge. On windows it uses the program globetrotter connect. By googleing i am unable to find how to configure this device. I don't know how to check if drivers are accepted or not. Where do i start?

---

### Post by nixscripter on 2008-06-08
You might try using **ndiswrapper** on the Windows drivers. There are general directions here:

[http://ubuntuforums.org/showthread.php?t=9454](http://ubuntuforums.org/showthread.php?t=9454)

If this is a novel device (it sounds like it), you will have to determine the INF and SYS files that ndiswrapper will need.

---

### Post by lswb on 2008-06-08
I believe your GlobeTrotter presents itself to the computer as a modem or serial port. You will need to set up a ppp connection. On your Windows machine, can you see the settings it uses to connect? In particular, a phone number, user name and password? You'll also need to find out how your system recognizes the device. Plug it in and in a terminal type 

  dmesg

Look for a message near the end of the output from dmesg that says something about a new device. It may be something like ttyACM0 or ttyS0; the 0 in the preceeding could be another number.

If you have the connection info that your ISP uses and the device name you may have enough info to try connecting. From a terminal, type 

    sudo pppconfig.

(If you get a message that pppconfig is not found, install it from synaptic )

Answer the prompts for phone number, name, password, etc. When it gets to the modem or device name, use /dev/ttyACM0, replace the ttyACMO part with whatever you saw from dmesg. Give the connection a name when prompted, select the save or write file option, then quit pppconfig.

Now, open a 2nd terminal, and type

tail -f /var/log/syslog.

Back to the 1st terminal, type

pon your-connection-name

The terminal with the tail -f command will show what's happening, don't be disapointed if you don't have a completely successful connection on the first try. Post back with what happens and good luck!

---

### Post by ThorRune on 2008-06-09
Thank you for the reply, however i failed at the first point. Here is the output, i was unable to gather anything concrete from it;

```
[ 1143.096289] usb 1-2: new full speed USB device using ohci_hcd and address 3
[ 1143.202810] usb 1-2: configuration #1 chosen from 1 choice
[ 1143.874282] usbcore: registered new interface driver libusual
[ 1143.909561] Initializing USB Mass Storage driver...
[ 1143.912617] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1143.914067] usbcore: registered new interface driver usb-storage
[ 1143.914077] USB Mass Storage support registered.
[ 1143.914202] usb-storage: device found at 3
[ 1143.914204] usb-storage: waiting for device to settle before scanning
[ 1144.881032] usb 1-2: USB disconnect, address 3
[ 1146.331439] usb 1-2: new full speed USB device using ohci_hcd and address 4
[ 1146.437963] usb 1-2: configuration #1 chosen from 1 choice
[ 1146.444027] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1146.458761] usb-storage: device found at 4
[ 1146.458767] usb-storage: waiting for device to settle before scanning
[ 1148.957540] usb-storage: device scan complete
[ 1148.959726] scsi 3:0:0:0: CD-ROM            ZCOPTION HSDPA Modem      3.00 PQ: 0 ANSI: 2
[ 1148.960214] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[ 1148.986460] Driver 'sr' needs updating - please use bus_type methods
[ 1149.017960] sr0: scsi-1 drive
[ 1149.018037] sr 3:0:0:0: Attached scsi CD-ROM sr0
[ 1150.010520] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 1150.020827] ISOFS: changing to secondary root

```

---

### Post by lswb on 2008-06-09
Really odd, the device is being recognized as a usb cdrom drive. Does an icon for a cd or disk appear on the Desktop when you plug it in? Perhaps it has some on-board storage that is being recognized as a disk drive.

OK, I just did some googling on this device. It apparently can connect as a data storage device, and in that mode you should be able to read data off the sim card installed in it, Apparently the computer can send a certain string to it that sets it to operate as a modem that takes regular AT commands. What I'm reading on a quick glance at a web page says it should be recognized as a serial port on /dev/ttyUSB0 or /dev/ttyACM0. If that's the case, it shouldn't be too tough to get it working, once you get it recognized as such.

Check out this wiki page: [http://wiki.clug.org.za/wiki/GPRS](http://wiki.clug.org.za/wiki/GPRS)  They sure know a lot more about it than I do! BTW, I just put the keywords "option globetrotter usb modem" into google and this site came up on the first page of results. I think you can find the information you need on the web. Good luck!

---

