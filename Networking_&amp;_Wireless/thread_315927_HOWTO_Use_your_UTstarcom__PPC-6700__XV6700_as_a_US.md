---
title: "HOWTO: Use your UTstarcom / PPC-6700 / XV6700 as a USB modem"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by CRCarl on 2006-12-09
Alrighty &#8211; This took a little work to figure out, but I have been able to recreate the process on 6.06 and 6.10. Also works on Gutsy. Bluetooth support still eludes me but I am working on it.(Bluetooth works with Gutsy and the Dell MT355 BT adapter, plus the bluez tools out of the box.)  I am also working on setting up dnsmasq as a local dns server. 

This HOWTO is based a significant part on this HOWTO: [http://andrewtv.org/fedora-ppc6700]("http://andrewtv.org/fedora-ppc6700"). Big thanks. 

First &#8211; Start the Wmodem program on the phone and plug it in via USB. Run lsusb
```
~$ lsusb. 

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0bb4:00cf High Tech Computer Corp. SPV C500 Smart Phone
Bus 001 Device 001: ID 0000:0000
```

In this case the vendor id = 0bb4 and the product id = 00cf. Write down your vendor and product ids. Stop the Wmodem program and disconnect the phone. 

Second - Run
```

~$ sudo gedit /etc/rc.local
```
Add these lines above &#8220;exit 0&#8221; and below the comments &#8211; (of course use your own vendor and product ids.)
```

/sbin/modprobe ipaq vendor=0x0bb4 product=0x00cf
touch /var/lock/subsys/local
```
Save and close. 
```

~$ sudo /etc/rc.local start 

```
Lets test our work &#8211; 
```

~$ tail -n 0 -f /var/log/messages

```
Start the wmodem program again and plug the phone in. If the driver loaded the output should look like - 
```

Dec  9 19:08:22 laptop kernel: [17181341.432000] usb 1-1: new full speed USB device using uhci_hcd and address 3
Dec  9 19:08:22 laptop kernel: [17181341.620000] usb 1-1: configuration #1 chosen from 1 choice
Dec  9 19:08:22 laptop kernel: [17181341.620000] ipaq 1-1:1.0: PocketPC PDA converter detected
Dec  9 19:08:22 laptop kernel: [17181341.624000] usb 1-1: PocketPC PDA converter now attached to ttyUSB0

```
Excellent. Almost there. (If the driver didn't load, restart.)

We are going to use wvdial to start pppd and dial the phone. We start by creating a configuration file for wvconfig;

```
~$ gedit mydialer.conf
```

Copy and past this into the file - 
```

[Dialer Defaults]
Stupid Mode = on
Idle Seconds = 0
Carrier Check = no
Init1 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = #777
Password = "blank"
Username = "blank"
Modem = /dev/ttyUSB0
Baud = 460800
```


You may need to change the phone number and username/password, this setup works for SprintPCS.
Save and close. 

One last thing.
```

~$ sudo gedit /etc/ppp/options

```
Find the lines;
```

lcp-echo-interval 30
lcp-echo-failure 4
```

Change to;
```

#lcp-echo-interval 30
#lcp-echo-failure 4
```

Save and close. 

Lets give this a shot;

```
~$ sudo wvdial --config ~/mydialer.conf
```

When I connect it looks like this;

```
~$ sudo wvdial --config ~/mydialer.conf
Password:
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Dec  9 19:08:45 2006
--> Pid of pppd: 5889
--> Using interface ppp0
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
--> local  IP address 68.27.169.225
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
--> remote IP address 68.28.49.69
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
--> primary   DNS address 68.28.50.11
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
--> secondary DNS address 68.28.58.11
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
```

Good luck! Post any questions here. 

EDIT: If you want a desktop icon - Right click on the desktop, click "Create launcher".  Name it whatever you want, paste "gksudo wvdial --config ~/mydialer.conf" into the command line, pick an icon, click OK. All done!

Craig

---

### Post by gotmonkey on 2006-12-15
> **CRCarl said:**
> Alrighty – This took a little work to figure out, but I have been able to recreate the process on 6.06 and 6.10. Bluetooth support still eludes me but I am working on it. I am also working on setting up dnsmasq as a local dns server. 

This HOWTO is based a significant part on this HOWTO: [http://andrewtv.org/fedora-ppc6700]("http://andrewtv.org/fedora-ppc6700"). Big thanks. 

First – Start the Wmodem program on the phone and plug it in via USB. Run lsusb
```
~$ lsusb. 

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0bb4:00cf High Tech Computer Corp. SPV C500 Smart Phone
Bus 001 Device 001: ID 0000:0000
```

In this case the vendor id = 0bb4 and the product id = 00cf. Write down your vendor and product ids. Stop the Wmodem program and disconnect the phone. 

Second - Run
```

~$ sudo gedit /etc/rc.local
```
Add these lines above “exit 0” and below the comments – (of course use your own vendor and product ids.)
```

/sbin/modprobe ipaq vendor=0x0bb4 product=0x00cf
touch /var/lock/subsys/local
```
Save and close. 
```

~$ sudo /etc/rc.local start 

```
Lets test our work – 
```

~$ tail -n 0 -f /var/log/messages

```
Start the wmodem program again and plug the phone in. If the driver loaded the output should look like - 
```

Dec  9 19:08:22 laptop kernel: [17181341.432000] usb 1-1: new full speed USB device using uhci_hcd and address 3
Dec  9 19:08:22 laptop kernel: [17181341.620000] usb 1-1: configuration #1 chosen from 1 choice
Dec  9 19:08:22 laptop kernel: [17181341.620000] ipaq 1-1:1.0: PocketPC PDA converter detected
Dec  9 19:08:22 laptop kernel: [17181341.624000] usb 1-1: PocketPC PDA converter now attached to ttyUSB0

```
Excellent. Almost there. (If the driver didn't load, restart.)

We are going to use wvdial to start pppd and dial the phone. We start by creating a configuration file for wvconfig;

```
~$ gedit mydialer.conf
```

Copy and past this into the file - 
```

[Dialer Defaults]
Stupid Mode = on
Idle Seconds = 0
Carrier Check = no
Init1 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = #777
Password = "blank"
Username = "blank"
Modem = /dev/ttyUSB0
Baud = 460800
```


You may need to change the phone number and username/password, this setup works for SprintPCS.
Save and close. 

One last thing.
```

~$ sudo gedit /etc/ppp/options

```
Find the lines;
```

lcp-echo-interval 30
lcp-echo-failure 4
```

Change to;
```

#lcp-echo-interval 30
#lcp-echo-failure 4
```

Save and close. 

Lets give this a shot;

```
~$ sudo wvdial --config ~/mydialer.conf
```

When I connect it looks like this;

```
~$ sudo wvdial --config ~/mydialer.conf
Password:
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Dec  9 19:08:45 2006
--> Pid of pppd: 5889
--> Using interface ppp0
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
--> local  IP address 68.27.169.225
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
--> remote IP address 68.28.49.69
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
--> primary   DNS address 68.28.50.11
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
--> secondary DNS address 68.28.58.11
--> pppd: 0[0b][06][08]&#65533;[08][06][08]
```

Good luck! Post any questions here. 

Craig

Craig,
thanks for the guide. I just did a fresh install of 6.10 and updated to latest levels. Your guide worked like a charm.

Is there a way to launch the dialer without doing it from the command line?

---

### Post by rpasell on 2006-12-17
OK so I followed the instructions, but ran into issues pretty early on.

When I get here:
/sbin/modprobe ipaq vendor=0x0bb4 product=0x00cf
touch /var/lock/subsys/local

and run:

sudo /etc/rc.local start

It tells me I have no /subsys/local directory, which I don't.

any ideas?

---

### Post by paulsomm on 2006-12-27
Sweet!  Worked first time.  Thank you very much for this post :-)

---

### Post by alasdairyoung on 2007-01-10
> **rpasell said:**
> OK so I followed the instructions, but ran into issues pretty early on.

When I get here:
/sbin/modprobe ipaq vendor=0x0bb4 product=0x00cf
touch /var/lock/subsys/local

and run:

sudo /etc/rc.local start

It tells me I have no /subsys/local directory, which I don't.

any ideas?

If you don't have this directory, just create it.

sudo mkdir /var/lock/subsys
sudo chown root /var/lock/subsys

and try again - it should work at this point.

---

### Post by lcohen999 on 2007-01-10
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Jan 10 13:05:11 2007
--> Pid of pppd: 15478
--> Disconnecting at Wed Jan 10 13:05:12 2007
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

any idea what exit code 2 is?

---

### Post by lcohen999 on 2007-01-10
fixed it :)

---

### Post by commonplace on 2007-01-16
> **lcohen999 said:**
> fixed it :)

What was wrong? How did you fix it?

/Kevin

---

### Post by benone on 2007-01-18
Any gold IDEAS whats goin on with my HTC Hermes / MDA Vario II Smartphone ??

After: ~$ tail -n 0 -f /var/log/messages

Am getting only:
Dec  9 19:08:22 laptop kernel: [17181341.432000] usb 1-1: new full speed USB device using uhci_hcd and address 3
Dec  9 19:08:22 laptop kernel: [17181341.620000] usb 1-1: configuration #1 chosen from 1 choice


The other two lines which are important, are not displayed....
What should I do ?????
Dec  9 19:08:22 laptop kernel: [17181341.620000] ipaq 1-1:1.0: PocketPC PDA converter detected
Dec  9 19:08:22 laptop kernel: [17181341.624000] usb 1-1: PocketPC PDA converter now attached to ttyUSB0

Cant find ttyUSB0...

Wrrrrr

Help pls.

Benone

---

### Post by jared234 on 2007-01-23
my problem starts with: when wmodem is running the usb drive that it is pluged into says nothing is there.  My second problem is when i run the "sudo gedit /etc/rc.local, there seems to be a problem with the gedit command. ANY help would be appreciated, PLEASE.

---

### Post by jared234 on 2007-01-29
yo.  stillll looking for some helpful info on this subject. I'm not looking forward to paying for a copy of windows, but if that's what it takes then i'll do it.

---

### Post by CRCarl on 2007-02-07
Jared - 
    Couple of things - when WModem is running nothing will mount. The best way to see if Ubuntu has seen your modem is to run;

Before pluging the USB cable in;

```
sudo tail -n 0 -f /var/log/messages
``` 

then start Wmodem and plug the modem in. You should see something that says a Pocket PC has been connected. 

What error do you get with ```
sudo gedit /etc/rc.local
``` that is a pretty simple command, just enter you password and press enter.  This is assuming you are running the desktop version, with a GUI. If not use vi. 

Craig

---

### Post by calemus on 2007-02-23
:confused: howdy howdy...i have a vx6600 and have not once been able to sync with my pc,,,not cool because it's all i got. dont have bluetooth,, and cant get microsoft activ Sync to run or install on any buntu i have installed..i have tried every buntu so far. trying to not be discouraged.....any help would be apreciated.:(

---

### Post by captain_bogus on 2007-03-02
Nice job CRCarl!  This worked beautifully for me.  I'm using 6.10 Edgy, and a PPC6600.

Thanks!

--bog

---

### Post by lcohen999 on 2007-03-06
> **calemus said:**
> :confused: howdy howdy...i have a vx6600 and have not once been able to sync with my pc,,,not cool because it's all i got. dont have bluetooth,, and cant get microsoft activ Sync to run or install on any buntu i have installed..i have tried every buntu so far. trying to not be discouraged.....any help would be apreciated.:(

This has nothing to do with sync'ing just using it as a modem.

I would look at a SyncML client for your syncing, I don't think Linux can do it natively.

---

### Post by JLAudioFan on 2007-04-27
Carl, you get a gold star for this one!!!  :KS 

Worked GREAT!  I'm posting this through my phone !

Now, I wonder if I can somehow get it to show up in the network manager applet ;)

