---
title: "Nokia CS-10 (Wind Italy) on Lubuntu 10.04"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by al.adab on 2010-10-12
(please also see
[http://ubuntuforums.org/showthread.php?t=1589289](http://ubuntuforums.org/showthread.php?t=1589289)) 

I'm in Italy and have been given a Nokia CS-10 dongle (Wind Italy) + facing the following issue: 

[I]~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ0
ATZ0
OK
--> Sending: AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet.wind","",0,0
AT+CGDCONT=1,"IP","internet.wind","",0,0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
ERROR
--> Invalid dial command.
--> Disconnecting at Tue Oct 12 22:55:17 2010[/I]

I also tried to connect through GNOME PPP and here's the result:

[I]--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: Init3 = AT+CGDCONT=1,"IP","internet.wind","",0,0
Init3 = AT+CGDCONT=1,"IP","internet.wind","",0,0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number. [/I]

After checking Ubuntu Forums Italy I've set the wvdial.conf file as follows: 

[I][Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init = ATZ0
Init2 = AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet.wind","",0,0
Modem Type = Analog Modem
Carrier Check = no
Phone = *99***1#
Password = wind
Username = wind
Stupid Mode = 1[/I]

I have usb_modeswitch + data installed and have also set up the connection on Network Manager...

Any idea?

---

### Post by alexfish on 2010-10-12
Hi
first need to see which ports are been used
and which part of the device is the modem

ensure only one device is connected , then from the terminal 

Code:

[COLOR=Blue]ls -al /dev/serial/by-id/usb*[/COLOR]

Code:

[COLOR=Blue]usb-devices[/COLOR]

look for the part which indicates the device and post only that part

don't forget to post details of the "[COLOR=Blue]ls -al /dev/serial/by-id/usb*[/COLOR]" command.

also mention in the link , tried Network Manager

can you check  if modem-manager is installed

alexfish

---

### Post by al.adab on 2010-10-13
here you go :) 

~$ ls -al /dev/serial/by-id/usb*
lrwxrwxrwx 1 root root 13 2010-10-13 09:14 /dev/serial/by-id/usb-Nokia_Nokia_Datacard_0.0.1-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 2010-10-13 09:14 /dev/serial/by-id/usb-Nokia_Nokia_Datacard_0.0.1-if03 -> ../../ttyACM1

~$ usb-devices
T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0421 ProdID=060e Rev=00.01
S:  Manufacturer=Nokia
S:  Product=Nokia Datacard
S:  SerialNumber=0.0.1
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=08 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm

"modem-manager" is installed. Thanks tons for your help!

---

### Post by PaulReaver on 2010-10-13
why use wvdial?

I've always found pon and pppconfig more reliable and its already installed in ubuntu by default

you need to know your isp username and password
and need to find out your modem port (probably /dev/ttyUSB0 or /dev/ttyACM0) 
and add yourself to the dip group.

---

### Post by al.adab on 2010-10-13
in Lubuntu for some reason NetworkManager doesn't detect GPRS modems like in Ubuntu (at least in my case). I find that wvdial is a good alternative (and use it with my UK dongle no problem). Also "discovered" Gnome PPP last night :) 

i might be mistaken but it doesn't look like a problem of port or username/password. I'm wondering if I shouldn't insert the PIN number in the *wvdial.conf* file, though. What string should I use, in this case? *PIN = xxxx* ? Tried it but doesn't make the difference.

---

### Post by al.adab on 2010-10-13
in Lubuntu for some reason NetworkManager doesn't detect GPRS modems like in Ubuntu (at least in my case). I find that wvdial is a good alternative (and use it with my UK dongle no problem). Also "discovered" Gnome PPP last night :) 

i might be mistaken but it doesn't look like a problem of port or username/password. I'm wondering if I shouldn't insert the PIN number in the *wvdial.conf* file, though. What string should I use, in this case? *PIN = xxxx* ? Tried it but doesn't make the difference.

---

### Post by al.adab on 2010-10-13
after installing modem-manager, I can now see the "Wind non-business" GPRS connection in Network Manager, although I cannot connect.

---

### Post by alexfish on 2010-10-13
Hi 

from the information above the modem is showing
lrwxrwxrwx 1 root root 13 2010-10-13 09:14 /dev/serial/by-id/usb-Nokia_Nokia_Datacard_0.0.1-if01 -> ../../[COLOR=Blue]ttyACM0[/COLOR]
lrwxrwxrwx 1 root root 13 2010-10-13 09:14 /dev/serial/by-id/usb-Nokia_Nokia_Datacard_0.0.1-[COLOR=Blue]if03 -> ../../ttyACM1
[/COLOR]

note the  [COLOR=Blue]if03 -> ../../ttyACM1

[COLOR=Black]the[/COLOR] [/COLOR][COLOR=Blue]if03 [COLOR=Black]may be[/COLOR]  [COLOR=Black]indicating  the modem part of the device,  the[/COLOR] [/COLOR][COLOR=Blue]/ttyACM1 indicates the tty port (node)

[COLOR=Black]**So for wvdial could try**[/COLOR]

[COLOR=Blue]modem = /dev[/COLOR][/COLOR][COLOR=Blue]/ttyACM1[/COLOR][B][COLOR=Blue]

[/COLOR][/B][COLOR=Black]but there appears to be an error[/COLOR][B][COLOR=Blue]

[/COLOR][/B]I: If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=08 Prot=00 Driver=(none)
I: If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I: If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
[COLOR=Blue]I: If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm[/COLOR]
I: If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm

the line highlighted in blue , part which shows " [COLOR=Blue]If#= 3[/COLOR] "  only shows one end point " [COLOR=Blue]EPs= 1[/COLOR]"    , normaly  this would be [COLOR=Blue]EPs= 3 , [/COLOR]EPs=3 normally indicates to the system the modem port
so any device manager looking for this ,  may not find it

as the listing does not show any EPs = 3 , something is wrong 

can you try wvdial can try adding this line to the conf file

[COLOR=Blue][COLOR=Black]modem = /dev[/COLOR][/COLOR][COLOR=Black]/ttyACM1[/COLOR][B][COLOR=Blue]

[/COLOR][/B][COLOR=Blue][COLOR=Black]see what happens[/COLOR][/COLOR][B][COLOR=Blue]


[/COLOR][/B][COLOR=Black]alexfish[/COLOR][B][COLOR=Blue]
[/COLOR][/B]

---

### Post by al.adab on 2010-10-13
thank you for taking the time to do this. 

both with modem = /dev/ttyACM1 and Modem = /dev/ttyACM0: 

(...)
[I]OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
ERROR
--> Invalid dial command.[/I]
--> Disconnecting at Wed Oct 13 13:13:24 2010

I won't be able to try the dongle on Windows before tomorrow - just to double-check it can actually connect.

---

### Post by alexfish on 2010-10-13
> **al.adab said:**
> in Lubuntu for some reason NetworkManager doesn't detect GPRS modems like in Ubuntu (at least in my case). I find that wvdial is a good alternative (and use it with my UK dongle no problem). Also "discovered" Gnome PPP last night :) 

i might be mistaken but it doesn't look like a problem of port or username/password. I'm wondering if I shouldn't insert the PIN number in the *wvdial.conf* file, though. What string should I use, in this case? *PIN = xxxx* ? Tried it but doesn't make the difference.

to check if the PIN code  required

[COLOR=Blue]AT+CPIN?[/COLOR]

to use a PIN code

AT+CPIN=<YOUR PINCODE>

EXAMPLE

*Init2 = *[COLOR=Blue]AT+CPIN=1234



[COLOR=Black]AS regards usb_modeswitch , will the device configure without it ( try to disable the switching)

Having read through  other threads + posts , your devices seem to be 3g( GSM Connection)

I could suggest trying Sakis3g(usb_modeswitch embedded), it will  put you more in control of switching the device
 
although can't say if it will solve the problem with this device

If Sakis3g(usb_modeswitch embedded) is installed , then try un-installing the usb_modeswitch from synaptic

[/COLOR][/COLOR]**[*Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CBUQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=R8y1TIqTJ8jm4Aa0ppj6DQ&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**

To all readers 

Read this thread and the link to sakis3g  in detail before committing ( or even wait till a SOLVE is POSTED )

regards

alexfish

---

### Post by al.adab on 2010-10-13
right: installed Sakis3g as 

s[I]udo bash
apt-get install ppp
cd /usr/bin
wget 'http://www.sakis3g.org/versions/latest/sakis3g.gz'
echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c
You should see: sakis3g.gz: OK
gunzip sakis3g.gz
chmod +x sakis3g[/I]

+ removed usb_switchmode. 

Will get back on this asap.

---

### Post by al.adab on 2010-10-13
a step forward, perhaps: 

1) inserted usb dongle
2) launched Sakis3G in terminal
3) dialogue window pops up 
- choose action>Connect with 3G
- select modem category>USB device>Nokia Datacard
- select modem interface>

