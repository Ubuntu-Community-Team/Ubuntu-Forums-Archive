---
title: "I need a modem expert."
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by t4thfavor on 2007-06-10
Hi, 
I have a question about my good ol' dial up service under linux.

I have a couple decent hardware modems (USR Courier, and USR Sportster) , and when I use them under linux. they will not connect to my ISP unless I set the serial port line speed to 38400? or lower. Under windows, if I set the port to 115200 they both work just fine.

My ISP uses regular chap authentication, and has v.92 support (I know both modems are only v.90, but they say their modems will do that too). Does anyone have any idea's on why this might be occurring. It is kind of frustrating since I use an ipcop server to share the dial up, and can only get speeds of 28.8...

---

### Post by Bartender on 2007-06-10
I've read on Linux forums that Linux will try to run the modem at ludicrous speed and when that fails things can go sideways.  Best to set the connection speed just above your typical speeds.  All I ever get on our rural road is 24.4 :( so no point in setting it higher than 38.
Don't know anything about this "Sharing" thing you mention.  What happens if you run one PC at a time?

---

### Post by Mr. C. on 2007-06-10
I'm not sure what the answer is here, as I have not use a dial up modem in years.

However, a distinction is important here.  There are two speeds being discussed here: 1) the speed of communication from serial port to modem, and 2) the speed negotiated between the two modems.

Setting the serial line speed to unlimited or the highest supported should work in Linux; you may need to configure your modem via initialization script to do this.  This would be done for your in Windows as the installer used, or init scripts would be present on your Windows system, and those may not exist, or be correct, on your Linux box.

The serial line speed can only limit your modem-to-modem connection.  Focus on getting the serial line speed as high as possible first.

MrC

---

### Post by t4thfavor on 2007-06-11
What is happening is that my modem connects to the ISP's modems at about 28.8, and it will only connect when the serial port is limited to 36.4 if the serial port is set higher than that I will get carrier lost messages from wvdial. This happens if I hook the modem up directly to my ubuntu box. 
When I hook it up to the  IpCop, the same thing happens. I don't know why the connection would care if my serial port is fast or not. Shouldn't it just be up to the two modems to negotiate the connect speed based on line quality? 

Line quality in my area is really crappy, so I am unlikely to get faster connect speeds, but I would like to at leaast have the posibility that they could occur.

Thanks for you relplies, I am going to keep looking for a solution.

Chance

---

### Post by Mr. C. on 2007-06-11
The modems will perform adaptive speed changes as allowable to ensure a solid connection.

Have you tried to manually configure the serial port speed of the modem and serial line of your PC, ignoring the modem-to-modem connection?  In other words, configure the serial ports of each device and issue manual modem commands using a terminal connection (eg. AT, ATDT, etc.).  Modern modems should be able to talk to the serial ports at the highest speeds, but both have to be configured correctly.  Ensure you are using hardware flow control, not software flow control.  This is critical above 28800.

MrC

---

### Post by t4thfavor on 2007-06-11
I will check the flow control, I am almost sure it is hardware. Is there a modem command that sets the serial connection speed on the modem (courier v.everything, and sportster 5686)? If so that may be my problem.  

Also I failed to mention that the problem does not seem to occur with that other OS (Windows), but it also seems that the other OS(Windows) can't handle sharing a modem when it is not allowed to be the DHCP server.

In short, Windows works to share the modem at reported speeds higher than 28.8, but allows for little to no network flexability (QoS, Traffic shaping, etc), while Linux allows much flexability, but will not let me set up the connection any faster than 28.8.

Its really no problem, as I have been living with it for a few years now, I just thought that the Ubuntu community may have the answer I was looking for. 

Thanks,

Chance

---

### Post by Mr. C. on 2007-06-11
There is a command to set the serial speed, but I don't remember what the magic is... it has been too long.  I did search google for you to find the modem's command reference.  You'll have to spend some time looking up the correct commands (sorry, don't have the time right now):

[http://www.usr.com/support/3453/3453-command-ref/chap%202-AT%20command%20set.htm](http://www.usr.com/support/3453/3453-command-ref/chap%202-AT%20command%20set.htm)

Problems with devices that occur in Linux but don't occur in Windows are typically due to better support; there is a very large target market for such products, and vendors put less effort into *nix variants.

I not sure I understand what you mean about your DHCP issue.  A modem's transmission rate is completely independent of a DHCP server.  One is the lower hardware layer, the other application layer.

You shouldn't live with these slow speeds.  I've connected at at least 48k in the past; you have a good modem, and should be able to connect at higher speeds.

MrC

---

### Post by t4thfavor on 2007-06-12
As far as Windows is concerned I hope I never hear ICS again. In the past I tried to have Internet Connection Sharing take care of all the NAT stuff. But I was unable to find a way to make the dhcp server serve out addressed in the 192.168.1.x range instead of the 192.168.0.x range. I have a vpn at my office that Is on the 192.168.0.x subnet and it caused a bit of trouble when it was on. Also I had trouble with the PC wanting to connect to the internet, when I didn't want it to. I have found that an ipcop server is much better at being a router than a windows xp box. 

I even tried 2003 server, which would answer the phone even when dial in was turned off. I am sure there was some kind of configuration mishap that was causing this, but I am not too troubled by it since Linux is free.

I have since found a connect string for the v.everything modem that allows me to set the port speed to whatever I want. I don't have it as of yet, but if anyone wants it I will probably post it here when I get home.

---

