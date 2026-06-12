---
title: "Starting eth0 as default gateway"
date: 2005-10-24
forum: Networking &amp; Wireless
---

### Post by Stratus on 2005-10-24
Hello all

Have had a look through the forums for a fix, but am oblivious to an answer that would work for me.

I have a cable modem with a static ip address.
Everytime I boot into Ubuntu I have to manually set eth0 as default gateway by going System -> Administration -> Networking.

Is there a way to do this without going through the above?
Any help appreciated.

Edit: Thought I better mention this was the same in Hoary also.

---

### Post by darth_vector on 2005-10-24
hi,

i assume you mean you are connecting to the default gateway (your cable modem) through eth0. if this is so then open up /etc/network/interfaces

you should have an entry like this:

iface eth0 inet static
address <your internal IP>
netmask <netmask - probably 255.255.255.0>
network <the network ip, eg. 192.168.0.0>
broadcast <the broadcast address, eg. 192.168.0.255>
gateway <the IP of your cable modem>
dns-nameservers <the ip's of the dns servers you are using>

having this in the file should bring the interface up automatically at startup.
when you change these settings you will have to do a

sudo /etc/init.d/networking restart

for the settings to take effect

---

### Post by blacksheep on 2005-10-24
Hi! I have the same problem!

I've configured my both ethernet devices (eth0 lan - includes gateway settings to internet, eth1 wlan). 

Everytime I boot I have to have to start the "network-admin". There on the first settings page is a label "Default gateway device:". Everytime I have to reselect "eth0" to get connection to the internet; after boot the field is cleared again.

Without this setting there is no chance to get access to the internet wit Firefox, Evolution, etc.

I seek a way to set eth0 permanent. Or is this a bug, that this field is cleared everytime?

Thanks in advance!

---

### Post by Stratus on 2005-10-25
[QUOTE=darth_vector]hi,

i assume you mean you are connecting to the default gateway (your cable modem) through eth0. if this is so then open up /etc/network/interfaces

you should have an entry like this:

iface eth0 inet static
address <your internal IP>
netmask <netmask - probably 255.255.255.0>
network <the network ip, eg. 192.168.0.0>
broadcast <the broadcast address, eg. 192.168.0.255>
gateway <the IP of your cable modem>
dns-nameservers <the ip's of the dns servers you are using>

having this in the file should bring the interface up automatically at startup.
when you change these settings you will have to do a

sudo /etc/init.d/networking restart

for the settings to take effect[/QUOTE]

Thnx alot for the reply Darth, but I have this already in the interfaces file; the only thing I have extra is auto eth0 in a line prior to where you have started above.

Still does not work.

---

### Post by Stratus on 2005-10-26
^^bump^^ Anybody else with this problem or a resolution to the above issues?
Is it worth posting it as a bug?

---

### Post by bonifacio on 2005-10-31
Started having this problem.  I've got 2 network interface.  In my case I normally use wifi (eth1).  And yes for the life of me the "Default gateway device" is cleared upon every boot.  As a result the interface never receives an ip address.  Double check both interface to use DHCP and they are.  What gives?

Here is a sample of what I got:

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
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid <myESSID>
wireless-key <myKey>

auto eth1


---

### Post by bonifacio on 2005-11-02
I got this resolved!  In my case network-manager seems to be the culprit.  I made this conclusion because when I removed it, all the problems described previously disappears.

Of course this only applies if you are in the same boat as me.  Cheers.

---

### Post by g man on 2006-03-16
I had the same problem, and fixed it.

The reply from Darth Vector told me where to find the file, "/etc/network/interface", but my file looked completely different of course. 

