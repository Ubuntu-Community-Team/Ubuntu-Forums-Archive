---
title: "Need Dial-up Help"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Javelin Dan on 2011-04-03
[FONT=Arial]Could someone please help me with some dial-up issues?  I’m trying to simply identify my US Robotics 5686 external modem in the “Detect Modem” tab in Gnome PPP. It  keeps telling me “No modem detected”. This is supposed to be a free-standing hardware modem requiring no drivers. I have chosen an ISP (Copper.Net)  but have not yet set up an account,  wanting to see my modem recognized before I do. I did call and talk to one of their reps, and she said I shouldn’t need service for my modem to be seen. I’ve read other forum entries and wiki’s  saying to have an account set up before trying to connect. I only have the power light lit on my modem - Copper.Net says I should have more. I have scoured all the dial-up how-to’s I could find, and there is very little on  this that I actually understand. From the little I can understand, it looks as though I may not have my serial port configured properly. I keep running across references to “setserial”. I read that it’s a program to identify serial port settings. Great! I enter “setserial” into the command line and get nothing. Likewise, I’ve entered various commands that were suggested using the word “setserial” and they all get rejected as bad commands. I search for “setserial” in synaptic, and the little ball spins and spins without even telling me it’s a bad search. What the hell?  No one anywhere I have seen tells you where this program is or how to get it. I have tried to do this in both Lubuntu and Antix 8.5 with the same results. Is it as simple as needing an ISP set up before I proceed? In any case, could someone  walk me through ([/FONT][FONT=Arial]*slowly) *[/FONT][FONT=Arial]the process of configuring my serial port and recognizing it in some window? Any other suggestions for dial-up how-to’s would be greatly appreciated. Thanks.[/FONT]

---

### Post by lkraemer on 2011-04-04
You just need a bit of information to get you started.......

First thing to do is go to SYSTEM -> ADMINISTRATION -> USERS & GROUPS
then MANAGE GROUPS, and add yourself to the Dialout group, and make sure
the checkbox is ticked......Then Logout and back in........


**SERIAL PORT NAMES:**
Dos/Windows use the COM name while the messages from the serial driver use ttyS00, ttyS01, etc.
Older serial drivers (2001 ?) used just tty00, tty01, etc.

The tables below shows some examples of serial device names. The IO addresses are the default
addresses for the old ISA bus (not for the newer PCI and USB buses).

dos common IO USB-BUS ( ACM => acm modem )
name name major minor address || common name common name
COM1 /dev/ttyS0 4, 64; 3F8 || /dev/ttyUSB0 | /dev/ttyACM0
COM2 /dev/ttyS1 4, 65; 2F8 || /dev/ttyUSB1 | /dev/ttyACM1
COM3 /dev/ttyS2 4, 66; 3E8 || /dev/ttyUSB2 | /dev/ttyACM2
COM4 /dev/ttyS3 4, 67; 2E8 || /dev/ttyUSB3 | /dev/ttyACM3
- /dev/ttyS4 4, 68; various


**SERIAL PORT or USB Converter:**
If you don't have a serial port on your Laptop, or want to use a USB port Converter check out the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008 SABRENT 1 ft.
USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, modems, etc.

[B]
SETUP UBUNTU (LINUX):[/B]
Open a Linux Terminal window and cut/paste the following commands with the
USB to Serial Adapter unplugged from a USB port.
```

dmesg | tail
lsusb

```
larry@ubuntu:~$ dmesg | tail
```

[10797.964432] domain 0: span 03
[10797.964434] groups: 01 02
[10797.964436] domain 1: span 03
[10797.964438] groups: 03
[10797.964440] CPU1 attaching sched-domain:
[10797.964441] domain 0: span 03
[10797.964443] groups: 02 01
[10797.964446] domain 1: span 03
[10797.964447] groups: 03
[12071.044928] usb 6-1: USB disconnect, address 3

```
larry@ubuntu:~$ lsusb
```

Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```
Then plug in the USB-Serial Port adaptor to one of your USB ports. (REMEMBER to ALWAYS use this
same port for when using your modem) Wait for about 15 seconds, then cut and paste the following
command in your Linux Terminal Window:
```

dmesg | tail
lsusb

```
You should see these messages.
```

larry@ubuntu:~$ dmesg | tail
[10797.964440] CPU1 attaching sched-domain:
[10797.964441] domain 0: span 03
[10797.964443] groups: 02 01
[10797.964446] domain 1: span 03
[10797.964447] groups: 03
[12071.044928] usb 6-1: USB disconnect, address 3
[12091.200574] usb 6-1: new full speed USB device using uhci_hcd and address 4
[12091.358706] usb 6-1: configuration #1 chosen from 1 choice
[12091.363887] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: This device cannot do calls on its own. It is no modem.
[12091.363914] cdc_acm 6-1:1.0: ttyACM0: USB ACM device

```
My device is /dev/ttyACM0