EDIT:  
I tried to add in the info in the modem section of network-manager;  however, it won't let me save the connection without putting something in for username....  Sprint is my ISP, so there is no user/pass...   Any idea where the file is stored with this connection information, so I can gedit it and remove the username?

---

### Post by gotmonkey on 2007-06-07
Did you ever find a solution for this? I just re-activated my xv6700 and created the connection in Fiesty Fawn. I would love to have it working straight out of network manager.




> **JLAudioFan said:**
> Carl, you get a gold star for this one!!!  :KS 

Worked GREAT!  I'm posting this through my phone !

Now, I wonder if I can somehow get it to show up in the network manager applet ;)

EDIT:  
I tried to add in the info in the modem section of network-manager;  however, it won't let me save the connection without putting something in for username....  Sprint is my ISP, so there is no user/pass...   Any idea where the file is stored with this connection information, so I can gedit it and remove the username?

---

### Post by WiseYoda on 2007-06-10
Confirmed working on Ubuntu 7.04 and PPC-6700 from Sprint.  No additional steps needed.

Thanks!

---

### Post by snyperof1 on 2007-06-10
I have a xv6700 with verizon and ubuntu 7.04.
followed the guide but when i run 

```
sudo wvdial --config ~/mydialer.conf
```

I get this:

```
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT3165296770
--> Waiting for carrier.
ERRORR
--> Invalid dial command.
--> Disconnecting at Sun Jun 10 21:36:11 2007
```

