---
title: "Keep losing connection..."
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by JbsTac on 2007-07-27
Ok, I just installed Ubuntu on my laptop two days ago. I've been able to get most of my stuff to work, but the AirCard is giving me problems. Everytime I connect using the wvdial instructions [here]("http://ubuntuforums.org/showthread.php?t=132473&highlight=Verizon+Wireless")
I get a connection for about two and a half minutes max and then it fails. It seems to fail more quickley if I'm downloading anything or using synaptic. Below are the scripts I'm using, as well as the wvdial configuration. Please Help!


> jbs17@jbs17-laptop:~$ sudo wvdial
-->WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=o &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Fri Jul 27 11:01:56 2007
--> Pid of pppd: 8828
--> Using interface ppp0
--> pppd: ?*
--> pppd: ?*
--> pppd: ?*
--> local IP address 70.221.7.41
--> pppd: ?*
--> remote IP address 66.174.38.5
--> pppd: ?*
--> primary DNS address 66.174.95.44
--> pppd: ?*
--> secondary DNS address 69.78.96.14
--> pppd: ?*
--> pppd: ?*
--> pppd: ?*
--> Connect time 2.5 minutes.
--> pppd: ?*
--> pppd: ?*
--> pppd: ?*
Disconnecting at Fri Jul 27 11:04:27 2007
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
-->man ppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded (often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)



> [Dialer Defaults]
Stupid Mode = on
Modem = /dev/ttyACM0
Baud = 921600
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777
Username = <my number>@vzw3g.com
Password = vzw
Init1 = ATZ
ISDN = 0
Modem Type = Analog Modem
Auto Reconnect = on
Carrier Check = no

[Dialer shh]
Init3 = ATM0

[Dialer pulse]
Dial Command = ATDP

---

### Post by Bartender on 2007-07-28
Cut off after 2.5 minutes.  Exactly my experience when trying to dial the internet with a friend's Samsung cellphone, his USB adapter cable, and Sprint.  I read something on the internet about putting in "web" and "web" for username/password so that's what I did.  Tthat may have something to do with it?
I think this is somehow related to the provider's software seeing someone on their system but not appearing to be a legitimate customer?

---

### Post by DLinn on 2007-08-03
This my conf file. There are some differences ... try 'em out.

This connects me as long as I am root, but if I try to log in as a user I get a pppd error code 2 and I'm looking for some help with that.

# /etc/wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Password = vzw
Phone = #777
Modem Type = USB Modem
Stupid Mode = on
Baud = 921600
Modem = /dev/ttyACM0
Init = ATZ
ISDN = 0
Username = [email]xxxxxxxxxx@vzw3g.com[/email]
Carrier Check = no
Auto Reconnect = on

[Dialer shh]
Init3 = ATM0

[Dialer pulse]
Dial Command = ATDP

---

### Post by corn13read on 2008-05-11
I was having these exact same issues. I use kppp in gnome it seems to work the best. I also use softwrea XON/XOFF for modem settings.

Upgraded phones and was only able to stay connected for exactly 2.5 minutes. I figured it was something vzw did. I found though if I modify my /etc/ppp/peers/kppp-options file to include these two lines it worked fine!:

lcp-echo-failure 0
lcp-echo-interval 0

Hope this helps someone.

I have been connected for 12 minutes and am posting this from my laptop.

---

### Post by dark_harmonics on 2008-05-26
wvdial was easier for me but i just edited the same options in /etc/ppp/options to be the same values and my connection has not dropped! YAAAAAY! I have spent hours on this one!

---

