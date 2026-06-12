---
title: "Really Odd Network Problem"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by superami on 2006-12-08
I just got a new laptop from work and I wanted to throw Ubuntu onto it.  

The short story the wired network has no trouble opening up my web pages located on my local web server, but can't access the router's web page or any web page beyond the router.  It can however ping any web site I try.  If I use the network-manager-gnome to switch to my neighbor's wireless network, I have no trouble accessing any web site, its just very slow.  
HOWEVER, I can access the web through wired network (and wireless) with no problem in WinXP and SuSE 10.2 RC1.


Long story:
So I currently am running a wired network at home with 1 Ubuntu 6.06 web/file server, 1 Ubuntu 6.06 / Windows desktop, 1 Ubuntu 6.10 desktop / Windows, and my new laptop.  With the exception of the laptop no computer has ANY problems with Internet connections.

The problems started with the install of Ubuntu 6.10.  If I had the wired network connected, then the install would fail at 82% trying to check repositories online or something.  I was able to install by disconnecting the network cable.  Then I was able to use the network connection to install network-manager and network-manager-gnome, and this helped me switch between wired and wirelessly, but the wired network still only has access to internal networks.

I have already tried disabling IPv6 in Firefox and /etc/modprobe.d/aliases but to no avail.  I have tried using Ubuntu 6.06, but with the same results.

I had similar problems with my last laptop from my last job and eventually gave up.  I really like Ubuntu and want to get it to work.

The laptop is a Dell D620 Latitude with gigabit ethernet.
I have no trouble getting an IP address per DHCP or pinging web address (ala ping [www.google.com](www.google.com), etc.)

Does anyone have any ideas?

I have been all over the forums and cannot seem to find anything.

---

### Post by dbott67 on 2006-12-08
Can you please post the output of the following commands:

```
ifconfig -a
```
```
route -n
```
```
cat /etc/resolv.conf
```

Thanks,
Dave

---

### Post by superami on 2006-12-09
Here is the Info for the three commands.  Its important to note that I currently change the MTU to 1490 through a script when /etc/init.d/networking start/restart is called.  By doing this I am able to get access to some web sites beyond my router, but not very many (and not this one).

Also I have tried comparing the SuSE 10.2 settings (where networking on the laptop works both wired and wireless) to the Ubuntu settings.  They both seem to use the same driver and the numbers as far as IP, and driver addresses all seem to be the same.  The only difference is that SuSE disables IPv6 by default.  So I added a blacklist entry for IPv6 in the blacklist folder, but that doesn't seem to help.

I also downloaded and ran the Knoppix 5.0 live CD.  It has the exact same problem as Ubuntu, where it gets an IP, gets DNS, but can't ever seem to get a reply.

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:15:C5:5A:5C:EE  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1490  Metric:1
          RX packets:91 errors:43 dropped:0 overruns:0 frame:43
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24814 (24.2 KiB)  TX bytes:14277 (13.9 KiB)
          Interrupt:185 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


cat /etc/resolv.conf

search home
nameserver 192.168.1.1

---

### Post by dbott67 on 2006-12-09
Try modifying **/etc/resolv.conf** to:

```
[B][COLOR="Red"]nameserver 208.67.222.222
nameserver 208.67.220.220
# [/COLOR][/B]search home
nameserver 192.168.1.1
```

Then issue the command:

```
sudo/etc/init.d/networking restart
```

Let me know what happens.

BTW, what is the make & model of your router & version of firmware?


-Dave

---

### Post by superami on 2006-12-09
Well I tried to change it.  However as soon as I call /etc/init.d/networking restart, the file is change back to simply:

nameserver 192.168.1.1

So the only change that stuck was the remove of "search home".

As for my router, its a supper generic "Digitus" ([http://www.digitus.info/scripts/digdetail.asp?artnr=DN%2D11004%2DO++++++++++](http://www.digitus.info/scripts/digdetail.asp?artnr=DN%2D11004%2DO++++++++++)) which can be purchased at Conrad in Germany. The firmware version is 02.00.00.03 in German.  I've never found a firmware update, or I wound have at least put on an english firmware.  Like I said though, the router has no trouble with 3 other Ubuntu installs in the house, and a SuSE install on the same computer.

---

### Post by dbott67 on 2006-12-09
Try changing the resolv.conf file as described above, but don't restart... just try to get online.

If it works, then you can modify the dhclient.conf and add the 2 nameservers:
```
sudo gedit /etc/dhcp3/dhclient.conf
```
Look for the section:
```
#prepend domain-name-servers 127.0.0.1;
```
Remove the comment (#) and change it to:
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```
Then restart the network and check resolv.conf.

Let me know.

-Dave

---

### Post by superami on 2006-12-10
Well unfortunately that didn't seem to do anything for me.  I can still only find a small number of web sites.

---

### Post by thelinuxguy on 2006-12-12
Since you have partial internet access, and if you are fine with it, someone could log onto your desktop via VNC and work with you in realtime to solve your problem. That would solve your problem much faster than executing commands and pasting the output in the forums. How far this succeeds would depend on whether someone can connect to your pc via vnc and more importantly, whether you are comfortable with it.

Regards.

---

### Post by superami on 2006-12-13
> **thelinuxguy said:**
> Since you have partial internet access, and if you are fine with it, someone could log onto your desktop via VNC and work with you in realtime to solve your problem. That would solve your problem much faster than executing commands and pasting the output in the forums. How far this succeeds would depend on whether someone can connect to your pc via vnc and more importantly, whether you are comfortable with it.

Regards.

Generally I wouldn't be too concerned about it, but since this is my business laptop, I have confidential customer information on it and my concern would be how to safe guard the windows partition against access from VNC and how to ensure that no spyware or back doors are left on the computer.

Also, my connection is not all too stable.  Sometimse I get through other times not.

---

### Post by dbott67 on 2006-12-13
Check this [thread...]("http://www.ubuntuforums.org/showthread.php?t=317721") appears to be very similar problem.  

Post #8 (copied below) seems to have fixed the issue:

You need to:

a) add the line in blue to use the OpenDNS server
b) remove the part highlighted in red below from **/etc/dhcp3/dhclient.conf**, then it won't request the name server from your router (which is the DHCP server for your network).

```
[COLOR="Blue"]**prepend domain-name-servers 208.67.222.222;**[/COLOR]
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **[COLOR="Red"]domain-name-servers,[/COLOR]** host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
```

Just be sure to backup the file first:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak
```

-Dave

---

### Post by superami on 2006-12-17
Well I was finally able to get my network connection to work fairly well.  I did a fresh install with the network cable unplugged.  Then I plugged in the network cable and modified:

/etc/networking/interfaces 

by adding the following
```
    up ifconfig eth0 mtu 1500
```

after 

```
auto eth0
iface eth0 inet dhcp
```

Then things seem to work fine.  

Thanks for all the help and suggestions.

---

