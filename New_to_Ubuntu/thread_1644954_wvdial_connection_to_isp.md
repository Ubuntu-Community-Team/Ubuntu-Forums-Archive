---
title: "wvdial connection to isp"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by Chough39 on 2010-12-13
I am using Ubuntu 10.04 with a USR 5637 USB Modem but cannot get a 
connection. Below are the terminal printouts which I get with the 
commands given. I need some help please.
 
_sudo wvdialconf /etc/wvdial.conf_ gerald@gerald-laptop:~$ sudo wvdialconf /etc/wvdial.conf  
 [sudo] password for gerald:  
 Editing `/etc/wvdial.conf'.  
 

 Scanning your serial ports for a modem. 
 

 Modem Port Scan<*1>: S0   S1   S2   S3    
 WvModem<*1>: Cannot get information for serial port.  
 ttyACM0<*1>: ATQ0 V1 E1 -- OK  
 ttyACM0<*1>: ATQ0 V1 E1 Z -- OK  
 ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK  
 ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK  
 ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK  
 ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK  
 ttyACM0<*1>: Modem Identifier: ATI -- 5601  
 ttyACM0<*1>: Speed 4800: AT -- OK 
 ttyACM0<*1>: Speed 9600: AT -- OK 
 ttyACM0<*1>: Speed 19200: AT -- OK  
 ttyACM0<*1>: Speed 38400: AT -- OK  
 ttyACM0<*1>: Speed 57600: AT -- OK  
 ttyACM0<*1>: Speed 115200: AT -- OK  
 ttyACM0<*1>: Speed 230400: AT -- OK  
 ttyACM0<*1>: Speed 460800: AT -- OK  
 ttyACM0<*1>: Max speed is 460800; that should be safe.  
 ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK  
 

 Found an USB modem on /dev/ttyACM0.  
 Modem configuration written to /etc/wvdial.conf.  
 ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"  
 gerald@gerald-laptop:~$  
 

 _sudo nano /etc/wvdial.conf_ (personal details changed)
 

 Baud = 460800  
 

 [Dialer Defaults]  
 Init1 = ATZ  
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0  
 Modem Type = USB Modem  
 ; Phone = 81*******8  
 ISDN = 0  
 ; Password = c*********3  
 New PPPD = yes  
 ; Username = j****g  
 Modem = /dev/ttyACM0  
 Baud = 460800  
 

 _sudo wvdial_ gerald@gerald-laptop:~$ sudo wvdialconf /etc/wvdial.conf  
 [sudo] password for gerald:  
 Editing `/etc/wvdial.conf'.  
 

 Scanning your serial ports for a modem. 
 

 Modem Port Scan<*1>: S0   S1   S2   S3    
 WvModem<*1>: Cannot get information for serial port.  
 ttyACM0<*1>: ATQ0 V1 E1 -- OK  
 ttyACM0<*1>: ATQ0 V1 E1 Z -- OK  
 ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK  
 ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK  
 ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK  
 ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK  
 ttyACM0<*1>: Modem Identifier: ATI -- 5601  
 ttyACM0<*1>: Speed 4800: AT -- OK 
 ttyACM0<*1>: Speed 9600: AT -- OK 
 ttyACM0<*1>: Speed 19200: AT -- OK  
 ttyACM0<*1>: Speed 38400: AT -- OK  
 ttyACM0<*1>: Speed 57600: AT -- OK  
 ttyACM0<*1>: Speed 115200: AT -- OK  
 ttyACM0<*1>: Speed 230400: AT -- OK  
 ttyACM0<*1>: Speed 460800: AT -- OK  
 ttyACM0<*1>: Max speed is 460800; that should be safe.  
 ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK  
 

 Found an USB modem on /dev/ttyACM0.  
 Modem configuration written to /etc/wvdial.conf.  
 ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"  
 gerald@gerald-laptop:~$ sudo nano /etc/wvdial.conf  
 gerald@gerald-laptop:~$ sudo wvdial  
 --> WvDial: Internet dialer version 1.60  
 --> Cannot get information for serial port.  
 --> Initializing modem.  
 --> Sending: ATZ  
 ATZ  
 OK  
 --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0  
 OK  
 --> Modem initialized.  
 --> Configuration does not specify a valid phone number.  
 --> Configuration does not specify a valid login name.  
 --> Configuration does not specify a valid password.  
 gerald@gerald-laptop:~$

