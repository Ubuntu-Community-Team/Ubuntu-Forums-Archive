---
title: "GT Max Globetrotter pcmcia"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by mozzi on 2007-04-12
Hi all

I have a globe trotter gt max 7.2 ready pcmcia card
I cannot seem to see where to start to get it working under edgy!
It seems that under windows it runs as a usb modem, and it works perfectly.

root@mozzi-laptop:~# lspcmcia
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:02:04.0)
Socket 1 Bridge:        [yenta_cardbus]         (bus ID: 0000:02:04.1)

root@mozzi-laptop:~# lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

root@mozzi-laptop:~# lspci
02:04.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:04.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)


This is all the output I can get and am no nearer to a solution, I don't want to cut&paste all the output of dmesg so just this snippet :-)
[17181676.728000] ohci_hcd 0000:03:00.0: HC died; cleaning up
[17181676.728000] ohci_hcd 0000:03:00.1: HC died; cleaning up
[17181676.728000] usb 6-1: USB disconnect, address 2
[17181676.744000] pccard: card ejected from slot 0
[17181676.780000] ohci_hcd 0000:03:00.0: remove, state 0
[17181676.780000] usb usb5: USB disconnect, address 1
[17181676.780000] ohci_hcd 0000:03:00.0: USB bus 5 deregistered
[17181676.780000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[17181676.780000] ohci_hcd 0000:03:00.1: remove, state 0
[17181676.780000] usb usb6: USB disconnect, address 1
[17181676.784000] ohci_hcd 0000:03:00.1: USB bus 6 deregistered
[17181676.784000] ACPI: PCI interrupt for device 0000:03:00.1 disabled
[17182458.404000] usbcore: registered new driver usbserial
[17182458.404000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[17182458.404000] usbcore: registered new driver usbserial_generic
[17182458.404000] drivers/usb/serial/usb-serial.c: USB Serial Driver core


Thanx all

Mozzi

---

### Post by gazzap on 2007-05-30
Not sure if you're still work on on your problem.  I'm similar situation with Feisty 7.0.4 and Globetrotter GT MAX 3.6 card serial number starts with FN.   So supposedly it should come up with a ttyUSB0  (1 and 2)  but may need some modprobe usbserial to get it to load those usb devices.  I've tried using nozomi drivers and icon-switch  but bets I hear about the GT MAX 3.6 (7.2 ready) cards, is that they should run as ttyUSB0.    

I'm close, I can use the command  #gcom -d /dev/ttyUSB0  

(go fetch the gcom package and install it - good diagnostics).   I suspect your initial problem is that the /var/log/syslog is not showing something like this when you first insert the card, and therefore you can't see:   #find /dev/ | grep ttyUSB*  

[http://www.pharscape.org](http://www.pharscape.org)   has a Linux and GT Max 3G forum - and I've been trying various approaches they have been talking about, and I beleive the ttyUSB0 is the better direction, however, bear with me, as I can't get mine to get an IP address after it connects at 3600000. (That's why I've come over to this forum to look for issues with:
 pppd[24102]: rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
May 30 21:35:43 absoutback pppd[24102]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
May 30 21:35:44 absoutback pppd[24102]: rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]

Anyway - here's what I think you should be lookgin for in your syslog:


May 30 21:57:40 absoutback kernel: [104004.484000] usb 6-1: new full speed USB device using ohci_hcd and address 2
May 30 21:57:40 absoutback kernel: [104004.700000] usb 6-1: configuration #1 chosen from 1 choice
May 30 21:57:40 absoutback kernel: [104004.700000] option 6-1:1.0: GSM modem (1-port) converter detected
May 30 21:57:40 absoutback kernel: [104004.704000] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
May 30 21:57:40 absoutback kernel: [104004.704000] option 6-1:1.1: GSM modem (1-port) converter detected
May 30 21:57:40 absoutback kernel: [104004.704000] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
May 30 21:57:40 absoutback kernel: [104004.708000] option 6-1:1.2: GSM modem (1-port) converter detected
May 30 21:57:40 absoutback kernel: [104004.708000] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB2

---

### Post by Kendrick_mark on 2008-02-28
I'm trying to get my globe trotter 3.6 to work in 7.10.  I'm a noob but I've been bumblking around with this for 3 months.

I reinstalled the packages for gcom and used the command you listed above..
mkendrick@mkendrick-laptop:~$ gcom -d /dev/ttyUSB0
SIM ready
Waiting for Registration..(120 sec max)
Registered on Home network: "Cingular",2
Signal Quality: 14,99

What is the next step?  ubuntu sees the device and it seems to function.  I just don't know how to utilize it as a modem or network interface.

Thanks,
Mark

---

### Post by Kendrick_mark on 2008-03-06
I posted this in another thread but...

I got it to work using the 'vodafone mobile connect card driver'

[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

After downloading and installing ( I followed the reame file in the download) it auto detected my modem.

I was able to connect using these settings( I am posting this from it now!!!):

user [email]ISP@CINGULARGPRS.COM[/email]
pwd CINGULAR1
apn name: isp.cingular

---

### Post by Chalzor on 2008-04-09
For me I got the gt max 7.2 Ready working quite easily.

Only thing I needed to do was edit my wvdial.conf with the snippet pasted below. This worked for Rogers here in BC, Canada,  probably all you'd have to change is the "internet.com" that seems to be a different domain provider to provider.  As far as drivers go I didnt need to install anything special. I think wvdial was installed by default at least in kubuntu,  but not sure, if not install it with apt.

-----Cut Here----
[Dialer Defaults]

Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]

Init1 = AT+CPIN=1234

[Dialer option]

Modem = /dev/ttyUSB0
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem


[Dialer internet]

Init5 = AT+CGDCONT=1,"IP","internet.com";
-----Cut Here----

Hope this helps someone, 

Chalzor

PS: writing this using the GT MAX,  also getting about 2Mbps down according to speed-test sites.

---

