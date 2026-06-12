---
title: "Changed /etc/network/interfaces and now no connection"
date: 2005-10-31
forum: Networking &amp; Wireless
---

### Post by atomicsmith on 2005-10-31
Hi everyone,

First post in the ubuntu forums. 
I installed Kubuntu about a week abo (loving it so far). The important stuff all worked just fine, but of course no wifi connection.
in the process of trying to get my wifi working I copied and pasted the text from a thread on this forum into the /etc/network/interfaces file and inserted as much info as I could find. when I restarted, I had lost my wired connection, and of course the wifi connection still didn't work. I suppose this is a dreaded two part question:

1) can someone please tell me what the default /etc/network/interfaces file says so that I can at least get a connection.

2)I've checked the web, the wiki and this forum, but I cannot find an explanation of what each line of the interfaces file means or even what some of the commands mean (what for instance does wlan0 mean? I'm guessing something about wlan on/off but which is it?). Could someone either explain, or point me towards an explanation of what I'm doing to this file?

Thanks,

Adam

---

### Post by daller on 2005-10-31
This is the "default" file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
 mapping hotplug
       script grep
       map eth0

#The primary network interface
iface eth0 inet dhcp

---------

Well, with "eth0" it depends what your card is named!

Run "ifconfig -a" to find out!!!

What wireless card do you have?

---

### Post by atomicsmith on 2005-10-31
Thanks, I'm connected again,

[QUOTE=daller]
Well, with "eth0" it depends what your card is named!

Run "ifconfig -a" to find out!!!

What wireless card do you have?[/QUOTE]

not quite sure i know what you mean, I have run that, and I get three sort of headings with text associated. the headings are: eth0, lo, sit0. the text for eth0 has lots of what looks like ipaddresses, but nothing i can easily identify as a name.

