---
title: "Help with Dialup?"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by mvelte54 on 2010-05-15
I absolutely love Ubuntu and have recently updated my machine C-3PO, to Lucid Lynx, my other machine, R2D2 is still in Karmic Koala mode. I have a netbook that I take every where with me and I have just upgraded from XP home edition to UNR Karmic Koala. I purchased a Zoom external modem for when I can't get a wireless connection. 
Here's my problem, I've installed gnome-ppp as well as wvdial and I have it set up to connect to an internet provider but when I try it doesn't see the modem. If I hook up a wired connection no problem, wireless no problem. 
I have installed the driver that came with the modem with no new results.

To be honest it has been many years since I have messed with dial up what am I doing wrong? Should the wireless internet connection be disabled first? (It currently is not hooked to any wireless I am just seeing my neighbors secure connections)
Or maybe tell me where to look?

Modem: Zoom 56k USB Modem series 1063
Netbook: Dell Inspirion mini
ISP: Dialinfree

---

### Post by lkraemer on 2010-05-15
Try having the modem unplugged and Open a Terminal Window:
```

lsusb

```
Then plug in the modem, wait a couple of minutes, and repeat the command.
```

lsusb

```
If the modem is detected there should be a change.
Post the two outputs.

How did you install the drivers?  Are you using ndiswrapper?
I don't know of any other way, unless there are Linux Drivers provided.

Did you configure wvdial and pppconfig?

lk

---

### Post by mvelte54 on 2010-05-15
[lkraemer]("http://ubuntuforums.org/member.php?u=365139")

Thanks for the reply. I installed the driver from the cd which I copied to a USB and installed it that way. I also tried pppconfig all to no avail. I just tried lsusb and waited a minute plugged it in again with the same results file attached below:

  	 	 	 	 	 	  ace@Ewok:~$ lsusb  
 Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device  
 Bus 001 Device 003: ID 174f:1403 Syntek 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 002: ID 0d62:0530 Darfon Electronics Corp.  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 ace@Ewok:~$ lsusb  
 Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device  
 Bus 001 Device 003: ID 174f:1403 Syntek 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 002: ID 0d62:0530 Darfon Electronics Corp.  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 002: ID 0803:3095 Zoom Telephonics, Inc.  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I'm going to attempt ndiswrapper next.
Unless when i transfered the file from the cd to the USB it was corrupted somehow.

---

### Post by mvelte54 on 2010-05-15
I just noticed:

  	 	 	 	 	 	  Bus 003 Device 002: ID 0803:3095 Zoom Telephonics, Inc. 



So it does see it now and I just installed ndiswrapper I'll reboot and see what happens.

---

### Post by lkraemer on 2010-05-15
First thing is you can't just install the Windows files in Linux.
But, there is a way to use the Windows 32 bit or 64 Bit Drivers
with ndiswrapper.  But, in your case I'd suggest removing ndiswrapper
and following the information in the posting referenced below:

[http://forum.eeeuser.com/viewtopic.php?id=7848&p=1](http://forum.eeeuser.com/viewtopic.php?id=7848&p=1)

If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. If memory serves me correctly the command is:
```

sudo ndiswrapper -e xxxx

```
where xxxx is the name of the driver you installed.
This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.

To remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```
Remove from startup file by editing:
```

sudo nano /etc/modules

```
to remove ndiswrapper.

Hopefully you only installed ndiswrapper with Synaptics.  If so mark it
for Complete Removal, and apply.

Then follow the information for your Modem above.
You should get it working.

lk

---

### Post by mvelte54 on 2010-05-16
[I]lkraemer
*Thanks again for the response. The* [/I]Modem *[I]I have is*[/I]: Zoom 56k USB Modem model #3095 that is compatible with WinDoze, Mac and Linux. The drivers I installed were for Linux. When I open Synaptic to install ndiswrapper I found the driver is listed as installed, weird I know if I knew it was listed there I could have saved my self alot of trouble. 
I will attempt to remove ndiswrapper and the driver module and start over. 

I've been spoiled, it's been so long since I've had to dial up I can't even remember what or how to do it.

---

### Post by lkraemer on 2010-05-16
Well, if the drivers are for Linux, why not try them and see if it works.
You may just have to go to SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS
and enable them.  Then  you will need to either use wvdial or gnome-PPP
to dialout.
[B]
SET UP PAP/CHAP[/B]

Locate your userlogin, password, Dialup Provider Info, Phone Number,
and what your ISP uses (PAP or CHAP)

Open a Terminal Window and run the following:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically, you just answer the questions
that are presented. You can delete a configuration and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppconfig

```
pap-secrets file contains:
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#       *       password
"yourusername" provider "yourpassword"

```
And the file is located at:
```

/etc/ppp/pap-secrets

```
Use pppconfig to create a modified file or edit the file with:
```

sudo nano /etc/ppp/pap-secrets

```

**REMOVE MODULES or BLACKLIST MODULES:**
You may have to remove other modules depending on what lsmod shows:......example only.....
What you will REMOVE depends on what you post as output from your lsmod
command.

**EXAMPLE ONLY:**
If lsmod shows module b43 and others installed you will
need to blacklist them.  You may have to remove the following
depending on what lsmod shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```
You can use:
```

sudo nano /etc/modprobe.d/blacklist.conf

```
and add the necessary modules to blacklist.


**SETUP WVDIAL:**

Now ppp is setup and the Drivers are loaded, you will need to set up wvdial.

In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file that is something like this,
but your modem and some of your parameters may be slightly different
depending on what wvdial detects.
Your PhoneNumber, LoginName, and PassWord will be what you use.
The Modem type ....as in Modem = /dev/ttyACM0 should be determined
by wvdial......hopefully.....
```

sudo nano /etc/wvdial.conf (you may need to edit/add/modify a few things...)

```
wvdial.conf contains:
```


[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```
You might want to double check the following settings:
Checking settings of: /etc/ppp/options
```


asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

```
Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
If wvdial gives you an error try:
```

sudo wvdial /etc/wvdial.conf

```
You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny
characters) and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN.....just minimize it) You may have to uncheck
the box marked OFFLINE when you open your browser to make it online. Surf, then
terminate the open session with CNTL C in the open terminal window where you
initiated wvdial.

If your configuration is wrong, it will disconnect in a few seconds because it
won't be able to authenticate properly......

wvdial.conf info:
[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf)

