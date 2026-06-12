---
title: "Using Imate JAM (HTC Magician) Pocket PCas a usb modem"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by wilzad on 2006-10-14
If anybody knows to use Imate Jam or O2 XDA mini or HTC Magician as a USB modem in Ubuntu 6.06 please  advice me

---

### Post by zybernav on 2006-10-19
Look here

[http://andrewtv.org/fedora-ppc6700/](http://andrewtv.org/fedora-ppc6700/)
[http://www.paulperkins.net/linux/spv-modem.php](http://www.paulperkins.net/linux/spv-modem.php)


I cannot figure it to my Prophet yet. Something must be get config first. Have to find out more.

---

### Post by wilzad on 2006-10-20
i have tried this already and found not working

---

### Post by moeFinley on 2006-10-21
How are you connecting you iMate JAM?  I have an O2 XDA mini and Ubuntu doesn't recognise the device?

```
Oct 21 17:38:09 moefinley-desktop kernel: [17238396.848000] usb 1-3.2: new full speed USB device using ohci_hcd and address 12
Oct 21 17:38:09 moefinley-desktop kernel: [17238396.928000] usb 1-3.2: device descriptor read/64, error -110
```

---

### Post by wilzad on 2006-10-21
Hi,
I just plugged it in  to the usb port and went to the hardware browser, under the usb devices section my phone was listed ,  so i can say it automatically recognises the phone. but if i sart the wmodem utility and selected usb, it is not detecting my phone as usb modem. i went to Imate site and asked technical support about this, they said they don't have a solution for linux.
 
Please let me know if you fount a solution
 
regards
wilzad

---

### Post by gotmonkey on 2006-10-31
> **zybernav said:**
> Look here

[http://andrewtv.org/fedora-ppc6700/](http://andrewtv.org/fedora-ppc6700/)
[http://www.paulperkins.net/linux/spv-modem.php](http://www.paulperkins.net/linux/spv-modem.php)


I cannot figure it to my Prophet yet. Something must be get config first. Have to find out more.

I am in the same boat at the other users with my PPC6700 Verizon phone. I used the first link to set up the phone as a modem in Fedora Core 5. I have tried to get the guide working in ubuntu, but the redhat system-config-network doesn't seem to be available in ubuntu.

---

### Post by fayizk1 on 2007-08-29
HAY EVERY BODY 


IT IS SIMPLE WAY TO USE IMATE JAM (HTC MAGICIAN) AS MODEM IN LINUX

_STEP 1_

PLEASE FIND YOUR MAGICIAN'S WMODEM   VENDOR ID(vid),PRODUCT ID(pid)  (IF YOUR NOT KNOW ABOUT HOW KNOW THIS TWO PLZ MAILME AT [email]fayizk1@yahoo.com[/email] )

ok 

_STEP2_

open console type

modprobe usbserial vendor=vid product=pid 
 ( i think jams vid=0x0bb4 and pid=0xcf pls confirm)

and  plug pda to computer 


and edit /etc/wvdial.conf append below line:





[magician]
;normaly modem device are /dev/ttyUSB0 (or /dev/ttyUSBX where x is numeric or confirm)
Modem =/dev/ttyUSB0
Baud = 115200
Init1 = ATZ

Init2 = AT+CGDCONT=1,"IP","APN"
;where APN is your access point name
;your dialing number 
Phone = *99#
;edit below
Username = my_login_name
 Password = my_login_password

;end cofigration




_STEP 3_

type below;


wvdial magician



now ur computer connected to internet

any query pls mail me :- [email]fayizk1@yahoo.com[/email]

---