when i made the fatal changes, I was trying to use ndiswrapper.
now that I'm reconnected, I'm going to follow these instructions from the wiki which are written specifically for my wifi radio.
[https://wiki.ubuntu.com/BuffaloWLIL11GUSB](https://wiki.ubuntu.com/BuffaloWLIL11GUSB)

I'm just at step three.

Adam

---

### Post by daller on 2005-10-31
Well, when you get the driver installed properly, I'll help you with your /etc/network/interfaces!!!

Run "iwconfig" to find out the interface name (was it wlan0, or did you just asume that?)

My extra lines in the file, looks like this:

iface eth1 inet dhcp
wireless-essid INTERFACE-NAME
wireless-key WEP-KEY

eth1 should probably be wlan0 in your case!

And then you activate it with "sudo ifup eth1" (wlan0???)

---

### Post by atomicsmith on 2005-11-03
This may be slightly off topic, but....

I'm at the end of step 5 on the wiki page I mentioned above. Everything up till now has been fine, but I get this message when try to install:

:/root/debs$ cd orinoco-usb-0.2.2
:/root/debs/orinoco-usb-0.2.2$ make && sudo make install
make -C driver
make[1]: Entering directory `/root/debs/orinoco-usb-0.2.2/driver'
mkdir -p .tmp_versions
cp /lib/modules/2.6.12-9-686/build/.tmp_versions/*.mod /root/debs/orinoco-usb-0.2.2/driver/.tmp_versions
cp: cannot stat `/lib/modules/2.6.12-9-686/build/.tmp_versions/*.mod': No such file or directory
make[1]: [modules] Error 1 (ignored)
make -C /lib/modules/2.6.12-9-686/build SUBDIRS=/root/debs/orinoco-usb-0.2.2/driver MODVERDIR=/root/debs/orinoco-usb-0.2.2/driver/.tmp_versions modules
make: *** /lib/modules/2.6.12-9-686/build: No such file or directory.  Stop.
make: Entering an unknown directorymake: Leaving an unknown directorymake[1]: *** [modules] Error 2
make[1]: Leaving directory `/root/debs/orinoco-usb-0.2.2/driver'
make: *** [all] Error 2



any ideas what's wrong? is there a resource to help figure out what error messages mean?

---

### Post by iNerdSure on 2005-11-03
Dear wireless expert, 

Please allow me to join in. I used to access the internet from various hot-spots at cafes and libraries using my laptop on the other M$WXPO$. Now that I've switched over to Breezy, I can no longer access from hot-spots.

An example of ifconfig ouput:
eth0    Link encap:Ethernet  HWaddr 00:13:CE:0C:5D:E6
          inet6 addr: fe80::213:ceff:fe0c:5de6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2000 Memory:b0101000-b0101fff

and  iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      radio off  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Am I doing something not correct or missing some steps? I am a Linux newbie convert. Please help. Many thanks in advance.

---

### Post by daller on 2005-11-03
[QUOTE=iNerdSure]Dear wireless expert, 

Please allow me to join in. I used to access the internet from various hot-spots at cafes and libraries using my laptop on the other M$WXPO$. Now that I've switched over to Breezy, I can no longer access from hot-spots.
[/QUOTE]

How does your /etc/network/interfaces look like?

---

### Post by iNerdSure on 2005-11-03
The /etc/network/interfaces file shows:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp

iface eth0 inet dhcp

auto eth0

auto eth1

iface wlan0 inet dhcp

What should I do next? Thanks.

---

### Post by daller on 2005-11-03
Insert this in the bottom:

iface name_of_your_choice inet dhcp
wireless-essid NETWORK_ESSID
wireless-key DAE2398479324EAD2937486134

(Insert all your hotspots!)

If they are not WEP-encrypted, use only one:

iface eth0 inet dhcp (only the following line is needed, right under this one, which is already there...)
wireless-essid any

Then you save the file, and run:

sudo ifup eth0=name_of_your_choice

Now it should work!

---

### Post by iNerdSure on 2005-11-03
Many thanks, Daller. Will try the solution at a hot spot tomorrow. Will keep you informed of results.

---

### Post by iNerdSure on 2005-11-05
Hi Daller, tried at hotspot again, but without any success. Looks like getting this wireless connection at hotspot isn't as easy as M$WinXP :(

---

### Post by daller on 2005-11-07
[QUOTE=iNerdSure]Hi Daller, tried at hotspot again, but without any success. Looks like getting this wireless connection at hotspot isn't as easy as M$WinXP :([/QUOTE]

Well, it is sad to hear that it troubles you that much!

Please post me your "/etc/network/interfaces"

...and the output of running "sudo ifup eth0=NETWORKNAME" (or sudo ifup eth0, if you configured your hotspots in one!)

---

### Post by iNerdSure on 2005-11-07
Hi Daller,

Tried with the modified interfaces file:
> ins@inerdsure:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp

iface eth0 inet dhcp

wireless-essid any

auto eth0

auto eth1

iface wlan0 inet dhcp
ins@inerdsure:~$
But no success. The 
sudo ifup eth0=NETWORKNAME ouput is:
> ins@inerdsure:~$ sudo ifup eth0=Bishan20
ifup: interface eth0 already configured
ins@inerdsure:~$
Am I missing something? What else can I try? Many thanks, again.:confused:

---

### Post by daller on 2005-11-08
[QUOTE=iNerdSure]Hi Daller,

Tried with the modified interfaces file:

But no success. The 
sudo ifup eth0=NETWORKNAME ouput is:

Am I missing something? What else can I try? Many thanks, again.:confused:[/QUOTE]

...you have to down the interface first:

sudo ifdown eth0

...but what is Bishan20? (You didn't configure it in the interfaces file !!!)

Insert this in the interfaces file: (and remove "iface eth0 inet dhcp" and "wireless-essid key")

iface eth0 inet dhcp
wireless-essid NETWORKNAME (Bishan20 here???)

Try this:

sudo ifdown eth0;sudo ifup eth0

What output now? (No working leases in persistant database?)

...Maybe you should remove "auto eth0" from the file. (It try to connect on startup)

---

### Post by iNerdSure on 2005-11-08
Thanks, Daller. I will down the interface first.
Re: "sudo ifup eth0=NETWORKNAME" , I thought I have to put in the network name of the unsecured network. So, in the case today, the network name was "Bishan20" which I can read from other Win laptops in the hotspot. So, that's my newbie mistake! Sorry.

Will try again and let you know the result.

---

### Post by iNerdSure on 2005-11-08
Hi Daller, just tried from my balcony, as there are several unsecured networks in my neighborhood!

Here's the result:
> 
11:~$ sudo ifdown eth0;sudo ifup eth0
ifdown: interface eth0 not configured
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:13:ce:0c:5d:e6
Sending on   LPF/eth0/00:13:ce:0c:5d:e6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
11:~$
No success. Cannot connect to wireless network.
:confused:
What should I try next? Thanks.

---

### Post by iNerdSure on 2005-11-08
Daller, one more attempt with /etc/network/interfaces:
> 
  11:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp


iface eth0 inet dhcp
wireless-essid NETWORKNAME


auto eth1

iface wlan0 inet dhcp

auto eth0
11:~$

Ran: sudo ifdown eth0;sudo ifup eth0
> 
ptc@sgc9711:~$ sudo ifdown eth0;sudo ifup eth0
ifdown: interface eth0 not configured
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:13:ce:0c:5d:e6
Sending on   LPF/eth0/00:13:ce:0c:5d:e6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
  11:~$

Hope you could advise what am I not doing right. Thanks.

---

### Post by daller on 2005-11-08
Sadly, your solution seems flawless :)

The output tells you that the "/etc/network/interfaces" is probably configured correctly... (You have replaced "iface eth0 inet dhcp
 wireless-essid NETWORKNAME" with whatever the SSID of the network is, right?)

In the example of Bishan20, it should be: (be sure about the capital letters !!!)

iface eth0 inet dhcp 
wireless-essid Bishan20

No luck with 

iface eth0 inet dhcp 
wireless-essid any

??? ("any" is not something I have come up with - It simply takes ANY interface found...)

Good luck!

---

### Post by iNerdSure on 2005-11-08
Thanks, Daller. Will try again at another hotspot to see if there's a difference in the result.

---

### Post by iNerdSure on 2005-11-09
Hi Daller, tried with the amended interfaces file:
> 
  11:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp


iface eth0 inet dhcp
wireless-essid NETWORKNAME


auto eth1

iface wlan0 inet dhcp

auto eth0
  11:~$


No success. I also ran:
> 
  711:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      radio off  ESSID:"LinkSys"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

   11:~$

and
> 
   11:~$ ip a
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth1: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:c0:9f:d2:bf:af brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.196/24 brd 192.168.0.255 scope global eth1
    inet6 fe80::2c0:9fff:fed2:bfaf/64 scope link
       valid_lft forever preferred_lft forever
3: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:13:ce:0c:5d:e6 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::213:ceff:fe0c:5de6/64 scope link
       valid_lft forever preferred_lft forever
4: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0
  11:~$

Any other diagnostics I can try? Thanks.

---

### Post by Elling on 2005-11-09
Did you install the correct headers in step 2? Make is looking for 686 headers -- did you upgrade your kernel?

The directions caveat that they worked under Hoary and *may* work under Breezy. Check those directory names in the error messages and see if they in fact exist.

i.e., /lib/modules/2.6.12-9-686/build/.tmp_versions

---

### Post by daller on 2005-11-09
You still didn't change:

iface eth0 inet dhcp
 wireless-essid NETWORKNAME

into:

iface eth0 inet dhcp
wireless-essid any

????

---

### Post by iNerdSure on 2005-11-09
Sorry, Daller. Missed out that important detail. Have amended the interfaces file:
> 
11:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp


iface eth0 inet dhcp
wireless-essid any


auto eth1

iface wlan0 inet dhcp

auto eth0
11:~$

and bootup at a hotspot:
> 
11:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      radio off  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
11:~$

Still no luck. In hotspot but unable to connect to network. Others around me with M$W connect ok.  :(  They must be wondering why I choose to struggle with this cool Linux in a hotspot?
What else can I try?

---

### Post by daller on 2005-11-10
radio off!!!

You probably have a switch somewhere on the pc, to turn on wireless?

And did you try:

sudo ifdown eth0;sudo ifup eth0

??? (after bootup)

What's the output?

---

### Post by iNerdSure on 2005-11-11
> **daller]radio off!!!

You probably have a switch somewhere on the pc, to turn on wireless?

And did you try:

sudo ifdown eth0 said:**
> 
I can't find the switch of "hotkeys" on laptop to turn on the wireless. Not sure if there's even one. 

Tried sudo ifdown eth0;sudo ifup eth0:
[QUOTE]
There is already a pid file /var/run/dhclient.eth0.pid with pid 6612
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:13:ce:0c:5d:e6
Sending on   LPF/eth0/00:13:ce:0c:5d:e6
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:13:ce:0c:5d:e6
Sending on   LPF/eth0/00:13:ce:0c:5d:e6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Does this help us understand the problem, or cause, better?
:confused:

---

### Post by daller on 2005-11-11
I'm really sorry, but I think I'll have to pass on this one!

I hope you'll get it to work!

---

### Post by iNerdSure on 2005-11-12
[QUOTE=daller]I'm really sorry, but I think I'll have to pass on this one!

I hope you'll get it to work![/QUOTE]
Thanks, Daller. You've tried your best. I guess this is why Linux isn't quite ready for the masses.

---

### Post by daller on 2005-11-14
[QUOTE=iNerdSure]Thanks, Daller. You've tried your best. I guess this is why Linux isn't quite ready for the masses.[/QUOTE]

Just a last spark!

What make & model is the card?

Have you considered buying a PCMCIA-card? (A D-link DWL 650+ is about $15)

---

