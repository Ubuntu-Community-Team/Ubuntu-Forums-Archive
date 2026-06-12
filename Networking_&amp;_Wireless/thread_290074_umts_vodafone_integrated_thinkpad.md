---
title: "umts vodafone integrated thinkpad"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by phatzac on 2006-10-31
Hi everyone, i've just recently purchased a new IBM thinkpad X60s

basically it has the UTMS card integrated thus no need to purchase the connect card

More info [http://www.thinkwiki.org/wiki/Verizon_1xEV-DO_WWAN]("http://www.thinkwiki.org/wiki/Verizon_1xEV-DO_WWAN")

I've search high and low and i'm unable to connect to vodafone using xubuntu 

below are some console output that i currently have hope it helps  anyone trying to trouble shoot i currently live in australia and there is no need for a pin or username.


I've follow a similar guide found on the forums though i have no luck, its not a pcmica card but its integrated into the pc not sure if thats going to be different or not

end story is if can't get this working i might have to go back using windows either way i hope i can remain using ubuntu 


> 
issac@mickey:~$ comgt -d /dev/ttyUSB0 info
##### Wireless WAN Modem Configuration #####
Product text:
====

Manufacturer: Sierra Wireless, Inc.
Model: MC8755
Revision: U1_2_8MCAP G:/WORKSPACES/FIRMWARE/U1_2_8MCAP/MSM6275/SRC 2006/03/07 21:31:16
IMEI: XXXXXXXXXXXXXXXXXXXXXXXXXx
FSN: XXXXXXXXXXXXXXXXXXXXXXX
3GPP Release 1999
+GCAP: +CGSM,+FCLASS,+DS
OK
====
Manufacturer:           Sierra Wireless, Inc.
IMEI and Serial Number: XXXXXXXXXXXXXXXXXXXXX
Manufacturer's Revision: 
U1_2_8MCAP G:/WORKSPACES/FIRMWARE/U1_2_8MCAP/MSM6275/SRC 2006/03/07 21:31:
Hardware Revision:      

Network Locked:         1
Customisation:          

Band settings:          (
)
APN:                    1,"IP","vfnetwork.au","",1,1
##### END #####


> 
issac@mickey:~$ comgt -d /dev/ttyUSB0
comgt 09:52:30 -> -- Error Report --
comgt 09:52:30 -> ---->                      ^
comgt 09:52:30 -> Error @139, line 8, Could not write to COM device. (1)

issac@mickey:~$ 



> 
issac@mickey:~$ sudo wvdial hsdpa vodafone 
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","vfnetwork.au","",1,1;
AT+CGDCONT=1,"IP","vfnetwork.au","",1,1;
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Nov  1 09:47:37 2006
--> Pid of pppd: 5023
--> Using interface ppp0
Caught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> Disconnecting at Wed Nov  1 09:47:43 2006


---

