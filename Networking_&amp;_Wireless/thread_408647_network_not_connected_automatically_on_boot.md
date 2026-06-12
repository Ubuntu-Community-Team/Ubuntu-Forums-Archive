---
title: "network not connected automatically on boot"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by sambody on 2007-04-13
**Problem:** I used to be connected automatically to the internet on startup, but now not anymore. It changed around the time that I installed kde-desktop (I was using Gnome), then uninstalled it.

**Workaround:** On every startup, I go to system>administration>networking. I then **uncheck** the checkbox "wired connection" (adress: DHCP), the **recheck** it, then there's a little window saying "activating network interface" for a few seconds, and then my  internet connection works ok. But on the next boot, I have to go through this again.

What can I do to have this connection automatically (like I had before) ?

**Setup:** I'm using Ubuntu 6.10 Edy Eft, and Network manager 0.6.3-2. My computer is connected (with a wire) to the ADSL modem/router.

Thanks in advance

---

### Post by heatrag on 2007-04-13
This sorted me out with the same problem, start at post 22.
[http://ubuntuforums.org/showthread.php?t=379553&page=3](http://ubuntuforums.org/showthread.php?t=379553&page=3)

---

### Post by dbott67 on 2007-04-13
Heatrag is suggesting that there is a command missing from your interfaces file (probably the 'auto eth0' command).  Can you post the output of your interfaces file:
```
dbott@dapper:~$ cat/etc/network/interfaces
auto lo
iface lo inet loopback

[COLOR=Red]** auto eth0  **[COLOR=Blue]*# <--- if this command is missing from one of your interfaces, then that device will not be active on startup.*[/COLOR][/COLOR]
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```Thanks,
Dave

---

### Post by sambody on 2007-04-13
Using Nano (as told in the forum thread linked above) , I opened the file (with "sudo nano /etc/network/interfaces").  I added the line "auto eth0" just before the line "iface eth0 inet dhcp". I doubled checked the file in Gedit, it looked ok.

Then I rebooted... and still no automatic connection. 

I manually switched the connection on again (like I explained in my first post), then I checked the file again... and the line that I had added was gone ! 

I'm not sure if the line "disappeared" at shut down or at boot up. I'll check it..

The file /etc/network/interfaces reads like this (after I added the line, before the manual connection):

--- start of file ---

auto lo
iface lo inet loopback

auto eth0  # this line disappeared !?
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

--- end of file ---

Any ideas ?

---

### Post by sambody on 2007-04-13
The situation:
1. adding the line "auto eth0" doesn't give me automatic connection. I've opened the file Interfaces, the line is still there after reboot (and **before** connecting manually). So it doesn't seem to work.
2. After manual connection, that line has disappeared.

So I don't have the solution yet.
Thanks for your help

---

### Post by dbott67 on 2007-04-13
Okay, let's try this:

Put the line back in & re-start.  Then when you get to the desktop, open a terminal & type:
```
sudo ifdown eth0 && sudo ifup eth0
```The output should look like this:
```
dbott@feisty:~$ sudo ifdown eth0 && sudo ifup eth0
Password:
There is already a pid file /var/run/dhclient.eth0.pid with pid 4847
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 236226 seconds.

```If it works, you could write a script to run the commands automatically.

1. Create a file called "reset_eth0.sh:
```
gedit reset_eth0.sh
```Add the following lines:
```
#!/bin/bash
sudo ifdown eth0 && sudo ifup eth0
```2. Save it and make it executable:
```
chmod +x reset_eth0.sh
```3. Double-click the file to run it & select "Open in Terminal"

Let me know what happens, as we can then refine some of the steps.

-Dave

---

### Post by manifoldronin on 2007-04-14
I'm having a similar problem since upgrading to Feisty beta - I also started with Ubuntu and then installed the kde meta pack.

My /etc/network/interface file does keep "auto eth0" though, and I can see in syslog that it does try to activate eth0 at startup, the only problem is it never gets a dhcp offer.  Once I'm in kde, I can always manually do it with "sudo ifdown eth0" and then "sudo ifup eth0".

Any thoughts?  Thanks.

---

### Post by tech4me on 2007-04-14
computer@computer-desktop:~$ sudo ifdown eth0 && sudo ifup eth0
Password:
ifdown: interface eth0 not configured
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

this is what it happens after doing above steps

---

### Post by tech4me on 2007-04-14
after creating restart_eth0.sh file

if the network is present the output as follows







There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:21:3c:90:45
Sending on   LPF/eth0/00:19:21:3c:90:45
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:21:3c:90:45
Sending on   LPF/eth0/00:19:21:3c:90:45
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
:
:
:
3 0r 4 lines missing it goes in a flash

---

### Post by tech4me on 2007-04-14
the attachment has the output of reset_eth0.sh

when no connection is present

plz   slove this.......................:confused:

---

### Post by sambody on 2007-04-14
@dbott67:

when doing "sudo ifdown eth0 && sudo ifup eth0" , I get this:

---
/etc/network/interfaces:56: interface eth0 declared allow-auto twice
ifdown: couldn't read interfaces file "/etc/network/interfaces"
---
what shall I do next ?

---

### Post by sambody on 2007-04-14
I discovered something: when activating my connection by hand, it **does not** make the line "auto eth0" disappear, it puts the line **way down** at the end of the file. That's probably why I get "declared twice": I thought it disappeared, so I put it back, but then I got the line twice in the file.

But this still doesn't solve my problem. When I move the line from the bottom up again, and reboot, I still have no automatic connection . And activating my connection puts this line at the bottom again...

---

### Post by sambody on 2007-04-14
@dbott67:

this time (when only having ONE auto eth0) when doing

```
sudo ifdown eth0 && sudo ifup eth0
```

I have the output: 

```

There is already a pid file /var/run/dhclient.eth0.pid with pid 5205
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:18:f3:0a:12:f2
Sending on   LPF/eth0/00:18:f3:0a:12:f2
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:18:f3:0a:12:f2
Sending on   LPF/eth0/00:18:f3:0a:12:f2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.3 -- renewal in 14523402 seconds
```

So I followed your instructions, and that little file does the trick of activating my connection when I double-click on it. It's not automatic yet (I'll have to click it on every bootup), but it's easier than going through the Network Manager, so thank you.

