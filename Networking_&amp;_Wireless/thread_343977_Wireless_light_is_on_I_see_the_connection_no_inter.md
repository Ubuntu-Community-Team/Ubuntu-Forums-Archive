---
title: "Wireless light is on I see the connection no internet"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by tacm on 2007-01-22
OK I am one of the poor SOB's that has the 4318 wireless card from hell.  After much research and advice I finally have my wireless light on and can "see" my connection.  I am still unable to get onto the internet.  Advice please?  I am a new Linux user so please made advice dumb *** friendly.  Thank you Steve

---

### Post by evilghost on 2007-01-22
Are you using ndiswrapper?  What does "iwconfig" say?

I had a similar issue with mine, I have to do this at startup (added to /etc/rc.local)

ifdown wlan0
rmmod ndiswrapper
modprobe ndiswrapper

Else my radio doesn't get turned on.  Also, if you're using ndiswrapper (I'm using ndiswrapper-utils-1.8 for Edgy and 1.9 for Feisty) be sure you're using the correct Win32 drivers.  I had to use 4.00c for my BCM4306 directly from HP.

---

### Post by tacm on 2007-01-22
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

This is the output from the iwconfig command.  I really am a novice user but from what ive read my wireless needs to be on eth0.  if this is correct I need to know how to change it.  I must say I am VERY gun shy right now as it took me days just to get the wireless light to even come on.  I hope Im getting close.  Any help would be spectacular.  Steve

---

### Post by phossal on 2007-01-22
You don't *have* to have your wireless extension on eth1. Mine is on wlan0 (although my hardware is different). Make sure you're working with an unprotected router. You want to establish a connection before enabling WEP/WPA.

What happens when you issue:  (where <ESSID> and <CHANNEL> are set to match the router?)
```
sudo dhclient eth1 essid <ESSID> channel <CHANNEL>
```

*Don't include the "<" or ">"

---

### Post by tacm on 2007-01-22
I dont have wpa or wep on, i was unsucsessful at running your command  I was supose to input my information between the < > correct?

---

### Post by evilghost on 2007-01-22
Have you installed the bcm43xx firmware using fwcutter?

You really haven't given us any information on your current setup.

---

### Post by tacm on 2007-01-22
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
11: ERROR while getting interface flags: No such device
11: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
channel: ERROR while getting interface flags: No such device
channel: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
ken126HOMEneK: ERROR while getting interface flags: No such device
ken126HOMEneK: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
essid: ERROR while getting interface flags: No such device
essid: ERROR while getting interface flags: No such device
Bind socket to interface: No such device


This is the result of the above command,  but I am useing the computer with the wired connection right now if that makes a difference.  Steve

---

### Post by tacm on 2007-01-22
I am sorry I am very inexperenced.  I followed the instuctions here [www.ubuntuforums.org/showthread.php?t=197102&highlight=amd64](www.ubuntuforums.org/showthread.php?t=197102&highlight=amd64)
I really dont know how it works.  i apologise for not having the anwsers to your questions

---

### Post by evilghost on 2007-01-22
Post the output of:

ndiswrapper -l
dpkg -l|grep -i ndiswrapper
lsmod|grep -i bcm


I suspect you have bcm43xx loaded and it's not in /etc/modprobe.d/blacklist.  I also suspect you may have used the wrong Win32 WLAN driver; did you get the one from your hardware vendor/manfacturer?

---

### Post by tacm on 2007-01-22
ndiswrapper -l

output

Installed ndis drivers:
bcmwl5          driver present, hardware present

dpkg -l|grep -i ndiswrapper

output

ii  ndiswrapper-utils                      1.8-0ubuntu2    Userspace utilities for ndiswrapper

lsmod|grep -i bcm
 
no output

Thank you. Steve

---

### Post by evilghost on 2007-01-22
Can you also post the output of /etc/network/interfaces?

---

### Post by tacm on 2007-01-22
If you wanted the command typed exactly as in your post the output is
bash: /etc/network/interfaces?: No such file or directory


Without the ? mark the output is
bash: /etc/network/interfaces: Permission denied


As I am sure you can probably tell I can cut and paste but I do not know what the commands mean.  Thankx again. Steve

---

### Post by phossal on 2007-01-22
Configuration of /etc/network/interfaces isn't necessary to establish a connection if the hardware is properly installed *and* he's issued a successful iwconfig command. 

To answer the question, the <ESSID> and <CHANNEL> do *not* use brackets. If my router "name" was MYNET and my channel was 3, I would issue it like so:
```
sudo iwconfig eth1 essid MYNET channel 3
```
Then I would try to get an ip like so:
```
sudo dhclient eth1
```

You find out what's in /etc/network/interfaces by issuing *this*:
```
sudo gedit /etc/network/interfaces
```

---

### Post by evilghost on 2007-01-22
> **phossal said:**
> Configuration of /etc/network/interfaces isn't necessary to establish a connection if the hardware is properly installed *and* he's issued a successful iwconfig command.

But it certainly makes it easier if you're going to specify ESSID as well as any WEP or WPA/WPA2 configuration.  Modify /etc/network/interfaces, specify ESSID, ensure there's a configuration for eth1, and bring the interface up.

ndiswrapper shows the hardware as working.  Either his radio is disabled (possibly the case) or upon boot the necessary information is not in /etc/network/interfaces (ESSID, interface, etc).

---

### Post by phossal on 2007-01-22
/etc/network/interfaces is okay for long-term configuration, but it isn't necessary. You're setting those parameters with iwconfig. If you're making the hardware permanent (as by MAC), you'd use iftab. It's not necessary to use *interfaces during initial connection, it's a nuisance and is likely to be overlooked if a *beginner* makes a mistake.

Setting up an initial connection should be done in the fewest steps possible, using the least permanent, most direct method possible.

---

### Post by tacm on 2007-01-22
Well......I cannot begin to tell yall how much I appriciate the help.....what do you think my next step should be?

---

### Post by phossal on 2007-01-22
You're going to scroll to a few posts earlier, and issue the commands I posted. Then you're going to post the output to the commands the other gentlemen asked you for. :D

---

### Post by tacm on 2007-01-22
> **phossal said:**
> 
```
sudo iwconfig eth1 essid MYNET channel 3
```
]

