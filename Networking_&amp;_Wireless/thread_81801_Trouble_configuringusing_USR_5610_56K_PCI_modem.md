---
title: "Trouble configuring/using USR 5610 56K PCI modem"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by JPZ on 2005-10-25
I've searched the forums and elsewhere and can't get a USR 56K PCI FaxModem to work, even though I've used setserial to set the driver details. setserial works when I boot a Knoppix CD so the hardware appears to be working.


System Details

The system is a low-profile Dell Optiplex GX1. It has two built-in serial ports in addition to the serial port with the PCI modem. The modem is a USR 56K PCI FaxModem Model 5610 (rev 01). The scanModem tool (see [http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/) ) reports the PCI IDs as follows:

    Primary: 12b9:1008      Subsystem: 12b9:00aa


With Knoppix: Good behavior

When Knoppix boots it discovers the built-in serial ports and names them ttyS0 and ttyS1. The PCI modem is discovered, but the serial port associated with the modem is not. Both dmesg and lspci were used to confirm these facts.

After becoming root, setserial was used to configure ttyS4:

    # setserial /dev/ttyS4 uart 16550A port 0xdcd8 irq 10

after which

    # wvdialconf /etc/wvdial.conf

scans ttyS0, ttyS1 and ttyS4. wvdialconf correctly finds a modem at ttyS4 at all tested baud rates.


With Ubuntu: Bad behavior

I've tried both Hoary and Breezy with identical results.

The system boots and discovers the built-in serial ports ttyS0 and ttyS1. Also discovered is another serial port called ttyS14. This appears to correspond to the modem (it is not discovered when the modem is removed). The PCI modem is also seen by lspci, and the device details (port, irq) are the same as with Knoppix.

After logging in and becoming root, the setserial command is typed:

    # setserial /dev/ttyS14 uart 16550A port 0xdcd8 irq 10

followed by wvdialconf. wvdialconf knows to look at ttyS0, ttyS1 and ttyS14, however when it gets to ttyS14, it claims that there is no modem (see the log below for actual results). I've tried using other tty devices (ttyS3, ttyS4) with the same results.

pppconfig also knows to look at ttyS0, ttyS1 and ttyS14, but it when it gets to ttyS14, the program hangs and CTRL/C must be typed.

Here is a log showing these results on Ubuntu Breezy. dmesg shows the serial ports that are found and lspci shows the device details. setserial is run next, followed by pppconfig, which hangs after it gets to ttyS14. CTRL/C is typed  then wvdialconf is run.

I would be very grateful for any suggestions on what to try next.

Thanks.

```
$ uname -a
 Linux dcl 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux
# lspci -v | grep -A 4 -i modem
0000:00:0d.0 Serial controller: 5610 56K FaxModem 56K FaxModem Model 5610 (rev 01) (prog-if 02 [16550])
        Subsystem: 5610 56K FaxModem USR 56k Internal Voice Modem (Model 2976)
        Flags: medium devsel, IRQ 10
        I/O ports at dcd8 [size=8]
        Capabilities: [dc] Power Management version 2
# dmesg | grep tty
[4294672.269000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.269000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294672.279000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.279000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294672.281000] ttyS14 at I/O 0xdcd8 (irq = 10) is a 16550A
# setserial /dev/ttyS14 uart 16550A port 0xdcd8 irq 10
# pppconfig

Probing /dev/ttyS0
Probing /dev/ttyS1
Probing /dev/ttyS14
<<<pppconfig hangs here>>>

# wvdialconf /etc/wvdial.conf
Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan<*1>: S2   S3   S4   S5   S6   S7   S8   S9
Port Scan<*1>: S10  S11  S12  S13
ttyS14<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS14<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS14<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan<*1>: S15  S16  S17  S18  S19  S20  S21  S22
Port Scan<*1>: S23  S24  S25  S26  S27  S28  S29  S30
Port Scan<*1>: S31  S32  S33  S34  S35  S36  S37  S38
Port Scan<*1>: S39  S40  S41  S42  S43  S44  S45  S46
Port Scan<*1>: S47  S48  S49  S50  S51  S52  S53


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wvdial/

If you still have problems, send mail to wvdial-list@lists.nit.ca.
```

---

### Post by az on 2005-10-25
I installed setserial and found that it had autoconfigured my Topic Semiconductor hardware modem by itself. (ttyS14)  It was then correctly detected by pppconfig and works out of the box.

---

### Post by JPZ on 2005-10-25
> 
I installed setserial and found that it had autoconfigured my Topic Semiconductor hardware modem by itself.


Your system probably has a file called /etc/serial.conf. It was created when you installed seterial; it contains the configuration details for your modem and is read by the startup script /etc/init.d/setserial (among others).

Invoking setserial manually accomplishes the same thing, and as I explained, doesn't work for me under Ubuntu.

Thanks anyway.

---

### Post by az on 2005-10-25
What I was getting at was why you did it a second time, if it was already configured for you?  I remember scratching my head, too.  After a reboot, I noticed that the device had been autoconfigured and worked fine.   I cannot explain...  

I was thinking it was a Udev thing....  I really dunno...

---

### Post by JPZ on 2005-10-26
Just wanted to let folks know how I resolved this: I decided to install Debian (sarge) and from there I installed the setserial package which worked just as it should. So although I'm not running Ubuntu, I did pick up on a reference for automatically adding /dev/modem [elsewhere in this forum]("http://ubuntuforums.org/showthread.php?t=29829&page=2"):

> 
create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:
#modem
KERNEL="ttyS14", SYMLINK="modem"


Therefore, I don't consider it an entire loss to try Ubuntu.

Thanks to all who pondered my question.

---

### Post by JPZ on 2005-10-26
Because I have two identical systems to configure, I still had one left with Ubuntu Hoary. On a whim, I decided to try the advice in dmesg. That advice is to add [FONT="Courier New"]pci=routeirq[/FONT] to the kernel boot options. After rebooting, the modem now works!

So the final solution for me to get the USR 5610 56K PCI modem to work is to do all of the following:

a) install setserial. When it installs, it creates a default configuration of the serial devices.

b) create the file in /etc/udev... as described in the previous update to automatically create /dev/modem each time the system boots.

c) add pci=routeirq to the kernel boot option. If you're using the grub bootloader (the default boot loader) then the file to edit is /boot/grub/menu.lst. Locate the first line that looks like this:

```
kernel    /boot/vmlinuz-xx.yy.zz root=/dev/hda...
```

Append the pci=routeirq option to the end of the line and save your changes.

d) reboot.

---

### Post by az on 2005-11-05
I did an install, too.

The modem was configured by alsa.  I do not even have to install setserial.

It is device /dev/ttyS14, but it is not autodetected by pppconfig or the gui networking tool.  It however, works like a charm.

---

### Post by sb73542 on 2005-11-13
This should be filed in Bugzilla.  The modem should create for itself /dev/ttyS4 , not /dev/ttyS14.

---

### Post by az on 2005-11-14
Maybe it should create a /dev/modem symlink or something, but I think the bug is that the gui networking tool (and pppconfig) do not look at ttyS14.

---

