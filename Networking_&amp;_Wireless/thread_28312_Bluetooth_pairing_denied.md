---
title: "Bluetooth pairing denied"
date: 2005-04-19
forum: Networking &amp; Wireless
---

### Post by escariot on 2005-04-19
Hi all, I'm quite new to this community, so if this thread is misplaced please let me know..

For the last two months I been working on my linux-skills, since I wanted to find out what the fuss was all about.. needless to say, I got bitten by the bug and finally ended on using Ubuntu as my linux (gnu/linux) of choice.. Needless to say (beeing a noob) the transition from Windows XP (where everything is beyond my control) to Ubuntu is difficult.. Most of my troubles are behind me now, but what I'm struggeling with nowadays is pairing my SE K700i cellular phone with my computer via bluetooth. I can find it alright, but it won't seem to pair.. I've also been googeling, and searching this forum, but can't seem to find out what's wrong..

Therefore I turn to you.. Please help a norwegian in dire need...

I've downloaded (apt-get) bluez-utils, bluez-pin, bluez-hcidump, gnome-bluetooth, libbluetooth1, mulitsync (with all the plugins), obexftp, obexserver and gnome-phone-manager (and of course number of libs which was downloaded via  apt-get to get these programs to work).

As i told you, I can find my phone, just not pair it.. I've "sudo gedit /etc/bluetooth/pin" to change the pin back to 1234, but it still won't work.

Here is my hcid.conf:
```
#
# HCI daemon configuration file.
#
# $Id: hcid.conf,v 1.4 2004/04/29 20:14:21 holtmann Exp $
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/bluez-pin;
	#pin_helper /usr/bin/bluepin;

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	#
	#lm accept,master;
	#
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	#
	#lp hold,sniff;
	#
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption
	#auth enable;
	#encrypt enable;
}

```
And this is my Pin:
1234

It just says 1234, should it not say something more??

Anyways.. hope you can help a man in a sinking ship...

Regards,

Escariot

---

### Post by Garyu on 2005-07-06
Hmm, can't help you (yet) but I have the same problem with my Sony Ericsson Z1010...

It is really irritating to see my mobile from gnome phone manager, and to see my computer name in the phone display, only to get a "wrong password" slapped in my face when I enter the PIN... *sigh*

And to think I bought a bluetooth adapter ONLY because I read on some posts that it was the only way to connect to the mobile from within linux... I have my digi-cam pictures in there from months back... I want them... badly... *sob*

Hmmz, I guess I _do_ have to install windows and dual-boot... and I was doing so well up until now without it...

---

### Post by darkone338 on 2005-08-04
i know its quite an old thread, but in case anyone is still wondering, I managed to fix this issue by changing hcid.conf to use /usr/bin/bluepin instead of bluez-pin and then restarting bluez-utils with /etc/init.d/bluez-utils restart

Hope this helps someone in the future...

---

### Post by sauveron on 2005-08-07
[QUOTE=darkone338]Hope this helps someone in the future...[/QUOTE]

Thank for your help! After 2 hours of unsuccessful tries to establish pairing with my S55 mobile phone, your solution solves my problem.

/etc/bluetooth/hcid.conf
```
        
        # PIN helper
        #pin_helper /usr/bin/bluez-pin;
        pin_helper /usr/bin/bluepin;

```

---

### Post by escariot on 2005-08-08
thank you for providing me with the means to put my pairing problems to an end darkone338! Had forgotten about this thread, but now it works... Next thing now is to make my SE K700i to talk to Evolution in a way that does not corrupt the characters.

-Escariot

---

### Post by driedger on 2005-10-18
Changing the pin-helper to bluepin from bluez-pin was the solution for me as well, and for that I thank you very very much. Every time I install a new distro I attempt to get my bluetooth headset (or bluetooth with my nokia 3600) working, and I have never succeeded until now. I upgraded to Breezy last week and this was my 2nd last major issue that I needed to get working in order to ditch my windows partition.

Thanks to the strong Ubuntu community I think I have finally found a distro that I'll stick with for an extended period of time!

Mark Driedger

---

### Post by rwabel on 2005-10-21
for me the pairing works fine and I can add my ubuntu to the phone. but whenever I try to send an image from my sony ericcson t610 to my ubuntu box nothing happens and my phone tells me connection failed. Anyone has an idea?

---

### Post by theToolman on 2005-10-24
Hey guys;

I got this going by changing the value to this:


> 
        # PIN helper
        #pin_helper /usr/bin/bluepin;
        pin_helper /usr/lib/kdebluetooth/kbluepin


then restarting bluez-utils.  I had the same problem - no pairing, but this fixed it, it gives you a PC window to put the pin in.  Think it depends on which version you have etc. so this worked on kubuntu 5.10 final, fresh from the iso (not upgraded).

---

