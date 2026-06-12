---
title: "Modem won't connect to my ISP"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Dan Flanagan on 2010-02-04
Hello, 
I have been using Windows since 1990 and recently installed Ubuntu on my computer.  Everything works OK with no issues with installing Ubuntu.  My machine is a 2.66 GHZ Celeron with Windows XP Professional and Ubuntu installed with dual boot.  512MB RAM, 80G HD.

Now, I am trying to get the internal modem, a PCI INTEL536EP to connect to my isp.  After reading many help files and posts I have installed the driver and wvdial and configured it for my isp.  I initially had dependency problems with wvdial but seem to have resolved them with the correct deb package that contained the additional files.

When I run wvdial, all starts normally.  I hear a dial tone, the phone number is dialed, I can hear the connection interrogation etc, but when it connects it immediately disconnects and says "carrier lost" and prompts for my username which I have entered in wvdial.conf.  After I enter my username it says it has "timed out".  NOTE: I am not sure I have saved the wvdial.conf in the correct folder, it's in two different folders.

I have run wvdiaconf and it tells me it cannot find any serial ports.  In windows the modem uses COM3, not sure which IRQ. I think I saw somewhere in the windows device manager the UART uses IRQ16 but I need to verify this.

Also, I have installed GNOMEppp and tried setting it up but it does not detect a modem on any serial port ttys0 to ttys3. I have run a command from terminal with does detect the modem... so I am confused, it seems my Linux system cannot find the modem serial port.

Any hints on what I'm doing wrong, or need to do, would be appreciated...:razz:

---

### Post by Silvertones on 2010-02-04
well i'm using an external US Robotics modem. I couldn't get it to work at first. I discovered a bug report that in order for it to work I needed to uninstall "modemmanager" in synaptic.

---

### Post by Bartender on 2010-02-04
Hi, Dan -
You got further with the Intel modem than I ever did.  I've tried a couple of times to make things go with a 536 modem and failed miserably.

Can you attach a log from wvdial?  Anything showing how far you get before it quits?

On the one hand, it sounds like your ISP isn't accepting your password.  But the part about "timed out" makes me wonder if the 536 is almost, but not quite, configured properly.

I don't like messing with wvdial directly.  I've gotten in the habit of using pppconfig to get online, then asking Synaptic to Search for gnome-ppp.  Gnome-ppp is a graphical front-end for wvdial.  In other words, you're looking at gnome-ppp on your screen, and gnome-ppp deals with wvdial so you don't have to.

If you've got the time, please take a look at my long-winded Dial-up Redux post, link below.  Might give you some ideas.

If you have access to broadband, it might be worthwhile to download Puppy Linux, which has much better modem detection than Ubuntu.  You can install Pup to a USB thumb drive, then boot from the thumb drive.  If you're really new to Linux that might be a little confusing.

Silvertones refers to the good old US Robotics 5686 Sportsters.  These are IMO the best, easiest, way to get online with Linux.  And you should get a faster, more robust connection too.  But there are some new modems available, such as the [Rosewill RNX56]("http://www.newegg.com/Product/Product.aspx?Item=N82E16825164005"), which might actually be a better solution.  I don't know because information is spotty and I haven't bought one to find out for myself.  

Unless I'm mistaken, you don't need to worry about the modem-manager bug he refers to unless you're running Ubuntu 9.10, and an external modem connected via USB interface.

I yak about all of this in the Dial-up Redux thread.

---

### Post by Silvertones on 2010-02-04
For $50 I got the US Robotics modem and it is better then the built in. I gave up real quick on trying to get that thing going. As an aside most new computers don't come with modems so, if like me, your stuck with dialup because of were you live it can be used on a new machine with USB. Even if you also use Windows. The Roswill is half the price but I didn't find the reviews that encouraging for Linux. I installed GNOME PPP and it set it up in abt 3 seconds. Done.

---

### Post by Dan Flanagan on 2010-02-04
This is what I see when I try to connect...
 
 
[EMAIL="dflanagan@ubuntu:~$"]dflanagan@ubuntu:~$[/EMAIL] wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT4432444055
--> Waiting for carrier.
ATDT4432444055
CONNECT 38666
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT4432444055
--> Waiting for carrier.
User Access Verification
Username: 
Username: [EMAIL="danflan@isp.com"]danflan@isp.com[/EMAIL]
% Username:  timeout expired!
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT4432444055
--> Waiting for carrier.
ATDT4432444055
NO DIALTONE
--> No dial tone.
--> Disconnecting at Thu Feb  4 19:41:03 2010
[EMAIL="dflanagan@ubuntu:~$"]dflanagan@ubuntu:~$[/EMAIL] [EMAIL="danflan@isp.com"]danflan@isp.com[/EMAIL]
[EMAIL="danflan@isp.com"]danflan@isp.com[/EMAIL]: command not found
[EMAIL="dflanagan@ubuntu:~$"]dflanagan@ubuntu:~$[/EMAIL]

---

### Post by audiomick on 2010-02-04
Dan, you seem to have accidently started a new thread with exactly the contents of the last post.

[http://ubuntuforums.org/showthread.php?t=1398671](http://ubuntuforums.org/showthread.php?t=1398671)
Maybe you would like to edit it empty and put a solved tag on it to stop people from answering in two different threads.

---

### Post by Bartender on 2010-02-04
Here's what a successful connection looks like, just for comparison sake:

```
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: AT&F1E0Q0V1&C1&D2S0=0
AT&F1E0Q0V1&C1&D2S0=0
OK
--> Sending: ATS7=60S19=0M1&M4&K1&H1&R2&I0B0X4
OK
--> Modem initialized.
--> Sending: ATM1L1DT*70, 8074090
--> Waiting for carrier.
CONNECT 36000/ARQ/V92/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
\nWelcome to the Intarweb
Login: 
--> Looks like a login prompt.
--> Sending: XXXXXXX@frys.com
XXXXXXX@frys.com
Password: 
--> Looks like a password prompt.
--> Sending: (password)
    Entering PPP Session.
    IP address is 69.41.142.39
    MTU is 1524.
--> Looks like a welcome message.
--> Starting pppd at Thu Feb  4 18:48:32 2010
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 10506
--> Using interface ppp0
--> local  IP address 69.41.142.39
--> remote IP address 69.41.141.5
--> primary   DNS address 64.136.173.8
--> secondary DNS address 64.136.164.66

```

I XXX'ed out my username, everything else is unadulterated.  I don't worry about the "pap and chap secrets flaky" stuff - the connection is as fast or faster than Windows.

I'm NOT an expert at reading these logs.  But it looks to me like you're doing OK right up til "Connected, but carrier lost".  isp.com claims to be compatible with Linux.  

Have you gone back to your wvdial configuration and made absolutely sure that the username/password/PAP/DNS settings are correct?  You can log in to this ISP in Windows, right?

I'm suspicious of all winmodems so I'd be inclined to think that's where your troubles lie.  But I'm biased.

Have you tried configuring a dialer in good old pppconfig instead of wvdial?

---

