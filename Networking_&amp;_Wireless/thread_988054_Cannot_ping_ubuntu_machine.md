---
title: "Cannot ping ubuntu machine"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by ramon82 on 2008-11-20
I setup a PC with ubuntu and dansguardian to act as a router and a content filter. This PC has two network interfaces, one connecting it to the modem (straight UTP cable) and the other directly to another PC with a cross over cable. More or less like this:

MODEM  - DHCP enabled
  |
  |
SERVER eth0 - Obtains IP from modem
SERVER eth1 - 192.168.0.1
  |
  |
CLIENT - 192.168.0.2


SERVER - Ubuntu 8.04
CLIENT - Windows XP SP2 with firewall turned OFF


From the server I can ping to the client without problems, but I cannot ping from the client to the server ie: I cannot get dansguardian to work.

My question is simple. What might be preventing the client to ping the server??? As far as I know there is no firewall set on ubuntu...

Please help..

Thanks!!

---

### Post by pqrs295 on 2008-11-20
Up to 70% Off, Hurry Sale Ends SoonAustralian Real Sheepskin Boots**[color=#c76200]Uggretailsale.com[/color]**Authentic ugg boots, crafted from 100% natural Australian merino sheepskin leather.**[color=#c76200]Uggretailsale.com[/color]****[color=#c76200][/color]**100% Genuine AustralianUgg BootsPay by Paypal, Non-tax, Hurry!**[color=#c76200]Uggretailsale.com[/color]**

---

### Post by vandalay on 2008-11-20
Could you post the output of 'route' on your Ubuntu box (from command line)?

I've run into this before where I ping one interface and it replies out the other due to misconfiguration...

---

### Post by superprash2003 on 2008-11-20
are you pinging via ip or hostname?

---

### Post by ramon82 on 2008-11-21
Ok solved the ping problem by entering this command:

sudo /etc/init.d/firehol stop


I know its not a good solution at all as I have disabled firehol from running. Is there a way how I can set exceptions??

---

### Post by Iowan on 2008-11-21
There is *some* "ping" information on the [FireHOL]("http://firehol.sourceforge.net/") web page under "services".

---

