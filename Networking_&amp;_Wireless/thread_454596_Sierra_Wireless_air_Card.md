---
title: "Sierra Wireless air Card"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by gonzoman3000 on 2007-05-25
Hello, I am new to this forum and new to migrating from Windows. I recently went with Sprint for wireless connectivity. I use a Sierra Wireless 595 usb air card and cannot find any support for it for Ubuntu. Will it be possible to use this air card with Ubuntu? Thanks in advance for whoever may help.

---

### Post by Super Carp on 2007-06-14
I have the same card and was wondering if anyone has got it to work.  Ubuntu recognizes it as a USB device but not a network device...

EDIT: This should provide some help.  I'll try it out tonight after work and let you all know how it goes: [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601)

---

### Post by Super Carp on 2007-06-14
Ok dudes, I'm stuck and can't figure out what to do.

I followed these instructions:

-------------
To install the driver the kernel source code will need to be downloaded and located at /usr/src/linux. Depending on the distribution it varies quite a lot, typically the distro package manager (e.g.  yum, yast, and apt) can do this (try searching in them for ‘kernel source’).
1.       Move to the driver package directory and extract the source.
# cd <directory of source>
# tar –zxf sierra.v.X.Y.Z.zip
# cd sierra.v.X.Y.Z
2.       If an older version of the sierra driver is installed, unload it.
# rmmod sierra
3.       Become root and browse to the directory where ‘Makefile’ and ‘sierra.c’ are located.
# su
# cd /<directory>
4.       Compile and install the driver
# make
# make install

That’s it; the driver should now be installed.
-----------------------

I can get to step 3.  When I try step 4, it just says "bash: make: command not found"

What do I need to do?

Thanks for the help

-Carp

---

### Post by Super Carp on 2007-06-15
bump, any help would be appreciated

---

### Post by WIVO_Riley on 2007-07-06
> **Super Carp said:**
> bump, any help would be appreciated

I have the same card- any help would greatly be appreciated!!

---

### Post by WIVO_Riley on 2007-07-06
EUREKA!!! I got it!!  I'm currently connected with my 595 sierra card (sprint).

I used the instructions from this url:

[http://www.pbandjelly.org/2006/12/sierra-wireless-aircard-595-configuration-sprintpcs/](http://www.pbandjelly.org/2006/12/sierra-wireless-aircard-595-configuration-sprintpcs/)


BUT, at least for a newb like me, it was difficult to figure out, but the instructions are correct- you just have to take your time and read it VERY VERY VERY carefully.  There are a couple of things in there that I overlooked and had to do over- it would have helped to make some of it bold to delineate some things- and it assumes you know some of the correct commands to change directories and create files in them using the terminal (I didn't, but DO KNOW :)! )

I'm kind of in a rush today, but if some still continue to have problems, when I get a chance, I'll switch over to my windoze os (where I'm alot more adept yet) and build a page with some screen shots to simplify it.

It does work though- when I got a connection, I about fell off my chair!! 

Good luck!!

---

### Post by hooltool on 2007-08-21
Well heres what we did to get it to work using Linux Mint (ubuntu 7.04).  Installed Gnome-ppp thru synaptic.   Run Gnome-PPP and go to setup.   Under the Modem tab we did autodetect.  It came up as ttyUSB0.  Unchecked wait for dialtone.   Close setup.  You need your username and password from verizon.  Mine was my name(username)  and the cell phone number assigned to the card by verizon (password).   The phone number was #777.  It worked this way.  If ubuntu recognizes the card like my computer did it should be easy. I'll try to answer any questions I can.

---

### Post by Jalke on 2007-08-29
I seem to almost have it going.  I downloaded the driver supplied on the sierra website and added my password and username to the /etc/ppp/options and /etc/ppp/pap-secrets files.  The device is making a connection and communicating - I got past the authentication step.  However that's where the modem and I seem to get stuck.  Any tips??

Here's the log:

[FONT="Courier New"]Starting Sierra Wireless CDMA connect script...



Setting the abort string



Initializing modem



Dialing...

Serial connection established.

using channel 16

Using interface ppp0

Connect: ppp0 <--> /dev/ttyUSB0

rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth pap> <magic 0x288af29e>]

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x5b233965> <pcomp> <accomp>]

sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth pap> <magic 0x288af29e>]

rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x5b233965> <pcomp> <accomp>]

sent [LCP EchoReq id=0x0 magic=0x5b233965]

sent [PAP AuthReq id=0x1 user="mobile@jamamobile" password=<hidden>]

