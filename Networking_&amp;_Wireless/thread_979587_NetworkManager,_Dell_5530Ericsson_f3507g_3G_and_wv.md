---
title: "NetworkManager, Dell 5530/Ericsson f3507g 3G and wvdial"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by barryjohnwilliams on 2008-11-12
I recently setup my Dell 5530/Ericsson f3507g card on a clean install of 8.10 Intrepid.  

I found I couldn't setup my Dell 5530 WWAN card using NetworkManager; whilst it detected the card after putting in the settings it didn't connect.  

I found another thread on this forum ([http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=941079](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=941079)) and followed the advice which created a wvdial.conf file.  It suggested patching the kernel, but I found I didn't have to do that with the stock kernel I am using (2.6.27-7-generic).  

I modified this conf to create my own wvdial.conf which I have extended to include GPS support.  This script allows switching the radio on and off, enabling GPS and connecting to the internet.  After enabling GPS just run gpsd on /dev/ttyACM0.  

```

[Dialer Defaults]
New PPPD = yes
Stupid Mode = 1
Modem Type = USB Modem

#[Dialer PIN]
#Init1 = AT+CPIN=

[Dialer signal]
Modem = /dev/ttyACM1
Init1 = AT+CSQ
Init2 = AT+COPS?

[Dialer gps]
Modem = /dev/ttyACM0
Init1 = AT*E2GPSCTL=1,10,1
Init2 = AT*E2GPSNPD

[Dialer on]
Modem = /dev/ttyACM1
Init1 = AT+CFUN=1

[Dialer off]
Modem = /dev/ttyACM1
Init1 = AT+CFUN=4

[Dialer connect]
Modem = /dev/ttyACM1
Init1 = AT 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Baud = 460800
ISDN = 0
Phone = *99***1#
Password = web
Username = web

```

The only way for me to run this is from the command line, this is a bit untidy especially for the connect script as it then runs pppd in the terminal - killing the terminal or ctrl-c quits the connection, useful for disconnecting but not really clean.  

Secondly, if I do run this through the terminal - NetworkmManager thinks I'm offline sending Firefox into an unending annoyance of having to keep switching it online.  

Is there anyway for me to run this connection through a GUI which stops me from having a terminal connection always open - better still to somehow integrate this within networkmanager to avoid the offline problem.  

Also, where are the AT scripts networkmanager uses to connect 3G devices - perhaps I can modify them directly to suit my card?  

Any further help much appreciated!

---

### Post by geek65535 on 2008-11-14
I haven't found where the AT commands for networkmanager are, either. They seem to be one of the worst FOSS for documentation. 
Thanks for the info on the gps. that was the last piece of the puzzle for me.

---

