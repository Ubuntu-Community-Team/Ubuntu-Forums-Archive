---
title: "How to connect using usb modem?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by kshtjsnghl on 2009-01-30
Hi everyone.
  i recently purchased the idea netsetter usb modem (a popular usb modem connection in india). But seemingly i cannot make out how do i configure to use it on my kubuntu system. In windows, it connects directly but i could not find a way out for ubuntu.
  So, if anyone has any idea please help me.

---

### Post by kshtjsnghl on 2009-01-31
hey can anyone plese help me out here.

---

### Post by kshtjsnghl on 2009-01-31
hey can anyone plese help me out here.

---

### Post by beyboo on 2009-01-31
> **kshtjsnghl said:**
> hey can anyone plese help me out here.


In India the Tata Indicom Plug2Surf definately does not work out of the box and you have to use the wvdial command to configure and use it. Something similar should work for your idea modem. 

It always helps others to help you when you provide some more information, like what distro are you using, what is the kernel in use, and ofcourse when you plugin the modem, output of the messages file.

Please do the following :

1) Output of uname -a command
2) compress and attach your /var/log/messages file after you plugin the modem.

---

### Post by kshtjsnghl on 2009-01-31
kshitij@kshitij-laptop:~$ uname -a
Linux kshitij-laptop 2.6.27-11-generic #1 SMP Thu Jan 22 17:22:40 UTC 2009 i686 GNU/Linux

cat /var/log/messages
Jan 31 12:43:36 kshitij-laptop kernel: [46886.800167] usb 2-2: USB disconnect, address 6
Jan 31 12:43:37 kshitij-laptop kernel: [46888.040161] usb 2-1: USB disconnect, address 7
Jan 31 12:43:47 kshitij-laptop kernel: [46897.896116] usb 2-2: new full speed USB device using uhci_hcd and address 8
Jan 31 12:43:47 kshitij-laptop kernel: [46898.052812] usb 2-2: configuration #1 chosen from 1 choice
Jan 31 12:43:47 kshitij-laptop kernel: [46898.056481] scsi11 : SCSI emulation for USB Mass Storage devices
Jan 31 12:43:47 kshitij-laptop kernel: [46898.208134] usb 2-2: USB disconnect, address 8
Jan 31 12:43:48 kshitij-laptop kernel: [46898.948178] usb 2-2: new full speed USB device using uhci_hcd and address 9
Jan 31 12:43:48 kshitij-laptop kernel: [46899.114769] usb 2-2: configuration #1 chosen from 1 choice
Jan 31 12:43:48 kshitij-laptop kernel: [46899.125772] usb-storage: probe of 2-2:1.0 failed with error -5
Jan 31 12:43:48 kshitij-laptop kernel: [46899.157041] usb-storage: probe of 2-2:1.1 failed with error -5
Jan 31 12:43:48 kshitij-laptop kernel: [46899.176712] usb-storage: probe of 2-2:1.2 failed with error -5
Jan 31 12:43:48 kshitij-laptop kernel: [46899.220056] scsi15 : SCSI emulation for USB Mass Storage devices
Jan 31 12:43:48 kshitij-laptop kernel: [46899.266897] usbcore: registered new interface driver usbserial
Jan 31 12:43:48 kshitij-laptop kernel: [46899.267191] usbserial: USB Serial support registered for generic
Jan 31 12:43:48 kshitij-laptop kernel: [46899.267458] usbcore: registered new interface driver usbserial_generic
Jan 31 12:43:48 kshitij-laptop kernel: [46899.267463] usbserial: USB Serial Driver core
Jan 31 12:43:48 kshitij-laptop kernel: [46899.303873] usbserial: USB Serial support registered for GSM modem (1-port)
Jan 31 12:43:48 kshitij-laptop kernel: [46899.304599] option 2-2:1.0: GSM modem (1-port) converter detected
Jan 31 12:43:48 kshitij-laptop kernel: [46899.305451] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
Jan 31 12:43:48 kshitij-laptop kernel: [46899.306085] option 2-2:1.1: GSM modem (1-port) converter detected
Jan 31 12:43:48 kshitij-laptop kernel: [46899.306741] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
Jan 31 12:43:48 kshitij-laptop kernel: [46899.307375] option 2-2:1.2: GSM modem (1-port) converter detected
Jan 31 12:43:48 kshitij-laptop kernel: [46899.308028] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
Jan 31 12:43:48 kshitij-laptop kernel: [46899.308679] usbcore: registered new interface driver option
Jan 31 12:43:48 kshitij-laptop kernel: [46899.308685] option: USB Driver for GSM modems: v0.7.2
Jan 31 12:43:53 kshitij-laptop kernel: [46904.232581] scsi 15:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Jan 31 12:43:53 kshitij-laptop kernel: [46904.320610] sr1: scsi-1 drive
Jan 31 12:43:53 kshitij-laptop kernel: [46904.321797] sr 15:0:0:0: Attached scsi generic sg3 type 5

 cat /var/log/messages | grep HUAWEI
