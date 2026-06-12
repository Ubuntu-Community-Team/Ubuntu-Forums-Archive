---
title: "wvdial and E220"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by akintoo on 2008-07-12
Hi i'm trying to get wvdial configured for E220 in HH.

wvdial.conf looks like this:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","vfinternet.au"
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
Username = *********
Dial Command = ATDT
Password = **********
Baud = 9600

when i, root@R2D2U:/home/cjb# wvdialconf
I get:

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

I edit with nano
root@R2D2U:/home/cjb# nano /etc/wvdial.conf

Then dial:
root@R2D2U:/home/cjb# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","vfinternet.au"
AT+CGDCONT=1,"IP","vfinternet.au"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sat Jul 12 17:27:13 2008
--> Pid of pppd: 7510
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]@&#65533;[06][08]&#1575;[06][08]
--> pppd: &#65533;&#65533;[06][08]@&#65533;[06][08]&#1575;[06][08]
--> pppd: &#65533;&#65533;[06][08]@&#65533;[06][08]&#1575;[06][08]
--> pppd: &#65533;&#65533;[06][08]@&#65533;[06][08]&#1575;[06][08]
--> pppd: &#65533;&#65533;[06][08]@&#65533;[06][08]&#1575;[06][08]
--> pppd: &#65533;&#65533;[06][08]@&#65533;[06][08]&#1575;[06][08]
--> pppd: &#65533;&#65533;[06][08]@&#65533;[06][08]&#1575;[06][08]
--> local  IP address 10.130.13.177
--> pppd: &#65533;&#65533;[06][08]@&#65533;[06][08]&#1575;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;&#65533;[06][08]@&#65533;[06][08]&#1575;[06][08]
--> primary   DNS address 202.135.30.4
--> pppd: &#65533;&#65533;[06][08]@&#65533;[06][08]&#1575;[06][08]
--> secondary DNS address 203.2.193.67
--> pppd: &#65533;&#65533;[06][08]@&#65533;[06][08]&#1575;[06][08]

It hangs here, modem light is on suggesting connectivity but there is no connectivity.
All help would be most appreciated.

---

### Post by akintoo on 2008-07-12
Since my first post I have gone on to try GNOME PPP and vodafone-mobile-connect-card-driver-for-linux (eventhough i really want to use wvdial) and again when i connect there is a steady light on th modem and th applications report that th connection is connected but firefox, evolution and Update manager are unable to find th internet.

Now i'm pretty sure i've got th settings right cause they are th same whether i'm using a mobile phone or a windows pc.

So i'm thinking there is something about linux i am yet to learn.

Has anyone experienced a connected modem with no internet connection or does anyone know what i could try or things i should look into.

thanks and all th best.

---

### Post by Kenda on 2008-07-12
I think I have a similar problem. I am using Huawei E220 with Three in the UK (PAYG) with Hardy. I have very very poor mobile reception so that might be an issue but it seems I can connect using WVdial and gnome-ppp or indeed vodaphone mobile connect card however I cannot  then access any Internet sites. I have tried using static DNS (as mentioned on another thread) but I don't really know what I am doing and I still had the same problem.

I think there is one more tweak that I am missing: wvdial looks like this after running wvdialconf:

# cat /etc/wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB0
Username = three
Password = three
Baud = 9600

Can anyone help?

---

### Post by akintoo on 2008-07-13
Hey Kenda were probably not getting many replies cause there is so many posts about this the first thing to try is enabling stupid mode if using gnome ppp go to settings, options and tick ignore terminal strings (stupid mode) if using wvdial add th line:

stupid mode = 1

to wvdial.conf

as outlined in [this post]("http://ubuntuforums.org/showthread.php?t=843973&highlight=e220")

That didn't work for me so the next thing to try is [here]("http://ubuntuforums.org/showpost.php?p=4817997&postcount=8")

Hope this works for ya.

If you search [Networking & Wireless]("http://ubuntuforums.org/search.php?searchid=44522752") forum for e220 there is lots of stuff to look through.

---

### Post by hellomoto on 2008-07-17
this is from hfdragons post and maybe helpful to you?

> 
   5. Ubuntu's network manager contains a serious error: it does not regard a PPP connection as being online, and will drive a number of applications into "offline mode" unless you forbid it by replacing every instance of

      Code:

      <allow send_interface="org.freedesktop.NetworkManager"/>

      in the file
      Code:

      /etc/dbus-1/system.d/NetworkManager.conf

      with (the only change is 'allow' to 'deny')

      Code:

      <deny send_interface="org.freedesktop.NetworkManager"/>

      This prevents the programs from being able to ask the network manager whether it thinks the computer is online.


---