### Post by rwabel on 2005-10-27
wow that's great! dunno know why the other 2 pin_helper don't work for sending files from the phone to the pc and kbluepin does, but I'm happy now this way

thanks alot

---

### Post by jaimono on 2006-09-26
Well, I'm really glad you got it working, but it is not working for me.

First the original pin-helper was /usr/bin/pinwrapper, it is installed by bluez-utils and first try to run /usr/bin/bluez-pin if it exists or else it runs /usr/lib/kdebluetooth/kbluepin, but it didn't worked so I changed it to /usr/bin/bluepin and it didn't worked so I took a look in to the bluepin script and it makes some X environment variables autodetection, that autodetection is wrong since it overwrites XAUTHORITY with a wrong value, fortunatelly the autodetect code is in a function so I just added a comment before the call to the function like this:

# Set X display before initializing GTK
# set_display()

But I still can't get my nokia 6670 to be paired with the computer, then I tried installing kdebluetooth and changed the pin-helper to /usr/lib/kdebluetooth/kbluepin and, guess what.... I doesn't works so now I don't know wath to do.

I hope someone can bring some light to this.

BTW, I'm using Ubuntu dapper

---

### Post by dvo on 2007-06-23
This is how I got the PIN popup working on feisty: call (even as a normal user)
```
passkey-agent --default /usr/bin/bluez-pin
```
before initiating the connection. This will register bluez-pin as the pin helper,
as you may check with ```
tail -f /var/log/syslog
```

N.B. Including in /etc/bluetooth/hcid.conf a line like
```
pin_helper /usr/bin/bluez-pin;
```
does not help - for some reason, this option is not recognized any more :(

---

### Post by blakeforeman on 2007-07-05
i read most of this fourm but i am stumped on something please if anyone would help me with this i would greatly aprecate it

i currently useing fistey fawn update relatively fresh install. 
i am trying to pair my bluetooth and the fourm describes my problem and sitituation

here is the issue that i have with the fourm and my settings
bluetooth related aps installed through synaptec manager are...
bluez-cups,bluez-utils libbbluetooth2, bluez-hcidump,bluez-pin,nautilus-sendto,libbtcl4, libgnomebt0, bluez-gnome


in the fourm the model config file is as displayed for all of the users

#
# HCI daemon configuration file.
#
# $Id: hcid.conf,v 1.4 2004/04/29 20:14:21 holtmann Exp $
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/bluez-pin;
	#pin_helper /usr/bin/bluepin;

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	#
	#lm accept,master;
	#
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	#
	#lp hold,sniff;
	#
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption
	#auth enable;
	#encrypt enable;
}



---------------------------------------------------------------------------------

i run into problems  at this area where as i do not have one in mine. 

# PIN helper
	pin_helper /usr/bin/bluez-pin;
	#pin_helper /usr/bin/blue

here is a copy of my config file 

#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}



any aditional info will be added  if needed

---

### Post by dilidon on 2007-08-02
> **dvo said:**
> This is how I got the PIN popup working on feisty: call (even as a normal user)
```
passkey-agent --default /usr/bin/bluez-pin
```
before initiating the connection. 

To thow in a positive note - this did do  the trick for me in Feisty.

---

### Post by vootele on 2007-09-17
The same mess of problems here.
Basically, it seems that the problem lies somewhere in passkey-agent. I have managet to get New pair dialog up. When I enter the correct passkey, it kinda works, but next time it's same again - almost as passkey was not remembered...and this time no passkey dialog also!
ARRGH!!"!!!
This thing sucks big time LINUX DEVELOPERS!!!Where are you, this is important!

---

### Post by ruibernardo on 2007-09-17
vootele,

to have passkey-agent always working on Gnome, add it to your Sessions on the menu System, Preferences, Sessions, click New/Add, give it a name and paste the passkey-agent command:

```
 passkey-agent --default /usr/bin/bluez-pin
```Now close the Sessions window. Logout from Gnome and then login again. The next time you try, you will be asked for the PIN, without the need of running passkey-agent from a terminal all the time.

---

### Post by erazz on 2008-02-01
bluepin worked for me too!   

Thanks!

---

### Post by Eric A Blair on 2008-03-03
I could never get bluetooth dialup to work in Dapper 6.06 LTS.  I used Breezy and it worked fine.  But every fresh install of Dapper would not provide straightforward support.  I tried editing the "pinwrapper" reference out of hcid.conf. But that did not work.  Could not get it to auth under hcid, although it does connect with the device.

This morning, at work, where I need this to work, on a whim, I logged in xterm as root and ran "pon bluetoothconn" and it fired up, no problem.  I have seen a number of references to root level priviledge problems with this.  I dont know if it will work for a more restricted user, but I can live with it like this.  I never did re run hcid to see if I can get it to auth....  This was just a whim that worked, maybe it can work for you.

Eric.

#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/bluepin;

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm master;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption (Security Mode 3)
	#auth enable;
	#encrypt enable;
}

---