If someone has an idea how to make it automatic, I would be very pleased. Otherwise, I'll just use this workaround.

Thanks

---

### Post by tech4me on 2007-04-14
@somebody
 can u tell how we can approach through network manager....


@dbott67
cann't we make it automatically boot at system starting..........

---

### Post by sambody on 2007-04-14
@tech4me: 

my original approach is described in my first post (the first post of this thread, where I talked about the "workaround" using the network manager). Does that answer your question ?

---

### Post by dbott67 on 2007-04-14
To make the script run at startup, you would need to do the following:

1. Create a new script to reset the network interfaces:
```
gedit ~/reset-interface.sh
```2. Add the following code (runlevel scripts run as root, so sudo is not required):
```
#!/bin/bash
ifdown eth0 && ifup eth0
```3. Save file.

4. Make script executable:
```
chmod +x reset-interface.sh
```5. Create a symlink to the file in runlevel 3:
```
sudo ln -s ~/reset-interface.sh /etc/rc.d/rc3.d/S99reset-interface.sh
```[I]Note: the S99 in front of the symlinked script name is to indicate S for START and the number is an arbitrary number assigned to prioritize the order in which the scripts are run.  The higher the number, the later the script runs.  If you wanted to STOP the script, you would rename the file using K for KILL.  Check the README in the /etc/rc.d/rc3.d directory for more details. I[COLOR=Blue]'m not sure if you need the S99 for this script[/COLOR].