But I noticed the line that ended in "# line maintained by pppoeconf" and I had the feeling that I screwed things up by using pppoeconf in the first place. (Ubuntu Live worked fine with my modem and I didn't have to do anything.) So my solution was to put the "#" at the very beginning of the line "#   pre-up.........." which I believe is supposed to change the whole line to a comment instead of executing or whatever.  My connection seems to work fine now, it was so bad before that I had to reset eht0 everytime I loaded a new web page.

My etc/network/interface file looks like this now:

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

# The primary network interface

iface eth0 inet dhcp

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

**#    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf**

auto eth0

Hope this helps someone else

---

### Post by SUparJErk on 2006-03-28
:confused:  I have a similar problem. I am building a router/gateway for home use. Everything is functional and properly configured except for the fact that when I boot, eth1 is always set as the "default gateway device" in System->Administration->Networking.  If I can manage to get eth0 to be the default gateway device, everything works peachy keen. The other problem I have is that even if I simply select eth0 from the drop-down menu and click OK, the change doesn't seem to stay. If I re-open the Networking window immediately after, it's still set to eth1. The only way I can get eth0 to stay the default gateway device is by deactivating and reactivating devices in a certain order, or simply completely deactivating eth1. I don't get it, and any help would be appreciated.

Here is my /etc/network/interfaces config:
-----

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

# The primary network interface
iface eth0 inet dhcp

auto eth0

iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1

---

### Post by g man on 2006-04-03
You probably saw how I fixed my problem in the previous post.
I am really new at Linux and don't want to point you in the wrong direction, but I do have something you could try.
My experience with other operating systems leads me to think that the last line in your config file "auto eth1" will over-ride the previous line that says "auto eth0". So maybe you could add a "# " to the beginning of the eth1 line so it will be ignored and see if that helps.
Also in my system I don't need to set the -address -netmask or gateway, so you might have to change those as well. Just try one solution at a time and see what happens. It won't hurt anything, since you can always change your config file back again.

example:

iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.1

# auto eth1

good luck

---

### Post by SUparJErk on 2006-04-05
in response to g man:
I tried this already; I discovered that what the 'auto' line actually does is it makes the specified device active on startup. If the 'auto' line is removed or commented out, then that device will be greyed out and deactivated in the Networking window. It doesn't really help my situation at all.

I'm thinking if Ubuntu is so darned insistent on having eth1 be my default gateway, I may just swap the roles of eth0 and eth1 and reconfigure everything.

---

### Post by jamesr on 2006-04-05
If I am reading/interpretating the file correctly> # The primary network interface
iface eth0 inet dhcp

auto eth0

iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
You are setting the address for eth0 as 192.168.1.1 and then later setting the gateway a 192.168.1.1 ie one and the same. Also where is the DHCP server? that is setting the address of eth0. 

Is your setup like this

internet=Modem=eth0/PC/eth1=HUB other PCs

---

### Post by SUparJErk on 2006-04-07
jamesr: no, look closer

iface eth0 inet dhcp

eth0 isn't 192.168.1.1. eth0's address is determined by dhcp. That's what that line is doing.

Also, the DHCP server is attached to a subnet, not an interface, so it's independent of the actual device itself. dhcpd also plays no role in determining a device's IP address. But for what it's worth, I have it configured to listen on 192.168.1.0. And yes, my setup is similar to what you described.

At any rate, I sidestepped this default gateway device problem by switching eth0 and eth1's roles in my system. I reconfigured everything so eth1 is now connected WAN-side and eth0 is LAN-side. Ubuntu continues to forcefully use eth1 as the default gateway device every time I reboot, but this is what I want since I reconfigured. I'm now typing this to you from a client machine behind the linux router, so my own problem is solved. It would be really nice if a solution could be found regarding the default gateway device staying how the user asks it to be.

--SUparJErk

---

### Post by soongwoo on 2006-06-08
I had same problem, too!

My working colleague suggests that just define ONLY ONE GATEWAY
which would be a default gateway. And then the default gateway device
is a device with defined gateway.

I resolved it with his suggestion.

soongwoo

---

### Post by wugoat on 2006-07-10
hey Ubuntu folks (loving your work!)

My Problem was that the default gateway would reset to eth0 in 
System -> Administration -> Networking.

No good for me as I wanted it to remain set at eth1.

After reading the comunity wisdom on this thread, I sudo gedit /etc/network/interfaces, and changed from


auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.38
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.1.37
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0


      ...to...


auto lo
iface lo inet loopback

[COLOR="Red"]auto eth0[/COLOR]
iface eth0 inet static
address 192.168.1.38
netmask 255.255.255.0
gateway 192.168.1.1

[COLOR="Red"]#auto eth1[/COLOR]
iface eth1 inet static
address 192.168.1.37
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


[COLOR="Red"]auto eth1[/COLOR]


this *seems* to have solved things, though I may be deluded, and now default gateway is set to eth1 on startup. :D


...deluded I was. It remains eth1 after soft restarts, but tun rn off overnight, and we're back to eth0

help anyone?

---

### Post by wugoat on 2006-08-21
:evil: Tricksy it is!!!

OK, so back again.. No answers yet, just more experimental data..:) 

Full Reinstall of Dapper from the CD.
Static IP addresses.
Install of Squid Proxy.
Install of Dansguardian (+ latest Blacklists).
Install of Webmin, and config for the above.

..and the setup is working fine.  Great was the celebration and cheerfullness.. Filtered Web access from elsewhere on the LAN. 
Could even run MSN messenger (though seemed a bit slow going through Dansguardian 8080, worked much happier through Squid's 3128)

Lastly, VNC... Synaptic installed x11vnc.

Could not get it to work... Furthermore now my Default Gateway Device (should be eth1) resets to eth0.  I suspect that eth0 is also deactivated, though it shows as active in system-> network.

Fix seems to be to reset Default Gateway Device in System-> Network, then Deactivate and Reactivate eth0. 

LAN then has web/IM access.

Uninstalling x11vnc does not help.

---

