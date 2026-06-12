---
title: "Motorola SM56 Data Fax Modem"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by longtom on 2009-03-19
Hi,

somehow I don't get it right....well...kind of becomes a habit.

I have identified above Modem with scanmodem and need to get it going. Somehow I only manage to either find tutorials which relate to old versions of Ubuntu or I fail to understand them...

Could somebody point me into the right direction in order to:

1. Get Ubunutu 8.10 to identify and accept, love and hug this modem.

2. Get me to be able to get a dial-up connection going with this modem. 
Step by step instructions somewhere? Any programs I need? I am confused....


THis is a modem which gets often used in this part of the world and you would make many people happy if we can get this going.


Greetings

longtom

---

### Post by longtom on 2009-03-20
bump

---

### Post by longtom on 2009-03-21
last, desperate, teeth gritting bump...

---

### Post by lkraemer on 2009-03-21
longtom,
You need to go to the [http://www.linmodems.org/](http://www.linmodems.org/) site, then download
the ScanModem.tool and execute that script to get the information
on the modem.  Then subscribe to the Linmodems discussion list.
Then send Marvin an email (in plain text..ONLY) to the discussion
list.  He will analyze your results and get back to you on what to
do to get the correct drivers to get the SM56 working.

You can also search the archives posted there for SM56 and read
those messages about how others have tried to get theirs working.
Use EDIT then FIND for SM56 and search each month for responses
to keep from pouring over each months' ton of postings.

Once that is done you're 80% done.........or you can use an External USR Modem
with your serial port or USB to serial Adapter and forget the extra
multiple days' hassel of the Winmodem.....  Walmart also is selling
a USB External Modem for around $44.00 that is supposed to work good
without a wallwart or extra serial cables......

If you don't have a serial port, or want to use a USB port check out
the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, etc.

Once that decision is made, you will need to set up the pap-secrets and/or chap-secrets file by running the following in a Terminal Window:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection.  (You can set up pap and
then chap, if pap doesn't work.)  Basically you just answer the questions
that are presented.  You can delete a configurations and start over if
you need to from the menu selections. 

For more information try:
```

man pppd
man pppconfig

```

pap-secrets file contains:
(NOTE: File Format has changed for versions later than 8.04)
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"yourusername@yourisp.net" provider "yourpassword"

```

Now after ppp is setup, you will need to set up wvdial.  Power up the modem,
and connect it to your serial port.
In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```

You should get a configuration file like this at
/etc/wvdial.conf (you may need to add a few things...)

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

You also need to do this after wvdial is installed and
after pppconfig is executed:
To enable dialout without Root permission do:
$ su - root (not for Ubuntu)
sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
sudo chmod a+x /usr/sbin/pppd

Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```

You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

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

Finally, when wvdial is working you can configure/set up Gnome-PPP.

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

So, Here is your guide.......I'd appreciate any feedback on problem areas
you encounter.  I've done it several times successfully, but made this
from several different postings over several months.  I hope it helps.
Let me know which modem you use, and how you progress.

lkraemer

---

### Post by longtom on 2009-03-22
Hi Ikraemer,

wow - thank you very much for your comprehensive guide to installing a dial-up modem.

I can see that this is not a process for the faint hearted or a beginner, like me.

Well - I guess the only way to get away from beginner is to get started.

I appreciate all your suggestions as what modem rather to use than the old Motorola.  I'm afraid I have to stick to the Motorola.  The next Walmart is a couple of thousand miles and a lot of water away :p and $44.00 is R440.00, which here is a 1-2 weeks salary for those people I'd like to help - provided they have work.

So we do with what we got - and in this case it's the Motorola.

So I printed out all the suggestions you gave me (apart from the complete ppp manual...;)) and subscribed to the mailing list of linmodems.
I'm also checking the old posts and found some nice suggestions which might work.  I'll only know once I sit in front of those machines and will let you know how things are going.

At the moment it looks like a huge mountain to climb just to install a modem, but I'd love to make it work.

regards

longtom

---

### Post by lkraemer on 2009-03-23
longtom,
I googled for "howto guide for Motorola SM56 with linux" and found this.

[http://ubuntuforums.org/showthread.php?p=5357553](http://ubuntuforums.org/showthread.php?p=5357553)

lkraemer

---

### Post by longtom on 2009-03-24
> **lkraemer said:**
> longtom,
I googled for "howto guide for Motorola SM56 with linux" and found this.

[http://ubuntuforums.org/showthread.php?p=5357553](http://ubuntuforums.org/showthread.php?p=5357553)

lkraemer

That looks nearly too simple to be true.  I can't wait to check it out.

Thank you!

---

### Post by lkraemer on 2009-03-30
longtom,
How is the progress going? 

Any feedback on my guide, so I can update it?

lkraemer

---

### Post by longtom on 2009-03-30
> **lkraemer said:**
> longtom,
How is the progress going? 

Any feedback on my guide, so I can update it?

lkraemer

Sorry lkraemer, but I haven't visited that PC yet.  This is part of a freetime project - so progress might be slow at times.

As soon as I get there you'll be the first one to know.

---

### Post by longtom on 2009-03-31
> **lkraemer said:**
> longtom,
I googled for "howto guide for Motorola SM56 with linux" and found this.

[http://ubuntuforums.org/showthread.php?p=5357553](http://ubuntuforums.org/showthread.php?p=5357553)

lkraemer

I did that.  My modem started running, got to a remote server and couldn't get in.

I saw somewhere in the terminal that it was looking for m-web, which is a provider but not mine.

I put the servers tel-no as well as the username and password in wvdial.conf.  It appears that whatever is standing in wvdial doesn't have an effect on where the modem is dialing to.  

I changed country settings in the daemon settings.

So - there is a partial success - my modem is recognised and running - just in the wrong direction.

---

### Post by lkraemer on 2009-03-31
OK,
Double check your /etc/wvdial.conf to make sure it is correct.

```

gedit /etc/wvdial.conf

```
If it isn't correct, cut and paste to make it correct.  You can use
what I posted as a guide, and cut/paste from it.  Save your edits.

Then you can do:
```

wvdial /etc/wvdial.conf

```
to make sure it used your new configuration file.  It should by default.

lkraemer

---

### Post by longtom on 2009-04-02
Update - to give you an idea what's the problem is.

This is what my wvdial.conf looks like:

```

[Dialer Defaults]
Phone = 0448010501
Username = xxxxxxxxx
Password = xxxxxxxxx
New PPPD = yes

```


This is, what my output is:

```

sudo wvdial /etc/wvdial.conf
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT0448010501
--> Waiting for carrier.
ATDT0448010501
CONNECT 45333
   /// GET YOURSELF CONNECTED. DON'T GET LEFT BEHIND)  M-WEB. ///
Unauthorized duplication of this text string is strictly prohibited.
                    NO UNAUTHORISED ACCESS
User Access Verification
username:
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT0448010501
--> Waiting for carrier.
username:
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT0448010501
--> Waiting for carrier.
```

What puzzles me no end, is that he produces an M-WEB ad, when my server is not with M-WEB and the tel no in my wvdial.conf is not that of an M-WEB server.

Just to assure you, the same credencials work in WinXP quite normal.

---

### Post by lkraemer on 2009-04-02
Well, it appears that wvdial finds the Modem.
 

Try adding this in your /etc/wvdial.conf
```

[Dialer Defaults]
New PPPD = yes
Stupid mode = yes
;carrier check = no
ISDN = 0

```

Also, double check your pap-secrets file and/or your chap-secrets file
to make sure they are correct.  I think that is where the problem is.
Your modem is dialing out, but then ppp is dropping the connection from
what you have posted.  Your ISP may use PAP or they may use CHAP.
You can try both.

Remember, you can run this from the Terminal window to delete your ppp configuration
or edit your existing pap-secrets OR your chap-secrets file:
```

sudo pppconfig

```

lkraemer

---

### Post by longtom on 2009-04-08
> **lkraemer said:**
> Well, it appears that wvdial finds the Modem.
 

Try adding this in your /etc/wvdial.conf
```

[Dialer Defaults]
New PPPD = yes
Stupid mode = yes
;carrier check = no
ISDN = 0

```

lkraemer

lkraemer,

you have just been elevated to hero status.  I am writing this from the PC with that stubborn modem.

Above code did the trick.  Thank you very much for your patience and all your help.!!

You are a :KS

---

### Post by crjackson on 2009-05-16
> **lkraemer said:**
> 
pap-secrets file contains:
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"yourusername@yourisp.net" provider "yourpassword"

```


lkraemer

I know this may sound stupid but I need clarification on something.

**"yourusername@yourisp.net" provider "yourpassword"**

When editing that information do I use the quotes or drop them? the word provider - do I replace it with something on use that word? For instance..

[email]israel@peoplepc.com[/email] provider password

Would that be correct or should it be ... **"**israel@peoplepc.com**"** provider **"**password**"**

or...

[email]israel@peoplepc.com[/email] peoplepc password  ....

Can you give me a clear(er) example that my feeble old mind can grasp?

---

### Post by lkraemer on 2009-05-17
Your first post is correct according to the way mine is on Ubuntu 8.04LTS.
"israel@peoplepc.com" provider "password"

mine is "myloginname@isp.net" provider "mypasswrd"

Quotes are included......Unless a later version has changed them.

If you run pppconfig, it should ask you the questions, then build the
proper file.  But lots of times there are some unusual added characters
from what I have seen.

lkraemer

---

### Post by crjackson on 2009-05-17
> **lkraemer said:**
> Your first post is correct according to the way mine is on Ubuntu 8.04LTS.
"israel@peoplepc.com" provider "password"

mine is "myloginname@isp.net" provider "mypasswrd"

Quotes are included......Unless a later version has changed them.

If you run pppconfig, it should ask you the questions, then build the
proper file.  But lots of times there are some unusual added characters
from what I have seen.

lkraemer

Okay, thanks for the info. I'm waiting for the owner of this PC to call me today so we can try and get this resolved. Me helping him is like the blind in one eye, leading the totally blind. ;) but hopefully we can get it sorted. He really wants to dump windows...

---

### Post by crjackson on 2009-05-17
Phase I still no success...

I ran through setting up the PAP connection and wvdial reports improper user name, improper password, and I think he said improper phone number, but probably not because it did dial the modem.

He can't cut and paste the output since there in no internet connection yet.

It got too frustrating to continue further tonight. Would this be a typical output if the CHAP settings were needed but only PAP was configured?

Do I need to delete the PAP file in order to create and use the CHAP connection?

---

### Post by lkraemer on 2009-05-18
No, Just run pppconfig, and select chap versus pap.

It should create a file named chap-secrets which contains
the exact same contents as pap-secrets.

OK, in wvdial, you can watch as the Modem is initialized and
you can see it dialing.  After wvdial dials, pick up the phone
and listen on the handset to hear what is going on.  I bet the
ISP answers with a Carrier and then after some time, it drops the
connection because you either don't have the proper login name,
wrong password, or don't have stupid mode = yes, New PPPD = yes,
in /etc/wvdial.conf. Here is what mine contains:

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = yes
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = 3314321
Password = Bluebird
Username = [email]joe@copper.net[/email]

Your modem port will be different, because I use a USB to Serial Converter.

One more point!  Let's assume his login is [email]joe@copper.net[/email], and his
password is Bluebird.  The information in pap-secrets and chap-secrets for
Ubuntu 8.04 LTS should be:

"joe@copper.net" provider "Bluebird"   



lkraemer

---

### Post by crjackson on 2009-05-18
I wish you could update this guide with Jaunty specs. I was re-reading the post where you said quotes are included. When editing the the file manually, it doesn't have quotes, it has <isp.com> profile <password>

I (probably wrongly) assumed that the <> should be removed. I think I'm going to have the user delete the whole thing and start over again.

---

### Post by lkraemer on 2009-05-18
Well, That is news to me!  I guess that is another change that
I didn't know about.  Sorry, because I haven't played with anything
after 8.04 LTS.

Yes, just have them run pppconfig again and rebuild the file.
Just have them verify it when you are done.

Then wvdial shouldn't have trouble connecting, if the /etc/wvdial.conf
is good.

lkraemer

---

### Post by crjackson on 2009-05-18
> **lkraemer said:**
> Well, That is news to me!  I guess that is another change that
I didn't know about.  Sorry, because I haven't played with anything
after 8.04 LTS.

Yes, just have them run pppconfig again and rebuild the file.
Just have them verify it when you are done.

Then wvdial shouldn't have trouble connecting, if the /etc/wvdial.conf
is good.

lkraemer

Okay thanks. I'll take another stab at it in a few days when my frustration tapers off... I could **NEVER** be a phone tech support guy.

---

### Post by crjackson on 2009-06-06
Okay, so I've been through all the stuff in the guide and still can't get it working.  My name is quickly becoming MUD.  Below are the contents of all the files mentioned. Perhaps you can spot an error and tell me what to try next.  the xxxxxx where the password IS correct, I just used xxxxx to hide the real password.

pap-secrets
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

"israelavilajr@peoplepc.com" peoplepc "xxxxxxxx"
```


chap-secrets
```
# Secrets for authentication using CHAP
# client	server	secret			IP addresses
"israelavilajr@peoplepc.com" * "xxxxxxxx"
```


wvdial.conf
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = 7574118
ISDN = 0
Password = xxxxxxxx
New PPPD = yes
Stupid mode = yes
;carrier check = no
ISDN = 0
Username = israelavilajr@peoplepc.com
Modem = /dev/ttyS0
Baud = 115200
```

options
```
# /etc/ppp/options
# 
# Originally created by Jim Knoble <jmknoble@mercury.interpath.net>
# Modified for Debian by alvar Bray <alvar@meiko.co.uk>
# Modified for PPP Server setup by Christoph Lameter <clameter@debian.org>
#
# To quickly see what options are active in this file, use this command:
#   egrep -v '#|^ *$' /etc/ppp/options

# Specify which DNS Servers the incoming Win95 or WinNT Connection should use
# Two Servers can be remotely configured
# ms-dns 192.168.1.1
# ms-dns 192.168.1.2

# Specify which WINS Servers the incoming connection Win95 or WinNT should use
# ms-wins 192.168.1.50
# ms-wins 192.168.1.51

# Run the executable or shell command specified after pppd has
# terminated the link.  This script could, for example, issue commands
# to the modem to cause it to hang up if hardware modem control signals
# were not available.
#disconnect "chat -- \d+++\d\c OK ath0 OK"

# async character map -- 32-bit hex; each bit is a character
# that needs to be escaped for pppd to receive it.  0x00000001
# represents '\x01', and 0x80000000 represents '\x1f'.
asyncmap 0

# Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
#auth
noauth
# ... Unfortunately, fixing this properly in the peers file
# (/etc/ppp/peers/ppp0, typically) is apparently incompatible with the
# paradigm used by gnome-system-tools and system-tools-backend for
# managing the peers files.  So in Ubuntu Feisty we change the default.

# Use hardware flow control (i.e. RTS/CTS) to control the flow of data
# on the serial port.
crtscts

# Use software flow control (i.e. XON/XOFF) to control the flow of data
# on the serial port.
#xonxoff

# Specifies that certain characters should be escaped on transmission
# (regardless of whether the peer requests them to be escaped with its
# async control character map).  The characters to be escaped are
# specified as a list of hex numbers separated by commas.  Note that
# almost any character can be specified for the escape option, unlike
# the asyncmap option which only allows control characters to be
# specified.  The characters which may not be escaped are those with hex
# values 0x20 - 0x3f or 0x5e.
#escape 11,13,ff

# Don't use the modem control lines.
#local

# Specifies that pppd should use a UUCP-style lock on the serial device
# to ensure exclusive access to the device.
lock

# Don't show the passwords when logging the contents of PAP packets.
# This is the default.
hide-password

# When logging the contents of PAP packets, this option causes pppd to
# show the password string in the log message.
#show-password

# Use the modem control lines.  On Ultrix, this option implies hardware
# flow control, as for the crtscts option.  (This option is not fully
# implemented.)
modem

# Set the MRU [Maximum Receive Unit] value to <n> for negotiation.  pppd
# will ask the peer to send packets of no more than <n> bytes. The
# minimum MRU value is 128.  The default MRU value is 1500.  A value of
# 296 is recommended for slow links (40 bytes for TCP/IP header + 256
# bytes of data).
#mru 542

# Set the interface netmask to <n>, a 32 bit netmask in "decimal dot"
# notation (e.g. 255.255.255.0).
#netmask 255.255.255.0

# Disables the default behaviour when no local IP address is specified,
# which is to determine (if possible) the local IP address from the
# hostname. With this option, the peer will have to supply the local IP
# address during IPCP negotiation (unless it specified explicitly on the
# command line or in an options file).
#noipdefault

# Enables the "passive" option in the LCP.  With this option, pppd will
# attempt to initiate a connection; if no reply is received from the
# peer, pppd will then just wait passively for a valid LCP packet from
# the peer (instead of exiting, as it does without this option).
#passive

# With this option, pppd will not transmit LCP packets to initiate a
# connection until a valid LCP packet is received from the peer (as for
# the "passive" option with old versions of pppd).
#silent

# Don't request or allow negotiation of any options for LCP and IPCP
# (use default values).
#-all

# Disable Address/Control compression negotiation (use default, i.e.
# address/control field disabled).
#-ac

# Disable asyncmap negotiation (use the default asyncmap, i.e. escape
# all control characters).
#-am

# Don't fork to become a background process (otherwise pppd will do so
# if a serial device is specified).
#-detach

# Disable IP address negotiation (with this option, the remote IP
# address must be specified with an option on the command line or in
# an options file).
#-ip

# Disable IPCP negotiation and IP communication. This option should
# only be required if the peer is buggy and gets confused by requests
# from pppd for IPCP negotiation.
#noip

# Disable magic number negotiation.  With this option, pppd cannot
# detect a looped-back line.
#-mn

# Disable MRU [Maximum Receive Unit] negotiation (use default, i.e.
# 1500).
#-mru

# Disable protocol field compression negotiation (use default, i.e.
# protocol field compression disabled).
#-pc

# Require the peer to authenticate itself using PAP.
#+pap

# Don't agree to authenticate using PAP.
#-pap

# Require the peer to authenticate itself using CHAP [Cryptographic
# Handshake Authentication Protocol] authentication.
#+chap

# Don't agree to authenticate using CHAP.
#-chap

# Disable negotiation of Van Jacobson style IP header compression (use
# default, i.e. no compression).
#-vj

# Increase debugging level (same as -d).  If this option is given, pppd
# will log the contents of all control packets sent or received in a
# readable form.  The packets are logged through syslog with facility
# daemon and level debug. This information can be directed to a file by
# setting up /etc/syslog.conf appropriately (see syslog.conf(5)).  (If
# pppd is compiled with extra debugging enabled, it will log messages
# using facility local2 instead of daemon).
#debug

# Append the domain name <d> to the local host name for authentication
# purposes.  For example, if gethostname() returns the name porsche,
# but the fully qualified domain name is porsche.Quotron.COM, you would
# use the domain option to set the domain name to Quotron.COM.
#domain <d>

# Enable debugging code in the kernel-level PPP driver.  The argument n
# is a number which is the sum of the following values: 1 to enable
# general debug messages, 2 to request that the contents of received
# packets be printed, and 4 to request that the contents of transmitted
# packets be printed.
#kdebug n

# Set the MTU [Maximum Transmit Unit] value to <n>. Unless the peer
# requests a smaller value via MRU negotiation, pppd will request that
# the kernel networking code send data packets of no more than n bytes
# through the PPP network interface.
#mtu <n>

# Set the name of the local system for authentication purposes to <n>.
# This is a privileged option. With this option, pppd will use lines in the
# secrets files which have <n> as the second field when looking for a
# secret to use in authenticating the peer. In addition, unless overridden
# with the user option, <n> will be used as the name to send to the peer
# when authenticating the local system to the peer. (Note that pppd does
# not append the domain name to <n>.)
#name <n>

# Enforce the use of the hostname as the name of the local system for
# authentication purposes (overrides the name option).
#usehostname

# Set the assumed name of the remote system for authentication purposes
# to <n>.
#remotename <n>

# Add an entry to this system's ARP [Address Resolution Protocol]
# table with the IP address of the peer and the Ethernet address of this
# system.
proxyarp

# Use the system password database for authenticating the peer using
# PAP. Note: mgetty already provides this option. If this is specified
# then dialin from users using a script under Linux to fire up ppp wont work.
# login

# If this option is given, pppd will send an LCP echo-request frame to the
# peer every n seconds. Normally the peer should respond to the echo-request
# by sending an echo-reply. This option can be used with the
# lcp-echo-failure option to detect that the peer is no longer connected.
lcp-echo-interval 30

# If this option is given, pppd will presume the peer to be dead if n
# LCP echo-requests are sent without receiving a valid LCP echo-reply.
# If this happens, pppd will terminate the connection.  Use of this
# option requires a non-zero value for the lcp-echo-interval parameter.
# This option can be used to enable pppd to terminate after the physical
# connection has been broken (e.g., the modem has hung up) in
# situations where no hardware modem control lines are available.
lcp-echo-failure 4

# Set the LCP restart interval (retransmission timeout) to <n> seconds
# (default 3).
#lcp-restart <n>

# Set the maximum number of LCP terminate-request transmissions to <n>
# (default 3).
#lcp-max-terminate <n>

# Set the maximum number of LCP configure-request transmissions to <n>
# (default 10).
#lcp-max-configure <n>

# Set the maximum number of LCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
#lcp-max-failure <n>

# Set the IPCP restart interval (retransmission timeout) to <n>
# seconds (default 3).
#ipcp-restart <n>

# Set the maximum number of IPCP terminate-request transmissions to <n>
# (default 3).
#ipcp-max-terminate <n>

# Set the maximum number of IPCP configure-request transmissions to <n>
# (default 10).
#ipcp-max-configure <n>

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
#ipcp-max-failure <n>

# Set the PAP restart interval (retransmission timeout) to <n> seconds
# (default 3).
#pap-restart <n>

# Set the maximum number of PAP authenticate-request transmissions to
# <n> (default 10).
#pap-max-authreq <n>

# Set the maximum time that pppd will wait for the peer to authenticate
# itself with PAP to <n> seconds (0 means no limit).
#pap-timeout <n>

# Set the CHAP restart interval (retransmission timeout for
# challenges) to <n> seconds (default 3).
#chap-restart <n>

# Set the maximum number of CHAP challenge transmissions to <n>
# (default 10).
#chap-max-challenge

# If this option is given, pppd will rechallenge the peer every <n>
# seconds.
#chap-interval <n>

# With this option, pppd will accept the peer's idea of our local IP
# address, even if the local IP address was specified in an option.
#ipcp-accept-local

# With this option, pppd will accept the peer's idea of its (remote) IP
# address, even if the remote IP address was specified in an option.
#ipcp-accept-remote

# Disable the IPXCP and IPX protocols.
# To let pppd pass IPX packets comment this out --- you'll probably also
# want to install ipxripd, and have the Internal IPX Network option enabled
# in your kernel.  /usr/doc/HOWTO/IPX-HOWTO.gz contains more info.
noipx

# Exit once a connection has been made and terminated. This is the default,
# unless the `persist' or `demand' option has been specified.
#nopersist

# Do not exit after a connection is terminated; instead try to reopen
# the connection.
#persist

# Terminate after n consecutive failed connection attempts.
# A value of 0 means no limit. The default value is 10.
#maxfail <n>

# Initiate the link only on demand, i.e. when data traffic is present. 
# With this option, the remote IP address must be specified by the user on
# the command line or in an options file.  Pppd will initially configure
# the interface and enable it for IP traffic without connecting to the peer. 
# When traffic is available, pppd will connect to the peer and perform
# negotiation, authentication, etc.  When this is completed, pppd will
# commence passing data packets (i.e., IP packets) across the link.
#demand

# Specifies that pppd should disconnect if the link is idle for <n> seconds.
# The link is idle when no data packets (i.e. IP packets) are being sent or
# received.  Note: it is not advisable to use this option with the persist
# option without the demand option.  If the active-filter option is given,
# data packets which are rejected by the specified activity filter also
# count as the link being idle.
#idle <n>

# Specifies how many seconds to wait before re-initiating the link after
# it terminates.  This option only has any effect if the persist or demand
# option is used.  The holdoff period is not applied if the link was
# terminated because it was idle.
#holdoff <n>

# Wait for up n milliseconds after the connect script finishes for a valid
# PPP packet from the peer.  At the end of this time, or when a valid PPP
# packet is received from the peer, pppd will commence negotiation by
# sending its first LCP packet.  The default value is 1000 (1 second).
# This wait period only applies if the connect or pty option is used.
#connect-delay <n>

# Packet filtering: for more information, see pppd(8)
# Any packets matching the filter expression will be interpreted as link
# activity, and will cause a "demand" connection to be activated, and reset
# the idle connection timer. (idle option)
# The filter expression is akin to that of tcpdump(1)
#active-filter <filter-expression>

# ---<End of File>---
```

---

### Post by lkraemer on 2009-06-06
Right now the only thing I see is this:

"israelavilajr@peoplepc.com" peoplepc "xxxxxxxx"

should be "israelavilajr@peoplepc.com" provider "xxxxxxxx"
assuming that provider is what you had as the name in pppconfig.
The chap-secrets file appears just like the one I made with 9.04 LiveCD

So, when you try wvdial what happens?  Do the LED's flash on the Modem
when it initializes?  Does the modem go offhook and you hear a dialtone?
Then it should dial the number.  The other modem should answer and a
connection should be made.  Then transfer should be made to ppp.

As soon as the modem dials pick up a handset and listen to the tones.
You should hear both and watch it on the screen.

It should be easy, it isn't this hard.  Something is being missed.

Double check that OFFLINE isn't selected in Firefox.

lkraemer

---

### Post by crjackson on 2009-06-07
> **lkraemer said:**
> Right now the only thing I see is this:

"israelavilajr@peoplepc.com" peoplepc "xxxxxxxx"

should be "israelavilajr@peoplepc.com" provider "xxxxxxxx"
assuming that provider is what you had as the name in pppconfig.
The chap-secrets file appears just like the one I made with 9.04 LiveCD

So, when you try wvdial what happens?  Do the LED's flash on the Modem
when it initializes?  Does the modem go offhook and you hear a dialtone?
Then it should dial the number.  The other modem should answer and a
connection should be made.  Then transfer should be made to ppp.

As soon as the modem dials pick up a handset and listen to the tones.
You should hear both and watch it on the screen.

It should be easy, it isn't this hard.  Something is being missed.

Double check that OFFLINE isn't selected in Firefox.

lkraemer

Okay, when setting up with pppconfig, provider was changed to peoplepc since it seems to be asking for the name of the provider.

The modem dials, the says connection and goes through the handshaking process. It establishes a connection and right after it reports logging in, it then disconnects as if being kicked for wrong name and password.

This is the same behavior I got when using gnome-ppp. It would start authenticating and then boot the user.

The same telephone number and login credentials work perfectly in windows with NO proprietary software installed. 

It's an external usr modem with a loud volume, I don't have to pull a phone receiver to listen. It dials normal, establishes proper handshaking, the familiar BONG, BONG, telling me it's a high speed connection, says it logging in, then kicks it off line.  That's it...

What now?

---

### Post by lkraemer on 2009-06-07
OK, the problem is with the pppconfig files.  Run pppconfig
again, delete ALL the setup files from the menu, meaning you will
pick them from a list and delete each one, until they are gone.
Then try doing this.
When it asks for Static or Dynamic, use Dynamic, then it will be a guess
as to chap or pap.  You pick pap, as the chap-secrets file looks good
to me.  Then answer the other questions.  Leave the name as provider.
Save the file.   exit.

Then view the pap-secrets file and chap-secrets file to verify them.
They should be as my previous post.

Unless there is something strange with peoplepc it should work.

If not run pppconfig again, edit the same file and change to chap, save, test.

It should work.  Do you have another dialup ISP that you can access to test that isn't peoplepc?

MAKE SURE YOU LEAVE THE TERMINAL WINDOW OPEN & RUNNING AFTER YOU START WVDIAL!
Otherwise you will close the connection.  Just Minimumize the window and open Firefox.
When you're done surfing re-open the Terminal window and type CNTL C.
That will kill wvdial.

UPDATE:.................................... 

For those interested it does work with the standard pppconfig setup.
Last of /etc/ppp/pap-secrets follows:
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password

"yourlogin@peoplepc.com" * "yourpassword"

```

/etc/chap-secrets  follows:
```

# Secrets for authentication using CHAP
# client	server	secret			IP addresses


"yourlogin@peoplepc.com" * "yourpassword"

```

wvdial.conf  follows:
password =, modem =, phone =, username =, will need to be modified. 
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = yes
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = 3211234
Password = yourpassword
Username = yourlogin@peoplepc.com

```

Once all that works set up Gnome-PPP.


I even have it working from LiveCD, by installing wvdial via Wifi,
then setting up pppconfig, and wvdial.  But, I have to use sudo wvdial
because pppd isn't found at /usr/sbin for some reason without sudo.

lkraemer

---

### Post by crjackson on 2009-06-13
UPDATE:

Using the modified files provided by lkraemer, the pc will now dial AND CONNECT using sudo wvdial.

gnome-ppp also dialed and connected properly after that. The problem now is that gnome-ppp won't let you hang up. There seems to be no option. It is configured to minimize on connect but it doesn't. It just goes away.

If you just turn the modem off, it will redial like it or not. So I had him change the settings to turn off auto-redial but then it wouldn't connect again after that.

Then running the wvdial command from the terminal established the connection again and seems to have re-set gnome-ppp so it will dial out and connect again, but it still wants to auto-redial and there seems to be no method of disconnecting.

How does one hang up the modem?

---

### Post by lkraemer on 2009-06-13
Typically, you would click on the minimized Gnome-PPP window, click
on DISCONNECT (Terminates the connection), then QUIT (exits Gnome-PPP)
from the left portion of the Gnome-PPP window.  But, I too have problems
with Gnome-PPP not going to a Minimum window.  In fact if you search the
forum, you will see my posting and that there are no answers, or the last
time I looked there were none.

[http://ubuntuforums.org/showthread.php?t=1137627&highlight=Gnome-PPP](http://ubuntuforums.org/showthread.php?t=1137627&highlight=Gnome-PPP)

Next time you would click on Gnome-PPP, and then click on Connect,
after which it would minimize again.........But it doesn't.  I think
there is a sticky bit causing the problem.  I can make mine go to
the toolbar and work properly, but mine just hangs on the screen....

And, if running wvdial from a Terminal window you shouldn't need to
use sudo.  Just wvdial should dial out and work.....

Glad to hear you're making progress.

lkraemer

---

### Post by crjackson on 2009-06-13
I still have 2 questions.

1) How do you close the connection when using wvdial? It won't hang up.

2) Does kppp work correctly? I can have him install kppp if that would work.

---

### Post by longtom on 2009-06-14
> **crjackson said:**
> I still have 2 questions.

1) How do you close the connection when using wvdial? It won't hang up.

2) Does kppp work correctly? I can have him install kppp if that would work.

to 1.)  press ctrl + C

I have no answer for question 2 since I use Gnome and wvdial.  Ctrl + C is easy enough for me.

---

### Post by crjackson on 2009-06-14
Thnksfor the info. When my friend calls I'll have him give the Ctrl+C a try and see what happens.

I'm also going to have him install kppp and give that a try too.

If it all fails, could I make a desktop launcher for the terminal command, or even a script?

Maybe someone could test that out on a working dial-up connection and let me know how to do it. I could probably do that myself if I had a modem and a dial-up connection to see how it all works, but I don't. I'm trying to help an OLD friend out who's about 2K miles away.

---

### Post by crjackson on 2009-06-14
Well, I never could get any dialer working, and wvdial only works if I use sudo.

I wrote a simple little bash script for his desktop and changed the icon to kppp's (very nice looking). Now he can get online pretty easy just by clicking on the script and providing his password.

It's a shame it won't work without sudo, bu at least he's finally online and downloading Ubuntu updates at this time.

Thanks for all the help.  Phew!!! It shouldn't be that darned hard. Someone needs to write a GOOD dial-up package that just works...

---

### Post by longtom on 2009-06-15
> **crjackson said:**
> Well, I never could get any dialer working, and wvdial only works if I use sudo.

I wrote a simple little bash script for his desktop and changed the icon to kppp's (very nice looking). Now he can get online pretty easy just by clicking on the script and providing his password.

It's a shame it won't work without sudo, bu at least he's finally online and downloading Ubuntu updates at this time.

Thanks for all the help.  Phew!!! It shouldn't be that darned hard. Someone needs to write a GOOD dial-up package that just works...

You know how many dial-up modems are out there?:o  **A** package will not do the trick - a couple thousand....

---

### Post by crjackson on 2009-06-15
> **longtom said:**
> You know how many dial-up modems are out there?:o  **A** package will not do the trick - a couple thousand....

So you think it's possible for Microsoft to write a dialer that works very well, but Linux developers aren't capable of it? :confused:

---

### Post by longtom on 2009-06-15
> **crjackson said:**
> So you think it's possible for Microsoft to write a dialer that works very well, ...

for modems especially designed for windows....or the other way arround...:)

Yeah - I get your point.  Dial-up support in Linux appears to be sketchy and it was so over the years.  I am not sure why it hasn't been done in those days.

These days most devlopers live in environments were dial-up is a distant relic from the past.  It's only us poor buggers in the developping world still having to stick to it.  So I don't see big developments in furture in that direction.

But I tell you that for nothing; - I'm not going back to Windows for that.  I got it going in Linux and it is actually faster than in Windows (for reasons I can not explain).

But for a school out there who got some old PIIIs and would like to use Ubuntu and get connected with dial-up (which is all that works in a way) it's probably a bridge to far...

---

### Post by halitech on 2009-06-15
> **longtom said:**
> 

But I tell you that for nothing; - I'm not going back to Windows for that.  I got it going in Linux and it is actually faster than in Windows (for reasons I can not explain).


*nix is built from the ground up to be a multiuser, networking OS so it handles tcp/ip connections alot better then windows does which was built as a single user OS and added networking abilities later.

---

### Post by crjackson on 2009-06-15
> **longtom said:**
> for modems especially designed for windows....or the other way arround...:) 

I'm not talking about modem support. USR External modems don't really need any support.

I'm talking about being able to input the needed login information into a dialer that actually works.

gppp & kppp don't work as expected. You have to jump through the wvdial hoops, make you own pap/chap file etc...  You should just be able to put that information into a dialer and connect.

Further, wvdial won't connect unless using **sudo wvdial /etc/wvdial.conf**

It's a mess... I know it's not supposed to be that way, but it's the ONLY way I can get that system to connect.

---

### Post by longtom on 2009-06-17
> **crjackson said:**
> I'm not talking about modem support. USR External modems don't really need any support.

I'm talking about being able to input the needed login information into a dialer that actually works.

gppp & kppp don't work as expected. You have to jump through the wvdial hoops, make you own pap/chap file etc...  You should just be able to put that information into a dialer and connect.

Further, wvdial won't connect unless using **sudo wvdial /etc/wvdial.conf**

It's a mess... I know it's not supposed to be that way, but it's the ONLY way I can get that system to connect.

Me thinks it would have helped if you would have read the rest of my post.  I said:

> Yeah - I get your point. Dial-up support in Linux appears to be sketchy and it was so over the years. I am not sure why it hasn't been done in those days.

And the way you are connecting is exactly the way I am connecting on the dial-up machines.  I just make a shortcut on the desktop.  Typing in a password before you connect I consider a good thing.  I would have made it that way if it wouldn't be so by default.  Keeps the kids of the net while I am not at home...;)

---

### Post by crjackson on 2009-06-17
> **longtom said:**
> Me thinks it would have helped if you would have read the rest of my post.  I said:



And the way you are connecting is exactly the way I am connecting on the dial-up machines.  I just make a shortcut on the desktop.  Typing in a password before you connect I consider a good thing.  I would have made it that way if it wouldn't be so by default.  Keeps the kids of the net while I am not at home...;)

 I did read the rest of your post. I just wanted to make it clear it wasn't just a modem support issue, but dial up as a whole.

---

### Post by Raghavan48 on 2009-11-18
> **lkraemer said:**
> longtom,
You need to go to the [http://www.linmodems.org/](http://www.linmodems.org/) site, then download
the ScanModem.tool and execute that script to get the information
on the modem.  Then subscribe to the Linmodems discussion list.
Then send Marvin an email (in plain text..ONLY) to the discussion
list.  He will analyze your results and get back to you on what to
do to get the correct drivers to get the SM56 working.

You can also search the archives posted there for SM56 and read
those messages about how others have tried to get theirs working.
Use EDIT then FIND for SM56 and search each month for responses
to keep from pouring over each months' ton of postings.

Once that is done you're 80% done.........or you can use an External USR Modem
with your serial port or USB to serial Adapter and forget the extra
multiple days' hassel of the Winmodem.....  Walmart also is selling
a USB External Modem for around $44.00 that is supposed to work good
without a wallwart or extra serial cables......

If you don't have a serial port, or want to use a USB port check out
the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, etc.

Once that decision is made, you will need to set up the pap-secrets and/or chap-secrets file by running the following in a Terminal Window:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection.  (You can set up pap and
then chap, if pap doesn't work.)  Basically you just answer the questions
that are presented.  You can delete a configurations and start over if
you need to from the menu selections. 

For more information try:
```

man pppd
man pppdconfig

```

pap-secrets file contains:
(NOTE: File Format has changed for versions later than 8.04)
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"yourusername@yourisp.net" provider "yourpassword"

```

Now after ppp is setup, you will need to set up wvdial.  Power up the modem,
and connect it to your serial port.
In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```

You should get a configuration file like this at
/etc/wvdial.conf (you may need to add a few things...)

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

You also need to do this after wvdial is installed and
after pppconfig is executed:
To enable dialout without Root permission do:
$ su - root (not for Ubuntu)
sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
sudo chmod a+x /usr/sbin/pppd

Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```

You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

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

Finally, when wvdial is working you can configure/set up Gnome-PPP.

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

So, Here is your guide.......I'd appreciate any feedback on problem areas
you encounter.  I've done it several times successfully, but made this
from several different postings over several months.  I hope it helps.
Let me know which modem you use, and how you progress.

lkraemer
Hi pal,

I have been trying all possible ways to connect to the internet using 9.04 Jaunty after a failed attempt to do so with the 9.10. Now, I installed GNOME PPP from my windows system and also tried my luck with the wvdial thing. Unfortunately, nothing seems to be working. Finally, your gedit /etc/wvdial.conf seemed to do something.

After I edited it and then tried to work my way through, this is what I got. 

raghavan@indhur:~$ sudo wvdial /etc/wvdial.conf
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

I dont know why my modem is not recognized. I use the one from BSNL, the state owned service provider in India using the modem from Huawei ETS 2288.

PLEASE HELP.

---

### Post by lkraemer on 2009-11-18
Check out this posting:
[http://ubuntuforums.org/showthread.php?t=993888&highlight=Huawei+ETS+2288](http://ubuntuforums.org/showthread.php?t=993888&highlight=Huawei+ETS+2288)
George was kind enough to help get this one working.

Your error is because of a faulty command.......should be:
sudo wvdialconf /etc/wvdial.conf

to create the configuration file.  Then use 
sudo wvdial /etc/wvdial.conf to dial out after you have made edits
to /etc/wvdial.conf to add your username and password and phone number etc.

lk

---

### Post by Mordy777 on 2009-11-23
I tried this out and uses an External USR Modem with my serial port or USB to serial Adapter and it worked beautifully.

Hope you had as much success with it as I did.  :)

---

