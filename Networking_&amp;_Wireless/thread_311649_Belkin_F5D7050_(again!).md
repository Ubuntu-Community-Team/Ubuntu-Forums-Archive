---
title: "Belkin F5D7050 (again!)"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by maccom on 2006-12-03
Hi there,

I have got the above mentioned usb adapter connected to my linux box. i have followed this tutorial

[http://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29]("http://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29")

I completd everything and reboot my box. System > Administration > Networking  now has wlan0    i configuredeverything let it change then tried the net...nothing.
so i shut down and restarted ...still nothing.

i installed 'wireless assistant' which would scan and pick up 3-4 wireless networks...the same as windoze.

When i selected my network and added my WEP key i tried the net again ... still nothing.

When i launched wlassistant  it gave an error, something to do with sudo.

so i corrected the error, launched through terminal. When i done this terminal was printing everything the app was doing, it was then i noticed a few errors.
This i what terminal printed:

> user@robert-desktop:~$ sudo wlassistant
Password:
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Wireless interface(s): wlan0
Permissions checked.
ifconfig_status: /sbin/ifconfig wlan0
scan: /sbin/iwlist wlan0 scan
Networks found: 4
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.


Could someone tell me what this means, and what i am doing wrong, thankyou..

I am trying to migrate to purely ubuntu but this has been delaying me for about a year now (since i got a copy of 5.10)

Now running 6.10


TIA
Rob

---

### Post by maccom on 2006-12-05
Ok, i have now reverted back to 6.06.

Followed the same tutorial again.

Now when i go to:

System > Adminsitration > Networking

I see wlan0  but i cant and i can see all the available networks (same as windoze ones)
when i select my one, and add me (128-bit) WEP key.
I press ok and it says
activating device (or something like that, sorry i cant remember excatly!) 
it then freezes whie activating the device, i have left it for about 20 minutes still showed the same screen.

I clicked on the little cross to close it.
and same with the networking box.

I then tried to open terminal to check the output of 'iwconfig' but terminal wouldn't even open, niether would anything else!.

I tried restarting, but i the 'quit' dialogue box wouldnt open!

So i hit the reset button on my front panel.
When the box started back up, i went back to the networking window, everything had been reset (emptied).

HELP ME PLEASE!!

I really need this to work soon!

why does this window freeze, is there someway of saving these settings without using the window? (ie. a file)

ALSO;
whilst installing 6.06 i didnt seem to set a root password, how can i set one now, or find out what it is (its not blank, i activating root login and tried :-D )

i hope someone can help me soon! ](*,) 

TIA
Rob

---

### Post by FrodoB on 2006-12-05
When you install Ubuntu you do not have a root password. If you are asked for a password you enter the password that you put in for yourself when you installed Ubuntu.

To use rootly commands at a command prompt just preface the command with sudo and when asked for a password enter the one that you logged in with.

---

### Post by maccom on 2006-12-05
ok thanks, any one want to help with the other issue.

I just tried again, this time when it said:

Activating interface wlan0

that windows took about 20 minutes to go,

the other one wouldn't

iwconfig
prints the ssid that i enter, but cant seem to find it

is there something, thats needs to be activated before it can actually be used??

TIA ROB

---

