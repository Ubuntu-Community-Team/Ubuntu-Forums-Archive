---
title: "wvdial configuration"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by Locutus_of_Borg on 2007-11-08
Can someone please point out what I am doing wrong.

In Terminal
```
none@blank:~$ sudo slmodemd -c USA --alsa hw:0,6
Password:
SmartLink Soft Modem: version 2.9.11 Aug  6 2007 22:02:27
symbolic link `/dev/ttySL0' -> `/dev/pts/2' created.
modem `hw:0,6' created. TTY is `/dev/pts/2'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.
```

In second Terminal
```
none@blank:~$ sudo wvdial
Password:
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
```


My wvdial.conf 
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttySL0
ISDN = 0
; Phone = 555-55555
; Password = mypass
; Username = myusername@login
```


I have run scanModem, it idetified my modem as Intel 82801G, and have installed slmodemd at its suggestion.


Any help would be greatly appreciated.  I've tried e-mailing [email]linmodems@discuss.org[/email], but consistently get a delivery failure.

Thanks for any response.

---

### Post by muzel on 2007-11-08
Hi,

I think you should uncomment these lines (remove the **;** ):

; Phone = 555-55555
; Password = mypass
; Username = myusername@login

cu, muzel

---

### Post by Locutus_of_Borg on 2007-11-08
That makes sense. I will try it next I have access to a phone line.

Thanks.

---

### Post by Locutus_of_Borg on 2007-11-08
Produces:
```
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT893-7846
--> Waiting for carrier.
ATDT893-7846
NO CARRIER
ERROR

```

and in the slmodemd terminal:
```
SmartLink Soft Modem: version 2.9.11 Aug  6 2007 22:02:27
symbolic link `/dev/ttySL0' -> `/dev/pts/3' created.
modem `hw:0,6' created. TTY is `/dev/pts/3'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.
error: cannot setup hw params for playback: Invalid argument

```

Sigh. :(

---

### Post by muzel on 2007-11-11
Sorry, no idea - I don't use winmodems anymore. You spend a lot of time, maybe it works, and with the next kernel or distribution you start again struggling...

Good luck, muzel

---