I dial a local AT&T dial-up number and use my AT&T user name and password in mydialer.conf
here's what it looks like:

```
[Dialer Defaults]
Stupid Mode = on
Idle Seconds = 0
Carrier Check = no
Init1 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = 3165296770
Password = *********
Username = ************
Modem = /dev/ttyUSB0
Baud = 460800
```

what is giving me the invalid dial command error?

---

### Post by _DjScrew_ on 2007-06-11
anyone with a treo tried following this guide? 

i'm getting
```
mike@Ubuntu~$ tail -n 0 -f /var/log/messages
Jun 11 05:27:19 Ubuntu kernel: [  687.552000] usb 2-1: new full speed USB device using uhci_hcd and address 4
Jun 11 05:27:21 Ubuntu kernel: [  689.528000] usb 2-1: new full speed USB device using uhci_hcd and address 5
Jun 11 05:27:21 Ubuntu kernel: [  689.696000] usb 2-1: configuration #1 chosen from 1 choice
 
```
instead of 
```
Dec  9 19:08:22 laptop kernel: [17181341.432000] usb 1-1: new full speed USB device using uhci_hcd and address 3
Dec  9 19:08:22 laptop kernel: [17181341.620000] usb 1-1: configuration #1 chosen from 1 choice
Dec  9 19:08:22 laptop kernel: [17181341.620000] ipaq 1-1:1.0: PocketPC PDA converter detected
Dec  9 19:08:22 laptop kernel: [17181341.624000] usb 1-1: PocketPC PDA converter now attached to ttyUSB0
```

