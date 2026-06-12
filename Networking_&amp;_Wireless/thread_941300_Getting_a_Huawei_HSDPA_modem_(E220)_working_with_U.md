---
title: "Getting a Huawei HSDPA modem (E220) working with Ubuntu"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by mthalis on 2008-10-07
im using the above mentioned modem(HSDPA modem (E220)) to connect to the internet. but it doesnt work in Ubuntu by default. can someone help me out with a solution to use it in ubuntu 7.10?

---

### Post by GeorgeVita on 2008-10-12
Hi, I would like to try with my E170 in my PC. Yesterday I downloaded a "Desktop" iso image (live CD) for 7.10. Can you supply more info:

a. What version of wvdial has your 7.10 (you can see it by running wvdial from terminal)?
b. what is the version of network manager (right click on icon, click "about")?
c. Attach the modem on the USB port, wait 10 seconds, type **lsusb** and **ls /dev/ttyUSB*** on a terminal window to see how the PC found the modem and post the results.

Regards,
George

---

### Post by PippoFranco on 2008-10-13
[SOLVED] I have Hardy 8.04.1 on a Acer TravelMate 8200.

I would like to use my Modem Huawaei E172 (same interface of the 220 model) to access Vodafone (Omintel)

I have NM 0.6.6

franco@franco8200:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
franco@franco8200:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:0892 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
franco@franco8200:~$ ls /dev/ttyUSB*
/dev/ttyUSB0  /dev/ttyUSB2  /dev/ttyUSB4  /dev/ttyUSB6  /dev/ttyUSB8
/dev/ttyUSB1  /dev/ttyUSB3  /dev/ttyUSB5  /dev/ttyUSB7
franco@franco8200:~$ 

Any suggestione to make it work?

Thanks

Franco

---

### Post by GeorgeVita on 2008-10-13
> **PippoFranco said:**
> I have Hardy 8.04.1 on a Acer TravelMate 8200.

I would like to use my Modem Huawaei E172 (same interface of the 220 model) to access Vodafone (Omintel)

I have NM 0.6.6

franco@franco8200:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory

...

Hi Franco,
there are many ways to use the 3G modem (wvdial, network manager, special s/w as betavine etc.). I prefer wvdial and that I am going to try with you. The problem seems to be in the /etc/wvdial.conf file. You can edit it through a terminal window:
**sudo gedit /etc/wvdial.conf**

Copy & paste the following lines into gedit (remove old lines):

[B][Dialer Defaults]
New PPPD = yes
Dial Command = ATDT
Dial Attempts = 3
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0

[Dialer hspa]
Phone = *99#
Stupid Mode = 1
Init3 = AT+CGDCONT=1,"IP","internet"

[Dialer myPIN]
Init4 = AT+CPIN=1234
[/B]

The Init3 line sets the APN and possibly needs a change. Ask your provider about the APN and if they need specific user and password ("internet", "user" and "pass" in the above example).

The last two lines will be used only if you want a SIM PIN check but for your first tries **remove the check of SIM PIN** using windows or a mobile phone.

Finally after a reboot, dial using: **sudo wvdial hspa**

More you can find at:
[http://forum.huawei.com/jive4/thread.jspa?threadID=322982](http://forum.huawei.com/jive4/thread.jspa?threadID=322982)

Post any message to follow up.
Regards,
George

---

### Post by PippoFranco on 2008-10-15
Thank you for the suggestion. I have installed the new NM release (NM 0.7.0) and I solved my problem. The NM recognizes the Huawei modem, asks for the name of the provider (Vodafone (Omintel) in my case) and the PIN.

It switched in few second from cable to the HSDPA connection and back.

Regards

Franco

---

