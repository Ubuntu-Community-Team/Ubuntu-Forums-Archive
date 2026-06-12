---
title: "can't get my Phone to Pair with PC via Bluetooth"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by gary4gar on 2008-10-01
[B]Hi,
[/B]

 			Posting it on behalf of my Friend because he does not have a Internet connection
He uses a GPRS connection for Internet, he was on Windows recently then i made him switch to Linux. 
Now the the problem with when we tried to pair Phone with PC, phone asks us for a Pass key, which we enter and it says Pairing failed.

I got his phone for some time for testing , I tried pairing it with my Box which runs Arch Linux. i also got the some error. and then i left the command "passkey-agent --default 1234" running in background and tried pairing the phone. it worked instantly.so if it works on Archlinux and then it should work on xubuntu also [IMG]http://linuxmint.com/forum/images/smilies/icon_confused.gif[/IMG] 

When i Tried the same on his machine, it said passkey-agent is not found.
His Distro is: xubuntu

```
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

   # Default PIN code for incoming connections
#   passkey "1234";
}

# Default settings for HCI devices
device {
   # Local device name
   #   %d - device id
   #   %h - host name
   name "BlueZ (%h)";

   # Local device class
   class 0x000100;

   # Default packet type
   #pkt_type DH1,DM1,HV1;

   # Inquiry and Page scan
   iscan enable; pscan enable;

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
```

```

rfcomm0 
{
#   # Automatically bind the device at startup
   bind yes;
#
#   # Bluetooth address of the device
   device 00:1D:98:C5:F6:27;
#
#   # RFCOMM channel for the connection
   channel   1;
#
#   # Description of the connection
   comment "Example Bluetooth device";
}

```

if any extra package needs to be installed, then please tell the package name & all its dependencies, the machine does not have internet connection. so we can't use the apt package manager.

---

### Post by PhilJ on 2008-10-01
deafault passkey is 1234 stored in hcid.conf I think     sorry misread your message  Phil  bluetooth  bluez-utils bluez-gnome  have you all these installed? I have just paired a nokia with these I can send from pc to phone but not the other way. if you run   bluetooth-applet  and get the icon in the systray selecting prefs right click you will see browse device option greyed out. All I did was delete pairing on phone and re - pair the phone and enter default passkey in phone 1234. I am led to believe that Nautilus is required to be installed for the browse device option to appear  phil  bluetooth bluez-utils gnome-blues  these are installed on my pc

---

### Post by gary4gar on 2008-10-01
But the problem is the Machine does not have a INTERNET connection :|

Looks like we gotta go back to windows xp

---

### Post by Pellervo Kässi on 2008-12-01
This is quite old thread, but i decided to answer, because I couldn't find almos any information considering this topic with google. I've been trying to establish an internet-connection with my girlfriend laptop and my gprs phone using bluetooth and ppp through rfcomm. The rfcomm-connection worked flawlessly, but I couldn't pair the laptop with the phone. 

According to launchpad the passkey-agent seems to have been missing from the ubuntu bluex-utils-package since 2006. Don't know wheter there is a reason or not. Anyway I got the pairing working doing as PhilJ told, installing bluez-gnome (I also installed gnome-bluetooth) and all its dependencies. After installing I ran on console bluetooth-applet and the bluetooth icon appeared on the xfce-panel. Without having nautilus installed I couldn't browse the devices, but now hitting the pair-button on the phone caused a pop-up to appear on my desktop and I could enter the pin I gave in the phone.

And about the problem in installing software without having an internet-connection: 
I downloaded the packages using [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/) took the downloaded with an usb-stick to the another computer and installed them using the gdebi (ofcourse you can use dpkg). The gdebi tells before installation, which dependencies are unsolved I had to fetch also files: 
libbluetooth2
libbtctl4
libgnomebt
libopenobex
obex-data-server

Total size of these files was about 500 kb.

Another option is to take an Ubuntu (not xubuntu) install cd (or the DVD) to him/her and install it as a repository and install the needed files from there.

edit: 
Found the documentation for bluez-utils @*/usr/share/doc/bluez-utils/examples there is a file README.Debian.gz from that file: 

"The old infrastructure /etc/bluetooth/passkey has been removed since the agent
is supposed to be started by a user session. It is not meant to be system-wide. "

-- snip --

"Note to the tech-savvy:
If you are stuck in console and absolutely need to pair with your bluetooth
device have a look at /var/lib/bluetooth/<your_device_address>/pincodes.
Please note that this mode of operation is _not_ _supported_.
The format is (one per line): <remote_address><whitespace><pincode>
Don't mess with files in /var/lib/bluetooth/ unless you know what you are
doing.  I repeat: manually adding a pincode for a remote device is NOT
SUPPORTED."

Does anyone know if the bluez-gnome is delivired with xubuntu 8.10 or will be in 9.04? This is a major flaw in xubuntu compared to (K)&Ubuntu. Or is there any non-gnome solution for pairing bt-devices?

---

