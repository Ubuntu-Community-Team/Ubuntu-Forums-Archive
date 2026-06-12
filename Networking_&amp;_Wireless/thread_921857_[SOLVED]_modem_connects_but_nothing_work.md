---
title: "[SOLVED] modem connects but nothing work"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by Ricardo_RSP on 2008-09-16
Hi, im used to the portuguese forum (im brazilian) and usually the people there are very helpful and smart, but i guess no one there seems to know how to fix this problem:

i got a Agere modem, downloaded the "agrsm-ubuntu8.04.1-2.6.24-19-generic" driver for it, there is a How-to that came with "agrsm_howto.txt" i followed every line to install, and it worked fine, the modem is detected using "sudo wvdialconf /etc/wvdial.conf", then i go to the wvdial.conf to make the right configuration, i added "Stupid Mode = on" too.

When i type wvdial, its connect to the internet, get the IPs, (primary and secundary) but i cant access nothing, i cant ping any address, firefox, cant locate the web, Amsn don't work too, like im not connected, with no error or warnings. the gnome-ppp and kppp do the same thing.

I added my login and password to the files pap-secrets and chap-secrets, but without success.

Someone know how to fix that?

Im using Ubuntu 8.04 hardy heron
linux kernel 2.6.24-19

Ricardo

---

### Post by Iowan on 2008-09-16
May need to disable IPv6.  There are How-To's on the forum - I'll have to look for one.

---

### Post by Ricardo_RSP on 2008-09-16
i googled about it and found this:

"Disable IPv6 in ubuntu

Steps
1. sudo gedit /etc/modprobe.d/aliases
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot"

i did that and still the same.
isn't this way to disable IPv6 or this didn't worked

---

### Post by figmentx on 2008-09-16
when it's connected, are you trying to ping URL's or ip addresses, it sounds like dns is not working.

Ping [www.google.com](www.google.com)  then ping 72.14.205.99

and tell us if you get a reply on either.

Also, if you know the IP address of your ISP's dns server and gateway, can you ping those?

---

### Post by Ricardo_RSP on 2008-09-16
this is when i connect by wvdial:
"
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT17003131
--> Waiting for carrier.
ATDT17003131
CONNECT 53333 V44
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!-} }8}"}&} }*} } }#}$@#}%}&a[0c]E5}'}"}(}"?=~
--> PPP negotiation detected.
--> Starting pppd at Tue Sep 16 21:39:02 2008
--> Pid of pppd: 6275
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]&#549;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#549;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#549;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#549;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#549;[06][08]
--> local  IP address 189.49.29.249
--> pppd: &#65533;&#65533;[06][08]&#549;[06][08]
--> remote IP address 201.4.82.4
--> pppd: &#65533;&#65533;[06][08]&#549;[06][08]
--> primary   DNS address 200.222.0.35
--> pppd: &#65533;&#65533;[06][08]&#549;[06][08]
--> secondary DNS address 200.202.193.75
--> pppd: &#65533;&#65533;[06][08]&#549;[06][08]
"

i tried to ping [www.google.com](www.google.com) and returned 
"ping: unknown host www.google.com"

pinging 72.14.205.99:
"PING 72.14.205.99 (72.14.205.99) 56(84) bytes of data.

--- 72.14.205.99 ping statistics ---
246 packets transmitted, 0 received, 100% packet loss, time 245293ms"

i saw that 2 DNS IPs in the wvdial connection and pinged them and got 100% packet loss too.

the local and remote IPs are dynamics.

---

### Post by Ricardo_RSP on 2008-09-16
guys, i worked it out and discovered the problem, someone told me to check the ethernet connections, so i disabled all them, and worked fine.

the problem was that i was using a shared connection to talk here in the forum, when i saw something and wanted to try, i was disconnecting the other pc and connecting this one, but i forgot to disable ethernet connection, so i was connecting with the modem, but the computer was trying to access the net by ethernet.

thanks a lot for the help, i hope this solution helps others users

---

### Post by Iowan on 2008-09-16
Glad you got it fixed.  If you believe the problem is [SOLVED], mark the thread as such (under Thread Tools).

---

### Post by Rosycode on 2008-10-19
Guys, I think I have similiar problem. But I am not able to fix it.
It goes like this. 

 I am trying to connect with pppoeconf. I am setting the same password and username that I use in Windows. However, I get CHAP and PAP failure. I checked the CHAP and PAP secret files and they have the "username" * "password".

I am using Ehthernet modem. I am getting connected as it correctly detect IP and DNS. But its during my user verification that causes the problem.

Is my ISP not using CHAP verification and uses some other handshake protocol ? Please help as I cant breathe without internet !!!

Regards
Rosy

---

