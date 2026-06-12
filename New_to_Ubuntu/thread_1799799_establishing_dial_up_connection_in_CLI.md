---
title: "establishing dial up connection in CLI"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by konsolelover on 2011-07-08
hello, i want to know how can i connect my dial up network using command  line in ubuntu 11.04 when my X server is in off mode....i have already  set up the mobile broadband settings and its working fine...i am using  Nokia 5130 Xpress Music phone and i connect through USB and select PC  suite mode....then i dont know what to do.....TIA

---

### Post by jtarin on 2011-07-08
[wvdial is what you want.]("http://linmodems.technion.ac.il/wvdial.html")
[Ubuntu Documentation]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer")

---

### Post by shibu_sawyer on 2011-07-08
> **konsolelover said:**
> hello, i want to know how can i connect my dial up network using command  line in ubuntu 11.04 when my X server is in off mode....i have already  set up the mobile broadband settings and its working fine...i am using  Nokia 5130 Xpress Music phone and i connect through USB and select PC  suite mode....then i dont know what to do.....TIA


To connect to Internet through mobile there are two ways 
1)mobile broadband suite(definitely works on recent mobiles)

2)Through Wvdial

These are the procedures to connect through command line:

Connect your phone via data-cable 

open terminal & type :lsusb  (this will list all your usb items)
 
now you will get the following output 
 
shibu@shibu-desktop:~$ lsusb 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 004: ID 0421:0445 Nokia Mobile Phones 
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 

shibu@shibu-desktop:~$ 
  
it is on my computer,your will not see exactly the same... 
 
Now note the line in which Nokia Mobile Phones are written...it has two number one is 0421 & other is 0445...we'll take these numbers as 0x421 & 0x445 
 
0421 is the Vendor ID & 0445 is the Product ID 
 
Now enter this command. 
 
sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid) 
 
eg, in my case::: sudo /sbin/modprobe usbserial vendor=0×421 product=0×445 
 
Now enter this command  :  wvdialconf /etc/wvdial.conf 
 
 
you'll get a long output which will be like 
 
Scanning your serial ports for a modem. 
Port Scan: S0 S1 S2 S3 
WvModem: Cannot get information for serial port. 
ttyACM0: ATQ0 V1 E1 — OK 
ttyACM0: ATQ0 V1 E1 Z — OK 
ttyACM0: ATQ0 V1 E1 S0=0 — OK 
ttyACM0: ATQ0 V1 E1 S0=0 &C1 — OK 
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 — OK 
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK 
ttyACM0: Modem Identifier: ATI — Nokia 
ttyACM0: Speed 4800: AT — OK 
ttyACM0: Speed 9600: AT — OK 
ttyACM0: Speed 19200: AT — OK 
ttyACM0: Speed 38400: AT — OK 
ttyACM0: Speed 57600: AT — OK 
ttyACM0: Speed 115200: AT — OK 
ttyACM0: Speed 230400: AT — OK 
ttyACM0: Speed 460800: AT — OK 
ttyACM0: Max speed is 460800; that should be safe. 
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK 
Found an USB modem on /dev/ttyACM0. 
Modem configuration written to create. 
ttyACM0: Speed 460800; init “ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0&#8243; 
 
 
Notice the output says that there is a modem at /dev/ttyACM0 & max speed is 460800 
 
now enter this command  : sudo gedit /etc/wvdial.conf 
 
