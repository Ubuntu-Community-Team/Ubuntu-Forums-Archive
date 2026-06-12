---
title: "HomePna internet connection problem"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by Sammel on 2008-05-13
I installed Ubuntu 7.10 some time ago and its working fine, except I can't get my internet connection to work.

My Network card is Advanced Micro Devices (AMD) AM79C978 PCnet Single Chip Home Networking Controller 1/10Mbps. My connection type is HomePna.
Connection works in Windows Xp which is intalled on same computer.

What should I do to make it work in Ubuntu too?

---

### Post by chili555 on 2008-05-13
HomePNA! Now there's a black magic protocol! You might try:```
sudo modprobe pcnet32 homepna=1
```Then see if *ifconfig* shows an interface, eth0 perhaps, that you can now configure through System -> Administration -> Network.

---

### Post by Sammel on 2008-05-13
Ifconfig shows eht0 and eht1. Is this good or bad?

---

### Post by chili555 on 2008-05-13
It's good. One of them is probably your HomePNA! Did you go to System -> Administration -> Network to see if you can configure it?

My guess is eth1 might be HomePNA. You can get a bit more information with:```
sudo lshw -C network
```See if your card has a logical name, eth1, for example, and the all important *link=yes* then I'd try:```
sudo dhclient eth1
```Did you connect?

---

### Post by Sammel on 2008-05-14
> delzun@Gaidin:~$ sudo dhclient eht0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eht0: ERROR while getting interface flags: No such device
eht0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
delzun@Gaidin:~$ sudo dhclient eht1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eht1: ERROR while getting interface flags: No such device
eht1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
delzun@Gaidin:~$
                                                                         

Whats wrong here?

---

### Post by chili555 on 2008-05-14
What's wrong here is that the interfaces are **eth0** and **eth1**, not eht0 nor eht1. eth as in ethernet, although most eth1 interfaces are wireless, HomePNA, etc., anything but actual CAT5 ethernet.

---

### Post by Sammel on 2008-05-15
What should I do now?

---

### Post by chili555 on 2008-05-15
```
sudo modprobe pcnet32 homepna=1
sudo dhclient eth1
```If you don't connect, please let us see the output.

---

### Post by Sammel on 2008-05-18
> delzun@Gaidin:~$ sudo modprobe pcnet32 homepna=1
[sudo] password for delzun:
delzun@Gaidin:~$ sudo dhclient eht1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eht1: ERROR while getting interface flags: No such device
eht1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
delzun@Gaidin:~$

Didn't work, this was what it gave.

---

### Post by chili555 on 2008-05-18
> **Sammel said:**
> Didn't work, this was what it gave.Please see post #6 above. Please try again:```
sudo dhclient eth1
```

---

### Post by Sammel on 2008-05-20
Same reply again.

---

### Post by chili555 on 2008-05-20
Please do:```
sudo modprobe pcnet32 homepna=1
sudo lshw -C network
```and post the result.

---

### Post by Sammel on 2008-05-20
> delzun@Gaidin:~$ sudo modprobe pcnet32 homepna=1
[sudo] password for delzun:
delzun@Gaidin:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 79c978 [HomePNA]
       vendor: Advanced Micro Devices [AMD]
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: eth1
       version: 52
       serial: 00:08:54:d5:da:d5
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.33 latency=32 link=no maxlatency=24 mingnt=24 module=pcnet32 multicast=yes
 

This is what I got this time.

---

### Post by chili555 on 2008-05-20
That looks very healthy except:> link=noPlease:
1. Make sure the phone line is connected to the device, the router, and, of course, the wall.
2. Are there any lights on the card? On or off? One or two?
3. No listing in *sudo lshw -C network* for any other devices?
4. Can you please post the last 6-8 lines of:```
sudo cat /var/log/messages | grep pcnet
```Thanks.

---

### Post by Sammel on 2008-05-22
1. Is connected
2. There are two lights. While Windows is up one light is on all the time, other flashes. While Linux is up, they both stay dark.
3. No
4.
> May 14 22:16:28 Gaidin kernel: [   42.149946] pcnet32.c:v1.33 27.Jun.2006 [email]tsbogend@alpha.franken.de[/email]
May 14 22:16:28 Gaidin kernel: [   45.042694] pcnet32: PCnet/Home 79C978 at 0xbc00, 00 08 54 d5 da d5 assigned IRQ 20.
May 14 22:16:28 Gaidin kernel: [   45.042775] pcnet32: 1 cards_found.
May 15 16:44:08 Gaidin kernel: [   49.977381] pcnet32.c:v1.33 27.Jun.2006 [email]tsbogend@alpha.franken.de[/email]
May 15 16:44:08 Gaidin kernel: [   52.876201] pcnet32: PCnet/Home 79C978 at 0xbc00, 00 08 54 d5 da d5 assigned IRQ 20.
May 15 16:44:08 Gaidin kernel: [   52.876283] pcnet32: 1 cards_found.
May 18 14:21:23 Gaidin kernel: [   40.012752] pcnet32.c:v1.33 27.Jun.2006 [email]tsbogend@alpha.franken.de[/email]
May 18 14:21:23 Gaidin kernel: [   42.909277] pcnet32: PCnet/Home 79C978 at 0xbc00, 00 08 54 d5 da d5 assigned IRQ 20.
May 18 14:21:23 Gaidin kernel: [   42.909357] pcnet32: 1 cards_found.
May 20 17:20:21 Gaidin kernel: [   37.105718] pcnet32.c:v1.33 27.Jun.2006 [email]tsbogend@alpha.franken.de[/email]
May 20 17:20:21 Gaidin kernel: [   40.004279] pcnet32: PCnet/Home 79C978 at 0xbc00, 00 08 54 d5 da d5 assigned IRQ 20.
May 20 17:20:21 Gaidin kernel: [   40.004358] pcnet32: 1 cards_found.
May 20 21:16:29 Gaidin kernel: [   36.895674] pcnet32.c:v1.33 27.Jun.2006 [email]tsbogend@alpha.franken.de[/email]
May 20 21:16:29 Gaidin kernel: [   39.792135] pcnet32: PCnet/Home 79C978 at 0xbc00, 00 08 54 d5 da d5 assigned IRQ 20.
May 20 21:16:29 Gaidin kernel: [   39.792213] pcnet32: 1 cards_found.
May 22 13:04:44 Gaidin kernel: [   39.202098] pcnet32.c:v1.33 27.Jun.2006 [email]tsbogend@alpha.franken.de[/email]
May 22 13:04:44 Gaidin kernel: [   42.100293] pcnet32: PCnet/Home 79C978 at 0xbc00, 00 08 54 d5 da d5 assigned IRQ 20.
May 22 13:04:44 Gaidin kernel: [   42.100376] pcnet32: 1 cards_found.
May 22 13:15:56 Gaidin kernel: [   39.638212] pcnet32.c:v1.33 27.Jun.2006 [email]tsbogend@alpha.franken.de[/email]
May 22 13:15:56 Gaidin kernel: [   42.536221] pcnet32: PCnet/Home 79C978 at 0xbc00, 00 08 54 d5 da d5 assigned IRQ 20.
May 22 13:15:56 Gaidin kernel: [   42.536304] pcnet32: 1 cards_found.
delzun@Gaidin:~$                                                             


---

### Post by chili555 on 2008-05-22
Please execute the following commands. Double check your typing, because each character and space is crucial:```
sudo su
```Give your password.```
echo 'options pcnet32 homepna=1' > /etc/modprobe.d/pcnet32
gedit /etc/network/interfaces
```The text editor 'gedit' will pop up with a file ready to edit. Don't remove anything! Make sure there are lines in place like this:```
auto eth1
iface eth1 inet dhcp
```Add them if not. Save and close gedit. Reboot. Did the lights come on on the card? When you run:```
ifconfig
```Did you get an IP address?

---

### Post by Sammel on 2008-05-22
>  
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth1 inet dhcp

auto eth1

iface eth0 inet dhcp

This was what I had in text editor, before I did anyting to it.
Should I change "iface eth0 inet dhcp" to "iface eth1 inet dhcp" or is ok now?

---

### Post by chili555 on 2008-05-22
Since you have nothing in *lshw* that relates to eth0, I would comment it out. Also, I'd like to have the *auto eth1* before the other eth1 stuff. Please make it look like this:```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth1
iface eth1 inet dhcp

