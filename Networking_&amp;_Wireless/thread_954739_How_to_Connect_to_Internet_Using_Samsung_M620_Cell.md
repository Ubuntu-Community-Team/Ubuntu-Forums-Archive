---
title: "How to Connect to Internet Using Samsung M620 Cell Phone"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by robrobinette on 2008-10-21
I successfully used my Samsung M620 UpStage cell phone to act as a usb modem by connecting it to my Eee PC 1000H running Ubuntu 8.10beta and using Ubuntu's built in wvdial. The M620 is a second generation EVDO phone that works great as a laptop modem. I used a usb cable but a Bluetooth connection should also work. Here's how I got online:

Start by editing the rc.local file:

sudo gedit /etc/rc.local
Add the following two lines above “exit 0” and below the comments. The vender and product codes are specific to the M620 phone:

/sbin/modprobe ipaq vendor=0x04e8 product=0x6640
touch /var/lock/LCK..ttyUSB2

Save and close. 

Now execute the rc.local file:
sudo /etc/rc.local start

I used Ubuntu's built in modem dialer wvdial. Create a configuration file for it called mydialer.conf and save it in your home directory. Notice the /dev/ttyUSB2, not the normal USB0:

[Dialer Defaults]
Stupid Mode = on
Idle Seconds = 0
Carrier Check = no
Init1 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = #777
Password = "Sprint password goes here"
Username = "rrobinet03@sprintpcs.com"
Modem = /dev/ttyUSB2
Baud = 460800

Next edit the ppp options file:
sudo gedit /etc/ppp/options
Comment out the following two lines:

lcp-echo-interval 30
lcp-echo-failure 4

Now plug the phone into a USB jack and run:

sudo wvdial --config ~/mydialer.conf

If you get a "Modem not responding" error simply unplug the phone, push the "Exit" key on the phone to wake it up, and plug it back in and run wvdial again.

Here's my wvdial dialog:

rob@Eee:~$ sudo wvdial --config ~/mydialer.conf
[sudo] password for rob: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port. [this is normal]
--> Initializing modem.
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
--> Sending: ATQ0
--> Re-Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
--> Modem not responding. [this is not normal:confused:]
[phone didn't respond, so I unplugged it and then plugged it back in and tried again]
rob@Eee:~$ sudo wvdial --config ~/mydialer.conf
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Oct 21 13:19:28 2008
--> Pid of pppd: 6125
--> Using interface ppp0
--> pppd: &#65533;Z[17][08]8_[17][08]
--> pppd: &#65533;Z[17][08]8_[17][08]
--> pppd: &#65533;Z[17][08]8_[17][08]
--> pppd: &#65533;Z[17][08]8_[17][08]
--> local  IP address 68.246.251.90
--> pppd: &#65533;Z[17][08]8_[17][08]
--> remote IP address 68.28.121.71
--> pppd: &#65533;Z[17][08]8_[17][08]
--> primary   DNS address 68.28.122.93
--> pppd: &#65533;Z[17][08]8_[17][08]
--> secondary DNS address 68.28.114.91
--> pppd: &#65533;Z[17][08]8_[17][08]
[internet connetion here:), then I unplugged phone]
--> Disconnecting at Tue Oct 21 13:20:54 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Disconnecting at Tue Oct 21 13:20:55 2008
rob@Eee:~$ 

-------------------------------------------------

Here's my /var/log/messages when the phone is plugged in, dialed, and unplugged:

rob@Eee:~$ tail -n 0 -f /var/log/messages
Oct 21 13:17:43 Eee kernel: [  204.612155] usb 3-1: new full speed USB device using uhci_hcd and address 2
Oct 21 13:17:44 Eee kernel: [  204.775827] usb 3-1: configuration #1 chosen from 1 choice
Oct 21 13:17:44 Eee kernel: [  204.779425] ipaq 3-1:1.0: PocketPC PDA converter detected
Oct 21 13:17:44 Eee kernel: [  204.785779] usb 3-1: PocketPC PDA converter now attached to ttyUSB0
Oct 21 13:17:44 Eee kernel: [  204.788437] ipaq 3-1:1.1: PocketPC PDA converter detected
Oct 21 13:17:44 Eee kernel: [  204.799817] usb 3-1: PocketPC PDA converter now attached to ttyUSB1
Oct 21 13:17:44 Eee kernel: [  204.802448] ipaq 3-1:1.2: PocketPC PDA converter detected
Oct 21 13:17:44 Eee kernel: [  204.833489] usb 3-1: PocketPC PDA converter now attached to ttyUSB2
Oct 21 13:17:46 Eee kernel: [  206.869559] usbcore: registered new interface driver cdc_acm
Oct 21 13:17:46 Eee kernel: [  206.869614] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[wvdial is run here]
Oct 21 13:19:28 Eee pppd[6125]: pppd 2.4.4 started by root, uid 0
Oct 21 13:19:29 Eee pppd[6125]: Using interface ppp0
Oct 21 13:19:29 Eee pppd[6125]: Connect: ppp0 <--> /dev/ttyUSB2
Oct 21 13:19:29 Eee pppd[6125]: local  IP address 68.246.251.90
Oct 21 13:19:29 Eee pppd[6125]: remote IP address 68.28.121.71
Oct 21 13:19:29 Eee pppd[6125]: primary   DNS address 68.28.122.93
Oct 21 13:19:29 Eee pppd[6125]: secondary DNS address 68.28.114.91
[connection to internet here, then I unplugged the phone]
Oct 21 13:20:54 Eee pppd[6125]: Modem hangup
Oct 21 13:20:54 Eee pppd[6125]: Connect time 1.5 minutes.
Oct 21 13:20:54 Eee pppd[6125]: Sent 0 bytes, received 0 bytes.
Oct 21 13:20:54 Eee pppd[6125]: Connection terminated.
Oct 21 13:20:54 Eee pppd[6125]: Exit.

I hope this helps other usb phone users out there get online using their cell phones and Linux.

Rob
:guitar:

---

