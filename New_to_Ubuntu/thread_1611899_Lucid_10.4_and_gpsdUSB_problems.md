---
title: "Lucid 10.4 and gpsd/USB problems"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by Therimin on 2010-11-02
:confused: Being totally new to Linux I have managed to put Lucid on my net book but I have been unable to get a bluetooth GPS to work I have read all of the posts and use a lot of the hints and tips (Thanks everyone) but I cannot get gpsd to receive data from the gps unit !  I have found the mac address, changed the rfcomm file and have arrived at a point when I don't know what to do next.  When I run xgps annoyingly I get the mack address shown but no data from the gps.  Yet I know that the gps is recognised when I browse the mac address. A nudge in the right direction would be appreciated.

---

### Post by sully101 on 2010-11-04
I have gps working on my dell mini9 with gpsd. Some times it takes a while to get the satellites. and must be outside to work. If you have gpsd configured your gps data should be at /dev/gps0?

gpscat /dev/gps0

lets me see the raw data.

Some more information about your specific hardware would be appreciated. In my case I have to turn the gps on by sending AT commands to the modem which must have a sim card in it to work.

---

### Post by Therimin on 2010-11-04
Many thanks for the reply, I have a EeePC Asus AU 900A which does not have a built in blue tooth so I am using a dongle which appears to work as it will allow me to interrogate the bluetooth GPS.  My understanding and use of Linux is not great but I am beginning to understand more, I have modified the config files and all seems to work in that I get the  answers when in Terminal but when I return and run Tango the program display says no gpsd no gps. if I run xgps in terminal I get the program the mac address is correct but no data from the gps via the bluetooth. [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by sully101 on 2010-11-05
Well it sounds like your hardware is quite different to mine, but I will try to help as much as I can, until someone with a bit more experience can step in.

I have had a quick read here [http://ubuntuforums.org/showthread.php?t=200142]("http://ubuntuforums.org/showthread.php?t=200142")

Have you been following a thread similar to this?

From the symptoms you describe it sounds like the COM port is not configured?

Would you post the output of

hcitool scan

and

sdptool browse YOUR:BLUETOOTH:MAC:ADDRESS

---

### Post by Therimin on 2010-11-06
Hi hcitool scan return the MAC address of the bluetooth GPS via the bluetoth dongle.
and sdptool browse returns
Service name: SPP
Service Rechandle : 0x90001
Service Class ID List:
"Serial Port" (0x1101)
Protocol Descriptor list:
"L2CAP" (0x0100)
"RFCOMM" (0x0003)
Channel:1
Language Base Attr List:
code_ISO639: 0x656e
encoding: 0x6a
base offset: 0x100

In otherwords the Gps is recognized and returns the correct info (as an aside it works well with my Palm as a GPS via bluetooth)

Many thanks for the help it is really appreciated.

---

### Post by sully101 on 2010-11-07
Could you post the output of 

cat /etc/bluetooth/rfcomm.conf

And do you have the actual device listed in /dev directory
it should be /dev/rfcomm4 or similar

---

### Post by Therimin on 2010-11-07
Hello again here is the output of RFCOMM config file

rfcomm4 {
             bind yes;
             device 00:15:4B:01:CB:23 ;   (device mac address)
             channel 1:
             }

The device is listed in the rfcomm4 file.
I am progressing slowly but its a steep learning curve on the system commands!

---

### Post by sully101 on 2010-11-07
So your /etc/bluetooth/rfcomm.conf should look like this?

rfcomm4 {
bind yes;
device 00:15:4B:01:CB:23;
channel 1;
}

Note the semi-colon after "channel 1" not a colon as in your post. [edit] I just noticed the space after your mac address [/edit] It could make the difference? Easiest to reboot after changing it to make sure the new file is used.

 OK, so the next step would be to give the command in a terminal

rfcomm connect 4

gpsd /dev/rfcomm4

leave that terminal open and in another terminal

gpscat /dev/gps0

Post the output if any of those three commands and we'll see where that leads us.

---

### Post by Therimin on 2010-11-11
[FONT=Times New Roman][SIZE=3]davek@davek-laptop:~$ rfcomm connect 4 
Can't connect RFCOMM socket: No route to host
davek@davek-laptop:~$ gpsd /dev/rfcomm4
davek@davek-laptop:~$ 
davek@davek-laptop:~$ gpscat /dev/gps0
Traceback (most recent call last):
  File "/usr/bin/gpscat", line 66, in <module>
    tty = os.open(arguments[0], os.O_RDWR)
OSError: [Errno 2] No such file or directory: '/dev/gps0'
davek@davek-laptop:~$ 

This is a screen copy of what I get note the gpsd /dev/rfcomm4 just returns to the prompt
this is a second go at posting a reply I think a cyber mouse ate the first reply[/SIZE][/FONT]

---

### Post by sully101 on 2010-11-12
Well I'm lost now. I've had a bit of a google and from what you have posted it looks like the "rfcomm connect 4" command is failing. So I'm out of my depth but guessing that bluetooth is not paired with your device.

Would you post the output of sudo hciconfig. I get this

sudo hciconfig
hci0:	Type: USB
	BD Address: 00:22:69:D0:15:2E ACL MTU: 1021:8 SCO MTU: 64:1
	DOWN 
	RX bytes:2002 acl:0 sco:0 events:65 errors:0
	TX bytes:1959 acl:0 sco:0 commands:65 errors:0

Hopeing someone else will churp in.

---

### Post by Therimin on 2010-11-13
I have been unable to get anything from the hciconfig command it just goes back to the command prompt. 
i am now completely confused!

---

### Post by Therimin on 2010-11-13
I tried the command sudo hciconfig and all I get is the command prompt. I realize I may have the file missing but do not understand what to do next !

---

### Post by sully101 on 2010-11-13
> **Therimin said:**
> I tried the command sudo hciconfig and all I get is the command prompt. I realize I may have the file missing but do not understand what to do next !

Would the missing file be /etc/bluetooth/hcid.conf ? You have to create one.

If so I would suggest following post 40 [http://ubuntuforums.org/showpost.php?p=9664806&postcount=40]("http://ubuntuforums.org/showpost.php?p=9664806&postcount=40") As It seems like the most up to date and complete one.

Does your bluetooth GPS show up in the bluetooth applet in the panel?

and could you show me the output of 

cat /etc/bluetooth/hcid.conf

Let me know where you get stuck and I'll try to help.

PS. You may get better support by posting a question to that thread, I see its been going since 2006.

---

### Post by Therimin on 2010-11-15
If I do a gedit on the hcid.conf the file is there. thanks for the info on the other post I am going to have a go at that to see if I  can find anything that  I may have caused myself!
It may take me some time as I have to make sure I understand what I am doing to the system so I can at least backtrack if necessary.

---

### Post by sully101 on 2010-11-15
Just to clear some things up that you may be having trouble with. If you enter in a terminal 

sudo gedit /etc/bluetooth/hcid.conf

and the file doesnot exist or is blank, then gedit will still open but the page will be blank. You will have to copy and paste the contents from that post and then save the file.

If the file does exist then it should have these contents

> #
# HCI daemon configuration file.
#

# HCId options
options {
# Automatically initialize new devices
autoinit yes;

# Security Manager mode
# none - Security manager disabled
# auto - Use local PIN for incoming connections
# user - Always ask user for a PIN
#
security none;

# Pairing mode
# none - Pairing disabled
# multi - Allow pairing with already paired devices
# once - Pair once and deny successive attempts
pairing multi;

# PIN helper
pin_helper /usr/bin/bluepin;

# D-Bus PIN helper
#dbus_pin_helper;
}

# Default settings for HCI devices
device {
# Local device name
# %d - device id
# %h - host name
name "My Laptop Ubuntu";

# Local device class
class 0x3e0100;

# Default packet type
#pkt_type DH1,DM1,HV1;

# Inquiry and Page scan
iscan enable; pscan enable;

# Default link mode
# none - no specific policy
# accept - always accept incoming connections
# master - become master on incoming connections,
# deny role switch on outgoing connections
lm accept;

# Default link policy
# none - no specific policy
# rswitch - allow role switch
# hold - allow hold mode
# sniff - allow sniff mode
# park - allow park mode
lp rswitch,hold,sniff,park;

# Authentication and Encryption (Security Mode 3)
#auth enable;
#encrypt enable;
}

---

### Post by Therimin on 2010-11-16
I have now found the file sudo gedit /etc/bluetooth/hcid.conf and verified that it is the same as posted. I have changed the rfcomm file to show the mac code of the device and made sure that it is correct. But when I run cgps or xgps the route and path is shown with the correct mac code but I get no information. When I interrogate the blue tooth device the computer via the bluetooth dongle it looks at the gps and returns its mac code so I know that it can see the device(gps)via bluetooth. I obviously have a software switch somwhere within the system which is preventing the program from seeing the data.  I have read lots of posts and it would seem that many people have had the same problem. I have even proved that the gps is sending data by monitoring it on my PALM which gives me a position fix instantly.
*I just cannot see the wood for the trees*

---

### Post by Therimin on 2010-11-16
I have cracked it. The problem all resolves round binding the rfcomm file and the sudo gpsd -b /dev/rfcomm4 command first. I also realised that I had ticked the boxes within Bluetooth preferences window  I assume that I had confused the system setup.
So thankyou very much for all the help it was much appreciated-and to  all of the other posts that I read in my quest to find the problem.

---

### Post by sully101 on 2010-11-17
Good to hear. Try not to get lost now :)

---