Jan 30 23:18:24 kshitij-laptop kernel: [11852.293421] scsi 11:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Jan 31 12:43:53 kshitij-laptop kernel: [46904.232581] scsi 15:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2

---

### Post by kshtjsnghl on 2009-01-31
sorry i dont know how to compress the messages
Hope this is helpful
it took long because i have to get the messages on my comp and then mail it through some others system.

---

### Post by beyboo on 2009-01-31
The modem is atleast initialized. However, I guess network manager is unable to recognize that its plugged in. I am gonna try and give you the configuration I use for my Tata Plug2Surf and we can fine tune it as we go along.

Unfortunately you will not be able to do this via GUI.

Go to a terminal window and make the following changes:

Edit the /etc/wvdial.conf file to reflect these lines

> [Dialer Defaults]

Modem=/dev/ttyUSB0
Baud=115200
Dial Command = ATDT
Baud=115200
Dial Command = ATDT
init1=ATZ
init2=AT+CRM=1
Flow Control= Hardware (CRTSCTS)
Username = internet (replace this with Idea given user name)
Password = internet (replace with Idea given password)
Phone = #777          (If this does not work will have to check)
Stupid Mode = 1




Try the above
then from a terminal use 
sudo wvdial and check the output. Also keep an eye on the system log from the System menu. Click on the messages. 

Let me know if this works. In your case there is all the way from USB0/USB1/USB2, plus we are not sure if your hardware model is the same as what Tata Plug2Surf is....

EDIT:
Kshitij, also try to find out what the model of the hardware is. Try opening up the sim card case and usually the model number is in fine print under the sim card on the case, once you remove it. In my case it says sxc-1080

---

### Post by beyboo on 2009-01-31
Also try this wvdial.conf


[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
+FCLASS=0
ISDN = 0
Modem Type = USB Modem
Phone = #777
Username = internet (replace with idea user name)
Password = internet (replace with idea password)
stupid mode = 1

---

### Post by beyboo on 2009-01-31
Hey Kshitij, Skip all the above. I think I found out what hardware you got. I checked with some people I know and you should have the HUAWEI EG162G Stick Modem. 

 Edit the etc/wvdial.conf and put the following lines in. The

> [Dialer Defaults]
Modem=/dev/ttyUSB0
Baud = 460800
Init 1 = AT+CGMM
Init 2 = AT+CMEE=1
Init 3 = ATE0
Init 4 = AT^HS=0,0
Init 5 = AT+CFUN?
Init 6 = AT+CLCK="SC",2
Init 7 = AT+CPIN?
Init 8 = AT+CLCK="SC",2
Modem Type = USB MODEM
Phone=*99#
Username = idea
Password = idea
Dial Command=ATDT
Stupid Mode=1
ISDN=0

Now try the wvdial command. This should definitely work for you. Let me know.

---

### Post by bigAane on 2009-05-10
Hey guys

I have the same problem on ubantu 9.04 JJ  but my problem is I'm unable to find the wvdial.conf which is talked about to edit. any help to find it or an alternative

plz do suggest.

Regards
Aane

---

### Post by ashmew2 on 2009-05-10
> **bigAane said:**
> Hey guys

I have the same problem on ubantu 9.04 JJ  but my problem is I'm unable to find the wvdial.conf which is talked about to edit. any help to find it or an alternative

plz do suggest.

Regards
Aane

Have you tried the command : 

```
sudo gedit /etc/wvdial.conf
```

?
It may sound silly , but its worth a try.. :)

