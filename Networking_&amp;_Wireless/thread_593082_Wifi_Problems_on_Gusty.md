---
title: "Wifi Problems on Gusty"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by Shabbro on 2007-10-26
Hello,
I have a Dell Inspiron 1505 notebook with Ubuntu 7.10 running, and today I ran across a particularly strange problem. When I started up my notebook everything seemed fine, my wireless internet said that it was connected to 'linksys' at 89%. I start up firefox and it does nothing.... at the bottom of the screen it says "connecting to http://www.google.com...." and it sits like that for a long, long time before it times out. I also cannot connect to my email client or any online games.
My wireless says that Im connected to Linksys (and the internet is working on all my other computers) It just stopped working today for some reason... even earlier today it was working, but it just stopped now and Im not sure what to do.

Is this a bug in the wireless management system? Is there anything to do to fix this?

Thanks!

---

### Post by Shabbro on 2007-10-26
Okay... this is getting even wierder....

I just realized that I can only browse and download things from Mozilla's official website.... I cant go anywhere else on the internet but Mozilla's site.... I even downloaded Sea Monkey from the site! But i still cant get online with any games or any other website!

---

### Post by kevdog on 2007-10-26
Can you post the following from the command line

ifconfig
iwlist scan
route -n

---

### Post by Shabbro on 2007-10-26
Here is what I got...

eric@eric-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:B9:5D:24:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

wlan0     Link encap:Ethernet  HWaddr 00:13:E8:09:68:C3  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::213:e8ff:fe09:68c3/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:2755 (2.6 KB)  TX bytes:6485 (6.3 KB) 

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-09-68-C3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

eric@eric-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 

wlan0     No scan results 

eric@eric-laptop:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0 
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

---

