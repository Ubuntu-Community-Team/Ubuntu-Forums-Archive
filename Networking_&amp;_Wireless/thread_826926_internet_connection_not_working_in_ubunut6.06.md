---
title: "internet connection not working in ubunut6.06"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by new_fan_of_linux on 2008-06-12
Hello everyone,

I have ubuntu 6.06 and an ADSL modem with ethernet cable which goes in my laptop. My internet is not working now. I went to system->administration->networking and then choose the modem connection. when i checked on the enable this device, it asks for phone number and Dial-prefix. As such i have a normal ADSL modem with dynamic ip with broadband. I tried my phone number in this but it is not proper.

I tried all the commands like
sudo dhclient eth0
sudo ifdown eth0
sudo ifup eth0

but still no progress. The problem is clear that the modem device is not activated but i dont know how to activate it. It asks for phone number and dial prefix options:(

---

### Post by superprash2003 on 2008-06-12
you dont have to configure modem connection mate, thats for dial up not broadband.. does your ADSL require you to dial to connect to the internet or does your modem do the dialing? if you used windows before, did you require to dial to connect to the internet? or did internet work as soon as you switch on your modem?

---

### Post by new_fan_of_linux on 2008-06-12
> **superprash2003 said:**
> you dont have to configure modem connection mate, thats for dial up not broadband.. does your ADSL require you to dial to connect to the internet or does your modem do the dialing? if you used windows before, did you require to dial to connect to the internet? or did internet work as soon as you switch on your modem?

Hello sir,

I have an ADSL broadband connection and i dont have to do anything in windows. I just switch on the modem and windows auto-detect it and internet works..

---

### Post by new_fan_of_linux on 2008-06-12
> **new_fan_of_linux said:**
> Hello sir,

I have an ADSL broadband connection and i dont have to do anything in windows. I just switch on the modem and windows auto-detect it and internet works..

Hello,

I checked in my system->administration->networking
But here there are only two option in the general tab i.e. wireless connection and modem connection. There is no ethernet connection in that list

I think ubuntu has not detected my ethernet device. Is there any solution..

---

### Post by new_fan_of_linux on 2008-06-12
> **new_fan_of_linux said:**
> Hello,

I checked in my system->administration->networking
But here there are only two option in the general tab i.e. wireless connection and modem connection. There is no ethernet connection in that list

I think ubuntu has not detected my ethernet device. Is there any solution..

Can someone help me how to configure my ubuntu so that it detects the ethernet connection also

---

### Post by kg87 on 2008-06-12
My suggestion would be to download a newer version of ubuntu, I tried 6.06 (when i first started using it), and got error after error. 7.04 proved awesome as everything worked out of the box. 8.04 just got better :D

** Even if you dont install it, run from liveCD and see what happens, like Dr Pepper, whats the worst that could happen? **

---

### Post by toolzen on 2008-06-12
The way our broadband connection works is that the modem assigns IP addresses to the computer/router connected to it, so I'll assume the same for yours.

As far as finding out if Ubuntu set up your ethernet device:

Open a terminal and type in *sudo ifconfig* and see if you have a listing other than "lo."

Like mine looks like this:

eth0      Link encap:Ethernet  HWaddr 00:0X:eX:12:176:79
          inet addr:192.168.254.201  Bcast:192.168.254.255            Mask:255.255.255.0
          inet6 addr: f90::132:a2ee:ee11:1111/22 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:299275 errors:684 dropped:0 overruns:0 frame:699
          TX packets:337234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:148961660 (142.0 MB)  TX bytes:36048215 (34.3 MB)
          Interrupt:12


If you don't see something similar then your net adapter probably wasn't recognized and installed. Remember you'll probably see the above for an adapter called "lo" but ignore that one. If you see a listing for something like *eth0* or some such that looks like the above, then your net adapter was probably installed. So see if you get that and we'll go from there.

---

### Post by superprash2003 on 2008-06-12
@new_fan_of_linux
  go to the terminal and type ifconfig and paste the output here
   better upgrade to a more stable release like ubuntu 7.10

---

### Post by new_fan_of_linux on 2008-06-13
> **toolzen said:**
> The way our broadband connection works is that the modem assigns IP addresses to the computer/router connected to it, so I'll assume the same for yours.

As far as finding out if Ubuntu set up your ethernet device:

Open a terminal and type in *sudo ifconfig* and see if you have a listing other than "lo."

Like mine looks like this:

eth0      Link encap:Ethernet  HWaddr 00:0X:eX:12:176:79
          inet addr:192.168.254.201  Bcast:192.168.254.255            Mask:255.255.255.0
          inet6 addr: f90::132:a2ee:ee11:1111/22 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:299275 errors:684 dropped:0 overruns:0 frame:699
          TX packets:337234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:148961660 (142.0 MB)  TX bytes:36048215 (34.3 MB)
          Interrupt:12


If you don't see something similar then your net adapter probably wasn't recognized and installed. Remember you'll probably see the above for an adapter called "lo" but ignore that one. If you see a listing for something like *eth0* or some such that looks like the above, then your net adapter was probably installed. So see if you get that and we'll go from there.

The output of ifconfig in my laptop is :




*********************************************
eth0      Link encap:Ethernet  HWaddr 00:1F:3C:54:E6:EB
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:fe7ff000-fe7fffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)


