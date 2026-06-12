---
title: "guide me to connect zte cdma modem on ubuntu 8.10"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by levirap on 2008-11-16
unable to connect usb modem .. guide me...
hi .. i m new to ubutnu .... 

jus yesterday i installed ubuntu 8.10 ... 

and i m happy with its successfull installation ... 

the problem is i have a tata indicom usb modem ... 

i donno how to configure and use it .... 


so i kindly request u guys to help me in this issue ... 


some info was given with my modem installation guide about installing it in linux ... 


i m posting it below .. i cant understant anytin from it .. 

can u guide me clealry plz ...

INFO PROVIDED WITH INSTALLATION DVD .. 

1, Load driver-zte evdo

1),Copy ztemt.ko from release's relevant directory to certain directory (take /home/lm/ztemt for example);
e.g., you need install Fedora core 6:
cp release/Fedora/FC6/ztemt.ko /home/lm/ztemt/

2),cp us-test/wvdial-conf /etc/

3),Load driver
insmod /home/lm/ztemt/ztemt.ko

4),Insert network card;

5),Run wvdial and to dial successfully (need root authorization). Normally, the following prompts will appear:
--> pid of pppd: 2450
--> Using interface ppp0
--> Authentication (CHAP) started
--> Authentication (CHAP) successful
--> local IP address 220.205.100.27
--> remote IP address 220.192.56.19
--> primary DNS address 220.192.32.103
--> secondary DNS address 220.192.0.130
--> Script /etc/ppp/ip-up run successful
--> Default route Ok.
--> Nameserver (DNS) Ok.
--> Connected... Press Ctrl-C to disconnect

6,FAQ
1),require software support:
udev
wvdial

2),It might not be able to resolve domain name after running wvdial to dial successfully. 
In this case, you need manually add primary DNS address and secondary DNS address to /etc/resolv.conf.

HELP ME OUT .. SINCE I CANT FIGURE OUT ANYTHING FROM THIS ..

---

### Post by sonu 1807 on 2008-11-17
I am using EVDO to reply to your post. I am using BSNL's (Indian Telecom Company) connection. After plugging in your EVDO

Step 1-: open terminal - from application-accesories

Step 2-: type lsusb- i get this 

Bus 001 Device 005: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 001 Device 004: ID 05c6:6000 Qualcomm, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 064e:a101 Suyin Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]

Qualcomm is your device

Step 3-: type sudo gedit 

Step 4-: open File system -> etc -> wvdial.conf

Step 5-: Copy paste the following

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Phone = #777
Modem = /dev/ttyUSB0
Username = 1111111111
Password = 1111111111
Baud = 460800
Stupid Mode = 1

1111111 is an example type your own username and password

Step 6-: save and close it

Step 7-: open terminal and type sudo wvdial 

You will be on net!

You got to enter sudo wvdial at the terminal to connect every time

Press Ctrl + C to disconnect

Hope this would help

---

### Post by levirap on 2008-11-17
dude  i am getting this message .. 

Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 19d2:ffff  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

i dont see any qualcom ...  

so wat should i do ..

---

### Post by levirap on 2008-11-17
also i installed  ubuntu 8.10 ..  is  wvdial already installed with it ... or should i install it mannualy .. 

if so how to install ... 

dude... i m newbee in linux .. plz .. help me.. 


and thznkx for ur previos replies...

---

### Post by levirap on 2008-11-17
[FONT="Arial Black"][COLOR="Magenta"][COLOR="Red"]help me out please . .. . i m trying as much i can to connect to internet with tata indicom usb modem (similar to bsnl evdo)from ubuntu 8.10 .. but i cant .. 

i have already posted several things .. and i m posting some of my results whichwud be informative to help me ..   plz solve my problem .. 
[/COLOR][/COLOR][/FONT]

$ modprobe usbserial vendor=0z05ca product=0x1839

FATAL: Error inserting usbserial (/lib/modules/2.6.27-7-generic/kernel/drivers/usb/serial/usbserial.ko): Operation not permitted


~$ wvdial config

--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer config] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory


~$lsusb

Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 19d2:ffff  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

from this i figured out that my modem vendor=0x05ca  , product=1839


i will be very much thankfull if u solve the problem ..  plz help me out. ..

---

### Post by sonu 1807 on 2008-11-18
Buddy! I am a police officer... preparing for IAS... no computer expert.. probably in your case it is Ricoh and not qualcomm. i did this on my computer .... sorry for delay in reply... internet was down from yesterday evening

Step 1-: I typed sudo su and then entered my root password
Step 2-: then cd /
step 3-: then lsusb i got this
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Purple"]Bus 003 Device 008: ID 05c6:6000[/COLOR] Qualcomm, Inc. 
Bus 003 Device 003: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a101 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
now this 05c6 is vendor and 6000 is product