### Post by kevdog on 2007-10-26
Do you think it might be a dns issue?  Do you think this thread may help:
[http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by Shabbro on 2007-10-26
Allright, I'll try to impliment those codes and tips tommorow (I have work in the morning....) I'll message back any info, or question I have...

Thanks A Bunch KevDog, you are a big help!

---

### Post by kevdog on 2007-10-26
Here is one other link you may want to look over 

[http://ubuntuforums.org/showthread.php?t=589034](http://ubuntuforums.org/showthread.php?t=589034)

---

### Post by Shabbro on 2007-10-27
I tried to do what the people suggested in the other threads, but to no avail, my problems are still happening.... 
By the way... I am a newer user to Ubuntu, so this is all a little new for me, and I have also never dealt with networking problems before. Is there any other thing that I can try, or is there any instructions I can have?


Thanks

---

### Post by kevdog on 2007-10-27
You could try wicd -- its like network manager.  Its worked for a lot of people.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Or if you just want to see if you can connect and everything works without network manager, you could try making the connection from the command line.  It strips away one layer of complexity/potential problems.  Think of it as direct interaction with the layer just below network manager.  The link is in my signature.  Its probably not a permanent solution, however it will at least tell you everything is working.

---

### Post by Shabbro on 2007-10-27
I got Wicd, but its still doing the same thing! :(
I would hate (really hate) having to reinstall ubuntu onto my computer again, but if that is what it is comming down to, then Im in a world of hurt...

I really have No idea what or why my internet isnt working. This is frustrating!

---

### Post by kevdog on 2007-10-27
Try the command line -- not only will you learn something however it will give us both something to work with as far as further troubleshooting your problem.

---

### Post by Shabbro on 2007-10-27
Ok, here is what I got from the command line....



eric@eric-laptop:~$ lshw -c network 
Hardware Lister (lshw) - B.02.10 
usage: lshw [-format] [-options ...] 
       lshw -version 

        -version        print program version (B.02.10) 

format can be 
        -html           output hardware tree as HTML 
        -xml            output hardware tree as XML 
        -short          output hardware paths 
        -businfo        output bus information 

options can be 
        -class CLASS    only show a certain class of hardware 
        -C CLASS        same as '-class CLASS' 
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
        -quiet          don't display status 

eric@eric-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Wireless interface 
       product: PRO/Wireless 4965 AG or AGN Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:0b:00.0 
       logical name: wmaster0 
       version: 61 
       serial: 00:13:e8:09:68:c3 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.106 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g 
  *-network 
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:19:b9:5d:24:58 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 module=b44 multicast=yes 



eric@eric-laptop:~$ sudo dhclient -r wlan0 
There is already a pid file /var/run/dhclient.pid with pid 14371 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:13:e8:09:68:c3 
Sending on   LPF/wlan0/00:13:e8:09:68:c3 
Sending on   Socket/fallback 
DHCPRELEASE on wlan0 to 192.168.1.1 port 67 
send_packet: Network is unreachable 
send_packet: please consult README file regarding broadcast address. 


eric@eric-laptop:~$ sudo ifconfig wlan0 
wlan0     Link encap:Ethernet  HWaddr 00:13:E8:09:68:C3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:2209 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1254 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1182567 (1.1 MB)  TX bytes:206601 (201.7 KB) 

eric@eric-laptop:~$ sudo dhclient wlan0 
There is already a pid file /var/run/dhclient.pid with pid 134519120 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:13:e8:09:68:c3 
Sending on   LPF/wlan0/00:13:e8:09:68:c3 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
DHCPOFFER from 192.168.1.1 
DHCPREQUEST on wlan0 to 255.255.255.255 port 67 
DHCPACK from 192.168.1.1 
bound to 192.168.1.106 -- renewal in 40999 seconds.

---

### Post by kevdog on 2007-10-27
Ok, what happens now:

bound to 192.168.1.106 -- renewal in 40999 seconds.

This tells you that your machine was offered the 192.168.1.106 ip address.  If you go to firefox and try to use the internet, are you having any of the problems that you were having before?

---

### Post by Shabbro on 2007-10-27
Alright... this is a little crazy now...

I open up Firefox and it does the same thing (connecting to google.com....) then I typed in [www.yahoo.com](www.yahoo.com) and it works! I go to any other website and it works! I try google.com and nothing happens... Im almost convinced that I cannot visit any google oriented site! I cant connect to these forums on my ubuntu machine because it freezes out on connecting to google-anaylist.com or something to that extent,
Also I cannot search from any search engine without it timing out!

Is this crazy or what?.....

---

### Post by kevdog on 2007-10-27
Maybe a dns related problem -- Im not sure.  Try this link out so you can try to use the OpenDNS servers.  it may help.  What's going on with you right now is a little schizophrenic:
[http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by Shabbro on 2007-10-27
I did what was on that blog, and nothing changed.  :O

---

### Post by Shabbro on 2007-10-27
Alright, so I spoke with a Dell-Ubuntu Rep and he told me that my computer is not talking outside our network and it is not pinging outside my gateway. Is this info any help in solving why I cannot get online? The rep said that this forum was the best place to find out what is wrong and how to fix it.


Thanks

---

### Post by kevdog on 2007-10-27
Ok, please post

route -n

Hmm wonder if I can get on the Dell payroll???

---

### Post by Shabbro on 2007-10-27
Here is what I got

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0 
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

Hope that can help! :)

---

### Post by kevdog on 2007-10-28
Your gateway is set up to be 192.168.1.1 -- which is correct in your setup.  So I dont think it is a gateway problem. 

Two other possibilities (but these are much more remote) are to disable ipv6 and/or change the mtu value.  Ive seen these two things cause similar problems however in very remote cases.  Try disabling ipv6 - here is how:


1.) open terminal

2.) sudo cp /etc/modprobe.d/aliases /etc/modprobe.d/aliases_backup

3.) sudo gedit /etc/modprobe.d/aliases

4.) find the section "alias net-pf-10 ipv6" change it to "alias net-pf-10 off"

5.) reboot your pc


What happens if you start pinging various address like yahoo.com, google.com, espn.com (just random sites). Do you get a response??

---

### Post by Shabbro on 2007-10-28
I changed that setting you described for me, after I restarted the system everything turned out the same.

Here is what I got from my pings
Yahoo.com
64 bytes from w2.rc.vip.scd.yahoo.com (66.94.234.13): icmp_seq=41 ttl=55 time=57.5 ms 
(Many Responses)
Google.com
PING google.com (64.233.187.99) 56(84) bytes of data. 
(No Response)
Ubuntuforums.org
 64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=69 ttl=53 time=125 ms 
