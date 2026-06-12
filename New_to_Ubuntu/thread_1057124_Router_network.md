---
title: "Router network"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by triplemaya on 2009-02-01
I have a ubuntu computer and a windows computer connected to a modem router, is this a network with which I can connect the two computers? I'm sure this info is on this forum somewhere but I don't know what to search for, there is masses of talk about samba but I have installed that and I don't seem to be any further forward. What I really want to do is to rlogin to the windows machine so I don't have to trust it with access to the linux machine, but I'll happily settle for mutual file access if that is much easier.

---

### Post by minsf on 2009-02-01
on the ubuntu/linux box, go to a command line interface enter
```
ifconfig -a | less
```
and post here the output.
on the windows box, go to Start>Run type "cmd" (no quotes) and enter.
this should give you a command line interface. then enter
```
ipconfig /all |more
```
and post here the output.

what we really need from this output is the ip addresses that your boxes get from the router.

---

### Post by minsf on 2009-02-01
i guess you are also going to open a port on the windows box and on the linux box. 
1) to open a port for the share on the windows box, go to ControlPanel>InternetConnections right click your connection (probably LAN or wireless) and choose properties. i think in the last tab you'll be able to access your firewall configuration. make sure it is "On" and that the "do not allow any exceptions" is checked OUT. then go to the exception tab, and make sure "File Sharing" is checked (maybe this is "file and printer sharing").

(i hope i remembered all the tabs' names in windows. havent been there in a while)

2) to open a port on the ubuntu box, the easiest way is to use firestarted, which is a graphical interface to handle the iptables firewall that is works on your box (if you have a default installation of ubuntu). to install, use synaptic, or from the command line:
```
sudo apt-get install firestarter
```
the first time you run it you'll have to configure it with the simple wizards. i'm sure there is also a howto out there to help you.
assuming firestarter is installed and configured, open it and in the policy tab you'll have to add a rule to allow the ip address of your windows box. that's why we need the info from my previous post (ifconfig and ipconfig to determine the ip addresses).

3) right click the "Shared Documents" on your windows box and choose to share it.

4) after that, and assuming samba is running on your ubuntu box (if it is not running, use "sudo /etc/init.d/samba start" from the command line) you'll probably be able to see the files in this folders from your ubuntu box by going to Places>Network

5) to do the reverse (sharing files from ubuntu to windows), you'll probably need to use the smbpasswd command to set a password, and then right click a directory (say Public in your home) and chose to share it.

i'll explain step 5 further later, but first we need the ip addresses from the previous post.

if you get stuck at some step- let us know. if a step didnt work - let us know.

---

### Post by triplemaya on 2009-02-01
Hi. Thanks for your excellent clear instructions.
Got everything installed ok, and places / network on the linux box shows me 'windows network', but nothing in the folder. I used GADMIN-SAMBA for samba since it has a nice gui, but it comes up with lots of settings which are probably all wrong by the look of them.

Here's the output as requested

:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:31:e6:e4:a6  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fee6:e4a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114953383 (114.9 MB)  TX bytes:6492621 (6.4 MB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5408 (5.4 KB)  TX bytes:5408 (5.4 KB)

pan0      Link encap:Ethernet  HWaddr 5a:e6:84:04:9d:7a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:00:80:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-00-80-D2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

output from windows box in a mo in next post from the other pc. Cheers.

---

### Post by triplemaya on 2009-02-01
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\pcpc>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.1.2
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1

C:\Documents and Settings\pcpc>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : pc
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VIA Rhine II Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-13-8F-DB-33-97
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.2
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : 01 February 2009 22:43:34
        Lease Expires . . . . . . . . . . : 01 February 2009 23:43:34

---

### Post by minsf on 2009-02-02
summarizing the output you posted:
all ip addresses on your local network start with 192.168.1.something
(this is what the subnet mask means)
your router is at: 192.168.1.1
your Windows sits at: 192.168.1.2
your ubuntu sits at: 192.168.1.3
when boxes needs packets outside of the local network (like when you load a google webpage) they send them via the router- that's what the gateway at 192.168.1.1 means.
-------------------------------------------
first thing i would try is to open a port in the ubuntu for the xp. do you have firestarter installed? if you do, go to the policy tab and in the upper pane add a rule that enables traffic from 192.168.1.2
i think right now you can see the windows network, but you cannot see anything inside since ubuntu's firewall doesnt let packets from Windows in.
if this does not work or if you had difficulties setting up/installing firestarter- let us know.

---

### Post by triplemaya on 2009-02-02
Hi. Thanks for that, I looked at all those numbers but didn't notice the ... 1, 2, 3 association. So simple once it's pointed out.

I set up firestarter ok and added 192.168.1.2 to the Allow connections from host box for Inbound Policy, your instructions got me that far already!

In GADMIN-SAMBA the settings are
Allowed	hosts and Networks:	127. 192.168.0.
Handle connections on:		127.0.0.1/8 192.168.0.0/24
Announce this server to:	192.168.0.255
Retrieve announcements from:	192.168.0.255

---

### Post by minsf on 2009-02-04
can you ping each box from the other?
```
ping 192.168.1.2
```
from the ubuntu (you'll have to press ctrl+c after a few packets and check if any was lost) and
```
ping 192.168.1.3
```
from the windows (via Run>cmd)

---

### Post by triplemaya on 2009-02-04
Hi. Ubuntu can ping windows ok but windows cannot ping ubuntu. Firestarter is running and allow connections from 192.168.1.2 is established in policy for inbound traffic.

---

### Post by minsf on 2009-02-04
In firestarter, go to Preferences, then in the second section, the 2nd subsection or maybe 3rd subsection should be about ICMP settings. check that the two ping boxes are checked. then try pinging from windows to ubuntu again.

---

### Post by triplemaya on 2009-02-04
That did it, ping works both ways now.

---

### Post by minsf on 2009-02-05
since pinging works, this probably means that the network layer is fine. we need to troubleshoot the application layer.
on the windows machine, open Internet Connection, right click the connection your are using (most likely wireless, but could be LAN too), and choose properties. make sure that the File and Printer Sharing Service is installed (it should appear near the TCP/IP and the Microsoft Network Client).
if you dont see it there, click Install>Service and choose to install the file and printer sharing. you may neet to reboot.
if it is already installed, go to My Computer and right click the Shared Documents folder. choose Sharing and Security. then in the second pane check the box near "share this folder". the default name "documents" will be fine. click ok. now try to access your xp's documents from ubuntu (Places>Network>MicrosoftNetwork>MSHOME>computername>documents).
if this does not work, we may need a samba guru here :)

---

### Post by triplemaya on 2009-02-05
File and Printer Sharing Service is installed already, but in the 'Network sharing and security' tab it said that 'Windows has disabled remote access to this computer ...'. So, I've enabled sharing of this folder, just followed the steps in the wizard, and restarted the computer as prompted, but still no go. Nothing showing up when I click on click on Windows Network.

I tried typing MSHOME into the go to box 
smb:///MSHOME
but that didn't help.
( contents of box changes from network:/// to smb:/// when I click Windows Network, presumably this is correct. )

I turned off the windows firewall but this did not help.

I tried this
~$ rlogin 127.198.1.2
ssh: connect to host 127.198.1.2 port 22: Connection refused
is port 22 any clue?

also

in the samba log there are over ten thousand lines repeating
[2009/02/01 23:00:41,  0] nmbd/nmbd_subnetdb.c:create_subnets(277)
  create_subnets: Unable to create any subnet from given interfaces. Is your interface line in smb.conf correct ?
Perhaps this is a problem? Or should I be able to see the windows directory without samba?

Above that line the samba log file says:
[2009/02/01 18:44:47,  0] nmbd/nmbd.c:process(646)
  Got SIGHUP dumping debug info.
[2009/02/01 18:44:47,  0] nmbd/nmbd_workgroupdb.c:dump_workgroups(281)
  dump_workgroups()
   dump workgroup on subnet     192.168.1.3: netmask=  255.255.255.0:
  	WORKGROUP(1) current master browser = PC-2
  		PC-2 40849a03 (pc-2 server (Samba, Ubuntu))
[2009/02/01 23:00:41,  0] nmbd/nmbd.c:main(849)
  nmbd version 3.2.3 started.

The line in gadmin samba for interfaces is
interfaces = 127.0.0.1/8 192.168.0.0/24

---

### Post by minsf on 2009-02-05
1. buddy, could you post here the output of
```
sudo dpkg -l | egrep 'samba|smb'
```
so that we know what samba packages are installed on your ubuntu?

2. on the windows box, go to Start>Run, then try \\192.168.1.3 does this give you anything?

3. are you sure that the samba service has been started? maybe enter ```
sudo /etc/init.d/samba restart
``` to be safe

---

### Post by minsf on 2009-02-05
> **triplemaya said:**
> 
I tried this
~$ rlogin 127.198.1.2

why 127.198.1.2?

---

### Post by bgates on 2009-02-06
The Samba settings are set for the wrong subnet also.  It's 192.168.0.X and your subnet is really 192.168.1.X

---

### Post by triplemaya on 2009-02-06
Problem solved!
Changed all references of 192.168.0.X to 192.168.1.X and it all works as it should. Many thanks for your patient assistance.

Incidentally, though I imagine this is now redundant
 sudo dpkg -l | egrep 'samba|smb'
ii  gadmin-samba                               0.2.7-2                                     GTK+ configuration tool for samba
ii  libsmbclient                               2:3.2.3-1ubuntu3.4                          shared library that allows applications to t
ii  libsmbios-bin                              2.0.3-0ubuntu1                              Provide access to (SM)BIOS information -- ut
ii  libsmbios2                                 2.0.3-0ubuntu1                              Provide access to (SM)BIOS information -- dy
ii  samba                                      2:3.2.3-1ubuntu3.4                          a LanManager-like file and printer server fo
ii  samba-common                               2:3.2.3-1ubuntu3.4                          Samba common files used by both the server a
ii  smbclient                                  2:3.2.3-1ubuntu3.4                          a LanManager-like simple client for Unix
ii  smbfs                                      2:3.2.3-1ubuntu3.4                          mount and umount commands for the smbfs (for
ii  system-config-samba                        1.2.63-0ubuntu4                             GUI for managing samba shares and users

also, while
\\192.168.1.3 simply brings up a dialog saying the network path was not found, though pcwin can ping 192.168.1.3 ok

(127.198.1.2 was probably fogged out weariness, I can find no rhyme or reason in retrospect!)

Finally, what I really want to do is to rlogin to the xp box, is this one simple further step now that everything is connected properly or a much more complicated business? (I hope it's not like the sign in LA Story wanting to direct!)

---

### Post by minsf on 2009-02-08
> **bgates said:**
> The Samba settings are set for the wrong subnet also.  It's 192.168.0.X and your subnet is really 192.168.1.X

bgate, good job spoting this.
triplemaya, glad things are working now. enjoy! you may want to look into ssh, rather than rlogin. this should get you started: 
[https://help.ubuntu.com/community/SSHHowto?action=show&redirect=SSH](https://help.ubuntu.com/community/SSHHowto?action=show&redirect=SSH)

---

### Post by triplemaya on 2009-02-08
Thanks minsf that page looks like what I need! Plus many thanks for all those posts.
Thanks also to bgates.

---

### Post by triplemaya on 2009-09-03
Thanks for your post minsf. I did get somewhere but abandoned the whole project. It seemed a lot easier in the end to run a few programs under wine rather than trying to remotely log in to a windows machine! That wasn't all I was trying to do, but I ran out of time. Cheers.

---