---

### Post by Topa_1 on 2007-06-13
***[CENTER][SIZE="3"]GREAT post works on alltel with no mods[/SIZE][/CENTER]***
Ok now I really love ubuntu my friend convinced me to try it and this was my biggest fear is not being able to wast time at work on my laptop anymore with out finding a hot spot the main reason I have one I am on ubuntu and ubuntu forums  for life Thanks alot now on to converting the wife too\\:D/

---

### Post by joex on 2007-06-13
THANK YOU!!!!!!
iT ACTUALLY SEEMS FASTER THAN WINBLOWZ!
Cant thank you enough.
are you aware of any development on the synce front?  I'd love it if I could keep my (too expensive) phone and sync data.  I understand the synce has not been working for this ppc6700.  know any different?

---

### Post by wmatthews on 2007-07-10
Excellent guide guys.

---

### Post by lumix on 2007-07-18
for this post, that is.  It may very well be the first Linux-related endeavor I've undertaken that actually worked--as directed, the first time.  Seriously, nothing in Linux EVER works as it should (at least not without undertaking a new hobby for it), but this thank you is being relayed through my PPC6700.

Thanks.

---

### Post by Ocyberbum on 2007-07-31
it works on my dell inspiron 9300 running the wubi install 3.5.6 (KDE) I had to use kate to edit but its working, i just ordered a 100gb hard drive to install a full version on my laptop, this is the first time i have put a distro on that gave me wifi and let me used my phone..this is awesome, and it seems faster, Has anyone found an easy way to start it with out using command line? \\:D/

