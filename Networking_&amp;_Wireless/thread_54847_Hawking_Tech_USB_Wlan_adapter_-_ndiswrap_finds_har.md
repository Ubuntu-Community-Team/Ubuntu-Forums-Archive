---
title: "Hawking Tech USB Wlan adapter - ndiswrap finds hardware but no wireless extensions??"
date: 2005-08-06
forum: Networking &amp; Wireless
---

### Post by dsmudger on 2005-08-06
The following should sum up my progress to date - I've followed the Wiki instructions and managed to get ndiswrapper to see the hardware, but I can't get the adapter to show up in the networking application...

If anyone can help me out I'd really appreciate it! (perhaps this is a USB hotplug thing? I know linux/bash a bit, but not really anything about hotplug/USB and wireless networking)

summary of progress:

[INDENT][FONT=Courier New][SIZE=2]**root@ubuntu:/home/dsmith # ndiswrapper -l**
Installed ndis drivers:
zd1211u driver present, hardware present

**root@ubuntu:/home/dsmith # ndiswrapper -m**
modprobe config already contains alias directive

**root@ubuntu:/home/dsmith # modprobe -l ath***
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ath_hal/ath_hal.ko
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ath/ath_pci.ko

**root@ubuntu:/home/dsmith # ifconfig**
eth0   Link encap:Ethernet  HWaddr 00:08:02:6A:8E:AF  
          inet6 addr: fe80::208:2ff:fe6a:8eaf/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:3798 (3.7 KiB)

lo       Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1049676 (1.0 MiB)  TX bytes:1049676 (1.0 MiB)

**root@ubuntu:/home/dsmith # ifconfig ath0 up**
ath0: ERROR while getting interface flags: No such device

**root@ubuntu:/home/dsmith # iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

root@ubuntu:/home/dsmith #
[/SIZE]
[/FONT]
[/INDENT]**note: **modprobe -c output contains the line 'alias wlan0 ndiswrapper'
(also tried 'ifconfig wlan0 up' with the same results as above...)

---

### Post by az on 2005-08-06
What kind of device is it?

Some devices have native linux drivers that get loaded by hotplug.  If you do not want to use the native driver, you need to blacklist it in /etc/hotplug/blacklist.

When two drivers are trying to use the same hardware, it won't work.

---

### Post by dsmudger on 2005-08-06
it's a Hawking Tech 'HWU54D Hi-Gain USB Wireless-G Adapter'

Product page here: [http://www.hawkingtech.com/products/productlist.php?CatID=19&FamID=33&ProdID=226](http://www.hawkingtech.com/products/productlist.php?CatID=19&FamID=33&ProdID=226)

(it's a really good network adapter by the way - built-in directional antenna gives truly awesome range  :smile: )

Haven't been able to find any reference to it under Ubuntu/Debian on Google (similar story to mine here with a little background about the chipset - don't know for sure if it's correct: [http://lists.linux-wlan.com/pipermail/linux-wlan-user/2004-May/012544.html](http://lists.linux-wlan.com/pipermail/linux-wlan-user/2004-May/012544.html) )

---

### Post by az on 2005-08-06
What do you see when you boot without the device in and then open up a terminal and type

sudo tail -f /var/log/messages

and then plug it in?

---

### Post by dsmudger on 2005-08-07
Now we're cookin'  :) 

[SIZE=2][FONT=Courier New][INDENT]Aug  7 12:47:52 ubuntu kernel: usb 3-1: new high speed USB device using ehci_hcd and address 2
Aug  7 12:47:52 ubuntu kernel:
Aug  7 12:47:52 ubuntu kernel: zd1211u: probe of 3-1:1.0 failed with error -22

[/INDENT][/FONT][/SIZE]

Tried to do the leg-work and google for it of course, but all I can find is similar problems but no solution...

[B][COLOR=Red]-----------------------------------------
UPDATED:[/COLOR][/B]

had another look in the Wikis (ndiswrapper wiki [http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ](http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ)) and it looks as though this could be an IRQ problem? 

here's some more from my /var/log/messages - I pluged in/unplugged the adapter several times - seems it's assigning different IRQs each time?

[FONT=Courier New][SIZE=2][INDENT]Aug  7 13:52:29 ubuntu kernel: usb 1-1: USB disconnect, address 4
Aug  7 13:52:46 ubuntu kernel: usb 1-1: new full speed USB device using ohci_hcd and address 5
Aug  7 13:52:46 ubuntu kernel:
Aug  7 13:52:46 ubuntu kernel: zd1211u: probe of 1-1:1.0 failed with error -22
Aug  7 13:52:51 ubuntu kernel: usb 1-1: hald timed out on ep0in
Aug  7 13:53:26 ubuntu last message repeated 7 times
Aug  7 13:53:46 ubuntu last message repeated 4 times
Aug  7 13:54:11 ubuntu kernel: usb 1-1: USB disconnect, address 5
Aug  7 13:54:15 ubuntu kernel: usb 1-1: new full speed USB device using ohci_hcd and address 6
Aug  7 13:54:15 ubuntu kernel:
Aug  7 13:54:15 ubuntu kernel: zd1211u: probe of 1-1:1.0 failed with error -22
Aug  7 13:54:20 ubuntu kernel: usb 1-1: hald timed out on ep0in
[/INDENT][/SIZE][/FONT]

I also captured my current IRQ status:
[FONT=Courier New][SIZE=2][INDENT]
**root@ubuntu:/home/dsmith # cat /proc/interrupts**
           CPU0
  0:     603588          XT-PIC  timer
  1:       1105          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:        554          XT-PIC  Intel 82801CA-ICH3
  7:          1          XT-PIC  parport0
  8:          1          XT-PIC  rtc
  9:        734          XT-PIC  acpi
 10:       1267          XT-PIC  ohci_hcd, ohci_hcd
 11:      31276          XT-PIC  yenta, radeon@pci:0000:01:00.0
 12:      33453          XT-PIC  i8042
 14:       7490          XT-PIC  ide0
 15:       1094          XT-PIC  ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0
**root@ubuntu:/home/dsmith #**
[/INDENT][/SIZE][/FONT]

The Wiki also sugested there's a kernel module that conflicts with ndiswrapper and it sugested disabling it ([FONT=Courier New]modprobe --remove ehci_hcd[/FONT]) - I tried that but wasn't sure how to reset ndiswrapper (tried doing a [FONT=Courier New]modprobe --remove ndiswrapper[/FONT] and then a [FONT=Courier New]modprobe ndiswrapper[/FONT], but I don't think it worked - could have done it wrong though - if this is the way to go, I'd appreciate some help with exacly what to type when to plug in/unplug etc..?

What do you think - IRQs or conflicting module? (or something else?)

Thanks for your help so far by the way!

---

### Post by danielhaden on 2005-08-07
You could also try that same antenna from Hawking, Edimax, SMC, Jaht attached to a PCI RAlink card from them or PcUsa or Gigabyte (all have a big black chip with RA on it).  There are native Linux drivers at RAlink's corporate website as well as open source.  
That way you wouldn't have to load any USB drivers or worry about connectivity.

---

### Post by dsmudger on 2005-08-08
[QUOTE=danielhaden]You could also try that same antenna from Hawking, Edimax, SMC, Jaht attached to a PCI RAlink card from them or PcUsa or Gigabyte (all have a big black chip with RA on it).  There are native Linux drivers at RAlink's corporate website as well as open source.  
That way you wouldn't have to load any USB drivers or worry about connectivity.[/QUOTE]
 Cheers for the sugestion - but it's a non-starter - I'm installing on a laptop! :)

---