rcvd [LCP EchoRep id=0x0 magic=0x288af29e]

rcvd [PAP AuthAck id=0x1 ""]

PAP authentication succeeded

sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]

sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]

rcvd [LCP ProtRej id=0xac 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]

Protocol-Reject for 'Compression Control Protocol' (0x80fd) received

rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]

sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]

rcvd [IPCP ConfReq id=0xf7 <addr 166.179.16.1>]

sent [IPCP ConfAck id=0xf7 <addr 166.179.16.1>]

rcvd [IPCP ConfNak id=0x2 <addr 166.179.28.76> <ms-dns1 202.27.158.40> <ms-dns3 202.27.156.72>]

sent [IPCP ConfReq id=0x3 <addr 166.179.28.76> <ms-dns1 202.27.158.40> <ms-dns3 202.27.156.72>]

rcvd [IPCP ConfAck id=0x3 <addr 166.179.28.76> <ms-dns1 202.27.158.40> <ms-dns3 202.27.156.72>]

Cannot determine ethernet address for proxy ARP

local  IP address 166.179.28.76

remote IP address 166.179.16.1

primary   DNS address 202.27.158.40

secondary DNS address 202.27.156.72

Script /etc/ppp/ip-up started (pid 8978)

Script /etc/ppp/ip-up finished (pid 8978), status = 0x0

sent [LCP EchoReq id=0x1 magic=0x5b233965]

rcvd [LCP EchoRep id=0x1 magic=0x288af29e]

sent [LCP EchoReq id=0x2 magic=0x5b233965]

rcvd [LCP EchoRep id=0x2 magic=0x288af29e]

sent [LCP EchoReq id=0x3 magic=0x5b233965]

rcvd [LCP EchoRep id=0x3 magic=0x288af29e][/FONT]


This just continues without me being able do anything with internet.  I'm not sure what the log output all means.  Am I connected? If anyone can translate and give some advice, that'd be great!

---

### Post by hooltool on 2007-08-29
Treat the card as if it were a dial up modem (PPOE).  It will work without any problems. I will try to answer any individual questions, it's a shame verzion and sprint chose to ignore linux users.



Hooltwl

---

### Post by hooltool on 2007-08-29
Just follow my direction (hooltwl) I posted right above you. You are way to involved, it's really very simple.

Don't forget to use your username, its the name on verizon wireless, usually your first and last name without a space in between. The password is the cell phone number assigned by verizon to the card. If you don't know your number, just call verizon and ask them or check your statement online at verizon wireless.

Jim (hooltwl)

---

### Post by hooltool on 2007-08-29
This is my connection log , once it connected it works great, probably faster than windows.

-> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX3
ATX3
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT#777
--> Waiting for carrier.
ATM1L3DT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Wed Aug 20 09:42:07 2007
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 8478
--> Using interface ppp0
--> local  IP address 90.208.169.92
--> remote IP address 66.174.12.5
--> primary   DNS address 66.174.95.44
--> secondary DNS address 69.78.96.14

Good luck, I changed my IP address for security purposes. I am running on linux mint 3.0 (ubuntu kernel), the driver for the card is already installed on this distro. Try Linux Mint 3.0, It's an excellent version of Ubuntu.

---

### Post by tOoLb0x on 2007-09-05
> **hooltool said:**
> Well heres what we did to get it to work using Linux Mint (ubuntu 7.04).  Installed Gnome-ppp thru synaptic.   Run Gnome-PPP and go to setup.   Under the Modem tab we did autodetect.  It came up as ttyUSB0.  Unchecked wait for dialtone.   Close setup.  You need your username and password from verizon.  Mine was my name(username)  and the cell phone number assigned to the card by verizon (password).   The phone number was #777.  It worked this way.  If ubuntu recognizes the card like my computer did it should be easy. I'll try to answer any questions I can.

Excellent suggestion hooltool!  gnome-ppp works great.   I do have a couple of things to add as an FYI.
   
-The username field can be any string without a space (ie. bob,  vzw, etc.).  

-The password field is the aircard phone number without any special characters. Just ten digits (ie.  3215551212)

-If you experience a disconnect after 2 minutes and/or receive the following error there's a simple workaround:

[INDENT]GNOME PPP: STDERR: --> Disconnecting at Tue Sep  4 21:57:40 2007
GNOME PPP: STDERR: --> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
GNOME PPP: STDERR: --> man pppd explains pppd error codes in more detail.
GNOME PPP: STDERR: --> I guess that's it for now, exiting
GNOME PPP: STDERR: --> Provider is overloaded(often the case) or line problem.
GNOME PPP: STDERR: --> The PPP daemon has died. (exit code = 15)

