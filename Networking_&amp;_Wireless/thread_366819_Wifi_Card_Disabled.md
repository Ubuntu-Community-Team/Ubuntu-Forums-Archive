---
title: "Wifi Card Disabled"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by 22350 on 2007-02-21
I have a dell inspiron 2200.

It has the Broadcom 4318

Edgy is installed. driver is installed

I went through the Wifi troubleshooting guide and the computer sees the card, but it is disabled.  Not sure how to get the card to be enabled.

Any ideas??

---

### Post by gradedcheese on 2007-02-21
What do you mean by disabled?  Can you run "ifconfig" and "iwconfig" in a terminal and post the output here?

---

### Post by 22350 on 2007-02-21
mateo@mateo-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:03:88:3A  
          inet addr:10.0.1.6  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe03:883a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:161035 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:242782445 (231.5 MiB)  TX bytes:6398345 (6.1 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

mateo@mateo-laptop:~$ iwconfig
lo        no wireless extensions.mateo@mateo-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:03:88:3A  
          inet addr:10.0.1.6  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe03:883a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:161035 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:242782445 (231.5 MiB)  TX bytes:6398345 (6.1 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

mateo@mateo-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

mateo@mateo-laptop:~$ 


eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

mateo@mateo-laptop:~$

---

### Post by gradedcheese on 2007-02-21
ok.  we'll troubleshoot this from the shell if that's ok with you... my assumption is that you know the SSID of your access point and you aren't using WEP or other encryption... is that right?  You can see a list of access points like this:

```

iwlist eth1 scan

```

you can associate like this:

```

sudo iwconfig eth1 essid put_ssid_here

```

you can see the status like this:

```

iwconfig eth1

```

if that looks good, you can bring up the interface and ask for an IP address (if your router is doing DHCP)

```

sudo ifconfig eth1 up
sudo dhclient eth1

```

---

### Post by 22350 on 2007-02-21
mateo@mateo-laptop:~$ iwlist eth1 scan
eth1      No scan results
mateo@mateo-laptop:~$ sudo iwconfig eth1 essid paul
Password:
mateo@mateo-laptop:~$ iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mateo@mateo-laptop:~$ sudo ifconfig eth1up
eth1up: error fetching interface information: Device not found
mateo@mateo-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:90:4b:d7:a7:ba
Sending on   LPF/eth1/00:90:4b:d7:a7:ba
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
mateo@mateo-laptop:~$

---

### Post by 22350 on 2007-02-21
oh, and i really appreciate your help

---

### Post by gradedcheese on 2007-02-21
> 
mateo@mateo-laptop:~$ sudo ifconfig eth1up
eth1up: error fetching interface information: Device not found


you missed a space, it's 

```

sudo ifconfig eth1 up

```

in general, when you run in to a problem like this, don't continue to the next step since it won't help (until you fix it)

---

### Post by 22350 on 2007-02-21
> **gradedcheese said:**
> you missed a space, it's 

```

sudo ifconfig eth1 up

```

in general, when you run in to a problem like this, don't continue to the next step since it won't help (until you fix it)


Ok, new to this terminal thing

mateo@mateo-laptop:~$ sudo ifconfig eth1 up
Password:
SIOCSIFFLAGS: No such file or directory
mateo@mateo-laptop:~$

---

### Post by gradedcheese on 2007-02-21
ah, sorry, can you just do:

```

sudo ifconfig eth1

```

---

### Post by 22350 on 2007-02-21
mateo@mateo-laptop:~$ sudo ifconfig eth1
Password:
eth1      Link encap:Ethernet  HWaddr 00:90:4B:D7:A7:BA  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:1 

mateo@mateo-laptop:~$

---

### Post by gradedcheese on 2007-02-21
ok, now your eth1 is not longer disabled... are you associated? (see above post, with iwconfig commands) If so, now ask for an IP address (see above post, with dhclient commands)

---

### Post by 22350 on 2007-02-21
mateo@mateo-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:03:88:3A  
          inet addr:10.0.1.6  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe03:883a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:167794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:247089595 (235.6 MiB)  TX bytes:7646811 (7.2 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:215 (215.0 b)  TX bytes:215 (215.0 b)

mateo@mateo-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

mateo@mateo-laptop:~$

---

### Post by gradedcheese on 2007-02-21
right, as per my original post, try and associate:

```

sudo iwconfig eth1 essid put_your_ssid_here

```

---

### Post by 22350 on 2007-02-21
mateo@mateo-laptop:~$ sudo iwconfig eth1 essid paul
Password:
mateo@mateo-laptop:~$

---

### Post by gradedcheese on 2007-02-21
ok, now are you associated? :)  To check:

```

iwconfig eth1

```

---

### Post by 22350 on 2007-02-21
mateo@mateo-laptop:~$ iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mateo@mateo-laptop:~$

---

### Post by gradedcheese on 2007-02-21
ok, that means you failed to associate.  You didn't answer my original questions:
1) are you using WEP or other encryption on the access point?
2) do you get scan results?
```

iwlist eth1 scan

```

---

### Post by 22350 on 2007-02-21
> **gradedcheese said:**
> ok, that means you failed to associate.  You didn't answer my original questions:
1) are you using WEP or other encryption on the access point?
2) do you get scan results?
```

iwlist eth1 scan

```

no, i am not using wep.  no i don't get scan results.



mateo@mateo-laptop:~$ iwlist eth1 scan
eth1      No scan results
mateo@mateo-laptop:~$

---

### Post by corytoneill on 2007-02-21
i am having the same problem but i don't know my ssid, ihave the same wireless card

---

### Post by 22350 on 2007-02-22
So i read a thread that relates directly the the 4318 card:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

but it warns that you need a relitively fresh install.

so i decided to reinstall ubuntu 6.10.

when it started to load the dvd, i got this:
[IMG]http://www.pauloberman.com/wifihell.jpg[/IMG]

little blurry, but notice all of the errors for the wifi card.

