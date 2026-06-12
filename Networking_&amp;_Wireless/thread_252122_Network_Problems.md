---
title: "Network Problems"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by JonParis on 2006-09-06
I originally posted this in the beginners area [http://www.ubuntuforums.org/showthread.php?t=248655](http://www.ubuntuforums.org/showthread.php?t=248655) but there's such a volume of traffic there that after the couple of responses it just died.

Hopefully someone here can offer some suggestions or I'm going to have to abandon this project.

As noted in the thread referenced above the laptops ethernet card is recognized by ubuntu and set up as eth0.  If I manually asign an IP it can ping its own IP.  However, it cannot see the rest of the network so DHCP won't work either.

If I boot puppy it works perfectly - I can pick up an IP etc. via DHCP and all works just fine after using the puppy wizard.  

So puppy is an option but I _much_ prefer ubuntu so I'd really like to solve this.

Machine is a Thinkpad 390X with a 3com ethernet PC card

---

### Post by tbonius on 2006-09-06
Post a copy of your /etc/network/interfaces to see how this interface is configured.

T

---

### Post by JonParis on 2006-09-06
Hi tbonius - thanks for responding.

The file looks like this:

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

The original file as configured by ubuntu during the install was missing the auto eth0 line - I added that as suggested by another responder.

In the earlier thread I was also asked about the ifconfig results these are the ones I obtained when I had it configured with a fixed IP.

eth0 Link encap:Ethernet HWaddr 00:50:04:B4:3D:F3
inet addr:192.168.1.110 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::250:4ff:feb4:3df3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:6211 errors:0 dropped:0 overruns:0 carrier:6205
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:502118 (490.3 KiB)
Interrupt:3 Base address:0x300

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:743 errors:0 dropped:0 overruns:0 frame:0
TX packets:743 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:66928 (65.3 KiB) TX bytes:66928 (65.3 KiB)

---

### Post by tbonius on 2006-09-06
Well it looks like youre getting an IP address.. in the 192.168.1.x subnet.  Where is your DHCP server?  Who maintains it?  Check your default gateway:

```
nestat -rn

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0                   0 eth0
0.0.0.0         192.168.1.1      0.0.0.0         UG        0 0          0 eth0

```

Something similar should appear... the bottom IP is usually your assigned gateway.  Can you ping that gateway?

Also check your kernel messages for eth0 entries:

```
dmesg |grep eth0
```

What info does it return?

T

---

### Post by JonParis on 2006-09-06
The results you saw were when I configured a fixed IP.  As I said in the earlier message "In the earlier thread I was also asked about the ifconfig results these are the ones I obtained when I had it configured with a fixed IP."

It cannot ping anything on the network except itself.  Both loopback (as expected) and its own 192.168.1.110 address respond.  Any other ping request is met with Network unreachable or some similar message.

I can try the netstat and will have a look at the logs - but that would be easier if you could tell me where the systems own name is stored.  I blanked it out of the network settings dialog in case it was part of the trouble and now cannot connect an xterm to the system, apparently becuase it has no name.

Thanks for your help - onward and upward!

Jon

---

### Post by Iowan on 2006-09-06
> **JonParis said:**
> ...- but that would be easier if you could tell me where the systems own name is stored...
Are you asking about /etc/hostname?  
There's also a /bin/hostname... which is the command for SETTING the hostname. For info:
```
hostname -h
```

---

### Post by JonParis on 2006-09-07
> 
Also check your kernel messages for eth0 entries:

```
dmesg |grep eth0
```

What info does it return?

T

In oder to ensure that previous attempts hadn't made matters worse - today I completely reinstalled.

eth0 is set to look for a DHCP server (which is a D-Link wireless router is it matters).  

The dmesg entries show:

eth0: found link beat
eth0: autonegotiation complete: 100baseT-FD selected
eth0: interrupt(s) dropped!
eth0: no IPv6 routers present

And that's it.  As noted earlier - puppy does pick up the DHCP server - but not Ubuntu (live or installed)

Once ahgain thanks for the help so far

Jon

---

### Post by tbonius on 2006-09-07
I did not realize you were configuring the machine statically.. considering your interface file showed eth0 to be dhcp.  Start with the bottom layers and work your way up..

Double check quality of the ethernet cable.. replace and try again.

Double check the ethernet interface in your Ubuntu computer.. replace and try again.

Double check the port on the (Dlink?) router... try another port and reboot the Ubuntu computer

Disable IPV6 on the Ubuntu computer. Create file called: bad_list in /etc/modprobe.d containing this line:

alias net-pf-10 off

Reboot and try again.

Check for any firmware updates on your Dlink router.  Try again.

This sounds more like a hardware issue somewhere.. but Im not sure.  If you are statically setting your address.. and you are positive you are using the correct address range.. netmask.. gateway.. and DNS server settings.. then there is another issue..   maybe the cable.. or the ethernet interface..

T

---

### Post by JonParis on 2006-09-07
I only tried static config when DHCP wouldn't work.  It is currently configured for DHCP

I have tried the IPV6 suggestion.  The messages in the log for eth0 are identical it made no difference.

It is hard to believe that it is a harware problem.  If I literally do nothing but tell it to reboot with a puppy linux boot CD in the drive it boots into puppy and the connection works perfectly.  Same thing with booting into Win2K.  Surely a hardware problem would also manifest itself in one or both?

---

### Post by compunuts on 2006-09-08
> **JonParis said:**
> I only tried static config when DHCP wouldn't work.  It is currently configured for DHCP
Okay, so if you do "ifconfig eth0", what does it return?

> Surely a hardware problem would also manifest itself in one or both?I tend to agree. If one distro of Linux picked it up good, then the hardware should be good but a screwed config somewhere.

With DHCP setting, try to ping your localhost. Issue also ifconfig to see if your NIC card is being assigned an IP via DHCP. Then we can go a step further.

---

### Post by JonParis on 2006-09-08
Ping to loopback works fine

ifconfig eth0 shows no IP being picked up - details are:

eth0 Link encap:Ethernet HWaddr 00:50:04:B4:3D:F3
inet6 addr: fe80::250:4ff:feb4:3df3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:736 errors:0 dropped:0 overruns:0 carrier:1
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:62736 (61.2 KiB)
Interrupt:3 Base address:0x300

---

### Post by tbonius on 2006-09-08
Very odd.. maybe dhclient is biting the big one.  Perform these commands (as sudo)

killall dhclient
ifdown eth0 && ifup eth0
dhclient eth0

Do you get an IP at all?  What does dmesg show?

T

---

### Post by JonParis on 2006-09-08
killall dhclient returns "no process killed"

ifdown ... returned a bunch of stuff (I won't try to re-type it all - if I miss somehting important please let me know)

Listening on LPF/eth0/....
Sending on LPF/eth0/....
Sending on Socket/fallback
ifup: failed to open statefile /var/run/network/ifstate: Permission denied

dhclient eth0 returns:

** Listening/sending as per idown info.
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
** above repeated with intervals 13, 15, 21 and 6
NO DHCPOFFERS received
No working leases in persistent database - sleeping

The dmesg items are much as before:

ASIC rev 1,<6>eth0: Megahertz 574B at io 0x300, irq 3, hw_addr ...
eth0: found link beat
eth0: autonegotiation complete: 100baseT-FD selected
eth0: interrupt(s) dropped!
eth0: no IPv6 routers present
eth0: no IPv6 routers present


As you will know from the above no IP address was picked up.

I may be able to dig out another ethernet card to try if you think it worth it - but since the set up of this one was via the auto config I'm not sure where to start.  For that matter I have wireless cards available but from the forums it sounds like they are more likely to cause a novice like myself more problems.

Again many thanks for your patience

Jon

---

### Post by tbonius on 2006-09-08
Make sure you are performing these commands as sudo (or root)

Verify that the ifstate is present and witht he correct permissions:

-rw-r--r--  1 root root   26 2006-07-29 15:18 ifstate

Also.. you arent getting any DHCP offers.. something wrong with the DHCP server?  Trying another NIC might work as well if you can verify that your DHCP server is indeed functioning correctly.

Wireless acrds are nother bag.. but if you have one that natively works in Linux.. Ubuntu makes it pretty easy to get it going.

T

---

### Post by 0be1 on 2006-09-10
FYI;

I have just made another posted along this topic line and I managed to fix my problem.

You can see it here: [http://www.ubuntuforums.org/showthread.php?t=254625](http://www.ubuntuforums.org/showthread.php?t=254625)

Now I never changed back my original config files to the way they were duing a fresh install, but I do know this is the last things I did, and I am working great now.

regards...

0be1

---