Edit /etc/ppp/options with your favorite (or not so favorite) editor.  Find and comment out the following line:  

before:
lcp-echo-failure 4

after:
#lcp-echo-failure 4

As far as I understand this will disable LCP request/replies which can be very helpful in fringe coverage areas.[/INDENT]

-Running  `sudo gnome-ppp` will create the appropriate files in /etc/ppp.  Without sudo it may error out since /etc/ppp can only be written to by root by default.  

[INDENT][FONT="Courier New"] 
$ ls -ld /etc/ppp
drwxr-xr-x 8 root dip 4096 2007-09-04 21:59 /etc/ppp[/FONT]
[/INDENT]

-For effect I like using  the "dock in notification area" option. It can be found at gnome-ppp -> Setup -> Options -> Dock in notification area

Hope this helps.

---

### Post by mimsmall on 2007-10-20
hooltool, Other posts on this forum say that the Seirra Aircard 875 must first be activated on a Windows machine. Would this action be needed using Linux Mint or can I just plug it in  and expect it to work properly after following your previously posted instructions?

---

### Post by akshunj on 2007-10-23
> **mimsmall said:**
> hooltool, Other posts on this forum say that the Seirra Aircard 875 must first be activated on a Windows machine. Would this action be needed using Linux Mint or can I just plug it in  and expect it to work properly after following your previously posted instructions?

This is true.  It must first be activated on a Windows machine.  Period.  There's an activation scheme which requires an activation code.  Once this is complete, your provider will recognize the connection as active.  This must be done from within the Windows program.  Sucks, but that's life.

A few hours later, I popped it into my Mint laptop, and used Gnome-PPP.  I was connected after 10 minutes of fiddling.  Just remember to run Gnome-PPP as sudo.  The username field is rather obscure, and it was necessary that I get the info from the Windows connection program.  For Sprint, it's called the ActiveVision username.  FYI...

But MAN, it sucks some battery juice!

--Akshun J

---

### Post by Eriks_Knor on 2007-11-04
> **WIVO_Riley said:**
> EUREKA!!! I got it!!  I'm currently connected with my 595 sierra card (sprint).

I used the instructions from this url:

