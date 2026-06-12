---
title: "Help required tp setup up CDMA wireless modem on Ubuntu DApper"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by ramnarayan on 2006-09-10
Hi

This is a question regarding how to setup a Wireless Data Card in India. The card is a Wireless PCMCIA CDMA modem

Model ZTE MC315


800 MHz CDMA 1X
Model MC315
PCMCIA Type -II
Wireless Modem

System -Laptop using Ubuntu Dapper 6.06

So I used infor from the following links

[http://www.linuxquestions.org/linux/answers/LinuxQuestions_org/CDMA_modem_phone_Howto](http://www.linuxquestions.org/linux/answers/LinuxQuestions_org/CDMA_modem_phone_Howto)

and

[http://spo0nman.blogspot.com/2006/08/huawei-ec321-cdma-on-linux.html](http://spo0nman.blogspot.com/2006/08/huawei-ec321-cdma-on-linux.html)

but after having progressed some still cannot figure out how to get the modem working.

The first link  got the  ZTE phone modem working and following the instructions from that link i seem to have got close but not close enough so need to understand what else to do to get the modem identified properly and working

Ran the following and got an ouput that that not show anyhting apart from the figerprint reader

ram:~$ sudo cat /proc/bus/usb/devices
Password:

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-26-686 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-26-686 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0483 ProdID=2016 Rev= 0.01
S:  Manufacturer=STMicroelectronics
S:  Product=Biometric Coprocessor
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   4 Ivl=20ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-26-686 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-26-686 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms


ran dmesg and got the following output

with lots of snips in between - 
[17179575.100000] usbcore: registered new driver usbfs
[17179575.104000] usbcore: registered new driver hub
[17179575.104000] USB Universal Host Controller Interface driver v2.3
[17179575.104000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179575.104000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179575.104000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179575.104000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179575.104000] uhci_hcd 0000:00:1d.0: irq 169, io base 0x00001800
[17179575.104000] hub 1-0:1.0: USB hub found
[17179575.104000] hub 1-0:1.0: 2 ports detected

and some of this as well
[17179588.892000] pccard: PCMCIA card inserted into slot 0
[17179588.892000] cs: memory probe 0xe4300000-0xe7ffffff: excluding 0xe4300000-0xe46cffff 
0xe4e70000-0xe523ffff 0xe5db0000-0xe7ffffff
[17179588.920000] pcmcia: registering new device pcmcia0.0
[17179588.972000] cs: IO port probe 0x100-0x3af: excluding 0x370-0x377
[17179588.984000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[17179588.988000] cs: IO port probe 0x820-0x8ff: clean.
[17179588.992000] cs: IO port probe 0xc00-0xcf7: clean.
[17179588.996000] cs: IO port probe 0xa00-0xaff: clean.
[17179589.032000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[17179589.100000] ttyS3: detected caps 00000700 should be 00000100
[17179589.100000] 0.0: ttyS3 at I/O 0x2e8 (irq = 4) is a 16C950/954

Then The ran the following to get the cdc_acm module - highlighted

ram@ram-t60:~$ sudo cat /proc/modules

Ram: THEN RAN dmesg again and got this

ram@ram-t60:$sudo dmesg
lots snipped

[17181174.212000] usbcore: registered new driver cdc_acm
[17181174.212000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and 
ISDN adapters
cdc_acm 14368 0 - Live 0xf8e71000

then
This is my reliance /etc/ppp/peers/reliance (file) 
# This optionfile was generated by pppconfig 2.3.10. 
# 
#
/dev/ttyS3
    115200
    debug
    lock
    asyncmap 0
    crtscts
    modem
    defaultroute
    usepeerdns
    noauth
    connect '/usr/sbin/chat -v "" at+crm=1 OK "atdt#777" CONNECT'
    mtu 264
    name reliance
    user my user name

The edited my pap secrets: 

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#”user name”	*	“password”


 "with my user name" * "with my password"

RAM: This is my copy of wvdial.conf

[Dialer reliance] 
Modem = /dev/ttyS3
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Name = CDMA

Modem Type = USB Modem
Phone = #777
Username = with my user name
Password = with my pass word
Stupid Mode = 1
PPPD Options = crtcts multilink usepeerdns lock defaultroute

***
Am assuming that since ttyS3 appeared in the dmesg it must be the device ??

Checked out pppd as instructed and got
ram@ram-t60:/$ pppd
~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&&#1153;&#65533;@}'}"}(}"&#65533;Y~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&&#1153;&#65533;@}'}"}(}"&#65533;Y~~&#65533;}#&#65533;!}!}!} 
}4}"}&} } } } }%}&&#1153;&#65533;@}'}"}(}"&#65533;Y~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&&#1153;&#65533;@}'}"}(}"&#65533;Y~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } 
}%}&&#1153;&#65533;@}'}"}(}"&#65533;Y~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&&#1153;&#65533;@}'}"}(}"&#65533;Y~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } 
}%}&&#1153;&#65533;@}'}"}(}"&#65533;Y~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&&#1153;&#65533;@}'}"}(}"&#65533;Y~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } 
}%}&&#1153;&#65533;@}'}"}(}"&#65533;Y~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&&#1153;&#65533;@}'}"}(}"&#65533;Y~ram@ram-t60:/$

as it was supposed to be
 So tried wvdial and got this:
error
ram@ram-t60:/$ sudo wvdial reliance
--> WvDial: Internet dialer version 1.55
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

***
what do i do next

thanks
ram

---

