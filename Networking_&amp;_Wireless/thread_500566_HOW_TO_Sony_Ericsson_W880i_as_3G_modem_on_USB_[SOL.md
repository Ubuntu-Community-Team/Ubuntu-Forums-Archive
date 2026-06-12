---
title: "HOW TO: Sony Ericsson W880i as 3G modem on USB [SOLVED]"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by JetPack on 2007-07-14
This is intended for Ubuntu 6.06 operated in the UK on the Orange network.

Plug in SE W880i using the USB lead suplied with the phone. There is no need to tell the phone what mode to work in - just leave the mode select message on screen.

Check the USB detection:-
$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 005: ID 0fce:d068 Sony Ericsson Mobile Communications AB
Bus 001 Device 004: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Autodetect the modem using WVDial:-
$ sudo wvdialconf
Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyACM1<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

Edit the .conf file:-
$ sudo gedit /etc/wvdial.conf

It must look like this:-
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","orangeinternet"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99 ***1#
Password = orange
Username = orange

Then launch the connection with:-
$ wvdial

And close the connection with:-
Ctrl^C

Original info found on:-
[www.perso.orange.fr/gja.frndz/ub1tulog/k800i.htm](www.perso.orange.fr/gja.frndz/ub1tulog/k800i.htm)
(Use Google to translate to English)

---

### Post by highcast on 2007-08-23
Absolutely good instructions for W880i. I got it working :) :mrgreen::KS

Thank you!

---

### Post by Ozztopia on 2007-09-06
The instructions provided by Jetpack worked perfectly for me. Thank you for the help.
I use a Sony Ericsson Z530i.
The only minor modification I had to make was to the wvdial.conf file.
Normally I don't need a user name or password to log into the net from the mobile, but wvdial will not work with blank fields for user name and password. So I just filled in the username with 'a' and password with 'b' (without the quotes) and it connected.:)
The number I dialled was *99***3#.
I have an Airtel connection, Mobile Office package in West Bengal, India.
Ubuntu 7.04

Where I stay, the only way to connect to the net is through GPRS. So no matter what anyone says about it's slow speed, at least it lets me connect to the net.
Thank you again, Jetpack.:)

---

### Post by moro1978 on 2007-09-07
HI to everyone here! ; )
HOW TO: Motorola V150 external USB modem get working?

---

### Post by Michl on 2007-09-26
I followed these instructions (the name and password that worked for me is "ointernet")
I connect, but the pppd daemon dies every time after a few seconds.  The error code is 
16.  The /var/log/message is LCP terminated by peer.    I have tried adding
Carrier Check = no
Stupid mode = yes
but this does not help.

At home in the US with dial-up I had a similar problem and added S19=0 to the init2
string and that did the trick, but now in the Czech Republic I am using my mobile
phone as a USB modem and S19=0 is rejected as a bad string.

In Windows 2000 I have no problems using the phone as a modem (on the same
laptop).

Thanks!!!
Michl

---

### Post by vmosorio on 2007-10-06
Just in case someone can help, I have tried to connect using wvdial with no sucess. This is the configration of the wvdial.conf file

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","web.megatel.hn"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99 ***3#
Password = webmegatel
Username = webmegatel

The output at the terminal is this:

--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","web.megatel.hn"
AT+CGDCONT=1,"IP","web.megatel.hn"
OK
--> Modem initialized.
--> Sending: ATDT*99 ***3#
--> Waiting for carrier.
ATDT*99 ***3#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sat Oct  6 08:46:37 2007
--> Pid of pppd: 5937
--> Using interface ppp0
--> pppd: ï¿½[08][06][08]x[0c][06][08]@ [06][08]
--> pppd: ï¿½[08][06][08]x[0c][06][08]@ [06][08]
--> pppd: ï¿½[08][06][08]x[0c][06][08]@ [06][08]
--> pppd: ï¿½[08][06][08]x[0c][06][08]@ [06][08]
--> pppd: ï¿½[08][06][08]x[0c][06][08]@ [06][08]
--> pppd: ï¿½[08][06][08]x[0c][06][08]@ [06][08]
--> Disconnecting at Sat Oct  6 08:46:38 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ

Exit code 16 is the key... why is the modem disconnecting? I'm in Honduras.

---

### Post by Rabindranath on 2007-10-07
I am using k510i as my usb modem and I have edited the wvdial.conf file and I have a error still. 
I fane edited the phone number to *99***1# and username is airtel and password is 'a'. Whan I type sudo wvdial in the terminal, everything goes well but i get an error " Configuration requires a valid phone mumber, Configuration requires a valid user name,  Configuration requires a valid password" even after editind the config file. When I use kppp, it seems to connect but I am unable to browse or do any other thing in the internet. It just shows the time taken since connection. Please help me... and thanks in advance...

---

### Post by mashruf on 2007-10-07
though username and password was O though.

---

### Post by Turgon on 2007-10-14
> **Rabindranath said:**
> I am using k510i as my usb modem and I have edited the wvdial.conf file and I have a error still. 
I fane edited the phone number to *99***1# and username is airtel and password is 'a'. Whan I type sudo wvdial in the terminal, everything goes well but i get an error " Configuration requires a valid phone mumber, Configuration requires a valid user name,  Configuration requires a valid password" even after editind the config file. When I use kppp, it seems to connect but I am unable to browse or do any other thing in the internet. It just shows the time taken since connection. Please help me... and thanks in advance...

Try browsing your service providers website. In my case they had written that I could just use my phone number for both username and password. Works nice.

---