[http://www.pbandjelly.org/2006/12/sierra-wireless-aircard-595-configuration-sprintpcs/](http://www.pbandjelly.org/2006/12/sierra-wireless-aircard-595-configuration-sprintpcs/)


BUT, at least for a newb like me, it was difficult to figure out, but the instructions are correct- you just have to take your time and read it VERY VERY VERY carefully.  There are a couple of things in there that I overlooked and had to do over- it would have helped to make some of it bold to delineate some things- and it assumes you know some of the correct commands to change directories and create files in them using the terminal (I didn't, but DO KNOW :)! )

I'm kind of in a rush today, but if some still continue to have problems, when I get a chance, I'll switch over to my windoze os (where I'm alot more adept yet) and build a page with some screen shots to simplify it.

It does work though- when I got a connection, I about fell off my chair!! 

Good luck!!


Two questions:

1) Does anybody know if this works for someone running Gutsy (7.10)?

2) I have ndiswrapper 1.46 on my Dell Inspirion E1505 to run the built-in Broadcom wireless card. Does this cause a problem at all with running the Sierra 595?

Thanks!

---

### Post by exwannabe on 2007-11-06
My 881 worked just fine following the instructions at 

[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=608](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=608)

The only glitch I saw was that they used a directory name with a space in it for the zip extraction. This space blows up the make script, so rename the directory per Unix std  dir names.

After compiling, I just did a manual modprobe sierra to get the driver up (I'm certain this can be avoided with proper udev/hotplug scripting).

To get a connection up, I followed the instructions in the link exactly (along with the APN/use/pwd from ATT (ex Cingular, ex ATT).

Am posting via the card now, less than 1 hour after starting downloading the driver.

BTW, I did make a false start and try to use the sierra.c from the Debian source, but this is old and wouldn't handle my card. My runnign version is v1.2.5c. Possibly your older card works out-of-the-box (along with pppd/kppp config).

---

### Post by davidstillson on 2007-12-13
> **hooltool said:**
> Well heres what we did to get it to work using Linux Mint (ubuntu 7.04).  Installed Gnome-ppp thru synaptic.   Run Gnome-PPP and go to setup.   Under the Modem tab we did autodetect.  It came up as ttyUSB0.  Unchecked wait for dialtone.   Close setup.  You need your username and password from verizon.  Mine was my name(username)  and the cell phone number assigned to the card by verizon (password).   The phone number was #777.  It worked this way.  If ubuntu recognizes the card like my computer did it should be easy. I'll try to answer any questions I can.

This worked flawlessly.  FYI, my username was actually the phone#, and the password was my verizon supplied password.

---

### Post by A. J. Rimmer on 2008-01-29
> **hooltool said:**
> Just follow my direction (hooltwl) I posted right above you. You are way to involved, it's really very simple.

Don't forget to use your username, its the name on verizon wireless, usually your first and last name without a space in between. The password is the cell phone number assigned by verizon to the card. If you don't know your number, just call verizon and ask them or check your statement online at verizon wireless.

Jim (hooltwl)

Thanks to hooltool for this information!  I just got a Verizon UM150 USB EVDO modem.  (Finally decided it was worth the cost to get away from dial-up.  We are in an area where neither DSL nor cable is available.)

Anyway, after setting up the modem in Windows, I rebooted to Ubuntu Feisty and used pppconfig to set up a dial-up connection.  The first try failed with the report that ttyUSB0 was not found.  I unplugged the modem,  opened /dev in Nautilus, switched to list view, sorted by date, and plugged in the modem.  Immediately, /dev/ttyACM0 popped up on the list.  Went back to pppconfig and changed the modem to /dev/ttyACM0, and tried dialing.

I was immediately connected to the Verizon EVDO network!

Thanks again -- great tip!

---

### Post by ZZbbssmm on 2008-02-17
Per exwannabe's post #16

First of all I must note that I am a Linux newby and think Ubuntu is what we all have been waiting for. 

I too followed the instructions offered by Sierra at [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=608](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=608) and once I figured out the root password issue attempted to extract the source by typing the following commands:

      # cd

      # tar &#8211;zxf sierra.v.X.Y.Z.zip

and I see the following repeatedly:

root@zzzzbbssmm:~# tar -zxf sierra.v.X.Y.Z.zip
tar: sierra.v.X.Y.Z.zip: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Per exwannabe's post they used a directory name with a space in it for the zip extraction. This space blows up the make script, so rename the directory per Unix std dir names.

At the risk of sounding ignorant I attempted the same command without the space and came up with nearly the identical error:

root@zzzzbbssmm:~# tar -zxfsierra.v.X.Y.Z.zip
tar: sierra.v.X.Y.Z.zip: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

The v.1.2.7(kernel2.6.21).zip is sitting in the Home Folder.

I can only assume that during the decompression process one or the other of the 2 files involved somehow creates a directory and this is where the error is? Using gedit I have gone over both the "Makefile" and the "sierra.c" files and can't see any such line that would involve making a directory. I feel I'm close but am at a standstill now.

HELP!

---

### Post by qewl on 2008-02-18
I too have a UM150 and am frustrated to no end trying to get it to work! I called Verizon tech support (why, I don't know), and (as expected), they told me to not use Linux; they have no plans of ever supporting it. I have used gnome-ppp and I keep getting the same error log everytime I try. Any help would be much appreciated!


(gnome-ppp:24212): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: WvDial<*1>: Connect time 0.2 minutes.
GNOME PPP: STDERR: WvDial<*1>: pppd: H&#65533;&#65533;&#65533;&#65533;&#65533;[06][08][10]&#65533;[06][08]

(gnome-ppp:24212): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: WvDial<*1>: pppd: H&#65533;&#65533;&#65533;&#65533;&#65533;[06][08][10]&#65533;[06][08]

(gnome-ppp:24212): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: WvDial<*1>: pppd: H&#65533;&#65533;&#65533;&#65533;&#65533;[06][08][10]&#65533;[06][08]

---

### Post by MikeyXX on 2008-03-26
> **ZZbbssmm said:**
> Per exwannabe's post #16

First of all I must note that I am a Linux newby and think Ubuntu is what we all have been waiting for. 

I too followed the instructions offered by Sierra at [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=608](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=608) and once I figured out the root password issue attempted to extract the source by typing the following commands:

      # cd

      # tar –zxf sierra.v.X.Y.Z.zip

and I see the following repeatedly:

root@zzzzbbssmm:~# tar -zxf sierra.v.X.Y.Z.zip
tar: sierra.v.X.Y.Z.zip: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Per exwannabe's post they used a directory name with a space in it for the zip extraction. This space blows up the make script, so rename the directory per Unix std dir names.

At the risk of sounding ignorant I attempted the same command without the space and came up with nearly the identical error:

root@zzzzbbssmm:~# tar -zxfsierra.v.X.Y.Z.zip
tar: sierra.v.X.Y.Z.zip: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

The v.1.2.7(kernel2.6.21).zip is sitting in the Home Folder.

I can only assume that during the decompression process one or the other of the 2 files involved somehow creates a directory and this is where the error is? Using gedit I have gone over both the "Makefile" and the "sierra.c" files and can't see any such line that would involve making a directory. I feel I'm close but am at a standstill now.

HELP!

You are taking the X.Y.Z.zip at face value. They are variables and saying to use the driver that you downloaded, whatever that may be. I renamed that v1.2.7.... to sierra.zip and then did tar -zxf sierra.zip

---

### Post by MikeyXX on 2008-03-26
I've got this problem.... It sees my 595 card. When I do dmesg I get this:

> [ 1085.524000] ohci_hcd 0000:04:00.1: irq 17, io mem 0x6c001000
[ 1085.592000] usb usb7: configuration #1 chosen from 1 choice
[ 1085.592000] hub 7-0:1.0: USB hub found
[ 1085.592000] hub 7-0:1.0: 1 port detected
[ 1087.004000] usb 6-1: new full speed USB device using ohci_hcd and address 2
[ 1087.216000] usb 6-1: configuration #1 chosen from 1 choice
[ 1087.216000] sierra 6-1:1.0: Sierra USB modem converter detected
[ 1087.220000] usb 6-1: Sierra USB modem converter now attached to ttyUSB0
[ 1087.220000] usb 6-1: Sierra USB modem converter now attached to ttyUSB1
[ 1087.220000] usb 6-1: Sierra USB modem converter now attached to ttyUSB2
][/QUOTE

And when I run "sudo wvdialconf" I get this:
[QUOTE]michael@michael-laptop:~$ sudo wvdialconf
[sudo] password for michael:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: Sierra Wireless, Inc.
ttyUSB0<*1>: Speed 4800: AT -- OK
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Speed 19200: AT -- OK
ttyUSB0<*1>: Speed 38400: AT -- OK
ttyUSB0<*1>: Speed 57600: AT -- OK
ttyUSB0<*1>: Speed 115200: AT -- OK
ttyUSB0<*1>: Speed 230400: AT -- OK
ttyUSB0<*1>: Speed 460800: AT -- OK
ttyUSB0<*1>: Max speed is 460800; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"


So far, so good. In wvdial.conf it shows this:

> [Dialer pulse]
Dial Command = ATDP

[Dialer shh]
Init3 = ATM0

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Password = 12345678910
Phone = #777
Modem Type = Analog Modem
Stupid Mode = on
Baud = 460800
Modem = /dev/ttyUSB0
Init = ATZ
ISDN = 0
Username = [email]905xxxxxxx@1x.telusmobility.com[/email]
Carrier Check = no
Auto Reconnect = on]

Ok, so now, when I run "sudo wvdial" I get this:> michael@michael-laptop:/etc$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT#777
WvDial Modem<*1>: NO CARRIER
WvDial<Warn>: No Carrier!  Trying again.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT#777
WvDial Modem<*1>: NO CARRIER
WvDial<Warn>: No Carrier!  Trying again.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.


Any suggestions? I have already activated it with Windows and it is FAST in windows.

---

### Post by MikeyXX on 2008-03-28
I found why it won't work in my Ubuntu. Turns out that I had inadvertently turned of the power through the software when it was loaded in Windows. I had to reload it into Windows to turn it back on.

---

### Post by Mach1US on 2008-06-23
Another thread if this still wont work
[http://ubuntuforums.org/showpost.php?p=2048477&postcount=1](http://ubuntuforums.org/showpost.php?p=2048477&postcount=1)

---

### Post by Jaxl on 2008-06-24
Hello i run 8.04 gnome buntu and i got a verizon wireless usb modem. all you need is one program GPPP find infos here for this exact moduel:

Verizon Wireless 1xEVDO USB720 Provider= Novatel Wireless running with UbuntU Gnomer 8.04 Linux OS:

Klick Heir : [http://ubuntuforums.org/showthread.php?t=838891](http://ubuntuforums.org/showthread.php?t=838891)

---