[/I]I have not tested this, but it should work.  If you want more information, you can do a search on 'runlevel scripts'.  If you have troubles, try creating the symlink without the _**S99**_ prefix.

-Dave

---

### Post by sambody on 2007-04-14
I've followed your instructions, but still no luck...

When doing

```
sudo ln -s ~/reset-interface.sh /etc/rc.d/rc3.d/S99reset-interface.sh
```

it gave me an error of file/directory not found. I found out that there is no "rc.d", so I changed the code to 

```
sudo ln -s ~/reset-interface.sh /etc/rc3.d/S99reset-interface.sh
```

This made the link work. But after rebooting, I still had no connection. I then tried without the S99:


```
sudo ln -s ~/reset-interface.sh /etc/rc3.d/reset-interface.sh
```

rebooted, but still no automatic connection.

Anything missing?
How do I "undo" these links ?

---

### Post by dbott67 on 2007-04-14
```
sudo rm /etc/rc3.d/reset-interface.sh
```
(or whatever the name of the symlink is)

-Dave

---

### Post by dbott67 on 2007-04-14
You could place the script in **SYSTEM > PREFERENCES > SESSIONS > STARTUP PROGRAMS**, but I think it will require root priveleges (i.e. the commands in the script will need to be preceded by sudo).  This means that the script will need to open in a terminal and wait for your password.

Not sure what the next step is...

-Dave

---

### Post by sambody on 2007-04-15
In system>preferences>session>startup programs, i've added

```
sudo /home/sam/Varia/reset_eth0.sh
```

but it has no effect (no connection, no password asked). I suppose I have to run in a terminal. Is there a way to make it run in a terminal in "startup programs" ?

---

### Post by dbott67 on 2007-04-15
Hi Sammy,

Try this:
In the startup programs, change the sudo to 'gksudo'
```

gksudo /home/sam/Varia/reset_eth0.sh
```In the script, you can remove any 'sudo' commands:
```
#!/bin/bash
ifdown eth0 && ifup eth0
```I just tried it & it seemed to work.  The network manager icon indicated the network was disabled and then a few seconds later it stated that the network was connected.  I've attached a few screenshots to show what happened.

1. Just after login (but before it reached the desktop), the graphical prompt popped up and prompted me for my password.  It was indicating that it wanted to run **/home/dbott/Desktop/script.sh**.

2.  After that, the Network Manager icon indicated that the network was disconnected.

3.  A few seconds later, Network Manager indicated that the network was re-connected.

**daemon.log snippet:**
```
dbott@feisty:~$ cat /var/log/daemon.log | grep DHCP
Apr 15 22:41:59 feisty dhclient: Internet Systems Consortium DHCP Client V3.0.4
Apr 15 22:41:59 feisty NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0 
Apr 15 22:41:59 feisty dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Apr 15 22:42:10 feisty dhclient: Internet Systems Consortium DHCP Client V3.0.4
Apr 15 22:42:12 feisty NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Apr 15 22:42:12 feisty NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Apr 15 22:42:13 feisty dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 15 22:42:13 feisty dhclient: DHCPOFFER from 192.168.1.1
Apr 15 22:42:13 feisty dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Apr 15 22:42:13 feisty dhclient: DHCPACK from 192.168.1.1
Apr 15 22:42:13 feisty NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Apr 15 22:42:20 feisty dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 15 22:42:20 feisty dhclient: DHCPOFFER from 192.168.1.1
Apr 15 22:42:20 feisty dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Apr 15 22:42:20 feisty dhclient: DHCPACK from 192.168.1.1
Apr 15 22:42:20 feisty NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Apr 15 22:42:20 feisty NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
dbott@feisty:~$ 
```-Dave

---

### Post by sambody on 2007-04-16
BINGO !!

I've followed your steps and it works, Dave. This is soooooo great.

Thank you very much, merci beaucoup, muchos gracias.

---

