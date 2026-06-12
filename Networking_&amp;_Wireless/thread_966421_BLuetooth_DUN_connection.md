---
title: "BLuetooth DUN connection"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by zongpog on 2008-11-01
Dear everybody,

I have attempted to establist a BT connction from my laptop to my mobile telephone and connect to the Internet over GPRS.  I know GPRS works because I can use it on the 'phone to read Emails and surf.  

The telephone is an Ericsson T68.

What is odd that i) it won't connect and ii) rfcomm disappeared after the failure and cannot reconnect with wvdial

I performed the following actions, 

(Note contents of /etc/bluetooth/rfcomm.conf,
rfcomm0 {
bind yes;
device 00:80:37:EE:4F:4E;
channel 1;
comment "T68 DUN";
}
)

```

1) Make BlueTooth 'phone discoverable

2) Scan for device
# hcitool scan
Scanning ...
	00:80:37:EE:4F:4E	T68


4) Check for DUN
# sdptool search DUN
Inquiring ...
Searching for DUN on 00:80:37:EE:4F:4E ...
Service Name: Dial-up Networking
Service RecHandle: 0x10000
Service Class ID List:
  "Dialup Networking" (0x1103)
  "Generic Networking" (0x1201)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100



5)  Connect with rfcomm0
# rfcomm connect rfcomm0 00:80:37:EE:4F:4E
Phone asks for Accept and passkey.
Next GUI window for passkey.

6) Open new window
# wvdial gibtel
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATM1L2
ATM1L2
OK
--> Modem initialized.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
root@axe:/home/sloewent# !vi
vi /etc/wvdial.conf 
root@axe:/home/sloewent# wvdial gibtel
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory
root@axe:/home/sloewent# /etc/init.d/dbus restart
root@axe:/home/sloewent# wvdial gibtel
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory
root@axe:/home/sloewent# wvdial gibtel
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATM1L2
ATM1L2
OK
--> Modem initialized.
--> Sending: ATDT*99***1#,
--> Waiting for carrier.
ATDT*99***1#,
CONNECT
--> Carrier detected.  Waiting for prompt.
AT
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sat Nov  1 14:41:31 2008
--> Pid of pppd: 9699
--> pppd: &#65533;&#65533;[06][08]
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> Authentication (PAP) started
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> Authentication (PAP) successful
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> Connect time 0.1 minutes.
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> Disconnecting at Sat Nov  1 14:41:33 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory
--> Disconnecting at Sat Nov  1 14:41:33 2008
root@axe:/home/sloewent# AT
bash: AT: command not found
root@axe:/home/sloewent# AT
bash: AT: command not found
root@axe:/home/sloewent# wvdial gibtel
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory

```

In /var/adm/messages there is,

Nov  1 14:41:31 axe kernel: [ 2093.692178] PPP generic driver version 2.4.2
Nov  1 14:41:31 axe pppd[9699]: pppd 2.4.4 started by root, uid 0
Nov  1 14:41:31 axe pppd[9699]: Using interface ppp0
Nov  1 14:41:31 axe pppd[9699]: Connect: ppp0 <--> /dev/rfcomm0
Nov  1 14:41:31 axe pppd[9699]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Nov  1 14:41:32 axe pppd[9699]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Nov  1 14:41:32 axe pppd[9699]: LCP: Rcvd Code-Reject for code 9, id 0
Nov  1 14:41:32 axe pppd[9699]: PAP authentication succeeded
Nov  1 14:41:32 axe pppd[9699]: Connect time 0.1 minutes.
Nov  1 14:41:32 axe pppd[9699]: Sent 64 bytes, received 58 bytes.
Nov  1 14:41:32 axe pppd[9699]: Modem hangup
Nov  1 14:41:32 axe pppd[9699]: Connection terminated.
Nov  1 14:41:32 axe pppd[9699]: Exit.

---

### Post by zongpog on 2008-11-03
Does anyone know how to work this out?

---

### Post by mishivia on 2008-11-14
Now that you have configured your rfcomm, you have to configure the wvdial. (enter without #)
#sudo gedit /etc/bluetooth/wvdial.conf

Once there you have to configure so that your laptop recognizes the rfcomm as your modem.
 whats your carrier? because this file is carrier-specific. but here is what is really vital to getting connected:

Modem = /dev/rfcomm0

this should help. as always I am doing a no-no@ work which is why my writing is very brief, but hopefully you understand. If not pm me or post back and when I am home. I will explain further.

regards niesha

---

### Post by zongpog on 2008-11-15
Thanks for points out where the error lies.  I thought that I had configured the wvdial file correctly.  It was a bit of a guess.

The carrier is Gibraltar Telecom (Gibtel).

# cat wvdial.conf
Phone = 
Username = 
Password = 
New PPPD = yes

[Modem1] 
Modem = /dev/ircomm0 
#Modem = /dev/rfcomm0 
Baud = 57600 
Init1 = ATZ 
SetVolume = 1 
Dial Command = ATDT 
Init4 = ATM1L2 
[Dialer Defaults] 
Modem = /dev/rfcomm0 
Baud = 57600 
Init1 = ATZ 
Init4 = ATM1L2 
Dial Command = ATDT 
SetVolume = 1 
[Dialer gibtel] 
Phone = *99***1#, 
Inherits = Dialer Defaults 
Stupid mode = 0 
Username = test
Password = test


There is no user and password so I put test test into it so it parses something.

---

### Post by mishivia on 2008-11-16
did that help, then?

---

### Post by zongpog on 2008-11-18
No. The wvdial.conf I have listed is the same one that I have used before.  As far as the mobile 'phone company is concerned it is fine.

root@axe:/home/sloewent# wvdial gibtel
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory

Who knows why.  The file (device) is there.

---

### Post by mishivia on 2009-01-16
happy new year...
sorry, I have been uber busy at work

this is a shot in the dark but this may be your problem...in blue
[Modem1]
Modem = /dev/ircomm0
[COLOR="Cyan"]#Modem = /dev/rfcomm0[/COLOR] [/COLOR]

the # disables that line so of the moment you only have the ircomm enabled you may want to place a # infront of that line instead...
at work g2run

---

### Post by Heero_Yuy_X on 2009-11-29
I don't know whether you got your method working or not, but there is another easier way in case you hit a dead end...

Install Blueman, pair your phone, choose dialup service.
Go to network connections, Mobile broadband, and then choose add...

Blueman should now have added your phone device to the wizard, and you should be able to setup your Cell phone network options through the wizard and connect normally...  

Hope this helps!

---

