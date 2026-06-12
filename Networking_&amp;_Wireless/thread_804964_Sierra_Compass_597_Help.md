---
title: "Sierra Compass 597 Help"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by _UsUrPeR_ on 2008-05-23
Trying to get this working in ubuntu. Has anyone had any luck so far?

Thanks

---

### Post by skydiver|goose on 2008-05-23
according to Sprint's website (link: [http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf) on page 4) the Compass 597 isn't supported on Linux. Disappointing, because that was the make-or-break factor for me getting one. Guess I'll have to go to another carrier...

---

### Post by zippy51 on 2008-08-22
> **skydiver|goose said:**
> according to Sprint's website (link: [http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf) on page 4) the Compass 597 isn't supported on Linux. Disappointing, because that was the make-or-break factor for me getting one. Guess I'll have to go to another carrier...

Sprint just doesn't feel like spending any time helping non-Windows users.  A colleague of mine got the Compass 597 working on my laptop under Ubuntu "Hardy Heron", as follows:

1) Install “KPPP” via “Applications” -> “Add/Remove” on Ubuntu desktop.  Be sure to request “Show” -> “All available applications” and look under “Internet” applications for KPPP.

2) Launch KPPP from drop-down menu at “Applications” -> “Internet” -> “KPPP”

3) When GUI appears, select “Configure” and configure as follows:

Connect to:            WWAN
Login ID:              user
Pwd:                   user

Accounts
========
Connection Name:       WWAN
Phone number:          #777
Authentication:        PAP/CHAP
Use Lock File:         checked
Callback type:         None
IP:                    Dynamic
Gateway:               Default
Assign default route 
to this gateway:       checked
DNS:                   Automatic

Modems
======
Modem name:             ATT
Modem device:		/dev/ttyUSB0
Flow control:           Hardware
Line termination:       CR
Connection speed:       921600
Use lock file:          checked


4) Insert Compass 597 USB modem and wait for kernel to see it.

user@Toshiba:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 1199:0023 Sierra Wireless, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

user@Toshiba:~$ dmesg | grep -i ttyusb
usb 2-1: Sierra USB modem (3 port) converter now attached to ttyUSB0
usb 2-1: Sierra USB modem (3 port) converter now attached to ttyUSB1
usb 2-1: Sierra USB modem (3 port) converter now attached to ttyUSB2

5) Then, enter the following commands:

user@Toshiba:~$ sudo modprobe -r usbserial

user@Toshiba:~$ sudo modprobe usbserial vendor=0x1199 product=0x0023

6) Launch “KPPP” from “Applications” -> “Internet” and try to Connect.  If works, should see something like this:

Looking for modem
Modem ready
Initializing modem
Dialing #777
Logging on to network...

GUI minimizes as connection completes.  You are (hopefully) connected via ppp0.  

Enter “ifconfig” command and verify that you've got an IP address on ppp0.

---

### Post by zippy51 on 2008-08-22
HOWEVER . . . I should add that my Download/Upload speeds are slow using "usbserial".  Many other posters in these forums appear to be talking about using the "airprime" driver, which I am now looking into.

Just wanted you to know that, yes, the Compass 597 can be made to work under Linux.  Just don't expect any help from Sprint.

---

### Post by Clean Escape on 2008-08-23
zippy51, your instructions got my new Compass 597 working on my Asus Eee running Ubuntu 8.04. Other instructions were talking about recompiling the kernel, but all I did was follow your steps and voila - working interwebs! You're the best. Thank you.

The only unexpected thing I ran into was this:

~$ sudo modprobe -r usbserial
FATAL: Module usbserial is in use.

Not knowing what that meant, I continued with the rest of the instructions without further difficulty, and everything's up and running. Any insight what that error means? I'm a total novice here, so I'm not sure what modprobe -r usbserial line even does...

---

### Post by jfollmann on 2008-08-25
zippy51's method worked perfectly for me, as far as straight internet connectivity goes.

However, the GNOME Network Manager applet has my VPN's greyed out in the menu. At first I assumed because this method uses a KDE utility, somehow the GNOME network manager was not aware I have an active internet connection, and that was why I couldn't initiate a VPN.

So, I tried KVPNc, thinking somehow using a KDE app for VPN might help. KVPNc claims to connect to my VPN successfully, however I can't ping anything on that LAN except for the PPTP server - I'm not sure why this is yet.

Then I tried setting up a PPP connection under the GNOME Network Manager, but it would not allow me to enable the conection - every time I'd check the box to enable it, the box would uncheck itself a few seconds later. This is probably just as well, as a lot of the settings used in zippy51's method didn't exist there, so that's probably not the right place to be looking.