### Post by dbott67 on 2007-04-16
You're welcome, de rien, de nada.

---

### Post by badboy_24u on 2007-04-16
[SIZE="3"]Hi, just want to ask about internet connection while on DOS mode? is this possible? coz i accidentally deleted the gnome desktop and gdm. so i'm stuck in the DOS mode and i can't seem to download the neccessary files and it's saying something like, " cannot find the url [www.u](www.u) buntu.org and so on. So, does ubuntu automaticaly connect to the internet while you're still on Dos mode? thnk You.[/SIZE]

---

### Post by dbott67 on 2007-04-16
Yes, you can still get online without a desktop environment like Gnome or KDE.

You just need to re-install the gnome desktop.  From the command line type:
```
sudo apt-get install ubuntu-desktop
```-Dave

---

### Post by badboy_24u on 2007-04-16
[SIZE="3"]thank you so much... may you both live happily ever after. :) 
[/SIZE]

---

### Post by sambody on 2007-04-26
just a quick note to say that since I upgraded to Ubuntu 7.04, my problem is definitely solved. Automatic connection without the above script.

---

### Post by dbott67 on 2007-04-26
Great to hear, Sammy.

---

### Post by rzelnik on 2007-04-27
Great, but the same problem occured for me just after upgrade to 7.04, so I should probably wait to upgrade to 7.10. :)

---

### Post by fuzzyeric on 2007-05-01
This problem was also created for me when I upgraded to Feisty 7.04.

I traced the problem to inexplicable behaviour by avahi-autoipd.  After dhclient successfully acquired an IP address from my DHCP server, avahi-autoipd discarded and released the IP, then fell back to a 169.x.y.z address.  (Since this address isn't on my network, it wasn't useful for network traffic.)  I too could revive my network access by "sudo ifup eth0" once the desktop had loaded.

Resolution (for me): "sudo apt-get remove avahi-autoipd avahi-daemon".  It will automatically remove a couple of additional small things and the big thing, "kubuntu-desktop".  "kubuntu-desktop" is a placeholder though, so its removal doesn't break anything.

Hope that helps, and good luck.

---

