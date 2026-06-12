---
title: "Wireless only works if Wired network is plugged in first."
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by lxtubman on 2008-09-03
So... basically I have a Toshiba laptop with Intel pro 3945ABG wireless. initially, ubuntu doesn't see the card at all, but, if i plug in an Ethernet cable and connect to a wired network, suddenly it sees the wireless card and works fine. once i reboot, it doesn't see the card again. I haven't used Ubuntu in a few months because i generally use it for school and i know it worked before my hiatus. I noticed it didn't work before i updated everything too, so it wasn't caused by any updates.

---

### Post by pytheas22 on 2008-09-03
That's strange.  Please post this information so that we can figure out what's going on:

First, reboot the computer without the Internet plugged in at all, then post the output of:
```

lshw -C Network
iwlist scan
dmesg | grep -e iwl -e eth
```

Now, plug in the ethernet cable and connect, and please post again:
```

lshw -C Network
iwlist scan
dmesg | grep -e iwl -e eth
```

Once we figure out why the presence of the ethernet brings the wireless up, we can probably write a script to fix the wireless automatically.

---

### Post by dvlong on 2008-09-06
I'm having a very similar problem with the same modem on a compaq v3000.  Only in my case, I must boot with the wired connection - plugging it in after booting doesn't always allow the wireless connection.

running iwconfig shows Power Management:off.

---

### Post by pytheas22 on 2008-09-06
dvlong,

Please post the information that I asked of the original poster above, as well as this information:
```

lspci -nn
```

---

### Post by dvlong on 2008-09-08
For the past two days, the wireless has not been working at all - On occassion it will try to connect but then drops - no matter if my wired connection is up or not.  In any case, here's a file with the outputs from the codes you gave.  

I thank you for any help you can give me on this. Tomorrow I will be in a different office and last week the connection worked there flawlessly.  I'm looking forward to seeing if it connects at all now.

---

### Post by pytheas22 on 2008-09-08
Unfortunately, I don't see anything in dmesg explaining why it won't work.  It could just be a quirk with the network you're trying to connect to, or it could be a problem with Network Manager, in which case you'd probably have better luck connecting with [wicd]("http://wicd.sourceforge.net").

If you can't connect in the second office and wicd doesn't work any better, then you may want to try installing the ipw3945 driver instead of iwl3945 (ipw is older, but more reliable).  There are instructions [here]("http://skzo.wordpress.com/2008/08/27/ipw3945-driver-on-ubuntu-hardy-heron/") on how to compile and install ipw3945 to replace iwl3945.  They should be relatively easy to follow provided you have some basic command-line experience, but if you need help with them let me know.  Note that you will have to run "sudo apt-get install build-essential" to get a compiler installed before you follow the directions on that site.

---

### Post by dvlong on 2008-09-08
Thanks for this.  I'll try things with ipw3945 and let everyone know what happens.  

Today I'm in my other office and the wireless connects perfectly.  Check my logic out here - it seems that the problem could still be almost anything.  I'm not sure that I've necessarily eliminated anything at all.  One thing I could do is start changing out hardware - i.e. change my wireless transmitter.  I'd really hate to start just changing things like that though, but it seems possible to my uneducated thinking that the problem could lie there somehow.  I have tried configuring it to match the setup in my office that works, but it didn't seem to help.

Will let you know on the older driver.

---

### Post by pytheas22 on 2008-09-08
If you can connect in one office but not the other, then you should take a look at the characteristics of the two wireless networks.  It's likely that differences in the encryption scheme between the two networks is the reason that you can only connect in one office.  If you post the output of the 'iwlist' command from both places, we can see information about the wireless configuration in each and compare it.  One may use WPA1 while the other uses WPA2, for instance, explaining what could potentially be going wrong.