larry@ubuntu:~$ lsusb
```

Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```
Now, cut and paste the following command in your Linux Terminal Window:
```

lsusb -v -d 058f:9720

```
```

Bus 006 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 2 Communications
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 8
idVendor 0x058f Alcor Micro Corp.
idProduct 0x9720 USB-Serial Adapter
bcdDevice 0.00
.
.
.
.

```


**DISCOVER the COMM PORT:**
To locate the possible used COMM PORTS in Ubuntu, cut and paste the following command:
```

ls -l /dev/ttyS*

ls -l /dev/ttyU*
ls -l /dev/ttyA*

```
Notice that ttyS0 through ttyS3 are defined as shown

crw-rw---- 1 root dialout 4, 64 2009-11-27 15:26 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-11-27 15:26 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-11-27 15:26 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-11-27 15:26 /dev/ttyS3


Running this command will determine the Baud rate of the Port:
```

stty -F /dev/ttyS5 -a

```
and to change it to 9600:
```

stty -F /dev/ttyS5 9600
stty -F /dev/ttyS5 -a

```
If you connect to a modem for testing you can transmit out an "ATZ"
causing the Modem to flash the lights and reset with:
```

echo ATZ > /dev/ttyS5

```
Which proves characters were routed to the modem.


Now you just need to take a step back and configure pppd and wvdial,
then when all this is working configure Gnome-PPP.

You will need to set up the pap-secrets and/or chap-secrets file by running the
following in a Terminal Window:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppconfig

```

The pap-secrets at /etc/ppp/pap-secrets file contains:
(NOTE: File Format for 10.04)
```

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       hostname        ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   hostname        "*"     -
master  hostname        "*"     -
root    hostname        "*"     -
support hostname        "*"     -
stats   hostname        "*"     -

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.
#       *       password
"yourusername@yourisp.net" provider "yourpassword"

```
Now that ppp is setup, you will need to set up wvdial. Power up the modem, and connect
it to your serial port. In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file like this at
/etc/wvdial.conf (you may need to add a few things...)

wvdial.conf contains:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```
You might want to double check the following settings:
Checking settings of: /etc/ppp/options
```

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

```
Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

Once this works just re-configure Gnome-PPP and do the connect from the
GUI.

Total time should be less than 15 minutes.....and Copper.net works well
with Linux.  I still use Copper.net as my Dialup.

lk

---

### Post by Bartender on 2011-04-11
Are the little dipswitches on the 5686 set correctly?  3,5, and 8 should be in the "down" position.

Do you have a genuine USRobotics wall wart?  I ran into a crazy problem once where the wall wart (Radio Shack, not USR) appeared to be OK - voltage was correct - but the wall wart only produced 800 mA, not 1K mA.  The modem's "on" light would glow, but the modem would not connect.

Speaking of which, with the modem connected to your PC and turned on, you will only get the one red light on the face of the modem - I believe it's the furthest to the right.  The other lights come on in various patterns when connecting, connected, transmitting, receiving, etc.

GnomePPP will say "Modem not detected".  Manually enter ```
/dev/tty/S0
``` or ```
/dev/tty/S1

```
depending on which of your serial ports you connected to, then ask GnomePPP to detect.

---

### Post by Bartender on 2011-04-11
I've gone online with several Ubuntu PC's and 5686 modems - never had to mess with setserial

---

### Post by Bartender on 2011-04-11
I've been going online via dial-up every day for a coupla years now with this PC - it's an old Dell 470 workstation and a USR 5686 modem.  Below is the output when I opened a terminal and typed "setserial"

```
bpbar@bpbar-desktop:~$ setserial
The program 'setserial' is currently not installed.  You can install it by typing:
sudo apt-get install setserial
bash: setserial: command not found
bpbar@bpbar-desktop:~$ 
```
 
I think we can set aside setserial as having anything to do with you getting GnomePPP to detect the USR modem...

---