What do you suggest about installing ubuntu 7.10. will it solve the purpose.

---

### Post by shameel on 2008-06-13
I am also facing the same problem with my ADSL service. But i am using Ubuntu 8.04. The link of  thread is [here]("http://ubuntuforums.org/showthread.php?p=5176021#post5176021"). 

So guys come to my thread and help me as well. 

Regards.

---

### Post by superprash2003 on 2008-06-13
@new_fan_of_linux
  i dont think you would need to actually..cause your ifconfig output shows eth0 which means it does detect your LAN card.. go to system->administraton->network and go to eth0 properties and set it to DHCP instead of Roaming mode and then post your ifconfig output again

---

### Post by toolzen on 2008-06-13
Ok, open a terminal and try:

sudo ifconfig eth0 down
sudo ifconfig eth0 dhcp up

and then open firefox or ping something to see if you got a connection.

anything good happen then?

Just to clarify - you don't use a router? You just have your computer hooked up via ethernet cable to your modem, which is hooked up to a phone jack, right?

---

### Post by new_fan_of_linux on 2008-06-18
> **toolzen said:**
> Ok, open a terminal and try:

sudo ifconfig eth0 down
sudo ifconfig eth0 dhcp up

and then open firefox or ping something to see if you got a connection.

anything good happen then?

Just to clarify - you don't use a router? You just have your computer hooked up via ethernet cable to your modem, which is hooked up to a phone jack, right?

Yes, my PC is connected via a wired internet connection which comes from my telephone. I went to system->Administrator->Networks, but here it shows wlan0 as active device and it is active through eth0.
I have tried the commands like
sudo dhclient eth0
sudo ifdown eth0
sudo ifup eth0
But no success was there. I will however, try the commands suggested by you also.

Thanks for your support

---

### Post by ettercap on 2008-06-18
if u have a broadband connection

use this command

sudo pppoeconf in terminal

just keep answering and press yes to everthing
it will ask to write changes in a file the do press yes

it will then ask your ISP's username and password
enter it..
ur connection will work

---

### Post by new_fan_of_linux on 2008-06-18
> **ettercap said:**
> if u have a broadband connection

use this command

sudo pppoeconf in terminal

just keep answering and press yes to everthing
it will ask to write changes in a file the do press yes

it will then ask your ISP's username and password
enter it..
ur connection will work

Hello, I have a broadband connection, but I have the ADSL type modem and I do not have any particular ISP username. Do i have to create my own username here?

---