a) if I choose modem interface #1, I get the following message: 
*Modem responded "SIM PUK" while checking for PI*
b) if I choose modem interface #3, I get the following messages: 
-*Port /dev/ttyACM1 is currently occupied by 781 modem-manager. *
-*Failed to connect* 

I recall reading somewhere re: removing the PIN by inserting the dongle's SIM into an ordinary mobile handset, but the PUK...

will look into Sakis3G documentation. In the meantime, if you have any suggestion...thanks!

---

### Post by al.adab on 2010-10-13
this might be of help re: PIN/PUK
[http://wiki.sakis3g.org/wiki/index.php?title=PIN_number](http://wiki.sakis3g.org/wiki/index.php?title=PIN_number)
I'll try out the mobile phone option...

re: *Port /dev/ttyACM1 is currently occupied by 781 modem-manager* I can't find much...

---

### Post by Sakis3G on 2010-10-13
Hi al.adab,

I am the author of Sakis3G script. 

> **al.adab said:**
> a step forward, perhaps: 
a) if I choose modem interface #1, I get the following message: 
[I]Modem responded "SIM PUK" while checking for PIN
[/I]
This means that your SIM card is already blocked. Some of your previous attempts kept sending to _wrong PIN_ to SIM card. This resulted into SIM card being blocked and PUK number being required instead. Solution is to temporarily plug your SIM card onto a mobile phone and unlock it by providing **PUK number**. This will unlock your SIM card back to normal operation. Under normal operation it only requests for a PIN.