---

### Post by Ocyberbum on 2007-08-10
Have a quick question, Everything worked fine when i first run the script, but now for some reason i can get my messengers to connect to the internet... Gaim says looking for network but i can browse with firefox.. any ideas?


thanks
Billy

---

### Post by loudnlownoma on 2007-08-17
Looking good here too!  HP Pavilion zd8000 series laptop, Samsung i730 w/ Verizon, on kubuntu 7.0.4.  Also, my phone currently has WM2003, not WM5.  Plugged it in and ran through the install procedure above, just skipping the steps to enable WinModem and it worked great for me!  Posting through it now!

---

### Post by JeSTeR7 on 2007-08-30
OK, everything looks good when I follow these steps, except actually connecting to the internet!

I can see that after running the wvdial program that everything logs in correctly.  ifconfig reports that it does in fact have an IP address, but when I try to open pages in firefox I immediately get an error that it cannot connect to the server.

Any ideas at all?

---

### Post by CRCarl on 2007-08-30
Paste the output from wvdial here and I will look at it. 

Also, what happens when you run 

```
dig yahoo.com
```

>
CRCarl

---

### Post by islandwebs on 2007-10-05
Excellent explanation.

One question is I believe unanswered:

How would you make a desktop shortcut to start the connection rather than going to the terminal and typing sudo wvdial --config ~/mydialer.conf

---

### Post by gavanaxe on 2007-10-09
Amazing!

I'm brand new to ubuntu, actually Linux all together.

Two days ago I installed debian and today I wiped it out to install ubuntu.

So refreshing to break free from MS...

Anyways, just wanted to give kudos. I don't know much about any of the many flavors of Linux but I was able to follow your forum and bingo my PPC-6700 is working already.

First hurdle was a piece of cake. Thanks for all the shared info... I think I'm gonna like this community...!

Beggers can't be choosers, but is there any way to find, or maybe create, a package that would perform the standard installation for my PPC-6700 on ubuntu? I only ask because I work for a computer retail store and I want to use Linux as an OS alternative to MS. But, that would require me to be able to quickly/briefly add my phone to each system for temporary internet connectivity on the road. This would be a very tedious task unless I had some sort of "driver installer package" ???

Just curious!?

Thanks,
-Knight

---

### Post by loudnlownoma on 2007-10-12
> **gavanaxe said:**
> 
Beggers can't be choosers, but is there any way to find, or maybe create, a package that would perform the standard installation for my PPC-6700 on ubuntu? I only ask because I work for a computer retail store and I want to use Linux as an OS alternative to MS. But, that would require me to be able to quickly/briefly add my phone to each system for temporary internet connectivity on the road. This would be a very tedious task unless I had some sort of "driver installer package" ???

Just curious!?

Thanks,
-Knight

Not too much of an advanced user myself, but there isn't much that would need to be loaded, outside of the mydialer.conf file, which should be about the same on each PC, and would be easily transferable.  The vendor/hardware id should remain the same, and it would just be a matter of adding the info the rc.local file and copying the mydialer.conf over.  I suppose an automated script would be a little simpler, but I've had some fun trying to get my ATI video card and wireless working, not to mention PC issues otherwise, so I've had a few tries to get this up and going and can almost set it up on a fresh install without looking at the guide at all now...lol

---

### Post by zackleys on 2007-10-25
Hello,
Did anyone ever get to answer the question regarding messenger and using the 6700 as a modem. I confirm that Gaim just says waiting for network connection although i am connected to the internet. Also i have the same issue with Evolution Mail. Unable to click on send/receive. Any help with this would be appreciated. Thnx

---

### Post by zackleys on 2007-10-25
I think i answered my own question regarding the messenger and evolution issue not connecting but still able to browse the internet, After connecting to the ppc-6700, click under the Manual Netowrk Configure icon in the system tray, i selected Manual Configuration, entered admin password selected wired connection, and under configuration selected **Local Zerofonf network IPv4 LL** and clicked OK. Now my messenger and Evolution now work while connected to the PPC-6700.  But im not sure if i have to change this back when i get plugged into my home network with the wire. Hope this helps others.