---

### Post by bigAane on 2009-05-10
Yeah, I got to know that if file dos't exist it creats and I can put the above details and save.

but still I'm unable to browse though in panel it shows mobile broadband, ideal cellular connected :(

these are silly and basic things I guess but I'm not aware of, plz help me

---

### Post by dptxp on 2009-05-10
Try Kppp.
Install it if you do not have it.
It is gui and it works for me for Micromax USB modem in sidux.

---

### Post by bigAane on 2009-05-10
> **dptxp said:**
> Try Kppp.
Install it if you do not have it.
It is gui and it works for me for Micromax USB modem in sidux.
but I'm using gnome desktop :(

---

### Post by ashmew2 on 2009-05-10
you can install Kubuntu Applications on Ubuntu , they are supported on each other..Like you can run Kaffeine and Kopete on Gnome flawlessly...You may run into an issue here and there but its no biggie ;)

Btw , im not really comfortable with the issue myself but the least i could do was to get you guys this page : [http://www.google.co.in/search?q=Ubuntu+USB+modem+india&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.in/search?q=Ubuntu+USB+modem+india&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by gandaran on 2009-05-10
> **bigAane said:**
> Hey guys

I have the same problem on ubantu 9.04 JJ  but my problem is I'm unable to find the wvdial.conf which is talked about to edit. any help to find it or an alternative

plz do suggest.

Regards
Aane
wvdial no longer comes preinstalled in jaunty 9.04, go to synaptic and install it.

edit:
sorry didn't remember you have no internet connection to install the package!

---

### Post by GeorgeVita on 2009-05-10
Hi,

if you do not have access to the internet from this Ubuntu 9.04 PC, you can RESTORE the MISSING wvdial with the solution at post#8 of [http://ubuntuforums.org/showthread.php?t=1138101](http://ubuntuforums.org/showthread.php?t=1138101)

It is a little bit "hard" but it works!

Regards,
George

---

### Post by bmdavis on 2009-05-11
Thanks for the above posts.  I'm using the Huawei eg162G, and here's what I get after my wvdial.  It shows up in lmesg, but can't connect:

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

Not sure where to go from here...

---

### Post by GeorgeVita on 2009-05-11
Hi **bmdavis**, please post here:

- exact version of Ubuntu
- the output of the terminal command: **lsusb**
- the output of: **ls /dev/ttyU***
- /etc/wvdial.conf

and if possible: boot without modem, attach it, wait 15 seconds and try: **dmesg**
post here ONLY the last 10-15 lines regarding the modem, option/usbserial driver or ttyUSBx

Regards,
George

---

### Post by sundar_ima on 2009-05-13
> **bigAane said:**
> Yeah, I got to know that if file dos't exist it creats and I can put the above details and save.

but still I'm unable to browse though in panel it shows mobile broadband, ideal cellular connected :(

these are silly and basic things I guess but I'm not aware of, plz help me you should not have any problem once you are connected to internet. try this... go to file in firefox and **ensure work offline mode is unchecked**...

---

### Post by sundar_ima on 2009-05-13
> **bmdavis said:**
> Thanks for the above posts.  I'm using the Huawei eg162G, and here's what I get after my wvdial.  It shows up in lmesg, but can't connect:

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

Not sure where to go from here...
try your modem in all usb ports...

---

### Post by sundar_ima on 2009-05-13
> **bmdavis said:**
> Thanks for the above posts.  I'm using the Huawei eg162G, and here's what I get after my wvdial.  It shows up in lmesg, but can't connect:

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

Not sure where to go from here...

which version of ubuntu r u using?

---

### Post by bmdavis on 2009-05-14
hardy heron...

---

### Post by sundar_ima on 2009-05-14
> **bmdavis said:**
> hardy heron...

did you modeprobe usbserial and vendor id???

---

