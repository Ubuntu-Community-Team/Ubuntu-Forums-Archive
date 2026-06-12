---
title: "Reliance Broadband EC1262"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by gauravkumar on 2010-07-12
Hello All,

I am using Reliance Broadband Netconnect for access to the internet...
The modem is Huawei EC1262...
But using as i am using a dual boot system with Ubuntu 10.04 its not working...
Please suggest...its urgent...

Thanks and Advance

---

### Post by cariboo on 2010-07-12
I have marked this thread as unsolved, otherwise you won't get any answers to your question. If you came up with an answer yourself, please share it so that others may benefit from your experience.

---

### Post by gauravkumar on 2010-07-12
> **cariboo907 said:**
> I have marked this thread as unsolved, otherwise you won't get any answers to your question. If you came up with an answer yourself, please share it so that others may benefit from your experience.


Thanks for making me aware...
The solution to my issue was as follows:
Follow the below shown command listing

  	 	 	 	 	 	  [COLOR=#666666][FONT=Arial, serif][SIZE=2]Firstly we need to install these packages [/SIZE][/FONT][/COLOR][COLOR=#666666][FONT=Arial, serif][SIZE=2]*usb-modswitch, usb-modswitch-data*[/SIZE][/FONT][/COLOR]
 [COLOR=#666666][FONT=Arial, serif][SIZE=2]Open up Terminal,and type the following
[/SIZE][/FONT][/COLOR][COLOR=#666666][FONT=Courier New, serif][SIZE=2]$sudo apt-get install -yq usb-modeswitch usb-modeswitch-data[/SIZE][/FONT][/COLOR]
 [COLOR=#666666][FONT=Arial, serif][SIZE=2]Then we need to edit wvdial.conf file,type this in the Terminal[/SIZE][/FONT][/COLOR]
 [COLOR=#666666][FONT=Courier New, serif][SIZE=2]$sudo gedit /etc/wvdial.conf[/SIZE][/FONT][/COLOR]
 [COLOR=#666666][FONT=Arial, serif][SIZE=2]Type the following in the file opened,be sure to add your phone number[/SIZE][/FONT][/COLOR]
  [COLOR=#666666][FONT=Courier New, serif][SIZE=2][Modem0]
Modem = /dev/ttyUSB0
Baud = 115200
SetVolume = 0
Dial Command = ATDT
Init1 = ATZ
FlowControl = Hardware (CRTSCTS)
[Dialer netconnect]
Username = your device phone number
Password = password usually the device phone number
Phone = #777
Stupid Mode = 1
Inherits = Modem0[/SIZE][/FONT][/COLOR]
 [COLOR=#666666][FONT=Arial, serif][SIZE=2]close the editor and reboot the system.
All done,now to connect you need to type
[/SIZE][/FONT][/COLOR][COLOR=#666666][FONT=Courier New, serif][SIZE=2]$sudo wvdial netconnect[/SIZE][/FONT][/COLOR][COLOR=#666666][FONT=Arial, serif][SIZE=2]
to connect to the Internet and Ctrl+C to disconnect[/SIZE][/FONT][/COLOR]




[COLOR=#666666][FONT=Arial, serif][SIZE=2]Hope this helps
[/SIZE][/FONT][/COLOR]

---

### Post by ragsnp on 2010-07-23
Hi
Thanks for the input. But still the error comes as below. 
*Cannot open /dev/ttyUSB1: No such file or directory*

I have tried removing echi_hcd module from the kernel as recommended in another forum.
[http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/](http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/)

After restarting it worked. Thanks a ton.

---

### Post by gauravkumar on 2010-08-03
Please help somebody...
i have tried many things but still nothing works for the same issue.....
Only once it got connected as i mentioned in my earlier post...but after restarting its gone again...
When i go to System->Preferences->Network Connections and try to add the new Mobile connection, it does not even detect the device...
Even gnome-ppp and "wvdial netconnect" does not work.....Both are not able to detect the device....
Below is the Log to clarify things...

gaurav@gaurav-laptop:/$ lsusb
Bus 002 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 002 Device 003: ID 0bc2:2120 Seagate RSS LLC 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 005: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 004: ID 0c45:6417 Microdia 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
gaurav@gaurav-laptop:/$ sudo wvdial netconnect
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
gaurav@gaurav-laptop:/$ 
gaurav@gaurav-laptop:/$ gnome-ppp

(gnome-ppp:8001): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gnome-ppp:8001): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
WVCONF: /home/gaurav/.wvdial.conf
GNOME PPP: STDOUT: Editing `/dev/null'.
GNOME PPP: STDERR: Modem Port Scan<*1>: S0   S1   S2   S3   
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Scanning your serial ports for a modem.
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Sorry, no modem was detected!  Is it in use by another program?
GNOME PPP: STDOUT: Did you configure it properly with setserial?
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

---