Also, as I mentioned, you should try using wicd to connect, as it tends to deal with peculiarities in WPA configuration etc. better than Network Manager.  In other words, NM could be having trouble negotiating authentication to a WPA2-encrypted networked (even though it can deal with WPA1 without a problem), but wicd would probably have better luck.

Either way, chances are good that ipw3945 would work better than iwl3945.

---

### Post by dvlong on 2008-09-08
I worked on loading ipw3945 according to the 10 steps on the website you indicated but received the following error on step 5: 

$ patch -pl < ipw3945-1.2.2.patch (target file - ipw3945.h)
bash: syntax error near unexpected token `(’

I'm not sure how to resolve this.

I also have installed Wicd and lost my wireless all together!  I'm now trying to troubleshoot it.  The wired connection is working however.

At Office2 I have always used my machine id's only - with no encryption or other security measures. At the HomeOffice I've tried no security, WPA1 and machine id, but nothing seemed to make any difference.

The output at Office2 for 'iwlist' is:

$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

I'll post the output for 'iwlist' at HomeOffice when I return to it.

---

### Post by pytheas22 on 2008-09-09
> patch -pl < ipw3945-1.2.2.patch (target file - ipw3945.h)
bash: syntax error near unexpected token `(&#8217;

I'm not sure how to resolve this.

The instructions are a little unclear.  You don't actually type all of that.  Just type:
```

patch -pl < ipw3945-1.2.2.patch
```

and it will ask you what the target file is, to which you answer 'ipw3945.h' 
> 
I also have installed Wicd and lost my wireless all together! I'm now trying to troubleshoot it. The wired connection is working however.

Perhaps you just don't have wicd open?  It should be under the Applications>Internet menu.  It doesn't have a system-tray icon like Network Manager; you have to start wicd manually (later you can make it start automatically if you want).

If you want to reinstall NM, though, run:
```

sudo apt-get install network-manager-gnome
```

Also, I made a mistake in my last post.  Please post the output of the command 'iwlist scan' in your office (not just 'iwlist').  And what do you mean by using the 'machine ID' to connect?  Where did you enter the machine ID?

---

### Post by dvlong on 2008-09-09
I've gotten the wireless working again at my office - you were right, I simply didn't have wicd open.  :)

The output from iwlist scan with the wireless connected and working and no wired connection (at Office2) is as follows:

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:01:38:46:63:2D
                    ESSID:"NB5Wireless"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=87/100  Signal level=-46 dBm  Noise level=-79 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000004ef2338dd

(Home Office)

No Wireless connection - though it shows up as an option with Wicd Manager - when I try to establish the connection, the Manager says it is waiting for an IP address and then times out.

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


The meaning of 'machine ID' is that I set the wireless GUI interface at the office to only allow connections to the computers whose ID's we enter.  In the GUI interface of the router, these are called machine id's.  I've not tried setting this router up with any specific security as it seems easier to set the other one's security off all together.  The other router did work normally for me for a few days.  Then it started connecting only when my wired connection was installed.  Now, it hasn't connected at all for about 4 days.

I will see if wicd helps, and then finish the installation of the ipw3945 driver if necessary - then we can go from there.  I will get to the other office in a few hours and try then - just in case you never sleep or anything like that. 

Again, thanks for all your help.

---

### Post by dvlong on 2008-09-09
I've run into errors on step 6 and have contacted the owner as well as posting here: 