ESPN.com
(No response)

---

### Post by kevdog on 2007-10-28
Can you post ifconfig, I want to see your mtu setting.

---

### Post by Shabbro on 2007-10-28
I'll do that right now.... it might take a few minutes (I have to switch between my windows partition  and my Ubuntu partition to reply)

---

### Post by Shabbro on 2007-10-28
Here are my results

eric@eric-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:B9:5D:24:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

wlan0     Link encap:Ethernet  HWaddr 00:13:E8:09:68:C3  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::213:e8ff:fe09:68c3/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:13546 (13.2 KB)  TX bytes:5584 (5.4 KB) 

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-09-68-C3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Shabbro on 2007-10-28
Isnt an MTU setting of 1500 a normal number for an ethernet connection?

---

### Post by kevdog on 2007-10-28
Yes, Ive read one post someone changed it to 1250 and their problems were solved.  I cant remember how they did it.  It was a one line command at the command line.  You might have to search for it, or call back dell and tell them its not a gateway problem.

---

### Post by Shabbro on 2007-10-28
sudo ifconfig wlan0 mtu 1250  seems to do the trick, but only temporarily, so Im still looking for a permanent solution.

---

### Post by Shabbro on 2007-10-28
At first it seemed to work (my internet after I did sudo ifconfig wlan0 mtu 1250) but now its doing the exact same thing.... I'll keep playing around with this.....

---

### Post by ahickey on 2007-10-28
I had this problem with Feisty and it re-appeared when I did the Gutsy update.

The situation I had was that nothing other than ping could resolve IP address for names.
Once ping resolved the name to an IP address I could then use the name in Firefox.  Strange but true.

The only way I can fix it is to use a static IP address.
I also use 208.67.222.222 and 208.67.220.220 as my DNS servers, but I'm not sure if just using a fixed IP address with sort it our or only using the openDNS servers.

I have just changed to a fix IP for Gutsy and it is all working well.
My ultimate test is if StumbleUpon works as it will definitely bring up sites I don't know the IP address for.

I hope this helps.  It's not a full fix, but at least it lets you use Ubuntu.

Albert.

---

### Post by Shabbro on 2007-10-28
Thanks for your tips, I tried them but for reasons unknown to me, my connection still refuses to get past my homepage!

When i say "ifconfig" it comes up and lists 
eth0
lo
wlan0
wmaster0


Is wmaster0 supposed to be there? that was a little confusing for me....

I think I might back up my files onto a disc and just reinstall Ubuntu if I cant get this fixed. :P

---

### Post by kevdog on 2007-10-28
I usually dont recommend that drastic of action, however perhaps in your case it might be good.

---

### Post by Shabbro on 2007-10-28
Alright, I got off the phone with the people at dell a few minutes ago, and they have **No** idea what is wrong with my laptop! :P
Even they reccomend that I backup my files and reinstall the system!
I'm going to delete Ubuntu from my HDD using Windows's Partition Management then reinstall 7.10 unto my HDD. 

Im looking to delete my vista partition from my Hard Drive, can I use one of the tools in Ubuntu to delete the vista partition and then expand the ubuntu partition?


By the way, kevdog, you were an excellent source of knowledge in this problem, thanks for helping me along the way! :)

-Eric

---

### Post by kevdog on 2007-10-28
I just know the basics about partitioning, so I really cant guide you.  Probably posting a question in another forum beyond networking & wireless (the current forum) might serve you better trying to get an answer.  Most people here answer questions really related to networking.

---

### Post by Shabbro on 2007-10-28
I reinstalled 7.10 and everything is working fine (so far :P ) So I suppose that reinstalling Ubuntu is really the only way to correct this unusual problem.

Thanks for the help kevdog,

Eric

---

### Post by kevdog on 2007-10-28
Glad its working for you.  Im sure it could have been solved in the old installation, however the problem was really diagnosing the problem, which unfortunately I couldnt do.  I dont really know what was causing your problem.  Glad everything worked out in the end.

---