### Post by geek65535 on 2008-11-14
One thing I've found that is pretty important:
This command AT*E2GPSCTL=1,10,1 appears to control the rate the NMEA messages get spit out. That '10' means 10 seconds. For faster updates (which would be important with mapping software), use a lower number, like 1. (I'm not sure about the other numbers, or what happens if you use a 0.)

---

### Post by barryjohnwilliams on 2008-11-14
Brill - Thanks for that!  I hadn't noticed the speed of the NMEA messages - I was also wondering what the numbers meant.  The original place I found these commands was:  

[http://www.nabble.com/X301-Ericsson-Modul-f3507g-AT-Command-reference-td20152955.html](http://www.nabble.com/X301-Ericsson-Modul-f3507g-AT-Command-reference-td20152955.html)

No more information on that thread unfortunately.  

Barry

---

### Post by H.i.M on 2008-11-15
What about to report a bugreport on lauchpad.net about that?
A lot of people in the forums are complaining about the 5530.
It should be noticed by the networkmanager developers.
This seem not to be done with a little *.conf"-fix.

I want to buy a dell latitude E6400 with dell 5530 HSDPA Modem.
I hope this is fixed until ill get the NB.


Greetings h.i.m

---

### Post by alpha27 on 2008-11-18
Has been filed yesterday: [Network Manager detects but cannot connect with Dell 5530]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/299274/")

---

### Post by barryjohnwilliams on 2008-11-28
I doubt anything is going to happen on the NetworkManager front for a while as it doesn't appear it has had any work for a few weeks.  Since posting the original bug report on launchpad I've been trying a few different programs.  

**Vodafone Mobile Connect for Linux:**
A Vodafone sponsored project with Vodafone's branding written in Python.  Unfortunately doesn't support the Dell 5530 - but a python plugin could be written.  

**Wader:**
A fork of the Vodafone Mobile Connect with a different interface and a few more plugins - but no D5530.  Again I was going to start writing a plugin until I found:

**Umtsmon:**
This works with the Dell 5530 card, provides signal information, GPRS/3G state and also usefully a data allowance monitor.  Make sure you add yourself to the 'can connect to the internet with a modem' group so you don't have to be root to dial out with pppd.  I modified the umtsmonrc file in my home directory to use usb data ports and at ports that were compatible with the wvdial configuration I have.  I.e. /dev/ttyACM0 for AT and /dev/ttyACM1 for PPP.  The wvdial script I use has been modified to use /dev/ttyACM0 for the signal, on and off.  /dev/ttyACM1 is used just for connect and the GPS is run using /dev/ttyACM2.  

This way I can run wvdial and umtsmon complimentary so I can run scripts to start and stop the modem (and add them to the Gnome menu) - and still have full access to the GPS on /dev/ttyACM2.  

Additionally I have removed NetworkManager and replaced it with another program called Wicd.  Wicd connects to my wifi network almost instantly - particularly after a resume so it's better than NM that way too.  Removing NM has the advantage is doesn't nag you about finding a 3G card (which it can't use) everytime it runs.  

There is a repository for wicd ubuntu binaries on the download page at:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

A debian file for Umtsmon can be found here:  
[http://people.debian.org/~winnie/umtsmon/](http://people.debian.org/~winnie/umtsmon/)

I had to install Umtsmon from the command file using dpkg -i rather than via Gdebi as it didn't work.  

Good Luck - this way you don't have to wait for NM guys to implement Dell support!

---

### Post by ignally on 2008-12-01
hi barry,

could you post the step by step guide to connect to internet using dell 5530 hspa modem by using umtsmon including your umtsmonrc config. Your help will be greatly appreciated.thanks :)

best regards,

ignally

---

### Post by barryjohnwilliams on 2008-12-01
Certainly, I am writing one up now and will post it online soon.

---

### Post by barryjohnwilliams on 2008-12-01
Here is a Howto Document for [configuring a Dell 5530 WWAN 3G Card with Ubuntu 8.10 and UMTSMon]("http://www.bjw.me.uk/2008/12/howto-ubuntu-810-dell-5530-3gwwan-and.html").  

Let me know if it works or if you spot any errors or things I've missed.

---

### Post by barryjohnwilliams on 2009-03-12
I've updated my howto on the Dell 5530/Ericsson f3507g mobile broadband card.  Whilst there seems to be a little bit of chatter on the NetworkManager bug there doesn't seem to be much movement.  

I've written a python application which monitors this broadband card and automatically enables the radio if it is off (for example on first boot or resume) and monitors the signal strength, network operator and connection type (GPRS, 3G, 3G+) and stores the data to a file so other programs like conky can access and display this information.  

Whenever the network operator changes or the connection type changes, a notification is issued via python-notify which displays a nice message.  Useful if traveling through areas with patchy coverage!  

The scripts are all released under Creative Commons and the howto guide can be found here:

[http://www.bjw.me.uk/2009/03/dell-5530ericsson-f3507g-on-linux.html]("http://www.bjw.me.uk/2009/03/dell-5530ericsson-f3507g-on-linux.html")

---

### Post by mloskot on 2009-03-14
Thanks Barry for the update.

However, on my ThinkPad T400, I have just upgraded to Jaunty (9.04) and Network Manager works well with F3705G (Vodafone). So, the problem has been fixed and no longer exists for me.

Best regards,

---

### Post by djupsjob on 2009-04-28
I have a LG X110 with f3507g, and can confirm that the 3G modem works out of the box on Jaunty.

I've been trying to find out whether the radio is on constantly, or if it is turned on when Network Manager connects. There is no LED for the 3G modem on this machine, and haven't been able to find out what AT commands NM send to the modem. Is there anybody who knows when the radio is turned on?

---