---

### Post by lkraemer on 2010-12-14
Have a look at:
[http://ubuntuforums.org/showthread.php?p=10197883#post10197883](http://ubuntuforums.org/showthread.php?p=10197883#post10197883)
Posting #3

You're almost there, but need to change a few things.....

FROM:
```

; Phone = 81*******8
ISDN = 0
; Password = c*********3
New PPPD = yes
; Username = j****g 

```

TO:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 81*******8
Password = c*********3
Username = j****g

```
You forgot to remove the ; in front of Phone, Password, and Username.......
That ; makes it a COMMENT......
 
I hope you have selected a Dialup ISP that works well with Ubuntu (Linux)
Search the forum for "Linux Dialup ISP"


lk

---

### Post by Chough39 on 2010-12-14
> **lkraemer said:**
> Have a look at:
[http://ubuntuforums.org/showthread.php?p=10197883#post10197883](http://ubuntuforums.org/showthread.php?p=10197883#post10197883)
Posting #3

You're almost there, but need to change a few things.....

FROM:
```

; Phone = 81*******8
ISDN = 0
; Password = c*********3
New PPPD = yes
; Username = j****g 

```

TO:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 81*******8
Password = c*********3
Username = Username = j****g

```
You forgot to remove the ; in front of Phone, Password, and Username.......
That ; makes it a COMMENT......
 
I hope you have selected a Dialup ISP that works well with Ubuntu (Linux)
Search the forum for "Linux Dialup ISP"


lk
Many thanks for your prompt help *lkraemer*. I have now achieved the following having entered exactly what you sent me and verified the password etc.  I note the threads which were mentioned and have now learned some more. There is no real choice of ISPs here, I am in the wilds of Canada at the moment. Any further help that you might be able to give will be much appreciated as I shall then be able to complete my change over to Ubuntu.
 

 

 gerald@gerald-laptop:~$ sudo wvdial  
 --> WvDial: Internet dialer version 1.60  
 --> Cannot get information for serial port.  
 --> Initializing modem.  
 --> Sending: ATZ  
 ATZ  
 OK  
 --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0  
 OK  
 --> Modem initialized.  
 --> Sending: ATDT8194296068  
 --> Waiting for carrier.  
 ATDT8194296068  
 CONNECT 45333/ARQ/V92/LAPM/V44  
 --> Carrier detected.  Starting PPP immediately.  
 --> Starting pppd at Tue Dec 14 12:13:48 2010  
 --> Pid of pppd: 4112  
 --> Using interface ppp0  
 --> pppd: X&#65533;&#65533;[08]@&#65533;&#65533;[08]  
 --> pppd: X&#65533;&#65533;[08]@&#65533;&#65533;[08]  
 --> pppd: X&#65533;&#65533;[08]@&#65533;&#65533;[08]  
 --> pppd: X&#65533;&#65533;[08]@&#65533;&#65533;[08]  
 --> pppd: X&#65533;&#65533;[08]@&#65533;&#65533;[08]  
 --> Disconnecting at Tue Dec 14 12:13:56 2010  
 --> The PPP daemon has died: Authentication error.  
 --> We failed to authenticate ourselves to the peer.  
 --> Maybe bad account or password? (exit code = 19)  
 --> man pppd explains pppd error codes in more detail.  
 --> I guess that's it for now, exiting  
 --> The PPP daemon has died. (exit code = 19)  
 gerald@gerald-laptop:~$

---

### Post by lkraemer on 2010-12-14
OK, you are almost connected......
```

--> Using interface ppp0
--> pppd: X&#65533;&#65533;[08]@&#65533;&#65533;[08]
--> pppd: X&#65533;&#65533;[08]@&#65533;&#65533;[08]
--> pppd: X&#65533;&#65533;[08]@&#65533;&#65533;[08]
--> pppd: X&#65533;&#65533;[08]@&#65533;&#65533;[08]
--> pppd: X&#65533;&#65533;[08]@&#65533;&#65533;[08]
--> Disconnecting at Tue Dec 14 12:13:56 2010
--> The PPP daemon has died: Authentication error. 

```
But, it is failing because pppd has an error in the login info/authentication.

You will need to set up the pap-secrets and/or chap-secrets file by
running the following in a Terminal Window:
```

sudo pppconfig

```

You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppconfig

```


You are at the funny HEX Characters referenced below:

You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters) and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

Once wvdial is working, download and setup Gnome-PPP and run it from the 
GUI.

lk

---

### Post by Chough39 on 2010-12-16
I have now tried PAPS and CHAPS. Having installed GnomePPP, I know that it is a front end for wvdial. It seems very neat, if only it would work, I get disconnection after 6 seconds and the following log. With Windows I get access with the same password, username and telephone number. This seems rather strange to me. Is there something in the inability to modify pap-secrets and chaps-secrets. Could these be deleted ? Any more suggestions please ?
 

 --> WvDial: Internet dialer version 1.60  
 --> Cannot get information for serial port.  
 --> Initializing modem.  
 --> Sending: ATZ  
 ATZ  
 OK  
 --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0  
 OK  
 --> Modem initialized.  
 --> Sending: ATM1L3DT8194296068  
 --> Waiting for carrier.  
 ATM1L3DT8194296068  
 CONNECT 44000/ARQ/V92/LAPM/V44  
 --> Carrier detected.  Starting PPP immediately.  
 --> Starting pppd at Thu Dec 16 20:49:01 2010  
 --> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied  
 --> --> PAP (Password Authentication Protocol) may be flaky.  
 --> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied  
 --> --> CHAP (Challenge Handshake) may be flaky.  
 --> Pid of pppd: 4245  
 --> Using interface ppp0  
 --> Disconnecting at Thu Dec 16 20:49:06 2010  
 --> The PPP daemon has died: Authentication error.  
 --> We failed to authenticate ourselves to the peer.  
 --> Maybe bad account or password? (exit code = 19)  
 --> man pppd explains pppd error codes in more detail.  
 --> I guess that's it for now, exiting  
 --> The PPP daemon has died. (exit code = 19)

---

### Post by lkraemer on 2010-12-17
Why don't you try this for a test:
Open a Terminal Window (Console) and do:
```

sudo wvdial /etc/wvdial.conf

```
to see if you can get it working that way......
even though you shouldn't have to use sudo.....

Also post the output of:
```

cd /
cd /usr/sbin
ls -alt pppd
cd /
cd /etc/ppp
ls -alt pap*
sudo gedit pap-secrets

```
Then post the output of pap-secrets, making sure you ****** out username
and password before posting

Your pap-secrets file, or username & password appear to be incorrect.


The pap-secrets at /etc/ppp/pap-secrets file contains:
(NOTE: File Format for 10.04)
```

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       hostname        ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   hostname        "*"     -
master  hostname        "*"     -
root    hostname        "*"     -
support hostname        "*"     -
stats   hostname        "*"     -

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.
#       *       password
"yourusername@yourisp.net" provider "yourpassword"

```

Once wvdial is working use this posting and Photo's to setup Gnome-PPP.

[http://ubuntuforums.org/showthread.php?t=1614599](http://ubuntuforums.org/showthread.php?t=1614599)
Posting #3.

Just be aware that you may also need to check/uncheck STUPID MODE to get it working.
Mine works as shown, but others have problems with this setting.
 
lk

---

### Post by Chough39 on 2010-12-18
Wvdial did not start, the other results follow.
 

 

 gerald@gerald-laptop:~$ sudo wvdial /etc/wvdial.conf  
 --> WvDial: Internet dialer version 1.60  
 --> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.  
 --> Cannot get information for serial port.  
 --> Initializing modem.  
 --> Sending: ATZ  
 ATZ  
 OK  
 --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0  
 OK  
 --> Modem initialized.  
 --> Sending: ATDT8194296068  
 --> Waiting for carrier.  
 ATDT8194296068  
 CONNECT 44000/ARQ/V92/LAPM/V44  
 --> Carrier detected.  Starting PPP immediately.  
 --> Starting pppd at Sat Dec 18 07:37:15 2010  
 --> Pid of pppd: 4215  
 --> Using interface ppp0  
 --> pppd: h&#65533;&#65533;[08][18]&#65533;&#65533;[08]  
 --> pppd: h&#65533;&#65533;[08][18]&#65533;&#65533;[08]  
 --> pppd: h&#65533;&#65533;[08][18]&#65533;&#65533;[08]  
 --> pppd: h&#65533;&#65533;[08][18]&#65533;&#65533;[08]  
 --> pppd: h&#65533;&#65533;[08][18]&#65533;&#65533;[08]  
 --> Disconnecting at Sat Dec 18 07:37:21 2010  
 --> The PPP daemon has died: Authentication error.  
 --> We failed to authenticate ourselves to the peer.  
 --> Maybe bad account or password? (exit code = 19)  
 --> man pppd explains pppd error codes in more detail.  
 --> I guess that's it for now, exiting  
 --> The PPP daemon has died. (exit code = 19
 

 #  
 # /etc/ppp/pap-secrets  
 #  
 # This is a pap-secrets file to be used with the AUTO_PPP function of  
 # mgetty. mgetty-0.99 is preconfigured to startup pppd with the login option  
 # which will cause pppd to consult /etc/passwd (and /etc/shadow in turn)  
 # after a user has passed this file. Don't be disturbed therefore by the fact  
 # that this file defines logins with any password for users. /etc/passwd  
 # (again, /etc/shadow, too) will catch passwd mismatches.  
 #  
 # This file should block ALL users that should not be able to do AUTO_PPP.  
 # AUTO_PPP bypasses the usual login program so it's necessary to list all  
 # system userids with regular passwords here.  
 #  
 # ATTENTION: The definitions here can allow users to login without a  
 # password if you don't use the login option of pppd! The mgetty Debian  
 # package already provides this option; make sure you don't change that.  
   
 # INBOUND connections  
 

 # Every regular user can use PPP and has to use passwords from /etc/passwd  
 *	hostname	""	*  
 

 # UserIDs that cannot use PPP at all. Check your /etc/passwd and add any  
 # other accounts that should not be able to use pppd!  
 guest	hostname	"*"	-  
 master	hostname	"*"	-  
 root	hostname	"*"	-  
 support	hostname	"*"	-  
 stats	hostname	"*"	-  
 

 # OUTBOUND connections  
 

 # Here you should add your userid password to connect to your providers via  
 # PAP. The * means that the password is to be used for ANY host you connect  
 # to. Thus you do not have to worry about the foreign machine name. Just  
 # replace password with your password.  
 # If you have different providers with different passwords then you better  
 # remove the following line.  
 

 #	*	password  
 

 

 Username\ \=\ ****	*	********  
 Username\ \=\ ****	*	********  
 Username\ \=\ ****	*	********  
 Username\ \=\ ****	*	********
 Username\ \=\ ****	*	********  
 

 

 Username\ \=\ ****	*	********  
 Username\ \=\ ****	*	********  
 Username\ \=\ ****	*	********  
 Username\ \=\ ****	*	********
 

 

 

 Username\ \=\ ****	*	********  
 

 

 Username\ \=\ ****	*	********  
 Username\ \=\ ****	*	********  
 Username\ \=\ ****	*	********  
 Username\ \=\ ****	*	********  
 Username\ \=\ ****	*	********  
 Username\ \=\ ****	*	********
 

 Username\ \=\ ****	*	********  
 

   
 Username\ \=\ ****	*	********
 

 

 Username\ \=\ ****	*	********
 

 

 The username and password are the same as I use to connect satisfactorally using MS Windows .
 

 

 

 Furthermore, what is the significance of the following :-
 

 Warning: Could not [COLOR=#ff0000]_modify_[/COLOR] /etc/ppp/pap-secrets: Permission denied 
--> --> PAP (Password Authentication Protocol) may be flaky. 
--> Warning: Could not [COLOR=#ff0000]_modify_[/COLOR] /etc/ppp/chap-secrets: Permission denied 
--> --> CHAP (Challenge Handshake) may be flaky.  
 

 Thanks for your continuing help *lkraemer.*

---

### Post by lkraemer on 2010-12-18
wvdial did in fact start, Dialed out, then transfered control to pppd, that
tried to authenticate, but didn't do it correctly, so the server dropped
the connection.

Your pap-secrets file is messed up, if it is actually as you have 
posted it.  There should be one entry as mine below.


Here is a copy of the one I created with Ubuntu 10.04 a few minutes
ago.  Yours should be similar, except for the last line with
username & password.  (REMOVE all the other entries in the OUTBOUND
section.  OR you could run sudo pppconfig again, and delete the
current file, then create a new one again, which will create it correctly.)

```

#
# /etc/ppp/pap-secrets
#
# This is a pap-secrets file to be used with the AUTO_PPP function of
# mgetty. mgetty-0.99 is preconfigured to startup pppd with the login option
# which will cause pppd to consult /etc/passwd (and /etc/shadow in turn)
# after a user has passed this file. Don't be disturbed therefore by the fact
# that this file defines logins with any password for users. /etc/passwd
# (again, /etc/shadow, too) will catch passwd mismatches.
#
# This file should block ALL users that should not be able to do AUTO_PPP.
# AUTO_PPP bypasses the usual login program so it's necessary to list all
# system userids with regular passwords here.
#
# ATTENTION: The definitions here can allow users to login without a
# password if you don't use the login option of pppd! The mgetty Debian
# package already provides this option; make sure you don't change that.

# INBOUND connections

# Every regular user can use PPP and has to use passwords from /etc/passwd
*	hostname	""	*

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest	hostname	"*"	-
master	hostname	"*"	-
root	hostname	"*"	-
support	hostname	"*"	-
stats	hostname	"*"	-

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"lzkrmer" provider "mypassword"

```

So, edit your pap-secrets file.  Open a Terminal Window (Console)
and do:
```

cd /
cd /usr/sbin
ls -alt pppd
cd /
cd /etc/ppp
sudo gedit pap-secrets

```
And then save the file when you have it corrected.  Also post the output
of the ls -alt pppd command above.........

lk

---

### Post by Chough39 on 2010-12-19
I believe that this is better PAP has been chosen and not CHAP. However wvdial still disconnects.
 

 #  
 # /etc/ppp/pap-secrets  
 #  
 # This is a pap-secrets file to be used with the AUTO_PPP function of  
 # mgetty. mgetty-0.99 is preconfigured to startup pppd with the login option  
 # which will cause pppd to consult /etc/passwd (and /etc/shadow in turn)  
 # after a user has passed this file. Don't be disturbed therefore by the fact  
 # that this file defines logins with any password for users. /etc/passwd  
 # (again, /etc/shadow, too) will catch passwd mismatches.  
 #  
 # This file should block ALL users that should not be able to do AUTO_PPP.  
 # AUTO_PPP bypasses the usual login program so it's necessary to list all  
 # system userids with regular passwords here.  
 #  
 # ATTENTION: The definitions here can allow users to login without a  
 # password if you don't use the login option of pppd! The mgetty Debian  
 # package already provides this option; make sure you don't change that.  
 

 # INBOUND connections  
 

 # Every regular user can use PPP and has to use passwords from /etc/passwd  
 *	hostname	""	*  
 

 # UserIDs that cannot use PPP at all. Check your /etc/passwd and add any  
 # other accounts that should not be able to use pppd!  
 guest	hostname	"*"	-  
 master	hostname	"*"	-  
 root	hostname	"*"	-  
 support	hostname	"*"	-  
 stats	hostname	"*"	-  
 

 # OUTBOUND connections  
 

 # Here you should add your userid password to connect to your providers via  
 # PAP. The * means that the password is to be used for ANY host you connect  
 # to. Thus you do not have to worry about the foreign machine name. Just  
 # replace password with your password.  
 # If you have different providers with different passwords then you better  
 # remove the following line.  
 

 #	*	password  
 

 

 

 

 Username\ \=\ uuuu	*	ppppppp
 

 gerald@gerald-laptop:~$ cd /  
 gerald@gerald-laptop:/$ cd /usr/sbin  
 gerald@gerald-laptop:/usr/sbin$ ls -alt pppd  
 -rwsr-xr-- 1 root dip 273312 2010-03-06 22:59 pppd  
 gerald@gerald-laptop:/usr/sbin$

---

### Post by robert shearer on 2010-12-19
It has been **some years** since I used wvdial and kppp/gnomeppp and had the 'disconnect for authentication failure' notice.

lkraemer, you know way more than I about this so have probably already covered this.....
my problem was with PPP starting too soon and I see in the output above this line...

```
--> Carrier detected. Starting PPP immediately. 
```

Sorry, I don't know the command-line fix but in kppp I was able to insert a pause (1 second from memory) before starting PPP there and that allowed the connection to complete and authentication to occour smoothly.

Again, apologies if this is a less than helpful digression.

---

### Post by lkraemer on 2010-12-20
OH WOW, I couldn't figure out what was keeping this from working.....
And I reviewed the previous postings, and found this mistake:

Change this code:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 81*******8
Password = c*********3
Username = Username = j****g

```

TO:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 81*******8
Password = c*********3
Username = j****g

```

Somehow during cut & paste I messed up the last line...........SORRY!
 
Then try it again.  If it doesn't work:
Go check your Groups, and make sure "USER" is a member of the "dip" and "dialout" groups,
so put all users who are supposed to connect via dialup into these groups.
Where "USER" is your Login name.

Now Log out, and back in (for the group setting to take effect).
Every "dialout/dip" user will now be able to connect and disconnect with these commands:

pon    # connect to the ISP configured as "provider"
poff   # disconnect the ISP configured as "provider"


You can also check the last messages generated by these commands with:
plog   # shows the (status) messages generated by pon and poff

If you want to configure more ISPs, start pppconfig again, go through the steps, but give
it a different name in step 3 (e.g. provider2). You can then (dis)connect by pon provider2
and poff provider2.

But, once again there is no provider being displayed in your pap-secrets
file, so I'm back to stating that your pap-secrets file is INCORRECT.

ASSUME:
your loging name is   GeraldJones
your password is      MyPassWord

Your last section of the pap-secrets file should be:
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"GeraldJones" provider "MyPassWord"

```  
If you named provider something different, then just substitute that
for the provider in pon and poff. Let's assume showmenet

Original ISP named provider 
```

pon provider
poff provider

```
 
Modified ISP named showmenet
```

pon showmenet
poff showmenet

```
 
This should at get you connected.  You then need to open your Browser,
and make sure OFFLINE is not checked.  It is in the Top Left selection
under FILE:

You should be able to browse, and surf.

When finished do the poff command in the terminal window.
```

poff showmenet

```

Now go back and try wvdial.  It should now work.  Then on to Gnome-PPP.
From now on, you can just click on Gnome-PPP and run it from the GUI.


REF:
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9)

lk

---

### Post by Chough39 on 2010-12-21
GNOME PPP now works very well.  
 One of the problems was that whilst using MS Windows I was using a password *****, however it is essential to include the full password i.e. *****@*******.net
 Having set up PAP and CHAP correctly as above the system still did not work.
 A file /etc/wvdial.confsave was deleted as it was incorrect and gedit was used to correct the password in /etc/wvdial.conf. GNOME PPP now works very well and an internet connection is rapidly established.


 The assistance through the forums is excellent.
 

 Many thanks to those who helped me, especially to lkraemer.
 

 Chough39

---

### Post by lkraemer on 2010-12-21
WHOO HOO!  GREAT!  I was getting worried.  WHEW!!!!

Glad to be of help.

lk

---