### Post by Turgon on 2007-10-14
JUst wanted to point out that these instructions are useful if you want to connect via bluetooth too.

Just follow this guide on how to set up the bluetooth device (ignore the rest, since it needs some tweeking to work with sony ericsson phones): [http://wiki.clug.org.za/wiki/GPRS_Internet_over_Bluetooth](http://wiki.clug.org.za/wiki/GPRS_Internet_over_Bluetooth)

rfcomm0 {
  bind yes;
  device 00:0A:D9:EA:A4:F8;               <- Insert your phone's ID here
  channel 4;
  comment "P900 PPP connection";
}

Be carefull not to include the ***<- Insert your phone's ID here*** likeI did at first. If the restart bluetooth command doesn't work, you can always restart the entire computer.

Then you just replace this line:
Modem = /dev/ttyACM0

with this:

Modem = /dev/rfcomm0

and you are good to go!

---

### Post by phun-ky on 2008-04-16
hm, i can get my k810i phone connected with this, but i can't use the net connection somehow, how do i do this?

---

### Post by plastichero on 2008-07-02
Source - [http://shubuntu.blogspot.com]("http://shubuntu.blogspot.com")

Well ... I have to search a lot to find the way to use my Sony Ericsson w810 mobile phone as a modem and enjoy internet in Ubuntu linux. And After searching a lot, I found the solution quite easy! It's so simple. You just have to write three commands sequentially. These commands work perfectly with other mobile also, not necessarily with SE only.

At first, open a terminal and run this command and it'll show you the connected modem:

[COLOR="DarkOrange"]sudo wvdialconf /etc/wvdial.conf[/COLOR]

Now, open the file wvdial.conf with gedit or mousepad(depends on whether you are running Ubuntu or Xubuntu; I use Xubuntu)

[COLOR="DarkOrange"]sudo mousepad /etc/wvdial.conf[/COLOR]

You have to set the username, password, dial no. and un-comment those three lines (normally those are commented with a '#' sign at the beginning of the line. Wipe out those '#' sign). Leave other lines unharmed.

Finally, just run this command:

[COLOR="DarkOrange"]sudo wvdial[/COLOR]

and you'll be online immediately!

---

### Post by somersetsimon on 2008-07-08
> **plastichero said:**
> Source - [http://shubuntu.blogspot.com]("http://shubuntu.blogspot.com")

Well ... I have to search a lot to find the way to use my Sony Ericsson w810 mobile phone as a modem and enjoy internet in Ubuntu linux. And After searching a lot, I found the solution quite easy! It's so simple. You just have to write three commands sequentially. These commands work perfectly with other mobile also, not necessarily with SE only.

At first, open a terminal and run this command and it'll show you the connected modem:

[COLOR="DarkOrange"]sudo wvdialconf /etc/wvdial.conf[/COLOR]

Now, open the file wvdial.conf with gedit or mousepad(depends on whether you are running Ubuntu or Xubuntu; I use Xubuntu)

[COLOR="DarkOrange"]sudo mousepad /etc/wvdial.conf[/COLOR]

You have to set the username, password, dial no. and un-comment those three lines (normally those are commented with a '#' sign at the beginning of the line. Wipe out those '#' sign). Leave other lines unharmed.

Finally, just run this command:

[COLOR="DarkOrange"]sudo wvdial[/COLOR]

and you'll be online immediately!

I think was trying all the right commands. I edited the wvconf file with what seem to be the right values for the Vodafone network. When I run wvdial it seems to say it's connected, but I can't connect to the internet. Here's some output...

```
simon@linux-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!}!} }4}(}"}'}"}"}&} } } } }%}&[05];i 8[1e]~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Jun 29 22:48:56 2008
--> Pid of pppd: 9736
--> Using interface ppp0
--> pppd: &#65533;[0f]&#65533;&#65533;@&#65533;[06][08]0&#65533;[06][08]
--> pppd: &#65533;[0f]&#65533;&#65533;@&#65533;[06][08]0&#65533;[06][08]
--> pppd: &#65533;[0f]&#65533;&#65533;@&#65533;[06][08]0&#65533;[06][08]
--> pppd: &#65533;[0f]&#65533;&#65533;@&#65533;[06][08]0&#65533;[06][08]
--> local  IP address 10.100.139.23
--> pppd: &#65533;[0f]&#65533;&#65533;@&#65533;[06][08]0&#65533;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;[0f]&#65533;&#65533;@&#65533;[06][08]0&#65533;[06][08]
--> primary   DNS address 10.205.65.68
--> pppd: &#65533;[0f]&#65533;&#65533;@&#65533;[06][08]0&#65533;[06][08]
--> secondary DNS address 10.205.65.68
--> pppd: &#65533;[0f]&#65533;&#65533;@&#65533;[06][08]0&#65533;[06][08]
Caught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: &#65533;[0f]&#65533;&#65533;@&#65533;[06][08]0&#65533;[06][08]
--> Connect time 0.9 minutes.
--> pppd: &#65533;[0f]&#65533;&#65533;@&#65533;[06][08]0&#65533;[06][08]
--> pppd: &#65533;[0f]&#65533;&#65533;@&#65533;[06][08]0&#65533;[06][08]
--> pppd: &#65533;[0f]&#65533;&#65533;@&#65533;[06][08]0&#65533;[06][08]
--> Disconnecting at Sun Jun 29 22:49:49 2008
simon@linux-laptop:~$ 

```

The 'exit gracefully' was when I did a CTRL-C

Any help would be gratefully received :)

---

### Post by somersetsimon on 2008-07-14
Bumped as I want to take my laptop on holiday this weekend!

---