---

### Post by zackleys on 2007-10-25
Someone also asked about creating a desktop icon for the script to run the dialer, i saved mine to a text document and saved it to my desktop as a .sh file, from there just configure it to execute as a program and run in a terminal windows.

---

### Post by jasonabate on 2007-11-02
In case it helps others, these instructions worked perfectly for me with an AT&T Tilt running Windows Mobile 6 and a laptop running Gutsy.  The only thing I had to do differently was change the phone number, username and password to work with Cing^h^h^h^hAT&T.  

My wvdial script is:
[INDENT][FONT="Courier New"][Dialer Defaults]
Stupid Mode = on
Idle Seconds = 0
Carrier Check = no
Init1 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = *99#
Password = "CINGULAR1"
Username = "ISP@CINGULARGPRS.COM"
Modem = /dev/ttyUSB0
Baud = 460800
[/FONT][/INDENT]

Thanks for the instructions, have been banging my head against this for a couple of days, messing around with Bluetooth, etc.  Also, for the record I have been able to get dialup working via XP running inside VirtualBox as well.  Feel free to contact me if you need help!

-jason

---

### Post by CRCarl on 2007-11-08
Islandwebs - 
   I have updated the HOWTO with these directions per your request. 

Craig

---

### Post by wallybman on 2007-12-25
Umm, I think I might have made a slight mistake...  I got a brand new 6700 in the mail today to replace the one that is dead on my counter.  Six months ago, the external speaker died, last week, the phone radio died, and while waiting for the new one to come in to replace it, the wifi radio died, and it stopped getting past the 2nd splash screen.  Here is my problem: As soon as I got the new one in today, I built a custom rom(using the kitchen) and flashed the brand new phone. Everything turned out just fine, but I need to know if anyone has used a wm6 flashed 6700 as a wireless modem for a rig running Ubuntu... My old laptop won't run xp, but it will run fiesty fawn like a dream, so my only hope of having internet on the go on the thing is through Ubuntu 7.04... 