### Post by new_fan_of_linux on 2008-06-18
> **superprash2003 said:**
> @new_fan_of_linux
  i dont think you would need to actually..cause your ifconfig output shows eth0 which means it does detect your LAN card.. go to system->administraton->network and go to eth0 properties and set it to DHCP instead of Roaming mode and then post your ifconfig output again

In the network settings, there is not any eth0 properties option. In general tab, it shows two options w)Wireless Connection and 2)Modem Connection

In wireless connection properties, there is not any option of setting DHCP mode instead of roaming mode. Also the output of ifconfig is:
*********************************************************************
eth0 Link encap:Ethernet HWaddr 00:1F:3C:54:E6:EB
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:2 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:177 Base address:0x4000 Memory:fe7ff000-fe7fffff

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:5 errors:0 dropped:0 overruns:0 frame:0
TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:272 (272.0 b) TX bytes:272 (272.0 b)
*********************************************************************

Please help

---

### Post by new_fan_of_linux on 2008-06-18
> **ettercap said:**
> if u have a broadband connection

use this command

sudo pppoeconf in terminal

just keep answering and press yes to everthing
it will ask to write changes in a file the do press yes

it will then ask your ISP's username and password
enter it..
ur connection will work

Hello ethercap,

I tried the command sudo pppoeconf and it detected a device on eth0, but after some processing, it failed with the following error:

*************************NOT CONNECTED*************************
"Sorry, I scanned the device but the access concentrator of your provider didn't respond. Check your modem cables and connections. May be another process would be running pppoe which control the same modem."

I am not getting how to fix it.

---

### Post by new_fan_of_linux on 2008-06-18
> **new_fan_of_linux said:**
> Hello ethercap,

I tried the command sudo pppoeconf and it detected a device on eth0, but after some processing, it failed with the following error:

*************************NOT CONNECTED*************************
"Sorry, I scanned the device but the access concentrator of your provider didn't respond. Check your modem cables and connections. May be another process would be running pppoe which control the same modem."

I am not getting how to fix it.

So any suggestions how to fix it

---

### Post by ettercap on 2008-06-19
it worked for me

i think there might be a problem with ur modem 
sorry me also noob

try a differnt connection manager...like wvdial

---

### Post by toolzen on 2008-06-20
Ok, eth0 is your ~wired~ ethernet adapter, and wlan0 is your wireless network card. If you aren't connecting through a wireless network, then don't worry about your settings for wlan0. As a matter of fact, you can just take it offline:

sudo ifconfig wlan0 down

Also, you don't want to use pppoeconf - that's for point to point connections. Your connection probably doesn't work that way (assuming it is one of the more popular high-speed internet providers). Most likely your DSL modem acts as a DHCP server and tries to assign an IP to your computer, in the event your computer requests one.

You should have a phone line coming from the wall to your dsl modem, and then an ethernet cord going from your modem to your computer (assuming you're not using a router). From what you have posted it sounds like all of that is in place. Just to make sure, unplug the power cord from your modem, count to 30, and then plug it back in and wait until all the little lights are telling you it's ready (mine has lights that flash while the modem is connecting and then turns steady when it is done).

Based on the output you posted from the "ifconfig" command, your LAN card is up and running, but it doesn't have an IP address. Do the following (after following the above instructions for reseting your modem):

sudo ifconfig eth0 up    (to make sure your card is still up).

if that works, then type:

sudo dhclient eth0

Wait until it finishes, and then try to connect to the internet. Notice I didn't use ifup or ifdown - use the ifconfig command with the "up" or "down" arguments.

Also, post the output from "sudo dhclient eth0" if the above steps don't give you a connection.

Another thing you might do, if after all of the above doesn't work, is try to connect to the net in a couple of different ways. I.e. try to open your browser, and if that doesn't work open a terminal and type:

ping google.com

This will make sure there isn't a problem with your browser settings (like if you had a proxy server address set up even though you're not using a proxy).

---

