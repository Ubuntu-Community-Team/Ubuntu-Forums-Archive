---
title: "Connecting to the internet"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by ronbrooks on 2006-11-28
After two week I got my modem to dial out on (pon Prodigy) but I can't get it to dial out on firefox.  I am using 6.10 and tried to set up a network connection using (adm./networking) I set my modem to defalt and set up my IP address.  I am not sure what I should use in the last tab (hosts).  The location name I am not sure what to put there either. 

Can anyone else figure out why I would not be able to connect to the internet.  I am new to Linux so I will need a step by step direction on how I should do this.](*,)

---

### Post by unisol on 2006-11-28
how did you dial out with prodigy?

---

### Post by ronbrooks on 2006-11-29
I set up my ppoeconf file and named it Prodigy then I used the terminal and typed in pon Prodigy and it started to dial out but when I start firefox I can't connect to the internet.  It will not dial.  I know I must have some settings wrong but I am new to Linux and don't know what is worng. If you have any help so I can get on the net.

---

### Post by unisol on 2006-11-29
did you try the modemlights applet? right-click on taskbar click add select modemlights click add. now right-click on modem app and click properties, fill in your internet info. username password isp etc.when you have entered everything rightclick on modem icon and click activate. good luck

---

### Post by ronbrooks on 2006-11-29
When I right click on Desktop I get a box that has create folder, create launcher, create document but I don't see any select modemlights listed.

---

### Post by unisol on 2006-11-29
right-click on the taskbar at the top of your screen

---

### Post by unisol on 2006-11-29
right-click on the taskbar at the top of your screen,then select add to panel then select modemlights and do as i  said.

---

### Post by ronbrooks on 2006-11-29
I don't have modemlight in there I have a Modem Monitor and a Network monitor. Will they work?

---

### Post by unisol on 2006-11-29
it should. you can also try system/adminstration/networking and fill in your isp settings. username password, phone number to dialupto your isp. if you have windows installed the phone number should show up

---

### Post by ronbrooks on 2006-11-29
I have done all that but still can't connect to the internet. When I open firefox and try to connect I keep getting an error message check your computer network connections.  I must be doing something wrong in the set up.  It keeps going to a wireless connection everytime I restart the computer. I am using a dial up modem. I can dial out if I got to the terminal and use pon Prodigy  (name of the config file.) At this point I don't know what else to do. I need help with this.

---

### Post by unisol on 2006-11-30
open a terminal and type sudo wvdialconf/etc/wvdial.conf and see what port your modem is on. if it works try using wvdial to dial out. dont give up someone will come up with the answer

---

### Post by ronbrooks on 2006-11-30
This is what I get when I use sudo /etc/wvdial.conf OK where I go from there.

---

### Post by ronbrooks on 2006-11-30
This is what I get when I try and use sudo wvdial:

ronbrooks@ronbrooks:~$ sudo wvdial
--> WvDial: Internet dialer version 1.56
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

This is what I get when I use sudo gedit /etc/wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = 5248571
ISDN = 0
; Password = my password
New PPPD = yes
; Username = my username
Modem = /dev/modem
Baud = 460800

Can you see anything wrong with this set up. Still when I restart the computer and check Network I find it is back in wired mode. It will not stay in Dial up mode.

---

### Post by unisol on 2006-11-30
try sudo gedit /etc/wvdial.conf add the appropriate settings:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS0
ISDN = 0
; Phone = <Target Phone Number>
; Password = <Your Password>
; Username = <Your Login Name>
see if that helps. by the way do you have an onboard wireless network chip? illtry to find a solution for you if possible

---

### Post by AnthonyG on 2006-11-30
Erm , I see a large problem... Your username , Phone number , And password are commented out :).

This hasn't helped me but you may be in a different scenario , After you uncomment your login information, If it still doesn't dial correctly, Add the following to wvdial.conf:

```

Carrier Check=no
Stupid Mode=on

```

If you have problems after that still, Try mixing combinations of the settings, I.E. Remove stupid mode, Keep Carrier Check, And vice-versa.

---

### Post by ronbrooks on 2006-11-30
Nothing is working with the changes to /etc/wvdial.conf.  I changed the file and try to connect to the net with sudo wvdial and got the same as in post #13

I don't know if this will help but while I was connected to the internet with pon Prodigy I used this to check my connection.  Hope this will help. 

ronbrooks@ronbrooks:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:30:18:A2:64:D1  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xed00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          POINTOPOINT NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ronbrooks@ronbrooks:~$ 


ronbrooks@ronbrooks:~$ sudo ip route
63.215.28.109 dev ppp0  proto kernel  scope link  src 4.152.192.96 
default dev ppp0  scope link 


ronbrooks@ronbrooks:~$ cat /etc/resolv.conf
# resolv.conf created by pppconfig for Prodigy
nameserver 68.94.156.1
nameserver 68.94.157.1

Maybe you can see something in this.  I feel I am close to getting it connected and thank you for your help.

---

### Post by AnthonyG on 2006-11-30
I wish you the best of luck with this, I'm surprised the other gentleman responded so many times. In this forum it's a 1/100 chance you will get any assistance with 56K Modem troubles. I've posted two threads so far and for the most part they were ignored. 

Why not have a go with scanModem , And post the dump here. If you do so , I'll take a look around for appropriate assistance :D.

---

### Post by ronbrooks on 2006-11-30
OK guys thanks a lot I got it to work and what it was, in the config file I delited the (:) in each of the statements for Phone, username, password. I am using it right now and I am very happy.  I guess you could call it an early Christmas Present. 

Thanks, you were a big help to me.  I hope to pass on the help when I get better at this.

---

### Post by AnthonyG on 2006-11-30
Hmph... Why is it no one else noticed that :)

---

### Post by unisol on 2006-11-30
AnthonyG:ive been there and for now still use dialup and realize that everyone deserves to get the best out of ubuntu

---

### Post by AnthonyG on 2006-11-30
Cheers to you for getting it to dial.... If only I could say the same about myself.

---

### Post by unisol on 2006-12-01
what seems to be the problem with your linux box? how come u cant use dialup?

---

