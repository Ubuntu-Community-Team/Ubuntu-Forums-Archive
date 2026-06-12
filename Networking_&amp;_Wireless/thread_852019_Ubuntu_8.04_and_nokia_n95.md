---
title: "Ubuntu 8.04 and nokia n95"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by caco on 2008-07-07
Good afternoon and greetings from Nigeria :),
  please I am in need of help, assistance or walk-through on how to solve some 'perceived' problems with my toshiba laptop running ubuntu 8.04 and trying to share the internet connection on my wired lan (eth0) via my PRO/Wireless 3945ABG Network Connection wireless (wlan0) as an adhoc network with my nokia N95. I would be grateful if your assistance would be easy and/or simple enough.
The output from my ifconfig lists these

eth0 ... ...
lo ... ...
vnet0 ... ...
wlan0 ... ...
wlan0:avahi ... ...
wmaster0 ... ...

ps: ufw is enabled

---

### Post by caco on 2008-07-11
I hope someone in the this lovely planet would be able to assist me in this. I'm using wicd manager.
Anytime I setup an adhoc network the nokia n95 does not detect it.

My guess is that the adhoc network is not being setup, hence my n95 cant detect it. :confused:
"**Just thinking aloud**" It would be nice if some knowledgable fellow would be able to walk-me-through setting up a fuctional adhoc network via the terminal

Maybe I should keep my fingers crossed ...

---

### Post by caco on 2008-07-15
Is it just me trying to do the impossible or am I not asking the right question?:(:confused:

Please if you have a link that would assist in this solution kindly post. All the ones I came across from using various search engines or websites did not resolve it.

A billion Naira worth of thanks in advance....

---

### Post by caco on 2008-07-18
Hello all this is the progress I have made so far...

I can create the adhoc network on my laptop with a certain ip address and network name and my N95 does recognise it, after configuring the n95 with an ipaddress from the same network.

I noticed that the settings of wicd under preferences had to be changed. The WPA Supplicant Driver should be wext (Generic Linux wireless extensions). Well, this is what I notice worked for my laptop.

The next stage is connecting. This is where my problem is now. Anytime I trying browsing a website on my N95 using the adhoc network create I get a gateway no reply error. I think this is my next hill to climb.

Please can someone help me out with forwarding network traffic / bridging the two networks (eth0 and wlan0).

Thanks in anticipation

---

### Post by caco on 2008-07-22
:(:confused:
I'm still trying out some possibilities on how to get this working.

I'm no expert, any luck or help blessed people....

:)

---

### Post by caco on 2008-08-19
Blessed evening all, while I am still 'bashing' my head on sorting out my prime problem, I followed the steps detailed out by HyRax @ [http://ubuntuforums.org/showthread.php?t=705103](http://ubuntuforums.org/showthread.php?t=705103)
and I could sync my N95 phone tasks, contacts & appointments with evolution.
A big 'Mbona' to him, oh that translates to 'A big thanks to him'

---

### Post by caco on 2008-08-26
Keeping with the theme of this thread, I tried my hands on getting my Toshiba laptop online using my mobile phone. On this side of the planet I am using MTN Nigeria prepaid service.

These links would prove helpful & thanks to them for their assistance...
[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)
[http://forums.overclockers.com.au](http://forums.overclockers.com.au)

---

### Post by caco on 2008-08-26
Use your favourite text editor and create the text file /etc/ppp/peers/mtn
Populate it with the info below

# MTN PPP initialisation/termination script
# Do not ask the remote to authenticate.
noauth
# Modem chat scripts
connect "/usr/sbin/chat -v -f /etc/chatscripts/mtn-connect"
disconnect "/usr/sbin/chat -v -f /etc/chatscripts/mtn-disconnect"
silent
debug
# Serial device to which the modem is connected.
/dev/rfcomm0
# Speed of the serial line.
115200
# Use this connection as the default route.
defaultroute
# Try to get the name server addresses from the ISP.
usepeerdns

Create the text file /etc/chatscripts/mtn-connect 
Populate it with the info below

# MTN PPP CONNECT script
TIMEOUT         5
ECHO            ON
ABORT           '\nBUSY\r'
ABORT           '\nERROR\r'
ABORT           '\nNO ANSWER\r'
ABORT           '\nNO CARRIER\r'
ABORT           '\nNO DIALTONE\r'
ABORT           '\nRINGING\r\n\r\nRINGING\r'
''              \rAT
TIMEOUT         12

OK              ATE1
OK              'AT+cgdcont=1,"IP","web.gprs.mtnnigeria.net"'
OK              ATD*99***1#

Create the text file /etc/chatscripts/mtn-disconnect 
Populate it with the info below

# MTN PPP DISCONNECT script
ABORT		"BUSY"		
ABORT		"ERROR"		
ABORT		"NO DIALTONE"	
SAY		"\nSending break to the modem\n"	
""		"\K"		
""		"\K"		
""		"\K"		
""		"+++ATH"	
""		"+++ATH"	
""		"+++ATH"	
SAY		"\nPDP context detached\n"

Create the text file mtn-ppp
Populate it with the info below

#!/bin/bash
sudo rfcomm release 0
echo "MTN 3.5g connection initialising ... "
rfcomm connect 0 &
sleep 5
pon mtn
read -p "Pls, press Enter to terminate your session."
poff mtn
echo "MTN 3.5g connection terminated ... "
exit 0

(I created this text file in my ~/bin so that I can easily execute it)
make this text file 'mtn-ppp' executable 'chmod a+x bin/mtn-ppp'

Since my laptop has no inbuilt bluetooth, I plug in my bluetooth dongle, active bluetooth on my phone, and on a terminal I enter ...

mtn-ppp

after entering my password ... the magic and enjoyment begins

ps I also ensure I have enough call credit in my account ... hoping MTN would make it extra cheap:)

---

### Post by caco on 2008-12-02
Well I have not updated this for a lot of reasons ... part of which is I upgraded my OS to Ubuntu 8.10.
Great work to the entire Ubuntu team (developers, users, ... others unknown).
Better graphics and my N95 got recognised with the proper settings, that I only had to decide on the better data plan from MTN Nigeria to keep me happy.
If you have any tricks with Ubuntu and your N95 or phone for that matter do the right thing... later.

---

