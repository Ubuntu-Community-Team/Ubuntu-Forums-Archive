---
title: "HOWTO: Connect with a Huawei E220 USB wireless modem"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by madhadron on 2008-07-13
I have just finished setting up my Huawei E220 USB wireless modem from Swisscom on Ubuntu Hardy Heron.  Before I go into the details, there are a few things you should know:

[LIST=1]
[*]I am told the modem needs to be connected to a Windows or MacOS X computer first to get some initial settings.  Mine was connected to a MacOS X machine for a long time before the machine was reincarnated at Ubuntu, so I don't know whether this is true.

[*]Ubuntu Hardy Heron correctly detects the modem when you connect it.  Other distributions may require some USB fiddling, but as I have only tried it on hardy, you will have to search abroad a bit.

[*]The modem requires a PIN exactly once each time it is attached to a computer.  Attempts to send more will simply return error messages.  In the PPP chat scripts below, we simply ignore all reponse from the command that issues the PIN, whether it be OK or error.

[*]You will need to know your gateway, username, password, and the number to dial for your provider.  For Swisscom it is:

**Access name point**: gprs.swisscom.ch
**Username**: gprs
**Password**: gprs

Some providers don't have usernames and passwords for GPRS.  You may have to put a dummy username and password in your configuration in order to make the software happy.

[*]Ubuntu's network manager contains a serious error: it does not regard a PPP connection as being online, and will drive a number of applications into "offline mode" unless you forbid it by replacing every instance of 

```
<allow send_interface="org.freedesktop.NetworkManager"/>

```

in the file ```
/etc/dbus-1/system.d/NetworkManager.conf
``` with (the only change is 'allow' to 'deny')

```
<deny send_interface="org.freedesktop.NetworkManager"/>

```

This prevents the programs from being able to ask the network manager whether it thinks the computer is online.
[/LIST]

Now to the actual configuration.  First go to the System->Administration->Network, click on the Unlock button and give it your password so you can change the settings, then clock on 'Point to point connection' and hit 'Properties.'

In the new window, entitled 'ppp0 Properties' (remember the ppp0 --- we will need it later when we go replace the chat scripts), enable the connection, set the connection type to 'GPRS/UMTS' and fill in your data (see note 4 above) in the rest of the fields.

Go to the modem tab.  Set the port to ```
/dev/ttyUSB0
``` (unless your computer has put it somewhere else).  Dial type should be Tones, and volume should be Off.  Finally go to Options, and make sure all three options are checked.

The network manager sets up a PPP peer in ```
/etc/ppp/peers/ppp0
```.  For those on other distributions, the contents of this file are:

```
connect "/usr/bin/char -v -f /etc/chatscripts/ppp0"
usepeerdns
defaultroute
persist
/dev/ttyUSB0
115200
user "gprs"

```

Now we have to make the chatscript mentioned above --- ```
/etc/chatscripts/ppp0
``` --- properly handle our modem.  Edit the file to contain (thanks to [http://www.dumpville.org/index.php/a/2007/10/31/proximus_mobile_internet]("http://www.dumpville.org/index.php/a/2007/10/31/proximus_mobile_internet") for some of the material herein:

```
TIMEOUT 3
ABORT BUSY
ABORT 'NO CARRIER'
ABORT VOICE
ABORT 'NO DIALTONE'
ABORT 'NO DIAL TONE'
ABORT 'NO ANSWER'
ABORT DELAYED
"" AT+CPIN=pin
"" ATZ
OK ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK AT+CGDCONT=1,"IP","access gateway"
OK ATDT*99#
CONNECT ""

```

You must make two changes.  In the line ```
"" AT+CPIN=pin
```, replace pin with your 4-digit PIN code.  The "" at the beginning of the line is what tells pppd to ignore any errors that might come back.  Second, replace 'access gateway' with your gateway you entered before (in my case, gprs.swisscom.ch).  Once you have saved the file, run

```
sudo chmod -w /etc/chatscripts/ppp0

```

This will prevent network manager from eating your chatscript as often, which it will otherwise do every single time.  It will still sometimes do so, so you may want to keep a copy elsewhere to copy back into place when it does.

Now you can connect by going back to System->Administration->Network, unlocking it again, and checking on the checkbox next to 'Point to point connection.'  When you wish to disconnect, uncheck the checkbox.

And now I'm going to put in that little guitar playing smiley the editor is kindly displaying for me because I just can't resist: :guitar:

---

### Post by hfdragon on 2008-07-17
which version of NM is this howto designed for ? 0.6 or 0.7 ?

---