> **al.adab said:**
> 
b) if I choose modem interface #3, I get the following messages: 
-*Port /dev/ttyACM1 is currently occupied by 781 modem-manager. *
-*Failed to connect* 

This means that Sakis3G is unable to reach tty provided by interface #3. Reason is that modem-manager (part of network-manager) has tty occupied. You either need to wait enough for modem-manager to release port, or to disable network-manager altogether (not recommended). However, even this will be useless, before unblocking your SIM card by providing PUK number (see above).

> **al.adab said:**
> 
 I recall reading somewhere re: removing the PIN by inserting the dongle's SIM into an ordinary mobile handset, but the PUK...

 Some software/modem combos are proven to be unable to handle PIN unlock. On those cases, permanently disabling PIN is indeed advised. Before getting into this path, you should try to provide PUK.

Maybe, reason behind expected plug-n-play not working, is just the PUK number being required instead of PIN (network-manager, gnome-ppp and wvdial do not inform accordingly when this is the case). Maybe you can carry on without the need for Sakis3G (after PUK is provided), and live an out-of-the-box experience.

Sakis

---

### Post by al.adab on 2010-10-14
thank you Sakis. 

Good news first: I managed to connect via the Nokia CS-10 dongle :) 

RE: Sakis3G: I'm afraid it didn't work. After sorting out the PUK + PIN issue (both unlocked in an ordinary mobile phone), I tried to connect through *sakis 3g* (in terminal). It did this time recognised modem, USB device, and network (Wind Italy), but failed to connect. No reasons are given at the error message. 

At the moment I'm connecting through *wvdial* in terminal, and with no need of Sakis3g, Modem-Manager, Gnome PPP. 

The *wvdial.conf* file is as it was when I initiated this thread (please see notes on possible modem error).  

Thanks tons everyone for their help.

---

### Post by alexfish on 2010-10-14
hi al.adab

good news , 

you can now see how Sakis3g can help as a precursor , for setting up  a usb devices such as yours

Sakis3g also have a forum , it is over looked by Sakis and also very helpful

one last thing can you post the results of the " usb-devices" 
to see if there are any changes, helpfull for debugging future posts with this device reference

regards

alexfish

---

### Post by al.adab on 2010-10-14
thanks alexfish for taking care of this. 

here's the usb-devices: 


[I]~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1bcf ProdID=0007 Rev=00.10
S:  Product=USB Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1668 ProdID=2441 Rev=05.46
S:  SerialNumber=&#12339;&#12852;&#12337;&#12594;&#12342;&#14640;
C:  #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=90mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0483 ProdID=2016 Rev=00.01
S:  Manufacturer=STMicroelectronics
S:  Product=Biometric Coprocessor
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)[/I]

---

### Post by al.adab on 2010-10-14
oops...forgot to run usb-devices without the very source of all troubles :) 

[I]~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0421 ProdID=060e Rev=00.01
S:  Manufacturer=Nokia
S:  Product=Nokia Datacard
S:  SerialNumber=0.0.1
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=08 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1668 ProdID=2441 Rev=05.46
S:  SerialNumber=&#12339;&#12852;&#12337;&#12594;&#12342;&#14640;
C:  #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=90mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0483 ProdID=2016 Rev=00.01
S:  Manufacturer=STMicroelectronics
S:  Product=Biometric Coprocessor
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)[/I]

---