i get no output with this command with my information pluged in  The router is on a working windows network and the owner of the network has turned off encription set it to channel 11 and set it up to broadcast the essid.  Thanx

---

### Post by evilghost on 2007-01-22
sudo iwconfig eth1 your_essid channel 11

Where 'your_essid' is the SSID you're network is setup with (the one being broadcasted)


Then post the output of iwconfig.

---

### Post by tacm on 2007-01-22
sudo dhclient eth1
 output
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:14:a5:71:9f:ed
Sending on   LPF/eth1/00:14:a5:71:9f:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

NEXT COMMAND
sudo gedit /etc/network/interfaces

output in seperate window
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid ken126HOMEneK
wireless-key s


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp








auto eth0

---

### Post by phossal on 2007-01-22
If you used channel 11, and your essid, it's good that you didn't get output. Once you've issued the command correctly, then issue:
```
sudo dhclient eth1
```

---

### Post by tacm on 2007-01-22
This is the command exactly as i typed it
sudo iwconfig eth1 ken126HOMEneK channel 11

the output was

Error : unrecognised wireless request "ken126HOMEneK"


am I typing the command wrong?

---

### Post by phossal on 2007-01-22
Yes, before the network name, you need the word essid

```
sudo iwconfig eth1 *essid *ken126HOMEneK channel 11
```

---

### Post by tacm on 2007-01-22
it asks me for my pass word.....I type it in then I get a new command line with no output

tacm@semubuntu:~$ sudo iwconfig eth1 essid ken126HOMEneK channel 11
Password:
tacm@semubuntu:~$

---

### Post by phossal on 2007-01-22
Yep. No output. Then issue:

```
sudo dhclient eth1
```

---

### Post by tacm on 2007-01-22
Well.....I really really thank you guys for your help......I dont know what we did but it is now working......I really want to learn more about this problem and WHY it works....Can you recomend a site for noob linux users I try to read the posts here but a lot of the information is over my head..  In addition do you mind if i keep your screen name and pm you if I run into other problems,  or would you prefer a public post.  Thank you very much!  Steven

---

### Post by evilghost on 2007-01-22
When you reboot you'll lose the changes, phossal will now walk you through committing those changes/commands to your /etc/network/interfaces ):P

---

### Post by phossal on 2007-01-22
Here is how I would do it: (I *still* wouldn't manually configure /etc/network/interfaces)

I would paste the following into my /home/<USER>/.bashrc file:
Open the file like this:
```
sudo gedit ~/.bashrc
```

Then paste this at the bottom:
```
[COLOR="DimGray"][SIZE="1"]# BEGIN COPYING (Paste this content at the bottom of your /home/<USER>/.bashrc
# --- This function issues these commands for you -- 
# --- When you reboot your computer, you open a terminal and enter w (as your command)
# --- It will connect you. When you reformat your computer, or back up, back up this file too! :).[/SIZE][/COLOR]
function w() {
   sudo iwconfig eth1 essid ken126HOMEneK channel 11
   sudo dhclient eth1
}
[COLOR="DimGray"][SIZE="1"]# END COPYING[/SIZE][/COLOR]
```

*I do it this way because I backup my .bashrc file, but I don't back up /etc/network/interfaces.

---

### Post by evilghost on 2007-01-22
You may also be able to remove this line from your /etc/network/interfaces since everything else appears setup correctly:

```

wireless-key s:eb20cd78599e4524bb00b823ba19415fd40e0f4d69962013 3cf3ef0bd844eca2

```

---

### Post by tacm on 2007-01-22
I have rebooted a few times and t seems to work fine

---

### Post by phossal on 2007-01-22
Have a great day/evening, guys! :D

---

### Post by evilghost on 2007-01-22
Definitely, always great to help out a fellow Ubuntu user and learn something along the way ):P

---