what does this all mean??

---

### Post by gradedcheese on 2007-02-22
The way WiFi cards work is that there's a little CPU on the card itself, with Flash memory and RAM.  When the card is plugged in (or detected), the PC must send firmware (compiled software) to the card's CPU for it to run.  This firmware is what actually does most of the work in that card, without it it's essentially 'brainless'.  The error message means that the card got detected but the firmware sending step failed.  This is likely because the firmware image it tried to send is wrong for that card.  This should be easy to fix: you might be able to grab the right firmware online, or you can grab it off the Windows driver installation disk or something of that sort.  Until you do that, the card will unfortunately not work (even though it will be detected).

---

### Post by teaker1s on 2007-02-22
okay first things first have you followed ndiswrapper in the other thread?
If so I'm guessing ndiswrapper wasn't started, also do you have an ethernet connection to the internet for it avaliable?

```
sudo modprobe ndiswrapper
```
with any wireless switch on does wireless light come on?

next post results from ```
sudo ndiswrapper -l
``` and ```
iwconfig

```

I'm guessing ndiswrapper wasn't started

---

### Post by 22350 on 2007-02-22
ok will do, but did you look at the image of my screen on the last page.  it looks like the firmware didn't load.

---

### Post by teaker1s on 2007-02-22
okay I'm no expert on these things, but think one of two things happening
1) the native driver may not be blacklisted
2) the driver file isn't correct for your card and you require one from manufacturers cd or site

