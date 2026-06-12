---
title: "us robotics sportster voice 33.6 faxmodem"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by zoonaid on 2007-02-10
hi to all.
i have just installed edgy and am trying to connect to the net with external modem.using pppconfig i can get modem to detect dialtone, then dial isp no .then appear to connect.i think.
light on front panel show activity.than hangs up .using plog it appears my password is not getting authenticated.3 methods of authentication possible pap,chat.and CHAP what ever that
means.contacted isp to find out what is their preferred protocol.but help desk staff unable to help.location is South Africa,isp is TELKOM.
also help required to set up wvdial.perhaps that may work but unable /do not know how to set
up isp no,username and password for wvdial.
please note 1st attempt at ubuntu or linux.so assume noob as you guys say in my country we say "moegoe" :(

---

### Post by koenn on 2007-02-10
try wvdial - its intelligent and will try several approaches to get you connected

to set it up, you'll need a config file, probably /etc/wvdial.conf 

This is from 'man wvdial':
> 
       The  configuration  file /etc/wvdial.conf is in Windows "ini" file for&#8208;
       mat, with sections named in square brackets and a number of variable  =
       value pairs within each section.

       Here is a sample configuration file:
```

              [Dialer Defaults]
              Modem = /dev/ttyS2
              Baud = 57600
              Init = ATZ
              Init2 = AT S11=50
              Phone = 555-4242
              Username = apenwarr
              Password = my-password

              Dial Command = ATDT

```

replace the examples by valid values (eg correct username, password, phone number, ...)

---

### Post by zoonaid on 2007-02-25
hi koen,
i have tinkering about with the modem and i got it to work using pppconfig but only at 9600 baud rate.at any other speed the modem does not even dial out.i tried your suggestion of using wvdial.first i detected modem using $ sudo wvdial /etc/wvdial.conf  ,modem detected on
/dev/ttyS1.then set up modem parameters using $sudo nano /etc/wvdial.conf.i put my username,password etc .then typed wvdial .system then throws back configuration file with out my changes.i did remember to cntl o to save changes .what am i doing wrong? many thanks once again

---