A file will open in text editor...paste the following there 
(Your phone number (the dial up number i mean) may vary depending on your provider....Call em' now....) 
 
Phone = *99# 
Username = username 
Password = password 
Stupid Mode = 1 
 
 
 
You Can Also delete everything & paste this 
 
[Dialer Defaults] 
Modem = Your Modem Name(eg, /dev/ttyACM0 in my case) 
Baud = ur max speed(460800 in my case) 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ISDN = 0 
Modem Type = Analog Modem 
Phone = *99# 
Username = username 
Password = password 
Stupid Mode = 1 
 
save the file & you are done 
 
 
Whenever you need to connect...open terminal & type 
 
sudo wvdial 
terminal will prompt for the password provide it...
 
wait till some sort of IP adress is displayed like 
 
pppd: &#65533;[06][06][08]` [06][08] 
primary DNS address 218.248.240.135 
pppd: &#65533;[06][06][08]` [06][08] 
secondary DNS address 218.248.240.79 
pppd: &#65533;[06][06][08]` [06][08] 
 
Now you are connected....hit control+c to dissconnect... 

Voila you are connected.. :guitar:

---

### Post by shibu_sawyer on 2011-07-08
i forget to say at first you should have wv dial installed in your system. its easy, go to synaptic package manager,type in wvdial in the quick search,if its already installed the checkbox will be green in color,if not click it to install..

---

### Post by konsolelover on 2011-07-08
installed wvdial ....and as described in documentation ,tried to edit wvdial.conf and it asked me to enter
phone, password, username,,,,,,assuming that phone is the number which is dialed in order to connect to internet, in my case it is *99# ,But my ISP (Airtel) has not provided any username or password  ...so left those sections blank....but when i tried to connect using

sudo wvdial
got the errer
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
edit: also when i tried
sudo /sbin/modprobe usbserial vendor=0×421 product=0×208
FATAL: Error inserting usbserial (/lib/modules/2.6.38-8-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

---

### Post by swaprava on 2011-07-08
perhaps you can try pppoeconf. usually some broadband services are via PPPOE, at least that worked for me at home.

```
sudo apt-get install pppoeconf
```

and then

```
sudo pppoeconf
```

it will ask for your username, password with which you connect to the broadband. only it requires the password to be written in plaintext.

---

### Post by shibu_sawyer on 2011-07-08
> **konsolelover said:**
> installed wvdial ....and as described in documentation ,tried to edit wvdial.conf and it asked me to enter
phone, password, username,,,,,,assuming that phone is the number which is dialed in order to connect to internet, in my case it is *99# ,But my ISP (Airtel) has not provided any username or password  ...so left those sections blank....but when i tried to connect using
sudo wvdial
got the errer
invalid phone, invalid username , invalid paaword....


it connects even if there is no username and password. but it needs phone number,i am using DOCOMO and my number is *99#.,please check yours

---

### Post by shibu_sawyer on 2011-07-08
post your o/p I'll find what went wrong..

---

### Post by konsolelover on 2011-07-08
I'm Using Airtel and my number is *99# too but i'm getting this error
sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

---

### Post by shibu_sawyer on 2011-07-08
there are two things i gotta say
1) if you don enter your vendor and product id correct you'll get a error...
2)
Phone = *99# 
Username = username 
Password = password 
Stupid Mode = 1 
if you have used this,i think dialler version needs more so re-edit it as
 
  [Dialer Defaults] 
Modem = /dev/ttyACM0 (get yours)
Baud = 460800
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ISDN = 0 
Modem Type = Analog Modem 
Phone = *99# 
Username = username 
Password = password 
Stupid Mode = 1 

For me when i first tried(i learned through ubuntu doc's),i had an error cos i tried the dialler defaults like this

Phone = *99# 
 Username = username 
 Password = password 
 Stupid Mode = 1  showed some error while connecting

so i switched to this way
Dialer Defaults] 
Modem = Your Modem Name(eg, /dev/ttyACM0 in my case) 
Baud = ur max speed(460800 in my case) 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ISDN = 0 
Modem Type = Analog Modem 
Phone = *99# 
Username = username 
Password = password 
Stupid Mode = 1
then it connected..

if this also doesn give hand then problem is pinning in your vendor id..

---

### Post by konsolelover on 2011-07-08
1- when i tried 
sudo /sbin/modprobe usbserial vendor=0×421 product=0×208
FATAL: Error inserting usbserial (/lib/modules/2.6.38-8-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

2-n when sudo wvdial

--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Jul  8 17:19:19 2011
--> Pid of pppd: 1999
--> Using interface ppp0
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> Disconnecting at Fri Jul  8 17:19:23 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Jul  8 17:19:30 2011
--> Pid of pppd: 2004
--> Using interface ppp0
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> Disconnecting at Fri Jul  8 17:19:34 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 10 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
 and kept repeating and in my mobile i saw the message -subscibe to packet data first

---

### Post by shibu_sawyer on 2011-07-08
> **konsolelover said:**
> 1- when i tried 
sudo /sbin/modprobe usbserial vendor=0×421 product=0×208
FATAL: Error inserting usbserial (/lib/modules/2.6.38-8-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

2-n when sudo wvdial

--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Jul  8 17:19:19 2011
--> Pid of pppd: 1999
--> Using interface ppp0
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> Disconnecting at Fri Jul  8 17:19:23 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Jul  8 17:19:30 2011
--> Pid of pppd: 2004
--> Using interface ppp0
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> pppd: `&#65533;$ ([02]% 
--> Disconnecting at Fri Jul  8 17:19:34 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 10 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
 and kept repeating and in my mobile i saw the message -subscibe to packet data first

have you set your access point correctly, if not this message will repeatedly occurs.
i tried connecting my nokia 2700 classic ,it works fine and also my LG KP175 works fine through wvdial.
infact now i surfing through my LG which i connected through wvdial. 

your modem works fine,so lets give a last shot,try downloading ppp from synaptic and again try wvdial this time insert the vendor id and product id using sudo modprobe usbserial vendor=0421 product=0208 or if ubuntu don allow this way use the old way itself and do the rest by editing and entering your information and then invoke wvdial. This time it must else the probs is with carrier.

---