#iface eth0 inet dhcp
```As always, please double-check your work.

---

### Post by Sammel on 2008-05-22
I made those changes. But lights on networking card still stay dark. Rebooting didn't help.

---

### Post by chili555 on 2008-05-22
Please post:```
cat /etc/modprobe.d/pcnet32
ifconfig
```Let's see if we made any errors.

---

### Post by Sammel on 2008-05-28
Finally I have some for this again.

> delzun@Gaidin:~$ cat /etc/modprobe.d/pcnet32
options pcnet32 homepna=1
delzun@Gaidin:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:05:78:DF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:08:54:D5:DA:D5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xbc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

delzun@Gaidin:~$
 


---

### Post by chili555 on 2008-05-28
Looks perfect. Does:```
sudo lshw -C network
```still show *eth1* as the relevant interface for your card? If so, please do:```
sudo ifdown eth1 && sudo ifup -v eth1
```Please let us see the output. Thanks.

---

### Post by Sammel on 2008-05-28
> delzun@Gaidin:~$ sudo lshw -C network
[sudo] password for delzun:
  *-network
       description: Ethernet interface
       product: 79c978 [HomePNA]
       vendor: Advanced Micro Devices [AMD]
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: eth1
       version: 52
       serial: 00:08:54:d5:da:d5
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.33 latency=32 link=no maxlatency=24 mingnt=24 module=pcnet32 multicast=yes
delzun@Gaidin:~$ sudo ifdown eth1 && sudo ifup -v eth1
ifdown: interface eth1 not configured
Configuring interface eth1=eth1 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:08:54:d5:da:d5
Sending on   LPF/eth1/00:08:54:d5:da:d5
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant
delzun@Gaidin:~$

This was reply this time.

---

### Post by Sammel on 2008-05-31
Does this look good or bad?

---

### Post by chili555 on 2008-05-31
It looks perfect, right up to:> No DHCPOFFERS received.
No working leases in persistent database - sleeping.Everything looks like it's humming along happily until it doesn't connect.

Let's try a few other things. ```
sudo gedit /etc/modprobe.d/pcnet32
```Make it look like this:```
options eth1 homepna=1
options pcnet32 homepna=1
```Save and close gedit. Reboot. Please do:```
lsmod | grep mii
```If *mii* got loaded, that's fine. Then do:```
sudo ifdown eth1 && sudo ifup eth1
```I hope you connect; I'm running low on ideas, clues and ammunition.

On the other end of the phone line, is there a HomePNA router that gets the internet from a DSL modem or cable modem?

---

### Post by Sammel on 2008-06-01
> **chili555 said:**
> 
On the other end of the phone line, is there a HomePNA router that gets the internet from a DSL modem or cable modem?

From my computer, cable goes to thing like [this.]("http://www.vekoy.com/images/PT-3.png") ( I dont know what that is called in english.) And it goes to telephone plug.

From there I can't know were it goes, but manual of my connection tells that:
There is one common ADLS-connection to Internet for housing organization.
There is one ADLS-router in housing organization's phonecenter.
ADLS-router acts as NAT-firewall.
ADLS-router acts as DHCP-server.
Housing organization's intranet is made by Home-PNA tech.
Home-PNA switch is located in housing organization's phonecenter.
Home-PNA switch is pluged into ADLS-router using ethernet-cable.
Pholines from each apartment are pluged into their own ports in Home-PNA switch.
Computers in aparments must be pluged into telephone plug.

Does this make any sense?
Manual was written in Finnish so my traslations might be inaccurate.
I didn't yet have time try commands you gave, but I will check them soon.

---

### Post by Sammel on 2008-06-01
This was orginal /etc/modprobe.d/pcnet32:
> options pcnet32 homepna=1

I made it to look like this.
> options eth1 homepna=1
options pcnet32 homepna=1 

After reboot
> delzun@Gaidin:~$ lsmod | grep mii
mii                     6528  1 pcnet32

And then.
> 
delzun@Gaidin:~$ sudo ifdown eth1 && sudo ifup eth1
ifdown: interface eth1 not configured
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:08:54:d5:da:d5
Sending on   LPF/eth1/00:08:54:d5:da:d5
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
delzun@Gaidin:~$

Connection not working yet.

---