type that and see what u get ... and replace 05c6 and 6000 above with that.....
in modprobe usbserial vendor=0x05c6 and product=0x6000 command
you then type sudo gedit  a window will open.... you click the open tab
in that and then you go to file system --> etc --> wvdial.conf

and copy paste what i sent u (except for username and pswd; use your own). then save it and close it....then open a terminal and type sudo wvdial.... i get some thing like this

--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Nov 18 16:24:31 2008
--> Pid of pppd: 6485
--> Using interface ppp0
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> local  IP address 10.20.105.164
--> pppd: &#65533;[7f]
--> remote IP address 192.168.52.12
--> pppd: &#65533;[7f]
--> primary   DNS address 218.248.240.79
--> pppd: &#65533;[7f]
--> secondary DNS address 218.248.240.135
--> pppd: &#65533;[7f]

once u get this kind of message in ur terminal u r connected

---

### Post by sonu 1807 on 2008-11-18
you got this **05ca:1839**

so that means you type modprobe usbserial vendor=0x05ca product=0x1839

sorry i didn't notice it earlier

---

### Post by sonu 1807 on 2008-11-18
Buddy wvdialconf command would not write anything in /etc/wvdial.conf because you are not logged in as root. there are two ways to edit it

1. press alt+f2 together;in the window type gksudo nautilus; in the left pane open File system.. then duble click etc folder .... then scroll down to find wvdial.conf file and open it... edit it .... save and close

2. second one is type sudo gedit in terminal and edit it as i have explained..... 

Ubuntu rocks.... i have vista CD... but i don't use it on my lappy.... it dual boots into 8.10 32-bit and 8.10 64-bit

---

### Post by sonu 1807 on 2008-11-18
One more thing unplug and replug device... sometimes this helps...

---

### Post by jka4321 on 2008-11-18
get a pentech 500 card from sprint and just plug it in works right off the bat

---

### Post by neelg22 on 2008-12-25
When I try to connect EVDO I get fallowing error. please tell me how to fix this. 

> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}!} }3}#}%B#}%}%}&} z}^z}'}"}(}"p#~~[7f]}#@!}!}"} }3}#}%B#}%}%}&} zf[13]}'}"}(}"w1~~[7f]}#@!}!}#} }3}#}%B#}%}%}&} zA)}'}"}(}"XH~~[7f]}#@!}!}$} }3}#}%B#}%}%}&} z:}^}'}"}(}""[10]~~[7f]}#@!}!}%} }3}#}%B#}%}%}&} zX}3}'}"}(}"G?~
--> Timed out while dialing.  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
~[7f]}#@!}!}!} }3}#}%B#}%}%}&} zG }'}"}(}"}([18]~~[7f]}#@!}!}"} }3}#}%B#}%}%}&} z}-K}'}"}(}"!4~~[7f]}#@!}!}#} }3}#}%B#}%}%}&} zM}0}'}"}(}"Lv~~[7f]}#@!}!}$} }3}#}%B#}%}%}&} z+i}'}"}(}"[07]W~


---

### Post by DominaDoom on 2008-12-26
> get a pentech 500 card from sprint and just plug it in works right off the bat

Hi, I have been using a Sprint USB modem, and it DID work fine for a few weeks without any configuring.  However, a few days ago some kind of mini disaster occured in my system.  I was booted off the internet, could not reboot my system, and could only reboot if I unplugged my modem from the USB.  Now, I don't get any options to connect with my mobile broadband.  I have to use WIFI, and have not solved the problem.  Any help with hardware detection greatly appreciated.

---

### Post by neelg22 on 2008-12-29
Hi,
I fallow Sonu1807's instructions and I get success to connect internet. I update and surf but when I restart my laptop something goes wrong.

Now I can connect to internet I can download updates but I cant surf the net with firefox.

It says its on offline mode.

What to do now?

---

### Post by ktorrent on 2009-06-03
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 004 Device 003: ID 19d2:ffff** 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
This is your modem.
open a terminal window and type 
#sudo -i wvdialconf
it will make a wvdial.conf file
edit the file and insert the configuration data.
Once you are through with it dial wvdial and hopefully you ll be connected to the internet in a jiffy.
I had been using the PCMCIA card offered by PTCL here in my country and just a couple of hours ago I exchanged it with the USB version which is ZTE USB Modem FFFF.
I plugged it in ubuntu, made the conf file and its working like a charm.

---

### Post by parth.khopkar96 on 2011-02-13
hi
i followed all the steps to make wvdial.conf.but when i try to open it in terminal it gives the following error
sudo: wvdial.conf: command not found
 please help

---