PPP HOWTO:
[http://tldp.org/HOWTO/PPP-HOWTO/index.html](http://tldp.org/HOWTO/PPP-HOWTO/index.html)

PAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1034.html](http://tldp.org/HOWTO/PPP-HOWTO/x1034.html)

CHAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1053.html](http://tldp.org/HOWTO/PPP-HOWTO/x1053.html)

Setting up PPP Manually
[http://tldp.org/HOWTO/PPP-HOWTO/manual.html](http://tldp.org/HOWTO/PPP-HOWTO/manual.html)

MORE REF's:
[http://www.ubuntugeek.com/setting-up...in-ubuntu.html](http://www.ubuntugeek.com/setting-up...in-ubuntu.html)
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[https://help.ubuntu.com/community/Di...to/SetUpDialer](https://help.ubuntu.com/community/Di...to/SetUpDialer)
osdir.com/ml/ubuntu.doc/2005-04/pdfuHGgEItwtF.pdf

[https://wiki.edubuntu.org/DialupModemHowtoOld](https://wiki.edubuntu.org/DialupModemHowtoOld)

wvdial info:
[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)
[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)
[http://tldp.org/HOWTO/PPP-HOWTO/x314.html](http://tldp.org/HOWTO/PPP-HOWTO/x314.html)
[http://www.squarebox.co.uk/cgi-squar.../wvdial.conf.5](http://www.squarebox.co.uk/cgi-squar.../wvdial.conf.5)

Finally, when wvdial is working you can Download & Install
Gnome-PPP and then configure/set up Gnome-PPP.

When you get everything working, I'd suggest backing up the pap-secrets,
chap-secrets, and wvdial.conf files....just in case.
You can use:
```

cd /
cd /etc/ppp
sudo cp pap-secrets pap-secrets.sav
sudo cp chap-secrets chap-secrets.sav
cd ..
cp wvdial.conf wvdial.sav

```
to save the backup files.

Once wvdial is working Install Gnome-PPP and configure it so you can
Connect from the GUI.

lk

---

### Post by mvelte54 on 2010-05-16
lk you are the best!!!
There is enough information here to make my head hurt... 
I installed the latest driver for my modem which is "dgcmodem 1.06"
I have removed ndiswrapper and also gnome-ppp. I have installed gppp and went in and changed the settings for wvdial. When I click on gppp it comes up as wvdial and that it is already on? but still no access. I am going to figure this out one way or another, and with your expert guidence it shouldn't take to long. I am off to my secret laboratory, I will post my failures as well as my successes. 
Any other suggestions please pass them along everything helps.

---

### Post by lkraemer on 2010-05-16
I wouldn't try gppp.  Just use wvdial for now and get it configured by
running the configuration command that was posted.  Then after wvdial
locates the modem, edit the file to add your personal information like
name, pwd, phone number etc.  Then try making wvdial dial and connect.
If it stays connected .......SUCCESS!  Then open Firefox and make sure
that under FILE -> WORK OFFLINE is NOT Checked.  You should be able to
surf.  You WILL have to leave the Terminal Window OPEN where you started
wvdial.......until you finish surfing.  Then just open that terminal window
and type CNTL C to exit the connection, and then you can close the window.

After this is all functional, re-connect and download & install Gnome-PPP.
Setup Gnome-PPP and then you can connect from the GUI.  ZIT ZOT....DONE!!

lk

---

### Post by mvelte54 on 2010-05-17
lk
Just a little report on my progress. I had it working and was on line for about 20 minutes. This all through the terminal I then typed in CNTL C then hit enter to exit and didn't notice anything happening, i.e. I don't know if I was still connected or not. I typed in cntl c then hit enter to exit, nothing I then did CNTL C then hit enter to exit again but saw nothing happening so I just shut the terminal. I then went in to check the wvdialer settings posted below:

  	 	 	 	 	 	  [Dialer Defaults]  
 Init1 = ATZ  
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0  
 Modem Type = USB Modem  
 ISDN = 0  
 New PPPD = yes  
 Phone = isp/phone/#  
 Modem = /dev/ttyACM2  
 Username = my/user/name  
 Password = my/password 
 Baud = 460800  
 

 [Dialer mdsl]  
 Init = ATZ  
 Stupid Mode = on  
 Phone = isp/phone/#  
 New PPPD = yes  
 Modem = /dev/ttyUSB0  
 Username = my/user/name  
 Password = my/password 
 Baud = 9216000 



I then went in to save all the settings and got this:


   	 	 	 	 	 	  ace@Ewok:/$ cd /etc/ppp  
 ace@Ewok:/etc/ppp$ cp wvdial.conf wvdial.sav  
 cp: cannot stat `wvdial.conf': No such file or directory  
 ace@Ewok:/etc/ppp$ cd ..  
 ace@Ewok:/etc$ cp wvdial.conf wvdial.sav  
 cp: cannot create regular file `wvdial.sav': Permission denied  
 ace@Ewok:/etc$


However I had no problems saving both the pap and chap settings.
Then I installed gnome-ppp and went through and set up all the settings and when I tried to connect nothing... can't find modem. So I have uninstalled gnome-ppp and wvdial and I am going to start over from scratch again.


When I connected the first time through the terminal I got 12 pages of what was happening I'll spare you the boring details as 1-12 are all the same thing:


   	 	 	 	 	 	  --> Unable to run /usr/sbin/pppd.  
 --> Check permissions, or specify a "PPPD Path" option in wvdial.conf.  
 --> Don't know what to do!  Starting pppd and hoping for the best.


But it did finally connect with no help from me.


If there is anything that stands out to you please point them out to me. I am a newbie of the greenest kind.
Thanks again for all your help.

---

### Post by mvelte54 on 2010-05-17
Whoopsie! Ha Ha! I was supposed to _press_ Ctrl then C not _type_ CNTL C. That would explain why the modem is no longer seen. Back the laboratory...

---

### Post by lkraemer on 2010-05-17
Well, it looks as if you are un-installing and installing for no good reason.  You need to slow down, print out the instructions I previously
posted, and do one thing at a time.

For example wvdial's configuration file is typically saved as /etc/wvdial.conf and that is in the subdirectory/folder /etc
not etc/ppp as you were trying to use to copy.

By going one step at a time and if you do get errors, you most likely have
a typo, or you are trying to do something that isn't correct.  Like using
a wrong command or wrong SOURCE or DESTINATION for your transfers.

As another good example.... your up the tree structure towards /
from /home/user when you are wanting to backup wvdial.conf to wvdial.sav
If you open a Terminal window and do:
```

pwd
ls -alt
cd /
pwd
ls -alt
cd etc
pwd
ls -alt
sudo cp wvdial.conf wvdial.sav

```
it will work correctly.  The reason is as you go up the directory tree 
in the / and subdirectories that are below you are in the system and you
need superuser power......thus the sudo command which makes you a superuser for that single command.  sudo su changes the last prompt
character to a # which means all further commands have superuser priviledges until you type exit   .......exit will take you back to the
normal logged in user's terminal or console.

All you had to do is correct those mistakes, and not do the install/un-install as this isn't your previous OS.  It's just new to you.....

If wvdial works correctly, then Gnome-PPP will also.  You just need
to get all the parameters set correctly, and your wvdial configuration
file will assist in those settings.  Print out the file and insert the
settings into Gnome-PPP.    :~)  BEEN THERE DONE THAT!!!!!


For Gnome-PPP just insert your Phone number, loginname, password, and detect the modem as you already
know what it is.  Then save the settings and dial out.
 
lk

---

### Post by mvelte54 on 2010-05-18
Thanks again lk 
I deleted it so I can do it again as you say, simply because the first time was hit and miss. I got lucky but I don't know why. I compare it to buying a car body then trying to build an engine from a block of steel. It will work eventually by hit or miss but what did I learn? 
I did print out all the instructions you gave me and bookmarked the rest. I am going to go back and do it again I will keep you posted on my progress. This time I'm starting with the engine...

---

### Post by mvelte54 on 2010-06-05
I'm back and I'm on line. Thank you for your patience lk. I am finally on line not with just wvdial through the terminal which was the only way I could get online. But with Gnome-ppp. I discovered that in order to use Gnome-ppp you need to be part of the dip and dialout settings.

sudo adduser USERNAME dip
sudo adduser USERNAME dialout

There are two ways that these settings can be accessed. 

Terminal or System>Administration>Users and Groups

Put above code into terminal and substitute your log in name (i.e. mikey1) where it says USERNAME. Or in Users and Groups click to unlock enter your password select the user you want to have access and find 'dip' then click properties select user to have access. The same for 'dialout'. Then go into advanced settings and unlock to make changes find 'connect to internet using modem' and select it for the same user. Save and close.

My next question is: When I connect it says that it is 'Sending/Receiving 1.4 KB/s' I have not played with 'dialup' in years is this normal? It seems a bit slow for a Zoom 3095 external modem V.92. I have switched to using 'Midori' web browser because it has a smaller footprint and loads faster. Thanks for any help you guys rock!!!

---

### Post by mvelte54 on 2010-06-05
I'm back and I'm on line. Thank you for your patience lk. I am finally on line not with just wvdial through the terminal which was the only way I could get online. But with Gnome-ppp. I discovered that in order to use Gnome-ppp you need to be part of the dip and dialout settings.

sudo adduser USERNAME dip
sudo adduser USERNAME dialout

There are two ways that these settings can be accessed. 

Terminal or System>Administration>Users and Groups

Put above code into terminal and substitute your log in name (i.e. mikey1) where it says USERNAME. Or in Users and Groups click to unlock enter your password select the user you want to have access and find 'dip' then click properties select user to have access. The same for 'dialout'. Then go into advanced settings and unlock to make changes find 'connect to internet using modem' and select it for the same user. Save and close.

My next question is: When I connect it says that it is 'Sending/Receiving 1.4 KB/s' I have not played with 'dialup' in years is this normal? It seems a bit slow for a Zoom 3095 external modem V.92. I have switched to using 'Midori' web browser because it has a smaller footprint and loads faster. Thanks for any help you guys rock!!!

---

