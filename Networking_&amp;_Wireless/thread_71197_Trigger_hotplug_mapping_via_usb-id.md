---
title: "Trigger hotplug mapping via usb-id ?"
date: 2005-10-02
forum: Networking &amp; Wireless
---

### Post by popeye on 2005-10-02
The problem:
A e-tech usb modem connects via usb and comes up with hotplug, hotplug causes the driver for the modem to be loaded and the firmware to be loaded. So far it goes ok.
Now to connect with internet module br2684ctl has to be loaded and this module creates nas0. 
With /etc/interfaces the interfaces are configured so in my view this is the place to create the trigger.
In interfaces i can point to nas0, but because it is created by module br2684ctl it is not triggered by it because it's not there yet. 
I wanted to load the module by interfaces via a pre-up line see example of how i did it now.
> 
# /etc/network/interfaces    
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
#This is a list of hotpluggable network interfaces.
#They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map nas0
# The primary network interface
iface nas0 inet dhcp
pre-up br2684ctl -b -c ${IFACE#NAS} -a 0.0.32
post-down kill $(cat /var/run/$IFACE.pid)
auto nas0
# The home network
auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255

Reason to load the module now and not via the hotplug script is because there is a need to supply to br2684ctl the VPI and VCI numbers which differs by internetprovider . Because this differs per internetprovider i want to put them here and therefore also load the driver here.
So i need another way to triggering in interfaces than the interfacename because the interfacename is not made yet. 
I am thinking of the usb modem id , but i don't know how to let this happen.
The question is:  Is it possible to put the usb id in the /etc/interfaces file and let this id trigger the rest by hotplug mapping.
I searched u bunch of sources and sites but came not across this problem.

---

### Post by mlomker on 2005-10-02
Are you saying that you connect to more than one ISP using this device?  If that's the case you'd remove the nas0 physical interface and create virtual profiles. 

```

iface home inet dhcp
pre-up br2684ctl xxx
post-down xxx

iface wherever inet dhcp
pre-up br2684ctl xxx
post-down xxx

```

In this case you'd issue the command **sudo ifconfig home=nas0 up** from a terminal and not use the **auto nas0** to bring it up.  You'd have to pick which one to bring up, so 'auto' isn't going to work.  You could create a script to execute that command and make an icon for it--that wouldn't be terribly inconvenient.

I got this from [here.]("http://arstechnica.com/columns/linux/linux-20040413.ars/2")

---

### Post by popeye on 2005-10-06
Thanks for the quick reply, i'm not so quick unfortunately.

I connect to only one ISP, but i'm plugging the modem to my laptop and my home computer.

I like to connect it on plugging and disconnect at unplugging automatically.

I have written a script that runs when the modem is plugged. But this script is run through before the firmware load script is run. So the things are in wrong order.

To trigger the interfaces file i use the nas interface. The problem is that nas is created when the bridge (br2684) is loaded and not when the modem is plugged.

The script i wrote loads the module br 2684 when the modem is plugged which is then triggering the interfaces file to be run. Problem is that the firmware then is not loaded yet. So i tried it with a sleep command in the interface file, though that is delaying the startup proces  for the sleeptime and that is not nice.

So now i'm looking for a command to read the line up statement in /proc so it's processed after the modem is up and running.

I am searching for a way to let the plugging of the modem trigger the interfaces file without a workaround. So not the nas because this is the bridge but a usb plug indication.

Then when unplugging to let it trigger again. (ifdown)

Anyway i keep searching for solutions.

---