### Post by jodoj80 on 2007-05-04
Hi. I think this is the third message about this issue that I wrote this week. :( 

Today I just follow what **dbott67** explain to **sambody**. And what I got was this:
```
May  9 23:25:33 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May  9 23:25:41 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May  9 23:25:49 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May  9 23:26:04 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May  9 23:26:13 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May  9 23:26:21 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  9 23:26:34 ubu dhclient: No DHCPOFFERS received.
May  9 23:32:07 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  9 23:32:13 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May  9 23:32:20 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May  9 23:32:35 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
May  9 23:32:55 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  9 23:33:08 ubu dhclient: No DHCPOFFERS received.
May  9 23:36:34 ubu dhclient: Internet Systems Consortium DHCP Client V3.0.4
May  9 23:36:54 ubu dhclient: Internet Systems Consortium DHCP Client V3.0.4
May  9 23:36:58 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May  9 23:37:05 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May  9 23:37:14 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May  9 23:37:23 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May  9 23:37:38 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May  9 23:37:47 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May  9 23:37:59 ubu dhclient: No DHCPOFFERS received.
May  9 23:41:35 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May  9 23:41:39 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  9 23:41:45 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  9 23:41:58 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
May  9 23:42:12 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May  9 23:42:27 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May  9 23:42:36 ubu dhclient: No DHCPOFFERS received.
May  9 23:48:18 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May  9 23:48:22 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May  9 23:48:27 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May  9 23:48:32 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  9 23:48:45 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
May  9 23:48:59 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May  9 23:49:14 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May  9 23:49:19 ubu dhclient: No DHCPOFFERS received.
May  9 23:52:51 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May  9 23:52:58 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May  9 23:53:08 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May  9 23:53:18 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May  9 23:53:33 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May  9 23:53:41 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May  9 23:53:51 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
May  9 23:53:52 ubu dhclient: No DHCPOFFERS received.
May  9 23:55:13 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  9 23:55:26 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
May  9 23:55:43 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May  9 23:55:58 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May  9 23:56:08 ubu dhclient: No DHCPOFFERS received.
May 10 00:03:19 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 10 00:03:27 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
May 10 00:03:45 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
May 10 00:04:01 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May 10 00:04:11 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May 10 00:04:20 ubu dhclient: No DHCPOFFERS received.
May 10 00:08:48 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 10 00:08:54 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May 10 00:09:05 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
May 10 00:09:19 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May 10 00:09:34 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May 10 00:09:43 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 10 00:09:49 ubu dhclient: No DHCPOFFERS received.
May 10 00:15:13 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May 10 00:15:17 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 10 00:15:24 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 10 00:15:32 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 10 00:15:40 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
May 10 00:15:58 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
May 10 00:16:14 ubu dhclient: No DHCPOFFERS received.
May 10 00:19:23 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May 10 00:19:28 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May 10 00:19:33 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May 10 00:19:44 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May 10 00:19:59 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 10 00:20:06 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
May 10 00:20:20 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May 10 00:20:24 ubu dhclient: No DHCPOFFERS received.
May 10 00:23:43 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May 10 00:23:47 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May 10 00:23:51 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May 10 00:24:02 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
May 10 00:24:23 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
May 10 00:24:44 ubu dhclient: No DHCPOFFERS received.
May 10 00:27:54 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 10 00:28:00 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 10 00:28:06 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
May 10 00:28:25 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May 10 00:28:36 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May 10 00:28:51 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May 10 00:28:55 ubu dhclient: No DHCPOFFERS received.
May 10 00:35:09 ubu dhclient: Internet Systems Consortium DHCP Client V3.0.4
May 11 14:39:54 ubu dhclient: Internet Systems Consortium DHCP Client V3.0.4
May 11 14:39:59 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May 11 14:40:03 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May 11 14:40:12 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 11 14:40:24 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
May 11 14:40:43 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
May 11 14:40:59 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
May 11 14:41:00 ubu dhclient: No DHCPOFFERS received.
May 11 14:43:41 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 11 14:43:48 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 11 14:44:00 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May 11 14:44:11 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 11 14:44:23 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 11 14:44:30 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 11 14:44:42 ubu dhclient: No DHCPOFFERS received.
May 11 14:48:18 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 11 14:48:26 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
May 11 14:48:43 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May 11 14:48:58 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May 11 14:49:09 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May 11 14:49:19 ubu dhclient: No DHCPOFFERS received.
May 11 14:55:52 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May 11 14:55:57 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May 11 14:56:08 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
May 11 14:56:29 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May 11 14:56:44 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May 11 14:56:53 ubu dhclient: No DHCPOFFERS received.
May 11 15:02:36 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 11 15:02:43 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May 11 15:02:56 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
May 11 15:03:17 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 11 15:03:24 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May 11 15:03:37 ubu dhclient: No DHCPOFFERS received.
May 11 15:07:50 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 11 15:07:53 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 11 15:07:59 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 11 15:08:07 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 11 15:08:19 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May 11 15:08:34 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May 11 15:08:43 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 11 15:08:51 ubu dhclient: No DHCPOFFERS received.
May 11 15:13:23 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May 11 15:13:28 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May 11 15:13:39 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May 11 15:13:54 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 11 15:14:06 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May 11 15:14:16 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 11 15:14:24 ubu dhclient: No DHCPOFFERS received.
May 11 15:17:30 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May 11 15:17:34 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 11 15:17:40 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May 11 15:17:51 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 11 15:18:03 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
May 11 15:18:21 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May 11 15:18:31 ubu dhclient: No DHCPOFFERS received.
May  4 10:54:18 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  4 10:54:31 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
May  4 10:54:50 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
May  4 10:55:08 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  4 10:55:14 ubu dhclient: No DHCPOFFERS received.
May  4 11:00:15 ubu dhclient: Internet Systems Consortium DHCP Client V3.0.4
May  4 11:00:15 ubu dhclient: Internet Systems Consortium DHCP Client V3.0.4
May  4 11:00:18 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May  4 11:00:23 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May  4 11:00:34 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May  4 11:00:41 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May  4 11:00:52 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  4 11:01:05 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May  4 11:01:12 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May  4 11:01:19 ubu dhclient: No DHCPOFFERS received.
May  4 11:06:12 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May  4 11:06:19 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May  4 11:06:34 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May  4 11:06:49 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May  4 11:06:58 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May  4 11:07:09 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May  4 11:07:13 ubu dhclient: No DHCPOFFERS received.
May  4 11:11:01 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  4 11:11:07 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  4 11:11:13 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  4 11:11:26 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  4 11:11:39 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
May  4 11:11:56 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  4 11:12:02 ubu dhclient: No DHCPOFFERS received.
May  4 11:16:52 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May  4 11:16:55 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  4 11:17:01 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May  4 11:17:11 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May  4 11:17:22 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
May  4 11:17:36 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May  4 11:17:51 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
May  4 11:17:53 ubu dhclient: No DHCPOFFERS received.
May  4 11:19:54 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May  4 11:20:06 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  4 11:20:19 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May  4 11:20:26 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  4 11:20:30 ubu dhclient: Internet Systems Consortium DHCP Client V3.0.4
May  4 11:20:30 ubu dhclient: Internet Systems Consortium DHCP Client V3.0.4
May  4 11:20:35 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May  4 11:20:39 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May  4 11:20:39 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May  4 11:20:43 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May  4 11:20:50 ubu dhclient: No DHCPOFFERS received.
May  4 11:20:51 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  4 11:21:04 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
May  4 11:21:21 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
May  4 11:21:35 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
May  4 11:21:36 ubu dhclient: No DHCPOFFERS received.
May  4 11:23:39 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May  4 11:23:47 ubu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
```I apologize if this message is huge, but I prefer that you read the hold message that a part of it.

---

### Post by jodoj80 on 2007-05-13
Thanks for the help. I resolve my issue. :)

