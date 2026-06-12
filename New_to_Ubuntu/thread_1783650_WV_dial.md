---
title: "WV dial"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by shibu_sawyer on 2011-06-16
hi.,
i want the procedures to connect my mobile to net using WVdial, The mobile broadband suite in ubuntu is not working for my LGKP175.,
pls help.. thanks in advance..

:D

---

### Post by jtarin on 2011-06-16
wvdial is an application for connecting via a dial-up modem.....are you certain this is what you want?

---

### Post by shibu_sawyer on 2011-06-16
yes,i got a problem in my broadband n i need to connect to net i checked many ways and the mobi-suite in ubuntu is not giving hand,so asking help to connect through wvdial...

---

### Post by jtarin on 2011-06-16
Is it ADSL? Then use PPPoE it's usually installed by default. [Here are the instructions]("https://help.ubuntu.com/community/ADSLPPPoE").....ignore the versions of Ubuntu it mentions. This app will run on anything.

---

### Post by shibu_sawyer on 2011-06-16
No mine is not a ADSL., lot of different names in ubuntu,whoof i am not getting use to it..

---

### Post by jtarin on 2011-06-16
> **shibu_sawyer said:**
> No mine is not a ADSL., lot of different names in ubuntu,whoof i am not getting use to it..
So are we going to keep playing this guessing game or are you going to tell how you connect.....the term broadband can be anything but dial-up?

---

### Post by shibu_sawyer on 2011-06-16
hi,
i found the solution. all i did is this,(i searched abt -wvdial in ubuntu documentation and found a solution):
shibu@shibu-desktop:~$ lsusb  (to find my modem id)
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 004: ID 0421:0445 qualcomm 
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 
shibu@shibu-desktop:~$
 
 Now note the line in which my qualcomm modem  is written...it has two number one is 0421 & other is 0445...i took these numbers as 0x421 & 0x445 
 
0421 is the Vendor ID & 0445 is the Product ID 
 
entered  this command. 
 
sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid) 
 
in my case: sudo /sbin/modprobe usbserial vendor=0×421 product=0×445 
 
Now enter this command 
 
wvdialconf /etc/wvdial.conf (to detect modem)
 
 
 i got a long o/p lik this:
 
Scanning your serial ports for a modem. 
Port Scan: S0 S1 S2 S3 
WvModem: Cannot get information for serial port. 
ttyACM0: ATQ0 V1 E1 &#8212; OK 
ttyACM0: ATQ0 V1 E1 Z &#8212; OK 
ttyACM0: ATQ0 V1 E1 S0=0 &#8212; OK 
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &#8212; OK 
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 &#8212; OK 
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 &#8212; OK 
ttyACM0: Modem Identifier: ATI &#8212; qualcomm
ttyACM0: Speed 4800: AT &#8212; OK 
ttyACM0: Speed 9600: AT &#8212; OK 
ttyACM0: Speed 19200: AT &#8212; OK 
ttyACM0: Speed 38400: AT &#8212; OK 
ttyACM0: Speed 57600: AT &#8212; OK 
ttyACM0: Speed 115200: AT &#8212; OK 
ttyACM0: Speed 230400: AT &#8212; OK 
ttyACM0: Speed 460800: AT &#8212; OK 
ttyACM0: Max speed is 460800; that should be safe. 
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 &#8212; OK 
Found an USB modem on /dev/ttyACM0. 
Modem configuration written to create. 
ttyACM0: Speed 460800; init &#8220;ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0&#8243; 
 
 
Notice the output says that there is a modem at /dev/ttyACM0 & max speed is 460800 
 
and edited my dialler configuration: 
 
sudo gedit /etc/wvdial.conf 
 
A file will open in text editor...
 
Phone = *7889# for my qualcomm modem
Username = username 
Password = password 
Stupid Mode = 1 
 
 
 
save the file &  done 
 
 
shibu@shibu-desktop~$ sudo wvdial 
 
wait till some sort of IP adress is displayed like 
 
pppd: &#65533;[06][06][08]` [06][08] 
primary DNS address 218.248.240.135 
pppd: &#65533;[06][06][08]` [06][08] 
secondary DNS address 218.248.240.79 
pppd: &#65533;[06][06][08]` [06][08] 
 
Now i am connected....
hurrahhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh

---

### Post by jtarin on 2011-06-16
Excellent....your own your way to independence and greatness. Mark this thread as solved. It will help someone else.

---

### Post by shibu_sawyer on 2011-06-16
Sure and thanks.......... :-) :-) :-)

---

