---
title: "Wvdial / bluetooth modem not responding"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by p221072 on 2008-07-24
Hello,
I configured dial-up connections with bluetooth mobiles several times and never got a problem.
Now I have a new laptop (running Ubuntu 7.10) a new mobile and a new operator and something doesn't work.
The bluetooth connection seems to be working fine:
```
paolo@Moon:~$ hcitool scan
Scanning ...
        00:1F:E4:23:2E:D2       Paolo Z310i

paolo@Moon:~$ cat /etc/bluetooth/rfcomm.conf
#
# RFCOMM configuration file.
#

rfcomm0 {
#       # Automatically bind the device at startup
        bind yes;
#
#       # Bluetooth address of the device
        device 00:1F:E4:23:2E:D2;
#
#       # RFCOMM channel for the connection
        channel 1;
#
#       # Description of the connection
        comment "Bluetooth Modem Z310i";
}

paolo@Moon:~$ hciconfig 
hci0:   Type: USB
        BD Address: 00:10:C6:8A:85:8C ACL MTU: 377:10 SCO MTU: 16:0
        UP RUNNING PSCAN ISCAN 
        RX bytes:1995 acl:13 sco:0 events:55 errors:0
        TX bytes:627 acl:12 sco:0 commands:33 errors:0

paolo@Moon:~$ sudo rfcomm connect hci0
Connected /dev/rfcomm0 to 00:1F:E4:23:2E:D2 on channel 1
Press CTRL-C for hangup

```
But when I try to run Wvdial, the modem (mobile) connected as /etc/rfcomm0 doesn't responde to the AT commands.
Here you can also see my wvdial.conf:
```
paolo@Moon:~$ rfcomm
rfcomm0: 00:10:C6:8A:85:8C -> 00:1F:E4:23:2E:D2 channel 1 connected [reuse-dlc release-on-hup tty-attached]

paolo@Moon:~$ cat /etc/wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","myMTN"
Modem Type = Analog Modem
ISDN = 0
Phone = *99***6#
New PPPD = yes
Modem = /dev/rfcomm0
Username = mtn
Password = mtn
Baud = 460800

paolo@Moon:~$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0
WvDial<*1>: Re-Sending: ATZ
WvDial<Err>: Modem not responding.
```
The only apparent problem could be a *TIOCGSERIAL is not supported* message in the log:
```
paolo@Moon:~$ dmesg
[...]
[   42.932000] Bluetooth: L2CAP ver 2.8
[   42.932000] Bluetooth: L2CAP socket layer initialized
[   43.056000] Bluetooth: RFCOMM socket layer initialized
[   43.056000] Bluetooth: RFCOMM TTY layer initialized
[   43.056000] Bluetooth: RFCOMM ver 1.8
[   46.484000] [drm] Initialized drm 1.1.0 20060810
[   46.508000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.508000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[ 1655.292000] rfcomm_tty_ioctl: TIOCGSERIAL is not supported

```
I'm really stuck with this ](*,) so any idea is welcome!
Cheers
Paolo

---

### Post by Sealbhach on 2008-07-24
I found this information about that error message on another site: [LINK]("http://66.102.9.104/search?q=cache:6HVf8ilhXmYJ:www.kriyayoga.com/love_blog/index.php/+%22TIOCGSERIAL+is+not+supported%22&hl=en&ct=clnk&cd=28&gl=uk")

> One additional error you may find in your /var/log/messages during dial up process is:

rfcomm_tty_ioctl: TIOCGSERIAL is not supported

this error message is apparently of no concern to proper connectivity !!! I have it and the connection is clean, stable and fast.

So hopefully you can rule that one out.


One other suggestion, install Gnome-PPP (a GUI dial-up interface)

sudo apt-get install gnome-ppp

If you set it to dock in the notification are you can view the connection log.. quite useful. It can also auto-detect modems.


.

.

---

### Post by p221072 on 2008-07-24
Yes, before posting I found the same information googling the error message, but it is the only hint of something not working properly so I decided to include it in the post.
Thank you, anyway.
For further information the same mobile works as bluetooth modem in windows, so the mobile's configuration should be correct and it is not faulty.

---

### Post by Sealbhach on 2008-07-24
Have you got it in Stupid Mode?


.

---

### Post by p221072 on 2008-07-25
Hi, I tried yesterday night.
I added the row
Stupid Mode = on
But it didn't help :(

---

### Post by Sealbhach on 2008-07-25
So the problem is "modem not responding" so one thing to check is if the modem actually works on amother machine e.g. windows or something.

Did you try the Gnome-PPP gui?

The connection log may give you more information.


If the modem is OK, all you can do is keep adjusting the settings until you get the right configuration:

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

It might be something simple like a password or something.

I'm probably telling you stuff you already know, sorry.:(


. 

.

---

### Post by p221072 on 2008-07-28
Is there any way to test / diagnose the bluetooth modem?
Just to understand if the problem relies on wvdial or on the modem itself.
I tried redirecting an echo to /dev/rfcomm0 but nothing happens...
Any idea?

---

### Post by p221072 on 2008-07-31
I can't believe there is no way to troubleshoot / diagnose a modem...

---

### Post by Sealbhach on 2008-08-01
Maybe try Scanmodem.

[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

Also, what happens when you sudo wvdialconf ?


.

---