---

### Post by dbott67 on 2007-05-13
Can you post what you did to resolve it?

It may help others who come across this thread.

Thanks,
Dave

---

### Post by jodoj80 on 2007-05-13
Hello everyone.

dbott67 as I said in other tread where I posted my situation before. All I do was made some hardware upgrades to my computer. I change the case and some cables (*not the patch cord, because I changed it five times before start posting my situation here*) and VOILA!!! when I turn on the computer it connects to firefox with problem.

I made the upgrades one week after my last thread posted here. So, maybe I found the solution trying all the procedures that people like you provide me. But, I'm not sure if the right solution was the hardware upgrades or one of the procedures provided to me.

I just know that I learned more about ethernet problem with Ubuntu than Windows XP. This open my interest to keep using Ubuntu.

Thanks everyone, :guitar:

---

### Post by dmatcott on 2008-05-04
I have upgraded from Xubuntu Gutsy to Hardy and have encountered same problem as Sambody. My wireless network is not automatically connecting at initial boot up.
I have followed the directions given above, and have succeeded in being able to reset the connection by running the reset_wlan0 script automatically on startup. However, I find that having to enter my password twice on login is a step backwards after an otherwise flawless upgrade. The problem becomes exacerbated when non super user accounts log in as the script cannot be run at all.
Does anyone have any ideas how I could return my network to automatically starting on reboot in the same way that it did with Gutsy?

---

### Post by cmnorton on 2008-05-05
This also happens with KUbuntu 8.04.. [https://bugs.launchpad.net/bugs/193964](https://bugs.launchpad.net/bugs/193964).
If you have time, please add your information there.

---

