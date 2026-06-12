---
title: "[SOLVED] Wired LAN connection does not last"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by msharma on 2008-03-18
Since I can not connect to our wired LAN using the network manager applet, I have been trying dhclient. When I run dhclient, I can connect for the first couple of internet addresses. But after around half a minute the connection is not possible. (e.g. I get message "Server Not Found" on Firefox.)

Here are the snapshots from my commandline:
-----------------------
> sudo dhclient eth0; ifconfig eth0;

There is already a pid file /var/run/dhclient.pid with pid 13934
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0f:1f:af:78:68
Sending on   LPF/eth0/00:0f:1f:af:78:68
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.26 -- renewal in 101897 seconds.

> ifconfig eth0;
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:AF:78:68  
          inet addr:192.168.1.26  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7219813 (6.8 MiB)  TX bytes:579757 (566.1 KiB)
          Interrupt:10 
-----------------------

Thanks,
Mohit

---

### Post by Eiríkr on 2008-03-18
What do you mean by "When I run dhclient, I can connect for the first couple of internet addresses"?  Do you mean you can browse a few different sites, and then connectivity fails?  Or do you mean you can connect for the first few DHCP address leases your client machine receives?

Cheers,

Eiríkr

---

### Post by msharma on 2008-03-18
"Do you mean you can browse a few different sites, and then connectivity fails?"

Yeah, that was what I meant.

Thanks,
Mohit

---

### Post by Eiríkr on 2008-03-18
A few questions, then --
[list=1][*]Why does Network Manager not work for you?  What kind of errors does it generate?
[*]What does [font=courier]ifconfig[/font] look like after the connection fails?
[*]Could you please post your [font=courier]/etc/network/interfaces[/font] file?[/list]

Cheers,

Eiríkr

---

### Post by msharma on 2008-03-18
1. Why does Network Manager not work for you? What kind of errors does it generate?
- It is in the forever "Requesting Network Address" loop. So, it does not pop up a message, but keeps trying to acquire a network address.

2. What does ifconfig look like after the connection fails?
- I can not give you the paste of ifconfing with network manager, as I uninstalled it as a last resort. But I ran ifconfing quite a few times when network manager was installed, and the ifconfig output was very similar to the dhconfing one (except maybe for the no. of bytes etc.)

3. Could you please post your /etc/network/interfaces file?
--------
> cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp
#address 192.168.1.26
#netmask 255.255.255.0
#gateway 192.168.1.1

auto eth0
---------

I had added the commented IP addresses in the last lines manually as a hit&try.

Thanks,
Mohit

---

### Post by Eiríkr on 2008-03-18
> - I can not give you the paste of ifconfing with network manager, as I uninstalled it as a last resort. But I ran ifconfing quite a few times when network manager was installed, and the ifconfig output was very similar to the dhconfing one (except maybe for the no. of bytes etc.)

Sorry for any confusion :), but [font=courier]ifconfig[/font] is actually a standalone command, and it doesn't really matter to me if you're running it together with Network Manager or [font=courier]dhclient[/font] -- I'm just interested in being able to compare the results from while your connection is up and running, and then from after it's gone funny.  

When you did your hit & try attempt, did you also change [font=courier]dhcp[/font] to [font=courier]static[/font]?  Did it work any better?

Next time your dhclient fails out, try simply running this and see if your connectivity is a) restored, and b) any longer-lasting.
```
sudo /etc/init.d/networking restart
```

If this generates any errors, please post them here.

Cheers,

Eiríkr

---

### Post by Iowan on 2008-03-19
Wonder if DNS address is getting overwritten? (I've heard of **dhclient** doing that)  There's a post around here somewhere that suggests setting DNS addresses in router, and pointing clients there.

---

### Post by msharma on 2008-03-19
"Sorry for any confusion , but ifconfig is actually a standalone command..."
I am a retard. :)

--------
> ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:AF:78:68  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40444 (39.4 KiB)  TX bytes:0 (0.0 b)
          Interrupt:10 
--------

"Next time your dhclient fails out, try simply running this and see if your connectivity is a) restored, and b) any longer-lasting."
This has led to the connectivity lasting a while (~20 minutes now and not dead yet). Here are the terminal logs:
--------
> sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
.
.
.
Failed to bring up wlan0.
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

/var/lib/dhcp3/dhclient.eth0.leases line 29: lease specified for unknown pseudo.
  expirelease {
              ^
/var/lib/dhcp3/dhclient.eth0.leases line 30: expecting semicolon.
  interface 
  ^
Can't allocate interface ethlease {
  interface .
Failed to bring up eth0.
--------

So I opened /var/lib/dhcp3/dhclient.eth0.leases. It had mismatched braces '{' and possibly other errors. I created an empty /var/lib/dhcp3/dhclient.eth0.leases.
--------
> sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
.
.
.
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 7228
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0f:1f:af:78:68
Sending on   LPF/eth0/00:0f:1f:af:78:68
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.26 -- renewal in 122358 seconds
--------
The connection has not not gone down yet.


"Wonder if DNS address is getting overwritten?"
Not very far from the mark.

---

### Post by Eiríkr on 2008-03-19
Not a retard at all, mate -- or I'm sitting next to you there on the short bus, for all I still have to learn.  :mrgreen:

Very obscure errors there in the leases file.  I wonder which process might have borked that?  Anyway, glad at least that wired connectivity seems to be working now.  Here's hoping it lasts!  :D  And do you even have a wireless interface on your machine?  If not, the lines relating to wlan0 can be safely removed from your interfaces file -- which should also get rid of those errors about failing to bring it up.  

Cheers,

Eiríkr

---

### Post by lavinog on 2008-03-19
what does dmesg say before and after you loose your connection?

have you tried a different ethernet cable...maybe the cable could be bad...also you should test to see that it isn't your router...i had a linksys router do that to me where it worked for a couple of minutes then it would not work until i let it sit for a couple of mins...try bypassing your router and hook up directly to your internet connection...(just to see if the problem goes away)

---

### Post by dacorr on 2008-03-19
what model is your router?

Some routers are DNS forwarders and dont handle the requests just pass them on.

if this is the case

sudo gedit /etc/resolv.conf

then add 

nameserver <IP> 

the IP is the address of the ISP DNS servers (obtainable from router status webpage page)

this file should be populated by the network manager when started but i have seen instances when it does not usually with netgear and belkin.

Dac

---

### Post by msharma on 2008-03-19
Thanks guys, this problem is resolved. It was corrupt 'dhclient.eth0.leases'.

Eiríkr, thanks for leading to the solution. I was trying to figure out the origin, but no luck.

Thanks,
Mohit

---

### Post by gedden on 2008-05-09
I am having this same problem, at this house I am house sitting for the weekend. I have to use static nameservers, and it seems to be overwritten every minute and a half. how can I find out if my file is corrupt also? from my syslog I see that my dhcp renewal is set for 113 seconds or so. Is there a way to set the time before a renewal? I have in the past edited my dhcp3 file to remove the request for a nameserver, but my file was still not working after a renewal.

---