dvlong@longslap2:~/ipw3945-1.2.2$ make SHELL-/bin/bash
Makefile:53:
Makefile:54: WARNING: $SHELL not set to bash.
Makefile:55: If you experience build errors, try
Makefile:56: ‘make SHELL=/bin/bash’.
Makefile:57:
/bin/sh: Syntax error: “(” unexpected
/bin/sh: Syntax error: “(” unexpected
make: *** No rule to make target `SHELL-/bin/bash’. Stop.
dvlong@longslap2:~/ipw3945-1.2.2$ make SHELL=/bin/bash

ERROR: A compatible subsystem was not found in the following path[s]:

/lib/modules/2.6.24-21-rt /lib/modules/2.6.24-21-rt/build

You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
and point this build to the location where you installed those sources, eg.:

% make IEEE80211_INC=/usr/src/ieee80211/

or use the ‘make patch_kernel’ within the ieee80211 subsystem to patch your
kernel sources.

make: *** [check_inc] Error 1

In addtion, I've been playing with my router setup and network setup just to double check for consistency, etc.  If I set everything for static IP, the my network configuration becomes wlan0 but am unable to connect.  If I set things up to automatic, then the network config is wlan0:avahi.  

When I restart the network there seems to be several points (from my perspective) that may indicate where the problem(s) are.  Here's what I get:

dvlong@longslap2:~$ sudo /etc/init.d/networking restart
sudo: unable to resolve host longslap2
[sudo] password for dvlong: 
 * Reconfiguring network interfaces...                                           * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-down.d/50firestarter exited with return code 200
There is already a pid file /var/run/dhclient.eth0.pid with pid 16779
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:d3:03:47:3f
Sending on   LPF/eth0/00:16:d3:03:47:3f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-down.d/50firestarter exited with return code 2
There is already a pid file /var/run/dhclient.wlan0.pid with pid 17556
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:02:39:76:27
Sending on   LPF/wlan0/00:13:02:39:76:27
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:d3:03:47:3f
Sending on   LPF/eth0/00:16:d3:03:47:3f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.2.100 from 192.168.2.1
DHCPREQUEST of 192.168.2.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.100 from 192.168.2.1
bound to 192.168.2.100 -- renewal in 42802 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 200
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:02:39:76:27
Sending on   LPF/wlan0/00:13:02:39:76:27
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 200
                                                                         [ OK ]

---

### Post by pytheas22 on 2008-09-09
hmmmm, very strange that Firestarter doesn't want to restart and doesn't say why (Google doesn't say much about what "code 200" means).  What if you kill it first (with 'sudo killall firestarter') before restarting networking?

As for the ipw compilation, I'll take a look and see if I can figure out why you can't get it to compile, although I may not get to that tonight.

---

### Post by dvlong on 2008-09-12
After 2 weeks and finally getting frustrated enough with getting nowhere, I decided to start with a clean slate.

I reinstalled Hardy.  Did all the updates.
then ran the codes:
1.sudo apt-get install linux-backports-modules-hardy-generic
2.sudo su
3.echo -e &#8220;alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1&#8243; > /etc/modprobe.d/iwl3945
4.reboot 

When this didn't fix anything I was beginning to get nervous.

I then simply reset my router to the factory defaults, (this makes no sense because the wireless initially stopped working without touching the router) and made the necessary ip changes so that it doesn't conflict with my adsl modem settings, and my wireless began to work immediately.

My wireless router is a Linksys WRT54GL.  

Now I can go back and work under the shade tree again!

---

### Post by pytheas22 on 2008-09-12
Well I'm glad that's finally fixed!  And I wish we knew what had been wrong.

Also, sorry for not getting back to you about compiling ipw3945 from source.  I couldn't do it either.  I kept running into the same errors that you were getting, which was strange because I found several independently written instructions around the Internet, but I got the same errors from make no matter which set I tried to follow.  I'm using the same kernel as these other people and have the dependencies installed, so I don't know why ipw3945 wouldn't compile for me.

Anyway, at least things are working now.

---

### Post by dvlong on 2008-09-12
(Just thinking outloud here) about what happened.  There was a 'deterioration' of the wireless - at first it worked, then only when I booted with a wired connection.  Then not at all.  In my office2 location, it worked until I tried to change the setup of the router, then no matter what - no wireless.  I'm not sure as to why but from an uneducated point of view, it seems that Linux itself is adapting to different changes and making changes of its own - perhaps these are not reversed by the changes we're making?  (Just thinking outloud here)

---

