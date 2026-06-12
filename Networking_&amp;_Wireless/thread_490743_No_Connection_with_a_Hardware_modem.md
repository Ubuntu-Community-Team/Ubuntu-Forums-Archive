---
title: "No Connection with a Hardware modem"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by Dan Nelson on 2007-07-02
Hi,
    I am new to the Lionux thing and have installed Ubuntu (It is my sole operating system).  To get a dial-up connection I put in a internal hardware modem from a friend of mine.  My situation is;
  1)The phone icon does not have the activate/deactivate highlighted.
  2)I have the modem connection set-up with my internet provider's number, my user-id, login, and using /dev/ttys2 (which the command $ sudo wvdialconf /etc/wvdialer.conf detects the modem at (speed 115200 ; init "ATQ0 V1 e1 s0=0 &C1 &D2 +FCLASS=0)).
 3) As soon as I select ttys2 in the modem properties (and on booting up), the modem makes all the usual dial-up noises but that is it.  The browser does not find any sites.  My phone handset is dead and I am at a loss.

Any ideas on what I am doing wrong?  The reason I chose Ubuntu was to avoid having to learn a lot of details but still be able to use Linux so I am a little frustrated at the moment.  (It feels like dealing with Windows! (-:)

---

### Post by Bartender on 2007-07-04
I'd try a PCLOS2007 LiveCD.  Fire up KPPP (in Applications>Internet) and see if it can find/talk to the modem.  You may have a problem with the modem itself, or the PCI slot it's plugged in to

OR

Your problem may just be that the latest 2 versions of Ubuntu are stupid about dial-up.  Trying another distro may be easier for you than than screwing around with Ubuntu.  If you have no luck with another distro, then that tells you something too and may at least give you some idea of what to try next.

EDIT:  You're *sure* it's a full hardware modem?  What's the brand/model?  You mention your handset is dead.  Do you mean you have a phone plugged into the second port on the back of the modem card?  Jeepers, I'm not sure about that but seems the second port should work if the modem has power, regardless of whether it's working properly with the OS.

---

### Post by Dan Nelson on 2007-07-04
It is at home so I don't have the make and model with me.  The handset works through the modem until I set up the modem and it tries to dial out.  I may give that PCLOS207 Live CD a look also.

Anybody else have any ideas?

---

### Post by Bartender on 2007-07-04
Who's your ISP?  Some ISP's just don't work with Linux, or require extra hassles.

You may be getting as far as making contact with your ISP and they're rejecting you because of username.  In Windows you might have seen an error message, but it's unlikely that you would in Linux.  I could hear my modem dial, then it'd quit.  All I had to do was either add or drop the domain, I can't remember which.  You know what I mean, right?  Adding the domain would make your username look like this: "linuxuser@copper.net" instead of just: "linuxuser".

---

### Post by Dan Nelson on 2007-07-04
I am using a local (Twin Cities Minnesota) ISP named tcinternet.  I think you may have hit on it.  I am going to try that out when I get home!:p

---

### Post by Dan Nelson on 2007-07-05
Well, I added the domain name to my login but no change.  I will contact my IP company next to see if they are the problem.

---

### Post by Bartender on 2007-07-06
Hi, Dan -
What's the modem?  I don't understand this problem, but have read several threads where guys had problems with the full-hardware USR modem on the PCI bus.  If I had one of these I'd like to figure out what the hang-up is but they're very expensive new or you gotta go hunting for a used one on ebay or etc.

It'd be good to look inside and write down the exact model#

---

### Post by Dan Nelson on 2007-07-09
I am not sure on the company.  I found a model number of 56IFXSP(c).  Parts on the board are from Cirrus Logic, Aptos, and Sanyou.

---

### Post by Dan Nelson on 2007-07-17
Well, My IP provider tells me I connected when I tried the PCLinuixOS 2007 but I get a timeout after the log says I connected.  I assume the same thing was happening Ubuntu.  Can I assume if the modem dialed out and a connection was established that the problem is not in the modem?

---

### Post by t4thfavor on 2007-07-17
I too have problems dialing out with Ubuntu, I have a few USR modems, and both work under IPCOP. Under Ubuntu I get a log message stating that something timed out while negotiating lcp setup. (I will get the exact wording if anybody wants it). 

What seemed to help was setting the serial port speed to something like 38600 instead of 115200.

---

### Post by Dan Nelson on 2007-07-21
I loked at all the configuration and network things I could find and can't find where to set the speed although I do remember seeing it in the past.  How can I set the speed?

---

### Post by Bartender on 2007-07-22
I think it's set in wvdial.  Try this in terminal
```
sudo gedit /etc/wvdial.conf
```
and see if it doesn't get you to a place where you can set the speed.  I've seen it said several times that turning down the connection speed helped.  The general theory seems to be that the software tries at 115K and has to fail before trying again at the next lower speed.  Sometimes it fails entirely instead of throttling back.  Sometimes it doesn't.  May have something to do with the ISP?  I left mine at ludicrous speed and it connected even though my actual data xfer was well below 115K.  I shoulda tried setting a slower speed to see if data transfer improved. 

Dang it, I'm always doing this from memory because our ISP doesn't work very well with Linux so I talk with you guys from a Windows PC!

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=480717").  duncan describes how to set up pppconfig, which also gives you the option of setting connection speed.

---

### Post by tweakbox on 2007-08-06
go pppconfig go through the steps there find out your isps dns server numbers should be two.then openup vim or whatever editor /etc/ppp/peer/provider enter your username,phone number, and change /dev/modem to /dev/ttyS0.then close and type pon to turn off your connection type poff

---

