---
title: "limited connection to internet"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Patggf on 2009-04-05
I have a Dell desktop 2400 with a direct wire dhcp ethernet connection to a sky router.
I'm running Ubuntu 8.04. When I start the computer sometimes I have no connection to the internet at other times it will work fine. I've tried reading the Absolute Beginners forumn and tried the following. I hope it helps.


/* first session */
-------------------------------------------------------------------
pat@pat-desktop:~$ sudo ifconfig eth0 down
[sudo] password for pat: 
pat@pat-desktop:~$ sudo ifconfig eth0 up
pat@pat-desktop:~$ ping google.com
ping: unknown host google.com
pat@pat-desktop:~$ ping 4.2.2.1
connect: Network is unreachable
pat@pat-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:54:27:5e  
          inet6 addr: fe80::20f:1fff:fe54:275e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4290 (4.1 KB)  TX bytes:984 (984.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49100 (47.9 KB)  TX bytes:49100 (47.9 KB)
pat@pat-desktop:~$ 
------------------------------------------------------------------------


Then I tried restarting the computer and had no connection either to the web with Firefox or with Synaptic Package manager. Then I tried sudo dhclient and was able to connect with Firefox and Synaptic. On restarting the computer again I had no connection. Again typing sudo dhclient and I was able to connect with Firefox and Synaptic.


Any clues about what is happening here. If you need more information please ask.

---

### Post by ronocdh on 2009-04-06
Try posting in the Networking forum; more knowledgeable (and faster!) responses might be found there. Great job on providing info!

Sounds to me like you might want to take a look at your /etc/network/interfaces and make sure that you have dhcp values set correctly for eth0.

---

### Post by Patggf on 2009-04-07
Thanks ronocdh.I'll post in the Networking forumn.As for your other advice could you explain in more detail. I'm very new to linux.

---

### Post by joeashcraft on 2009-04-07
from [cyberciti.biz]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/"):
> 
/etc/network/interfaces file contains network interface configuration information for the both Ubuntu and Debian Linux. This is where you configure how your system is connected to the network.
You can modify this file to make sure eth0 is active upon boot, and automatically looks for a DHCP server for an IP. Check the link for more detailed info. 

If you're still having trouble, the contents of /etc/network/interfaces would help us help you.

---

### Post by Patggf on 2009-04-08
As requested:
-------------------------
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp








auto eth0
------------------------------------
I followed your link and got the gist of the info. but I am not clear about a lot of networking terms and background. However, I have a hunch that 'auto etho0' should come before 'iface eth0 inet dhcp.'I'll try this and see if it works. If I do not reply again to you you will know that this worked. Thanks for the help.

---

### Post by Patggf on 2009-04-08
The problem is solved now. Sorry about saying I would not reply back. I was not thinking. It was a bit rude. 

Anyway, have you any ideas as to why the file was like that. Was it corrupted in some way? When I first updated to 8.04 internet worked fine. I messed around with clamav but was not really sure what I was doing. Apart from that all I did was go on the net. Thanks for your help.

---

### Post by Patggf on 2009-04-09
I thought this problem was solved because I restarted the computer three times and was able to get on the net, but I started the computer today and was unable to connect. In the past the problem has shown up most of the time: about seven times out of ten starts. I thought there was a regularity there. Anyway, below is the contents of my /etc/network/interface file as far as I can see it is already set for dhcp. Are there any other settings I should add? By the way after editing the interface file as described in a previous post I checked the file to see it was as it was when I edited it in case it had become corrupted again, but the contents are as below. I'm just going on hunches really as linux is very new to me.

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by JoshuaRL on 2009-04-09
On my server it has the same interfaces file, but only the first two entries.  I really don't think that "auth lo" being first is your problem.  Have you checked this on another OS?  Are you sure it isn't your router thats having the problems?

---

### Post by Patggf on 2009-04-09
It works fine with xp. I'm not sure what auth lo is is that a typo, you mean auto eth0. I reset the router and anyway it works with xp. Thanks for the reply.

---

### Post by joeashcraft on 2009-04-10
The interface 'lo' is for the local loopback. It's important, and is set correctly in your interfaces file.

When you restart and can't get online, do you have an IP address? If you have an IP and can't get online, it could be the routing tables. If you *don't* have an IP address then that's a different problem.

To see if you have an IP address you can right click the network-manager applet and choose Connection Information.

To display the routing table use the command ```
$ route -n
``` Do this when you can't access the internet, then if you can restart/fiddle enough to get a connection, please post the output again.
The routing tables *should* look something like:```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1

```

---

### Post by Patggf on 2009-04-11
Hello joe. Network manager applet? Under System--> Admin I've got two networking tools. The first Network Settings shows only automatic configuration for dhcp the IP field is blank and the second Devices Network Tools shows an IP address of 192.168.0.2. And I'm online at the moment.

I'll now recreate the problem and see if this is still the case...

I can't get online now and Devices Network tools is no longer showing an IP address.In the field for IP address it is showing a long hexadecimal number. 

I'll fiddle ( enter sudo dhclient ) which has always enabled me to get an IP address. And then I'll check Devices Network tools again to see if I get the IP address...

DHCPACK of 192.168.0.2 from 192.168.0.1
bound to 192.168.0.2 -- renewal in 41252 seconds.
pat@pat-desktop:~$ 

Yes, so that is the same IP address I get every time.


And, yes again in devices network tools I get an IP address of 192.168.0.2.


I'm guessing but the computer is getting the IP address under IPV4 when it can't do this it defaults to IPV6 which just shows the hexadecimal number.

Anyway, so what do I do now?
I guess the routing table info. is not required at the moment?

---

### Post by joeashcraft on 2009-04-11
The Network Manager applet should be on the top of the screen, to the left of the clock. It should look like
[IMG]http://i43.tinypic.com/2a9d6zc.png[/IMG] OR [IMG]http://i39.tinypic.com/v8hhkz.jpg[/IMG] OR [IMG]http://i44.tinypic.com/2w1ts2b.png[/IMG] OR two computer monitors, one in front of the other. 
If you don't see it you can start it by pressing Alt + F2 to bring up the Run Application dialog and type in ```
nm-applet
```More helpful info at _[https://help.ubuntu.com/8.10/internet/C/connect.html](https://help.ubuntu.com/8.10/internet/C/connect.html)_ 

As for the hexidecimal IP address. You can disable IPv6 to see if that helps. Detailed _i[nstructions here]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4")_; **summary below**.


**[SIZE=3]This is the official way to disable IPv6[/SIZE]**.
The instructions below is equivalent to that documented in _[Documentation for Ubuntu 8.04 LTS - 3. Wireless Networking - Troubleshooting]("https://help.ubuntu.com/8.04/internet/C/troubleshooting.html")_: 
     
1.  Open up a terminal and type (it is recommended to copy-and-paste it instead): 
```
sudo sed -i -e 's/alias net-pf-10 ipv6/#&\nalias net-pf-10 off/' /etc/modprobe.d/aliases 
``` The above command comments the original line (**alias net-pf-10 ipv6**) and adding the effective line (**alias net-pf-10 off**). You may use your favorite editor to achieve the same result, if you find that using **sed** does not meet your taste.

2.  To restart your computer, type: 
```
sudo reboot
```

---

### Post by Miljet on 2009-04-11
You might try editing your /etc/network/interfaces file again and removing everything except the first two lines. Those two lines should be all you need. I had problems with an install before and that is what fixed it.

---

### Post by joeashcraft on 2009-04-11
> **Miljet said:**
> You might try editing your /etc/network/interfaces file again and removing everything except the first two lines. Those two lines should be all you need. I had problems with an install before and that is what fixed it.

I'd definitely try this first, it's much simpler ;)

---

### Post by Patggf on 2009-04-12
> **Miljet said:**
> You might try editing your /etc/network/interfaces file again and removing everything except the first two lines. Those two lines should be all you need. I had problems with an install before and that is what fixed it.


That did not work. Thanks anyway.

---

### Post by Patggf on 2009-04-12
> **joeashcraft said:**
> The Network Manager applet should be on the top of the screen, to the left of the clock. It should look like
[IMG]http://i43.tinypic.com/2a9d6zc.png[/IMG] OR [IMG]http://i39.tinypic.com/v8hhkz.jpg[/IMG] OR [IMG]http://i44.tinypic.com/2w1ts2b.png[/IMG] OR two computer monitors, one in front of the other. 
If you don't see it you can start it by pressing Alt + F2 to bring up the Run Application dialog and type in ```
nm-applet
```More helpful info at _[https://help.ubuntu.com/8.10/internet/C/connect.html](https://help.ubuntu.com/8.10/internet/C/connect.html)_ 

As for the hexidecimal IP address. You can disable IPv6 to see if that helps. Detailed _i[nstructions here]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4")_; **summary below**.


**[SIZE=3]This is the official way to disable IPv6[/SIZE]**.
The instructions below is equivalent to that documented in _[Documentation for Ubuntu 8.04 LTS - 3. Wireless Networking - Troubleshooting]("https://help.ubuntu.com/8.04/internet/C/troubleshooting.html")_: 
     
1.  Open up a terminal and type (it is recommended to copy-and-paste it instead): 
```
sudo sed -i -e 's/alias net-pf-10 ipv6/#&\nalias net-pf-10 off/' /etc/modprobe.d/aliases 
``` The above command comments the original line (**alias net-pf-10 ipv6**) and adding the effective line (**alias net-pf-10 off**). You may use your favorite editor to achieve the same result, if you find that using **sed** does not meet your taste.

2.  To restart your computer, type: 
```
sudo reboot
```


This is what I tried:


Here is what I tried to turn IPV6 off:
------------------------------------------------------------

pat@pat-desktop:~$ sudo sed -i -e 's/alias net-pf-10 ipv6/#&\nalias net-pf-10 off/' /etc/modprobe.d/aliases
pat@pat-desktop:~$ 
pat@pat-desktop:~$ sudo sed -i -e 's/alias net-pf-10 ipv6/#&\nalias net-pf-10 off/' /etc/modprobe.d/aliases
pat@pat-desktop:~$ sudo gedit -i -e 's/alias net-pf-10 ipv6/#&\nalias net-pf-10 off/' /etc/modprobe.d/aliases
Unknown option -i
Run 'gedit --help' to see a full list of available command line options.
pat@pat-desktop:~$ gedit --help
Usage:
  gedit [OPTION...] [FILE...] - Edit text files

Help Options:
  -?, --help                     Show help options
  --help-all                     Show all help options
  --help-gtk                     Show GTK+ Options
  --help-bonobo-activation       Show Bonobo Activation options
  --help-gnome                   Show GNOME options
  --help-gnome-session           Show session management options

Application Options:
  --encoding=ENCODING            Set the character encoding to be used to open the files listed on the command line
  --new-window                   Create a new toplevel window in an existing instance of gedit
  --new-document                 Create a new document in an existing instance of gedit
  --display=DISPLAY              X display to use

pat@pat-desktop:~$ gksudo gedit -i -e 's/alias net-pf-10 ipv6/#&\nalias net-pf-10 off/' /etc/modprobe.d/aliases


                                        
pat@pat-desktop:~$ 
pat@pat-desktop:~$ 
pat@pat-desktop:~$ 

-------------------------------------------------------------------------------

It created the following output in the file aliases. I'll post a bit of the file:

----------------------------------------------------------------------------
# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
##alias net-pf-10 ipv6
alias net-pf-10 off
alias net-pf-10 off
a

----------------------------------------------------------------------

By the way the command to alter the file aliases seemed to hang so I cancelled it. But it looks like it has worked. I then saved the file.

I'll reboot now sudo reboot...


I could not get online. Had to type in the terminal as before sudo dhclient:

---------------------------------------------------------------
pat@pat-desktop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 5904
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0f:1f:54:27:5e
Sending on   LPF/eth0/00:0f:1f:54:27:5e
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.2 from 192.168.0.1
bound to 192.168.0.2 -- renewal in 41320 seconds.
pat@pat-desktop:~$ 

----------------------------------------------------------------------

I'll take a break now. I think I need to review the posts and read some of the links in more depth to get a firmer grasp of what is going on. In the meantime thanking the posters for their help :)

---

### Post by joeashcraft on 2009-04-12
The sed command won't produce output if it worked without error. So when you ran it the first time and it didn't appear to do anything, it worked (for most commands, no output means it worked). Since that didn't fix anything you can go back and undo the changes (remove the # from the commented line "##alias net-pf-10 ipv6" and remove the whole line "alias net-pf-10 off"). You can do that by running ```
$ gksu gedit /etc/modprobe.d/aliases
```
One thing you can that *should* guarantee a connection after a reboot is set a static IP address for the desktop (I didn't suggest this earlier because I thought it'd be an simpler thing. This doesn't really fix the problem but is a work around). I don't imagine you'll be moving your desktop to different networks often, so this shouldn't cause any troubles. To do this we first need to get some information. Right click on the network-manager applet and choose Connection Information. You can keep this window open or take note of the IP Address, Subnet Mask, and Default route.

To set the static IP goto System > Administration > Network. In the Connections tab select the Wired Connection and click "Properties". Make sure "Enable this connection" is checked and select "Static IP" from "Configuration". Then fill in the next three fields with the info from the Connection Infomation dialog from earlier.

---

### Post by Patggf on 2009-04-13
Thanks Joe I appreciate your help but I'd rather not switch to a static IP address as a workaround because I can always get on the net when I have a problem connecting by typing dhclient. 

In an earlier post you wanted to establish whether I was getting an IP address when I can't get on line. You asked me to select the Network Applet and click on 'Connection Information'. I took another route to establish if I was getting an IP using the network apps under System-->Administration.( This is when I posted I was getting the same IP that dhclient gets when on line and when I couldn't get on line in the field where the IP address was previously there was a long hexidecimal number instead.)I had to take this other route because the 'Connection Information' tab is faded out so I can't click on it.

Finally, I'll enable IPv6 again as per your advice.

I've got a book on Ubuntu and will work my way through it to become more familiar with the system before I make any more changes and do a bit of online reading.

Thanks very much for your time and effort.

---

