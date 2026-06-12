---
title: "NetworkManager Applet text settings"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by r3bol on 2011-01-02
Hi, I have the NetworkManager Applet connecting my USB 3G modem to the internet. I was wondering where the text file with the connection setting would be located?

I was looking for something like this...
> [Dialer pin]
Modem = /dev/ttyUSB0
Init1 = AT+CPIN=1234...................,.....!!here's your pin!!

[Dialer umts]
Modem = /dev/ttyUSB0
ISDN = off
Modem Type = USB Modem
Baud = 460800
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Dial Prefix =
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = off
Idle Seconds = 0
Init3 = AT+CGDCONT=1,"IP","drei.at".....!!here's your string!!
Username = drei.at...........................!!here's your Usern!!
Password = drei.at...........................!!here's your Passw!!
Phone = *99#.................................!!here's your Phone!!

I've tried looking /etc/ but couldn't find anything there.

Thanks in advance.

---

### Post by earthpigg on 2011-01-02
on my system:

```
ls /etc/NetworkManager/system-connections
```

```
sudo cat "/etc/NetworkManager/system-connections/file name here"
```

the quotes are needed because that file will contain spaces.

two things may differ between mine and yours.

1) this is an internal wireless network card, not usb.
2) i have previously set my local router as "available to all users", which requires sudoer permissions.

it would stand to reason that a file similar to that would exist somewhere in /home if that network hadn't been set to 'available to all users', but I can't seem to find it.

---

### Post by r3bol on 2011-01-02
Thanks for the reply. /etc/NetworkManager/system-connections is empty. I also had a look through some of the 'hidden' config files in the /home/user/ directory, but couldn't see anything that would indicate the file there either.

---