Then I used the utility "Gnome PPP" instead. It doesn't allow me to set the modem speed quite as high as KPPP but that doesn't seem to make much difference, and other than that everything worked just as well. That one also got me internet connectivity, but the GNOME Network Manager still does not allow me to initiate a VPN. I guess just being GNOME-native isn't good enough.

So my question is, does anyone know how to get the GNOME Network Manager to allow me to initiate a VPN connection with either PPP utility active, (doesn't make any difference to me which one I use)? Or how to get the Network Manager itself to initiate the PPP connection?

Alternatively, does anyone know why I can't get through the VPN when using KVPNc? I have no problem with using KPPP and KVPNc, if it will work.

Fyi, I use two different VPN connections to test with, both are Microsoft PPTP, and for all practical purposes are identical, the only difference being that the two networks have different IP subnets. I am able to use both of these VPNs through the Network Manager, when using a standard ethernet or wifi connection.

---

### Post by zippy51 on 2008-08-26
> **Clean Escape said:**
> The only unexpected thing I ran into was this:

~$ sudo modprobe -r usbserial
FATAL: Module usbserial is in use.

Not knowing what that meant, I continued with the rest of the instructions without further difficulty, and everything's up and running. Any insight what that error means? I'm a total novice here, so I'm not sure what modprobe -r usbserial line even does...

First, try entering "man modprobe" at the Ubuntu command prompt and read-up on the command. 

USBSerial is a Linux kernel driver module that facilitates a serial communication link via USB.  The "-r" command line switch tells modprobe to "remove" the usbserial driver from the kernel (in preparation for re-installing it with the unique Vendor ID and Product ID for the Compass 597).  But since your Compass 597 was already plugged-in the driver was in use (somehow).  Try booting-up without the Compass 597.  It should (hopefully) then let you enter "modprobe -r usbserial".  It won't hurt anything.  Then you can re-install with the Vendor/Product ID.

---

### Post by amp711 on 2008-09-19
zippy, thanks for doing the grunt work on this.  I got the usbserial in use message as well, but my 597 works like a champ!  \\:D/:-D

---

### Post by saro on 2008-09-19
What is the download speed you are getting using usbserial driver ?

---

### Post by amp711 on 2008-09-20
Per cnet's speed test, it comes back at 300.9 kbps.

Not great, but not bad for my needs.  Mostly I need this for google and OWA for work..

---

### Post by nootrak4 on 2008-09-23
KPPP For some reason this application keep on frezzing up on me. I have tried to re-install about 5 times. when i got to the internet under application KPPP shows up with the default icon. In the Windows world which is where i came from this means something is wrong or it didnt install correctly. any ideas?

---

### Post by Red-Shield on 2008-10-06
kppp can not find:
/dev/usb/ttyUSB0
Please make sure you have setup your modem device properly and/or adjust the location of the modem device on the modem tab of the setup dialog.

not sure what to make of this error message i followed instructions to the T i am not using 8.04 i love 7.10 so for what it's worth that could be the problem but i cant see it being just that any one out there able to help i need it for work or can some one suggest something similar that works great in ubuntu my boss will force me to use windows otherwise and i dont want my pecker to fall off....???????

sick-****@linuxuser:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1199:0fff Sierra Wireless, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

it is the compass 597 by sierra wireless as you can see.

---

### Post by amp711 on 2008-10-07
> **Red-Shield said:**
> kppp can not find:
/dev/usb/ttyUSB0
Please make sure you have setup your modem device properly and/or adjust the location of the modem device on the modem tab of the setup dialog.

not sure what to make of this error message i followed instructions to the T i am not using 8.04 i love 7.10 so for what it's worth that could be the problem but i cant see it being just that any one out there able to help i need it for work or can some one suggest something similar that works great in ubuntu my boss will force me to use windows otherwise and i dont want my pecker to fall off....???????

sick-****@linuxuser:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1199:0fff Sierra Wireless, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

it is the compass 597 by sierra wireless as you can see.

Your device ID is coming in at 0fff.  Mine is 0023 as well as the previous folks posting.  Could that be the problem?  

I have googled changing the device ID and have found a couple of posts (mostly here) that are saying that it is difficult to change it and there are no resolutions.  As a last ditch effort, have you thought about Hardy?

---

### Post by Red-Shield on 2008-10-07
thought about hardy but have no need or desire to switch other then this problem and i am not sure that switching will fix the problem i was hoping that an ubuntu expert could tell me how the two versions differ in this situation i did the setup just as it said if the version switch is the only thing stopping me then i would rather switch then use windows. but there must be a person out there that can help with this problem ????????

---

### Post by Red-Shield on 2008-10-13
there only seems to be one problem with this whole setup and my lap top i cant seem to tel any of the 3 ppp programs where the usb modem is located when it is plugged in i am building a new laptop any way this one is on it's last few boot's it is 6 years old and has more ram then suggested and it's hurting when the new lap top is done i will switch to hardy heron...

---

### Post by Red-Shield on 2008-10-24
ok well i have finished building my new lap top it runs mac os and ubuntu ultimate 1.9 with 500 gb sata drive and the sierra device seems to be working great it is fast i still wish there was someone out there who could tell me why it failed using 7.10 i have never used any thing but ubuntu ultimate it is awsome look for it on the net....

---

### Post by mikeysweet on 2008-12-04
I just got the Dell Mini 9 and it's running Ubuntu 8.04 Hardy Heron and GNOME 2.22.2.

When I searched and found the KPPP application, It said I can't install it:

"KPPP cannot be installed on your computer type (lpia). Either the application requires special hardware features of the vendor decided to not support your computer type"

I'm not sure what lpia is.
Is there a way to work around this so I can get my Compass 597 working? Would installing this package help, and if so which one:
[https://launchpad.net/ubuntu/hardy/lpia/kppp](https://launchpad.net/ubuntu/hardy/lpia/kppp)


Thanks for your help. I'm a newbie to all this so please excuse my ignorance while I try to ramp up my knowledge.
-Mike

---

### Post by mikeysweet on 2008-12-04
Ok so I was able to figure this out on my Mini 9
I needed to use GNOME PPP to connect and I didn't have to run any commands to get it to work.
1 - plugged in the Compass 597
2 - waited a few seconds and opened GNOME PPP
3 - clicked on Setup and clicked "Detect" for the Device
4 - Changed the Type to USB Modem
5 - Typed in 921600 into the speed
6 - Under the Options part uncheck everything except for "Dock in notification area"
7 - Click Close
8 - Type in user for Username, user for Password, and #777 for Phone Number
9 - Click Connect
10 - Click on Log to watch the progress. You should see the IP address assigned near the end of the log file.
11 - Enjoy the internet!

---

### Post by urug on 2009-01-23
Just playing around with the Compass 597 (TELUS) on Ubuntu 8.10 on an old IBM laptop. Plugged the Compass in and tried messing around with Gnome PPP without a ton of success. Gave up, uninstalled Gnome PPP and used the built-in Network Manager. Everything worked perfect. The only configuration I needed was to make the phone number #777.

Speeds from within a thick-walled college campus building ranged from 30KBps up to 250 KBps.

Running some more tests on it with some different drivers tomorrow. I'll post some results.

---

### Post by felixayalajr on 2009-04-09
> **mikeysweet said:**
> Ok so I was able to figure this out on my Mini 9
I needed to use GNOME PPP to connect and I didn't have to run any commands to get it to work.
1 - plugged in the Compass 597
2 - waited a few seconds and opened GNOME PPP
3 - clicked on Setup and clicked "Detect" for the Device
4 - Changed the Type to USB Modem
5 - Typed in 921600 into the speed
6 - Under the Options part uncheck everything except for "Dock in notification area"
7 - Click Close
8 - Type in user for Username, user for Password, and #777 for Phone Number
9 - Click Connect
10 - Click on Log to watch the progress. You should see the IP address assigned near the end of the log file.
11 - Enjoy the internet!


Hi, am new to this site and to Ubuntu. I followed your instructions to the letter and this is what I get:
..Ignoring malformed input line:";Do NOT edit this file by hand!"
..WvDial: internet dialer version 1.60
..Cannot get information for serial port.
..initializing modem.
..Sending: ATZ
ATZ
ok
..Modem initialized
..please enter password (or empty password to stop):

                                           Connecting..

                                           Sending password

                                           Log    X cancel


And nothing. Help please

---

### Post by canek1 on 2009-04-10
I activated my 597 in Windows, cus the Telus guy told me it didn't work in Linux, but when I later tried it in Ubuntu 8.10, found that - unlike in Vista - it worked right out of the box, no extra configuration necessary. I haven't compared my speeds between the two OS, but it's fast enough in Ubuntu to use Skype, so I'm happy.

---

### Post by marsrover on 2009-04-26
> **canek1 said:**
> I activated my 597 in Windows, cus the Telus guy told me it didn't work in Linux, but when I later tried it in Ubuntu 8.10, found that - unlike in Vista - it worked right out of the box, no extra configuration necessary. I haven't compared my speeds between the two OS, but it's fast enough in Ubuntu to use Skype, so I'm happy.


so u just plug it in and click connect

is the tower you connect to cdma rev a or 1xrttt

if it's 1xrttt then CRAP

if it's cdma rev a then GOOD BY WINDOWS:lolflag:

---

