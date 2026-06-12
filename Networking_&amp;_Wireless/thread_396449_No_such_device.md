---
title: "No such device"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by voltage on 2007-03-29
Hi,

may I know why below message appear while I type **sudo /etc/init.d/networking restart**

[COLOR="Blue"]* Reconfiguring network interfaces....
There is already a pid file /var/run/dhclient.eth.pid with pid 5798864
Internet Systems Consortium.
All right reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags : No such device
eth0: ERROR while getting interface flags : No such device
Bind socket to interface: No such device
Failed to bring up eth0[/COLOR]

Please advice ..
Thanks

---

### Post by dannyboy79 on 2007-03-29
please post the output from

**sudo cat /etc/network/interfaces**

and also

**sudo ifconfig -a**

did you go thru the system, admin, networking dialog box and configure whatever interface showed up there? Do you want to use static or dhcp?

---

### Post by voltage on 2007-03-29
> **dannyboy79 said:**
> please post the output from

**sudo cat /etc/network/interfaces**

and also

**sudo ifconfig -a**

did you go thru the system, admin, networking dialog box and configure whatever interface showed up there? Do you want to use static or dhcp?

**sudo cat /etc/network/interfaces**

[COLOR="Blue"]# auto lo
# iface lo inet loopback

auto eth0
iface eth0 inet dhcp[/COLOR]

**sudo ifconfig -a**

[COLOR="Blue"]lo     Link encap:Local Loopback
       LOOPBACK MTU:16436 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0     
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions: 0 txqueuelen:0
       RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)[/COLOR]

---

### Post by Mr. C. on 2007-03-29
> **voltage said:**
> Hi,

may I know why below message appear while I type **sudo /etc/init.d/networking restart**

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags : No such device
eth0: ERROR while getting interface flags : No such device
Bind socket to interface: No such device
Failed to bring up eth0[/COLOR]


This means the system has not associated the device "eth0" with a physical piece of hardware, or that the hardware's driver was not loaded and initialized.

Examine output from 

```
dmesg | less
```

for lines indicating eth0 (and any other ethN lines) and the lines nearby to find out why the device failed to initialize.

MrC

---

### Post by voltage on 2007-03-29
> **Mr. C. said:**
> This means the system has not associated the device "eth0" with a physical piece of hardware, or that the hardware's driver was not loaded and initialized.

Examine output from 

```
dmesg | less
```

for lines indicating eth0 (and any other ethN lines) and the lines nearby to find out why the device failed to initialize.

MrC

So what should I need to do ? Install the device ? How ?

Please advice .. thanks

---

### Post by Mr. C. on 2007-03-29
Let me clarify my request.  Show us the output of dmesg, for all lines pertaining to eth0 and lines immediately before/after.  If you want to post the entire file as an attachment, thats fine.  We'll search for you.

MrC

---

### Post by dannyboy79 on 2007-03-29
please also show us the output from this command

sudo lspci -v | grep Ethernet

and to clarify Mr. C.'s request, please show us the result of this also

dmesg | grep eth

---

### Post by voltage on 2007-03-29
> **dannyboy79 said:**
> please also show us the output from this command

sudo lspci -v | grep Ethernet

and to clarify Mr. C.'s request, please show us the result of this also

dmesg | grep eth

Hi,

     I have try the ***sudo lspci -v | grep Ethernet*** and ***dmesg | grep eth***. but that was nothing show.

---

### Post by dannyboy79 on 2007-03-29
ok, well then please just post the output from 

sudo lspci -v | grep E

because when I do that it shows me ethernet device. also when I do

dmesg | grep eth

it shows me my ethernet interface as well. don;'t put a period on the end of eth
is your ethernet plug built into your motherboard or is it a seperate card? can you try and plug it into a different pci slot?

---

### Post by voltage on 2007-03-29
> **dannyboy79 said:**
> ok, well then please just post the output from 

sudo lspci -v | grep E

because when I do that it shows me ethernet device. also when I do

dmesg | grep eth

it shows me my ethernet interface as well. don;'t put a period on the end of eth
is your ethernet plug built into your motherboard or is it a seperate card? can you try and plug it into a different pci slot?

Thanks for you help, unfortunedly it still appear any ethernet device. So do you feel that do my ethernet card doesn't support Ubuntu O/S ?

---

### Post by dannyboy79 on 2007-03-30
can you please read my post and when you respond answer my questions. This way I won't have to ask them over again. Also, I don't really understand your english, are you meaning to write that ethernet does NOT appear?

is your ethernet plug built into your motherboard or is it a seperate card? can you try and plug it into a different pci slot?

---