please look at this thread and work your way through to check you haven't missed a step
[http://ubuntuforums.org/showthread.php?t=285809]("http://ubuntuforums.org/showthread.php?t=285809")

---

### Post by 22350 on 2007-02-22
from the screen, it seems that the firmware isn't loading

---

### Post by 22350 on 2007-02-22
Ok, this is really starting to drive me nuts.....

1.  it looks like the the firmware isn't loaded, per the screen posted earlier.

2. if you use ndiswrapper, do you have to eliminate the bcm43xx driver?

3. when i try and follow the instructions at the link you listed, blacklist says that it can't find the bcm43xx driver:

mateo@mateo-laptop:~$ sudo gedit /ect/modprobe.d/blacklist
Password:

** (gedit:9612): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
mateo@mateo-laptop:~$ 

So, my question is:  Am i trying to enact two different methods of getting this card running?  one being the use of the bcm43xx firm ware and driver.  the other being the use of ndiswrapper.  

if you use ndiswrapper, do you still need the firmware loaded?  does anyone have a copy of the firmware, as my original system disks are gone?

WHY IS THIS SO HARD?

---

### Post by teaker1s on 2007-02-22
yours is typed incorrectly above
```
sudo gedit /etc/modprobe.d/blacklist
```

you are stopping native driver loading so we can use ndiswrapper with windows driver

---

### Post by 22350 on 2007-02-22
ok, that worked, here is what the terminal looked like:

mateo@mateo-laptop:~$ sudo gedit /etc/modprobe.d/blacklist
Password:
mateo@mateo-laptop:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
mateo@mateo-laptop:~$ 


does this mean that the driver  is blacklisted?

so next, i guess i need ndiswrapper and the windows driver.  where do i get these? i don't have the windows cd for this laptop.

also, do i still need the firmware for this card, as it didn't load when we installed the system?

---

### Post by teaker1s on 2007-02-22
okay, the native driver module has been removed, this is good as we won't get a conflict.

:mrgreen: \\:D/ 

okay well your broadcom uses the same driver as mine so mine should work, you will need to download the file and extract by double clicking on the archive

---

### Post by teaker1s on 2007-02-22
*
   

```
      sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.inf
```

```
Sudo modprobe ndiswrapper
```
    * Check to see if hardware found
      

```
      sudo ndiswrapper -l
```

should say driver and hardware present and light on, if it doesn't then post before rebooting and following next step so I can suggest


Setup ndiswrapper to load driver (and itself) at startup

    * Edit the following file:
      

```
      sudo gedit /etc/modules
```

    * Add a line which says:
      Code:

      ndiswrapper

    * Restart

---

### Post by 22350 on 2007-02-22
this is the error i get when i put in the first command:

mateo@mateo-laptop:~$ sudo ndiswrapper -i/home/mateo/Desktop/bcmwl5.inf
Password:
sudo: ndiswrapper: command not found
mateo@mateo-laptop:~$ 
mateo@mateo-laptop:~$

---

### Post by teaker1s on 2007-02-22
you have a typing error, you need a space between the command and the location

```
sudo ndiswrapper -i /home/mateo/Desktop/bcmwl5.inf
```

failing that

```
cd /home/mateo/Desktop
```

```
sudo ndiswrapper -i bcmwl5.inf
```

---

### Post by 22350 on 2007-02-22
i installed ndiswrapper and then ran the first command in your post:


mateo@mateo-laptop:~$ sudo ndiswrapper -i /home/mateo/Desktop/bcmwl5.inf
Password:
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
mateo@mateo-laptop:~$

---

### Post by teaker1s on 2007-02-22
your still not using the command as i typed

yours
 sudo ndiswrapper -i//home/mateo/Desktop/bcmwl5.inf

mine
sudo ndiswrapper -i /home/mateo/Desktop/bcmwl5.inf

okay so we now have a driver installed

```
sudo ndiswrapper -l
```

small L not i

post result

---

### Post by 22350 on 2007-02-22
mateo@mateo-laptop:~$ Sudo ndiswrapper -l
bash: Sudo: command not found
mateo@mateo-laptop:~$

---

### Post by teaker1s on 2007-02-22
my mistake linux is case sensitive should be little s

```
sudo ndiswrapper -l
```

---

### Post by 22350 on 2007-02-22
mateo@mateo-laptop:~$ sudo ndiswrapper -l
Password:
Installed drivers:
bcmwl5  invalid driver!
mateo@mateo-laptop:~$

---

### Post by 22350 on 2007-02-22
i feel like i am inventing cold fusion

---

### Post by gradedcheese on 2007-02-22
No, you're installing a Windows driver in Linux via a hacked together wrapper that translates system calls so that the Windows driver can support your card, which your chipset manufacturer refuses to release any documentation for (making writing a real driver for it next to impossible).  Basically, you're doing something that normally wouldn't even be possible, so I guess it is sort of whacky stuff ;)

---

### Post by 22350 on 2007-02-22
cool, based on where i was,     
What next??

---

### Post by teaker1s on 2007-02-22
okay we tried my version of the driver and it would seem that the one you want is named the same but customised for your hardware. you will need to download the appropriate windows driver for your country from dell and if the driver files are not in a folder and it is an exe file you will need cabextract or unzip.

I really must sleep as it's 03:29 and I must be out the house at 08:30- if you find an english speaking section of dell with the correct model of your machine I will download the driver and extract for you.

find and post a link to driver and I will extract, don't give up you are doing well, ndiswrapper isn't the easiest of projects:popcorn:

---

### Post by 22350 on 2007-02-22
i installed the driver on the page that was suggested, but i am starting to think that it isn't the right one.

i have the 4318 broadcom do we think that this is the right driver?, since the sudo command says that it is invalid?

---

### Post by 22350 on 2007-02-22
thanks, i am on it

---

### Post by teaker1s on 2007-02-22
off to sleep, but I'm subscribed to the thread and will return:KS

---

### Post by jackrobinson on 2007-02-22
> **22350 said:**
> I have a dell inspiron 2200.

It has the Broadcom 4318

Edgy is installed. driver is installed

I went through the Wifi troubleshooting guide and the computer sees the card, but it is disabled.  Not sure how to get the card to be enabled.

Any ideas??
have you tried this howto?
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by 22350 on 2007-02-22
thanks teaker1s

the driver for windows is at this location:

[http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE)

i really appreciate the help


ps.  do i need to remove the driver that is incorrect?

---

### Post by 22350 on 2007-02-22
yea, it didn't work for me.  not sure why not.

---

### Post by teaker1s on 2007-02-24
okay I  tried the link and get a 0 byte unextractable file, it may be that i'm not in usa so they block the download or it may be their server. I have looked at ndiswrapper and downloaded/extracted and archived the driver known to work on your chipset from what I found I hope your laptop is 32bit- thats the driver I've given you.

It is also known that kernel 2.6.17-11 kernel breaks wifi  
[http://www.ubuntuforums.org/showthread.php?t=358004]("http://www.ubuntuforums.org/showthread.php?t=358004")

to check if your using earlier or later kernel ```
uname -r
```

to remove a driver from ndiswrapper

```
sudo ndiswrappr -r bcmwl5
```


to install a driver, make sure you leave the .sys file in the same folder as the

```
sudo ndiswrappr - i bcmwl5.inf
```

different model but an excellent tutorial worth looking at [http://ubuntuforums.org/showthread.php?t=201902]("http://ubuntuforums.org/showthread.php?t=201902")
failing this compiled version of ndiswrapper may be the only way.

I'm sorry for delay I left at 8:30am and finished stripping/cleaning,fitting new parts and rebuilding the engine and road testing a landrover freelander at 23:45pm-so I jumped in a bath and fell into bed:(

---

### Post by swedish cook on 2007-02-25
I found this thread looking to fix wifi on ubuntu 6.10 on my mac mini G4 Broadcom 4318, this how to fixed it in one download and about 3 commands [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174). Note the guide says may not work if devices is v02, but worked ok for me !!

---

### Post by 22350 on 2007-03-04
ok, so i'm back for more fun.  i was gone on a job and couldn't follow up.

so teaker, i deleted the driver, but closed the terminal, so i re-entered the commands, to show you what i did.  the final command confirms that i did remove the driver on my first try:

mateo@mateo-laptop:~$ sudo ndiswrapper -r bcmwl5
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
mateo@mateo-laptop:~$ sudo ndiswrapper -e bcmwl5
Driver bcmwl5 is not installed.Use -l to list installed drivers
mateo@mateo-laptop:~$ 


So now i have downloaded the the exe windows file from the dell site and reposted it for you at this link:

[http://www.pauloberman.com/R115321.EXE.zip](http://www.pauloberman.com/R115321.EXE.zip)

do you think you could extract the USA driver for me?

Thanks


oh, ps i am running 2.6.17-10-generic

---

### Post by 22350 on 2007-03-04
tried to do an install the driver you suggested, which i extracted to the desktop, with this result:

mateo@mateo-laptop:~$ sudo ndiswrapper - i bcmwl5.inf
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
mateo@mateo-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
Installing bcmwl5
couldn't copy bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144.
mateo@mateo-laptop:~$

---

### Post by 22350 on 2007-03-04
ok, it looks like i finally flushed the driver, which apparently doesn't work for my machine:

mateo@mateo-laptop:~$ sudo ndiswrapper -e bcmwl5
Password:
Driver bcmwl5 is not installed.Use -l to list installed drivers
mateo@mateo-laptop:~$ sudo ndiswrapper -l
No drivers installed
mateo@mateo-laptop:~$

---

### Post by 22350 on 2007-03-04
Just finished perfecting cold fusion, but i still cant get this wifi card working under ubuntu.


did the install at:

[http://ubuntuforums.org/showthread.php?t=185174&highlight=extract+4318+driver+from+.exe](http://ubuntuforums.org/showthread.php?t=185174&highlight=extract+4318+driver+from+.exe)

after rolling the dice, i restarted and it didn't work, of course.

i ran modprobe in terminal and got this:

mateo@mateo-laptop:~$ modprobe bcm43xx
WARNING: Error inserting ieee80211_crypt (/lib/modules/2.6.17-10-generic/kernel/net/ieee80211/ieee80211_crypt.ko): Operation not permitted
WARNING: Error inserting ieee80211 (/lib/modules/2.6.17-10-generic/kernel/net/ieee80211/ieee80211.ko): Operation not permitted
WARNING: Error inserting ieee80211softmac (/lib/modules/2.6.17-10-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko): Operation not permitted
FATAL: Error inserting bcm43xx (/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko): Operation not permitted
mateo@mateo-laptop:~$

---

### Post by 22350 on 2007-03-04
i just read in that instruction, that it installs the firmware from the driver, but when i typed sudo ndiswrapper -l into the teminal, i got this:

mateo@mateo-laptop:~$ sudo ndiswrapper -l
Password:
No drivers installed
mateo@mateo-laptop:~$ 


seems like this could be a problem

---

### Post by teaker1s on 2007-03-04
okay I've managed to get "usa" driver,  we need to install, if need be copy to text file so you get commands right

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils ndiswrapper-utils-1.1 ndiswrapper-utils-1.8 unzip

```

now with the R115321.EXE create a folder called "r115321" and paste the exe into it as we are going to unzip it

now "cd" to directory example

```
cd /home/daniel/r115321
```

```
sudo unzip R115321.EXE
```

```
gksudo  nautilus
``` in "r115321" we created there is a driver folder,copy all contents into main "r115321"

```
sudo ndiswrapper -i bcmwl5.inf
```

```
sudo ndiswrapper -l
``` do we have driver/hardware present?

**reboot and  wireless switch on**
```
sudo modprobe ndiswrapper
``` is light on?

if so:-
when you are happy that your wireless networking is correct then

```
gksudo gedit /etc/modules
```

Add the word ndiswrapper and save the file using "save as" this will then load everytime you boot




******note linux is case sensitive, eg mine and MINE are two different files with same name, same with commands********

---

### Post by 22350 on 2007-03-04
just saw your reply, working...

---

### Post by Prometheus.172214 on 2007-03-04
You can also give this a try.....

[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

I had to blacklist my Wifi Controller, remove all Wifi Managers including Network Manager and then get the Wifi fixed and then use Wireless Radar to connect.

Teaker1s  is showing you the right set of commands.

---

### Post by 22350 on 2007-03-04
ok, got through the first few steps.  made the folder on the desktop and unstuffed the driver exe file there.  when i try to copy the driver files out of the duplicate folder into the main folder, it says i don't have the rights and there is an error.  i have little locks on all of the icons.

i also did this:


(nautilus:5232): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:5232): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
mateo@mateo-laptop:~/Desktop/r115321$ 


not sure what next.  i did try and run the ndiswrapper command, but didn't work

---

### Post by 22350 on 2007-03-04
ok, i ran your instructions from root.  everything seemed good.  it said that the driver was already installed, so i un-installed it and reinstalled it from the folder that we created.  after i got this:


mateo@mateo-laptop:~$ sudo ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 
bcmwl5o invalid driver!
mateo@mateo-laptop:~$ 

i then started the card  with sudo modproble ndiswrapper

that worked. i went into system - administration - network and activated the card.

no go!!

---

### Post by 22350 on 2007-03-05
ok, now my wife is going to divorce me if i don't stop screwing around with this.

here is the latest:

i reloaded the whole os, to get a fresh start.  

i decided to try linuxant and it didn't work, of course.  i did see an output which said something like "bcm43xx micros5.fw" (sure i spelled that wrong) failed to load or wasn't found.

i located what appeared to be a version of that file and installed it.  

still nothing works.

it is frustrating, because i am puting this machine together for a friend and i deleted windows.  now i have a machine, which i cant get online for him.

anyone have any experience with linux ant or any idea how to get this thing going.

---

### Post by teaker1s on 2007-03-06
gksudo nautilus should give you a root file browser appear and you should be able to copy and alter permissions at will

---

### Post by 22350 on 2007-03-06
that's true, it did.  anyway, did a fresh install and tried driverloader.  didn't work either.

it appears that the firmware isn't loading.

tried to install the firmware, by downloading a copy off the internet and using a command i found.  didn't make a difference.

i am wondering, can these machines be controlled remotely?  i feel like i am missing something.

thanks,

paul

---

### Post by 22350 on 2007-03-06
i am starting another fresh install, in preparation for a last attempt at getting this wifi card working.


during the start up from the install dvd.  i get the text bcm43xx micocode5.fw missing or failed to load.  i think that this might be at the root of all of my problems.  if the firmware isn't loading at startup, doesn't that mean that the card won't work??

---

### Post by teaker1s on 2007-03-06
for ndiswrapper you must blacklist native driver-see link in my signature

---

### Post by 22350 on 2007-03-06
teaker, are you in instant messanger?

---

### Post by teaker1s on 2007-03-06
I'm not on instant messenger, may I suggest carefully following this link
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

I must go to bed as I have my commercial course tomorrow an I'm doing a year course in a month of one day a week =4 days.

please follow the link and if you need more help then please reply on this thread-I'm watching it:KS

---

### Post by 22350 on 2007-03-06
looked at the page you referred me to and it referrers to the 4311, not the 4318.  is it the same process?

---

### Post by 22350 on 2007-03-06
went through the instruction listed on your link.

got to step 6.  the output listed eth1 as the location of the wireless card.  i followed the instructions, to comment out the eth1 line and ran iwconfig again, but still got the same read out.

blah

---

### Post by 22350 on 2007-03-07
another update:

restarted the computer and the card information, that was listed under eth1, disappeared.  i guess the "commenting out" worked, but it didn't reassign itself to wlan0, like it was supposed to.

---

### Post by teaker1s on 2007-03-07
bcm 4318 and bcm 4311 use same named driver,  have you got it to light up yet?

---

### Post by 22350 on 2007-03-07
no, still stuck on 6 check above to see what is going on.  won't assign the card to wlan0.  commented out the eth1 location, but still won't give me wlan0

---

### Post by 22350 on 2007-03-07
other than that, everything seemed to be moving forward correctly.  i don't think that the inspiron 2200 has a wifi light.

---

### Post by teaker1s on 2007-03-07
okay here for a little while, lets try a quick and dirty way of getting you going. Remove the # you put to  force card to wlan.
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils ndiswrapper-utils-1.1 ndiswrapper-utils-1.8 unzip
```
```
sudo modprobe ndiswrapper
```
```
sudo ndiswrapper -l
``` little L not big L
post output do we have a light?

---

### Post by 22350 on 2007-03-07
darn it, the laptop is sitting up at my office.  when i get there, i will do it and post the results.  

thanks for all the help. i am in california, so it makes this process a little sticky.

did you catch the pics i sent you?

paul

---

### Post by teaker1s on 2007-03-07
sure did, love the old school cars, lime green suits them well. 

if we can get the light on then we can install 

```
sudo apt-get network-manager-gnome
``` 
while we may not easily be able to get wlan to show up, if the light comes on then if ubuntu sees it as eth1 or eth2 we can still get desktop wireless easily.


I truely belive that the wiki documentation is the best howto to follow, I would also recommend that people recheck they remember doing each stage-I've done it before and missed a step:lolflag: 


I've had my commercial electrical course and it's mind numbing, we went over many things inc cable factors for conduit (ie calculating capacity while leaving sufficient cooling and also factoring in bends and de-rating cable capacity).
In the uk from jan 2005 there is legislation to stop DIY electrical and improve Electrical safety-It is now very much a design of a service

---

### Post by 22350 on 2007-03-07
what did you  think of the 36hp vespa?

---

### Post by teaker1s on 2007-03-07
fun, I've a Suzuki Bandit 600

---

### Post by 22350 on 2007-03-07
ok, ran the first instruction, to install ndiswrapper.  said it wasn't found.  downloaded it and decompressed it to the desktop.  cd'd to the directory and ran the three commands you suggested:

mateo@mateo-laptop:~/Desktop/ndiswrapper-1.8$ sudo apt-get install ndiswrapper-common ndiswrapper-utils ndiswapper-utils1.1 ndiswrapper-utils-1.8 unzip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswapper-utils1.1
mateo@mateo-laptop:~/Desktop/ndiswrapper-1.8$ sudo modprobe ndiswrapper
mateo@mateo-laptop:~/Desktop/ndiswrapper-1.8$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
mateo@mateo-laptop:~/Desktop/ndiswrapper-1.8$ 


i don't know if this thing has a wifi light and if it does, not sure where it is??

---

### Post by 22350 on 2007-03-08
ok,  i downloaded the ndiswrapper 1.8 and went through the directions attached with it.  i also downloaded the driver which was posted in the read me file with the software.

i went through all of the instructions and install seemed to go fine. 

the one problem i keep seeming to have is that the card keeps turning up under eth1, rather than wlan0.  i think that this might be why i am still getting failure with the card.

anyway, here is a copy of the terminal from the install:

mateo@mateo-laptop:~$ sudo ndiswrapper -e
Password:
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid'
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
mateo@mateo-laptop:~$ sudo ndiswrapper -r bcmwl5.inf
couldn't delete /etc/ndiswrapper/bcmwl5.inf: No such file or directory
mateo@mateo-laptop:~$ sudo ndiswrapper -r bcmwl5
mateo@mateo-laptop:~$ sudo ndiswrapper -l
mateo@mateo-laptop:~$ cd /home/mateo/Desktop
mateo@mateo-laptop:~/Desktop$ cd /ndiswrapper-1.8
bash: cd: /ndiswrapper-1.8: No such file or directory
mateo@mateo-laptop:~/Desktop$ cd /home/mateo/Desktop/ndiswrapper-1.8
mateo@mateo-laptop:~/Desktop/ndiswrapper-1.8$ make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
/bin/rm: cannot remove `/sbin/loadndisdriver': Permission denied
make: *** [uninstall] Error 1
mateo@mateo-laptop:~/Desktop/ndiswrapper-1.8$ su ~
Unknown id: /home/mateo
mateo@mateo-laptop:~/Desktop/ndiswrapper-1.8$ su~
bash: su~: command not found
mateo@mateo-laptop:~/Desktop/ndiswrapper-1.8$ su -
Password: 
root@mateo-laptop:~# cd /home/mateo/Desktop/ndiswrapper-1.8
root@mateo-laptop:/home/mateo/Desktop/ndiswrapper-1.8# make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
removing /usr/sbin/ndiswrapper
removing /lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper': Is a directory
removing /lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
removing /lib/modules/2.6.17-10-generic/misc/ndiswrapper.ko
root@mateo-laptop:/home/mateo/Desktop/ndiswrapper-1.8# make
make -C driver
make[1]: Entering directory `/home/mateo/Desktop/ndiswrapper-1.8/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/mateo/Desktop/ndiswrapper-1.8/driver \
                DRIVER_VERSION=1.8
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  LD      /home/mateo/Desktop/ndiswrapper-1.8/driver/built-in.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/hal.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/iw_ndis.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/loader.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/misc_funcs.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/ndis.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/ntoskernel.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/ntoskernel_io.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/pe_linker.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/pnp.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/proc.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/wrapndis.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/wrapper.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/usb.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/divdi3.o
  LD [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/mateo/Desktop/ndiswrapper-1.8/driver/ndiswrapper.mod.o
  LD [M]  /home/mateo/Desktop/ndiswrapper-1.8/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/mateo/Desktop/ndiswrapper-1.8/driver'
make -C utils
make[1]: Entering directory `/home/mateo/Desktop/ndiswrapper-1.8/utils'
gcc -g -Wall -DUTILS_VERSION=\"1.7\"  -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/mateo/Desktop/ndiswrapper-1.8/utils'
root@mateo-laptop:/home/mateo/Desktop/ndiswrapper-1.8# make install
make -C driver install
make[1]: Entering directory `/home/mateo/Desktop/ndiswrapper-1.8/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/mateo/Desktop/ndiswrapper-1.8/driver \
                DRIVER_VERSION=1.8
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
mkdir -p /lib/modules/2.6.17-10-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.17-10-generic/misc
/sbin/depmod -a
make[1]: Leaving directory `/home/mateo/Desktop/ndiswrapper-1.8/driver'
make -C utils install
make[1]: Entering directory `/home/mateo/Desktop/ndiswrapper-1.8/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/mateo/Desktop/ndiswrapper-1.8/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
root@mateo-laptop:/home/mateo/Desktop/ndiswrapper-1.8# cd /home/mateo/Desktop/driver
root@mateo-laptop:/home/mateo/Desktop/driver# ndiswrapper -i bcmwl5a.inf
Installing bcmwl5a
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
root@mateo-laptop:/home/mateo/Desktop/driver# ndiswrapper -l
Installed ndis drivers:
bcmwl5a         driver present, hardware present 
root@mateo-laptop:/home/mateo/Desktop/driver# modprobe ndiswrapper
root@mateo-laptop:/home/mateo/Desktop/driver# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@mateo-laptop:/home/mateo/Desktop/driver#

---

### Post by teaker1s on 2007-03-08
appears on 
> eth1 IEEE 802.11g ESSIDff/any
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power:25 dBm
RTS thr:2347 B Fragment thr:2346 B
Encryption keyff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


with ethernet connection
```
sudo apt-get install network-manager-gnome
```

when you are happy that your wireless networking is correct then
```

gksudo gedit /etc/modules
```

Add the word "ndiswrapper " if not there already and save the file using "save as" this will then load everytime you boot



now on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

---

### Post by 22350 on 2007-03-08
ok took the first step and got this:

mateo@mateo-laptop:~$ sudo apt-get install network-manager-gnome
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dhcdbd libnl1-pre6 libnm-util0 network-manager
The following NEW packages will be installed:
  dhcdbd libnl1-pre6 libnm-util0 network-manager network-manager-gnome
0 upgraded, 5 newly installed, 0 to remove and 132 not upgraded.
Need to get 726kB of archives.
After unpacking 2863kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main dhcdbd 1.14-2ubuntu2 [47.7kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libnl1-pre6 1.0~pre5+svn21-2ubuntu2 [76.5kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libnm-util0 0.6.3-2ubuntu6 [123kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main network-manager 0.6.3-2ubuntu6 [228kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main network-manager-gnome 0.6.3-2ubuntu6 [251kB]
Fetched 726kB in 17s (41.5kB/s)                                                
Selecting previously deselected package dhcdbd.
(Reading database ... 89958 files and directories currently installed.)
Unpacking dhcdbd (from .../dhcdbd_1.14-2ubuntu2_i386.deb) ...
Selecting previously deselected package libnl1-pre6.
Unpacking libnl1-pre6 (from .../libnl1-pre6_1.0~pre5+svn21-2ubuntu2_i386.deb) ...
Selecting previously deselected package libnm-util0.
Unpacking libnm-util0 (from .../libnm-util0_0.6.3-2ubuntu6_i386.deb) ...
Selecting previously deselected package network-manager.
Unpacking network-manager (from .../network-manager_0.6.3-2ubuntu6_i386.deb) ...
Selecting previously deselected package network-manager-gnome.
Unpacking network-manager-gnome (from .../network-manager-gnome_0.6.3-2ubuntu6_i386.deb) ...
Setting up dhcdbd (1.14-2ubuntu2) ...
 * Reloading system message bus config                                   [ ok ] 
 * Stopping DBUS aware dhcp client: dhcdbd                               [ ok ] 
 * Starting DBUS aware dhcp client: dhcdbd                               [ ok ] 

Setting up libnl1-pre6 (1.0~pre5+svn21-2ubuntu2) ...

Setting up libnm-util0 (0.6.3-2ubuntu6) ...

Setting up network-manager (0.6.3-2ubuntu6) ...
 * Reloading system message bus config                                   [ ok ] 
 * Stopping NetworkManager daemon                                        [ ok ] 
 * Starting NetworkManager daemon                                        [ ok ] 
 * Stopping NetworkManager dispatcher                                    [ ok ] 
 * Starting NetworkManager dispatcher                                    [ ok ] 

Setting up network-manager-gnome (0.6.3-2ubuntu6) ...

mateo@mateo-laptop:~$ 


[SIZE="5"]then the wifi card disappeared from the network manager, under administration[/SIZE]

---

### Post by teaker1s on 2007-03-08
network-manager-gnome is on desktop panel by volume icon normally,click on it asn see if you can select avaliable wireless network

---

### Post by 22350 on 2007-03-08
yes, the network manager is there, but it doesn't list any wireless networks.

i thought that i read some other instructions, posted by you about 2 hours ago.

something about typing in an instruction with ndiswrapper and making load at start up??

i wasn't able to do that, as the instructions seem to be missing

paul

---

### Post by 22350 on 2007-03-08
ok, i ran the command:

sudo ndiswrapper

and got a list of the commands

i then ran the command to associate the driver with the device id xxxx:xxxx

it then said that the device would be associated with the  bcmwl5a driver.

i then ran modprobe ndiswrapper.

next i added ndiswrapper to the module file under the ect directory.

restarted and guess what


STILL NOTHING!!!!

the network manager now sees the card and says that it is activated.  


AAAAAAHHHHHHHHHHHH!!!!!!!!!!!!!!!!!!!!

i tried linux a couple of years ago, with suse, on another dell.  I had exactly the same problem, but solved it with driverloader.  tried it on this and it didn't work either.

i just wonder why in all this time, no one had devised a more solid solution for such a common problem.

---

### Post by teaker1s on 2007-03-09
? are you using repository version or downloaded directly from ndiswrapper project?
if from your repositories this is most likely why it's not working as verson too old

---

### Post by 22350 on 2007-03-09
using the one which was pointed to from the info file, with ndiswrapper 1.8


bcmwl5a

---

### Post by 22350 on 2007-03-09
it's the driver listed at this link:

[http://ndiswrapper.sourceforge.net/wiki/index.php/List](http://ndiswrapper.sourceforge.net/wiki/index.php/List)

---

### Post by teaker1s on 2007-03-09
[http://sourceforge.net/project/showfiles.php?group_id=93482]("http://sourceforge.net/project/showfiles.php?group_id=93482")

and the driver from laptop manufacturer

---

### Post by 22350 on 2007-03-09
ok, i have the laptop manufacturers driver.

the version of ndiswrapper, i have installed is 1.81, which seems to be newer than the one you have linked.

what do i do?  uninstall ndiswrapper and the driver? if so, can you give me the correct commands?  i think i know how to uninstall the driver, but not sure how to do ndiswrapper.

thanks

---

### Post by teaker1s on 2007-03-09
I'm still trying to get my head round why this is being such a problem:confused: , what output does 
```
iwconfig
``` give?

At this point I'd hoped we could just get it to work, if iwconfig shows card alive we could try uninstalling network-manager-gnome and trying wifi radar

---

### Post by 22350 on 2007-03-09
mateo@mateo-laptop:~$ sudo ndiswrapper
Password:
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
mateo@mateo-laptop:~$ sudo ndiswrapper -e bcmwl5a
mateo@mateo-laptop:~$ sudo ndiswrapper -l
No drivers installed

---

### Post by 22350 on 2007-03-09
mateo@mateo-laptop:~$ iwconfig
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

mateo@mateo-laptop:~$

---

### Post by 22350 on 2007-03-09
mateo@mateo-laptop:~/Desktop/ndiswrapper-1.8$ su -
Password: 
root@mateo-laptop:~# cd /home/mateo/Desktop/ndiswrapper-1.8
root@mateo-laptop:/home/mateo/Desktop/ndiswrapper-1.8# make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
removing /usr/sbin/ndiswrapper
removing /lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper': Is a directory
removing /lib/modules/2.6.17-10-generic/misc/ndiswrapper.ko
root@mateo-laptop:/home/mateo/Desktop/ndiswrapper-1.8#

---

### Post by teaker1s on 2007-03-09
other than installing the driver, checking driver and hardware are installed you have you
ndiswapper-common ndiswrapper ndiswrapper-utils ndiswrapper-utils-1.8 WITH SYNAPTIC?
 Other suggestion:-uninstalling network-manager-gnome and trying wifi radar -I'm stumped

---

### Post by 22350 on 2007-03-09
ok, i've uninstalled dniswrapper 1.8 and downloaded 1.38

i have also uninstalled the driver, ndiswrapper recommended, in lieu of the driver from the manufacturer's site.

i am going to install the two and associate the driver with the device.  i will put up a copy of the terminal for you to look at.

---

### Post by teaker1s on 2007-03-09
okay:KS

---

### Post by 22350 on 2007-03-09
mateo@mateo-laptop:~$ su -
Password: 
root@mateo-laptop:~# cd /home/mateo/Desktop/ndiswrapper-1.38
root@mateo-laptop:/home/mateo/Desktop/ndiswrapper-1.38# make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /usr/sbin/ndiswrapper-buginfo
root@mateo-laptop:/home/mateo/Desktop/ndiswrapper-1.38# make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
root@mateo-laptop:/home/mateo/Desktop/ndiswrapper-1.38# make
make -C driver
make[1]: Entering directory `/home/mateo/Desktop/ndiswrapper-1.38/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/mateo/Desktop/ndiswrapper-1.38/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  LD      /home/mateo/Desktop/ndiswrapper-1.38/driver/built-in.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/crt.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/hal.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/iw_ndis.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/loader.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/ndis.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/ntoskernel.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/ntoskernel_io.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/pe_linker.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/pnp.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/proc.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/rtl.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/wrapmem.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/wrapndis.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/wrapper.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/usb.o
  CC [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/divdi3.o
  LD [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/mateo/Desktop/ndiswrapper-1.38/driver/ndiswrapper.mod.o
  LD [M]  /home/mateo/Desktop/ndiswrapper-1.38/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/mateo/Desktop/ndiswrapper-1.38/driver'
make -C utils
make[1]: Entering directory `/home/mateo/Desktop/ndiswrapper-1.38/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/mateo/Desktop/ndiswrapper-1.38/utils'
root@mateo-laptop:/home/mateo/Desktop/ndiswrapper-1.38# make install
make -C driver install
make[1]: Entering directory `/home/mateo/Desktop/ndiswrapper-1.38/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/mateo/Desktop/ndiswrapper-1.38/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
echo /lib/modules/2.6.17-10-generic/misc
/lib/modules/2.6.17-10-generic/misc
mkdir -p /lib/modules/2.6.17-10-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.17-10-generic/misc
/sbin/depmod -a 2.6.17-10-generic -b /
make[1]: Leaving directory `/home/mateo/Desktop/ndiswrapper-1.38/driver'
make -C utils install
make[1]: Entering directory `/home/mateo/Desktop/ndiswrapper-1.38/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/mateo/Desktop/ndiswrapper-1.38/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
root@mateo-laptop:/home/mateo/Desktop/ndiswrapper-1.38# sudo ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid'
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
root@mateo-laptop:/home/mateo/Desktop/ndiswrapper-1.38# cd /home/mateo/Desktop/driver
root@mateo-laptop:/home/mateo/Desktop/driver# sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper line 174.
root@mateo-laptop:/home/mateo/Desktop/driver# cd /home/mateo/Desktop/driver
root@mateo-laptop:/home/mateo/Desktop/driver# sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
root@mateo-laptop:/home/mateo/Desktop/driver# sudo ndiswrapper -e bcmwl5
root@mateo-laptop:/home/mateo/Desktop/driver# sudo ndiswrapper -e bcmwl5.inf
couldn't delete /etc/ndiswrapper/bcmwl5.inf: No such file or directory
root@mateo-laptop:/home/mateo/Desktop/driver# sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
root@mateo-laptop:/home/mateo/Desktop/driver# sudo ndiswrapper -i bcmwl5.sys
installing bcmwl5.sys ...
couldn't get manufacturer section - installation may be incomplete
root@mateo-laptop:/home/mateo/Desktop/driver# sudo ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid'
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
root@mateo-laptop:/home/mateo/Desktop/driver# sudo ndiswrapper -a 14e4:4318 bcmwl5.inf
ls: /etc/ndiswrapper/bcmwl5.inf/: No such file or directory
driver 'bcmwl5.inf' is not installed (properly)!
root@mateo-laptop:/home/mateo/Desktop/driver# sudo ndiswrapper -a 14e4:4318 bcmwl5
couldn't create symlink for "14E4:4311:0007:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4311:0008:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4311.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312:0007:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312:0008:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4318:0005:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4318:0006:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4318.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4319:0005:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4319:0006:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4319.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320:0001:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320:0002:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320:0003:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320:0004:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4324:0001:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4324:0002:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4324:0003:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4324:0004:1028.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4324.5.conf": File exists -
installation may be incomplete
driver 'bcmwl5' is not installed (properly)!
root@mateo-laptop:/home/mateo/Desktop/driver#

---

### Post by teaker1s on 2007-03-09
99% sure should be
```
sudo ndiswrapper -i bcmwl5.inf
``` if .sys etc are required then they will be used provided they are in the same directory

---

### Post by 22350 on 2007-03-09
mateo@mateo-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
Password:
driver bcmwl5 is already installed
mateo@mateo-laptop:~$

---

### Post by teaker1s on 2007-03-09
can't see hardware but
```
sudo modprobe ndiswrapper
```
```
sudo ndiswrapper -l
``` 
```
lwconfig
```

post output, I fail to see why we are having a mission with this when It's straight forward on 99% of computers. 

Possibly does this laptop have a wireless setting in bios(some with software switch can be forced on by bios setting) 
Other than this I would suggest consulting the ndiswrapper project.

---

### Post by 22350 on 2007-03-09
mateo@mateo-laptop:~$ sudo modprobe ndiswrapper
Password:
mateo@mateo-laptop:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
bcmwl5.sys : invalid driver!
mateo@mateo-laptop:~$ lwconfig
bash: lwconfig: command not found
mateo@mateo-laptop:~$ lwconfig
bash: lwconfig: command not found
mateo@mateo-laptop:~$ 



bios is set to default on. switch is hardware

---

### Post by teaker1s on 2007-03-09
> **22350 said:**
> mateo@mateo-laptop:~$ sudo modprobe ndiswrapper
Password:
mateo@mateo-laptop:~$ sudo ndiswrapper -l
[COLOR="Red"]bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
bcmwl5.sys : invalid driver![/COLOR]
mateo@mateo-laptop:~$ lwconfig
bash: lwconfig: command not found
mateo@mateo-laptop:~$ lwconfig
bash: lwconfig: command not found
mateo@mateo-laptop:~$ 



bios is set to default on. switch is hardware

okay well if you have the utilities I suggested installed then it would suggest that everything is okay as far as the point the driver is installed. 
Provided you have all the driver files in the same directory-we can surmise that ndiswrapper dislikes driver. all I can suggest is looking here for the driver
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

---

### Post by 22350 on 2007-03-09
already went down that road.  didn't work

---

### Post by teaker1s on 2007-03-09
I can only suggest contacting ndiswrapper team and outlining what you have tried. I'm out of Ideas why your wireless fails to work, we've got the utilities installed, ndiswrapper is installed and we have a driver known to work.

I feel for your fustration and am at a loss what to suggest, unless one last thing- are you 100% sure that native kernel driver is blacklisted?

---

### Post by 22350 on 2007-03-09
let's give that a try again.  can you shoot me the command?

also, how do in install the .sys file?

---

### Post by teaker1s on 2007-03-09
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-ea76065f30b99d3b8472289cd049e2b141856b55]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-ea76065f30b99d3b8472289cd049e2b141856b55")

provided bcmwl5.inf is installed and the .sys files have been in the same directory then ndiswrapper has automatically used them

---

### Post by 22350 on 2007-03-09
mateo@mateo-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
Password:
blacklist bcm43xx
mateo@mateo-laptop:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
bcmwl5.sys : invalid driver!
mateo@mateo-laptop:~$ sudo ndiswrapper -e bcmwl5.sys
mateo@mateo-laptop:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
mateo@mateo-laptop:~$ sudo ndiswrapper -e bcmw43xx
couldn't delete /etc/ndiswrapper/bcmw43xx: No such file or directory
mateo@mateo-laptop:~$

---

### Post by teaker1s on 2007-03-10
time to consult the ndiswrapper team, for further guidance

---

### Post by 22350 on 2007-03-10
do you just make a post on their forum page?  is that how it works?

---

### Post by teaker1s on 2007-03-10
try the forums:popcorn:

---

### Post by 22350 on 2007-03-11
you want to hear funny, i think the antenna on this wifi card is disconnected.

didn't work under windows, unless i stand 2 feet from the base station.

---

### Post by teaker1s on 2007-03-11
no worries- I'm just glad you have a cause of your problem

---

### Post by Goliath! on 2007-03-13
I spent the last two days slogging thru forums and IRCs and everything else.  This thread EXACTLY described my problem, except that the antena of my card was not disconnected.  The network card is inside my Dell D610.  It works fine from XP.

In desperation I pulled out an old, old Netgear wireless card and plugged it into the pci slot.  I acitvated the connection, and I am now posting on this forum wirelessly.  No screwing with drivers, no ndiswrapper, nothing.  IT JUST WORKS.

Lesson: Don't use anything from Dell.

Many many thanks to 22350 and gradedcheese and teaker1s.  You are my heros!

---