( [http://forum.ppcgeeks.com/forumdisplay.php?f=53](http://forum.ppcgeeks.com/forumdisplay.php?f=53) )

I can't fire up this laptop at the moment to test it, seeing as how my battery gave up the ghost long ago, and my charger ate itself (new one on the way). Yeah, I know, my lucky week when it comes to electronics, right?

Anyways, any help would be appreciated.

p.s. My laptop CAN run xp, its just that I REFUSE to spend another $100 on ANOTHER copy of xp, when Ubuntu can get the job done just as well, if not better.

---

### Post by Tux.Ice on 2008-01-16
```
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Err>: Cannot open /dev/ttyUSB0: No such file or directory
WvDial<Err>: Cannot open /dev/ttyUSB0: No such file or directory
WvDial<Err>: Cannot open /dev/ttyUSB0: No such file or directory
```


thats what wvdial gives me- can any one help?

---

### Post by Tux.Ice on 2008-01-17
**bump**

---

### Post by anystupidname on 2008-01-17
> **Tux.Ice said:**
> ```
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Err>: Cannot open /dev/ttyUSB0: No such file or directory
WvDial<Err>: Cannot open /dev/ttyUSB0: No such file or directory
WvDial<Err>: Cannot open /dev/ttyUSB0: No such file or directory
```


thats what wvdial gives me- can any one help?

I'm seeing the same thing as benone and tux.ice

Does this have something to do with udev changing the device names?
I tried fiddling with my wvdial conf file substituting what I thought the device might be.

my device is a HTC PPC-6800 (sprint mogul)

uname -a
Linux sexy 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
(this is linux mint 3.0 main I think)

lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 020: ID 0bb4:0b04 High Tech Computer Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

ls -hasl /dev/ | grep -i usb
   0 crw-rw----  1 root   root    189,   0 2008-01-11 18:48 usb1
   0 crw-rw----  1 root   root    189, 128 2008-01-11 18:48 usb2
   0 crw-rw----  1 root   root    189, 256 2008-01-11 18:48 usb3
   0 crw-rw----  1 root   root    254,   0 2008-01-11 18:48 usbdev1.1_ep00
   0 crw-rw----  1 root   root    254,   1 2008-01-11 18:48 usbdev1.1_ep81
   0 crw-rw----  1 root   root    254,   2 2008-01-11 18:48 usbdev2.1_ep00
   0 crw-rw----  1 root   root    254,   3 2008-01-11 18:48 usbdev2.1_ep81
   0 crw-rw----  1 root   root    254,   6 2008-01-17 20:07 usbdev2.20_ep00
   0 crw-rw----  1 root   root    254,   9 2008-01-17 20:07 usbdev2.20_ep03
   0 crw-rw----  1 root   root    254,   7 2008-01-17 20:07 usbdev2.20_ep81
   0 crw-rw----  1 root   root    254,   8 2008-01-17 20:07 usbdev2.20_ep82
   0 crw-rw----  1 root   root    254,   4 2008-01-11 18:48 usbdev3.1_ep00
   0 crw-rw----  1 root   root    254,   5 2008-01-11 18:48 usbdev3.1_ep81

as you can see above there is no /dev/ttyUSB anything

please help?

---

### Post by loudnlownoma on 2008-01-18
Sometimes mine will do that if I remove the USB and reconnect it, or remove the phone from the cradle.  Basically, it just means it doesn't see the phone on that port.  To change, edit the wvdial script where it says "modem=/dev/ttyUSB0" and change it to USB1, USB2, etc - as reported by the tail command you run when connecting the USB in the guide.

---

### Post by takmsdsm on 2008-04-23
I get this error:
> 
alex@geek:~$ sudo wvdial --config ~/mydialer.conf
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
--> Sending: ATQ0
--> Re-Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
--> Modem not responding.


I noticed that WvDial is a different version. I am using a PPC6700 with WM6.1 installed. any ideas?

---

### Post by takmsdsm on 2008-04-23
wasw able to get it working using this guide.

note: this is only for 6700s using WM6 and 6.1 i believe

[http://forum.xda-developers.com/showthread.php?t=340747](http://forum.xda-developers.com/showthread.php?t=340747)

---

### Post by arrrghhh on 2008-04-25
So this thread helped me a lot to tether my phone... just a few things that didn't work quite right.  Not sure if that's because I'm on Kubuntu or because I'm using 8.04 (was on 7.10... works the same).  The problem I'm running into is at EXACTLY 2:30 into the data session (2 min 30 sec) kPPP disconnects.  Every single time!  I'm not sure if this is Sprint booting my device off or what... somehow I doubt it's the phone or Sprint, and I think it's more Kubuntu/kPPP.  I tried to tether my phone under WinXP and failed miserably... So at least it tethers and I can access the internet, but every 2:30 disconnect is kind of annoying... Any help is greatly appreciated!  Thanks.

---

### Post by .chaos on 2008-06-13
> **benone said:**
> Any gold IDEAS whats goin on with my HTC Hermes / MDA Vario II Smartphone ??

After: ~$ tail -n 0 -f /var/log/messages

Am getting only:
Dec  9 19:08:22 laptop kernel: [17181341.432000] usb 1-1: new full speed USB device using uhci_hcd and address 3
Dec  9 19:08:22 laptop kernel: [17181341.620000] usb 1-1: configuration #1 chosen from 1 choice


The other two lines which are important, are not displayed....
What should I do ?????
Dec  9 19:08:22 laptop kernel: [17181341.620000] ipaq 1-1:1.0: PocketPC PDA converter detected
Dec  9 19:08:22 laptop kernel: [17181341.624000] usb 1-1: PocketPC PDA converter now attached to ttyUSB0

Cant find ttyUSB0...

Wrrrrr

Help pls.

Benone

try USB1 in mydialer.conf

---

### Post by .chaos on 2008-06-13
my problem is that i keep getting a hangup on the other end.  says a modem hung up.

i'm on cingular, *99# is the number, pw= CINGULAR1, user= [email]ISP@CINGULARGPRS.COM[/email]

:(

---

### Post by .chaos on 2008-06-13
also, is there a way to use the tilt's wifi instead?  card reader is dead on this lappy.  don't have a wifi card anyway.

---

