---
title: "Network won't start at boot"
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by claco on 2005-10-13
I've got Breezy running on my laptop with a Cisco AIR-PCM352 wireless card working.
There are some strange things about it however.

First, the network config gui shows an eth1 and an eth2, both pointing to the single wireless card. Configuring eth1 does nothing, and it's activate/deactivate does nothing. Configuring eth2, and activating/deactivating it turns the wireless cards light on/off, so clearly eth2 is the real interface.

Even stranger, when I configure eth2, all of it's config shows up on eth1 as well. But I digress...

After every reboot, the network interface refuses to start. Simply opening the network config tool and clicking on activate activates the card right away, so clearly it's config in interfacesis somewhat correct. How can I get this card to starton boot, and possibly even start earliier? For that matter, hotplugging the card doesn't start the network either...

This all worked fune under Hoary, although there I had an wifi0 and an eth1, both point to the same card..

Watching the boot screen, when it's start network services, the wireless card does nothing...and th ntp.ubuntulinux.org call fails...

Here's my interfaces file:

```

#auto eth2
iface eth2 inet dhcp
wireless-essid Matrix
wireless-key restricted XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX
wireless-channel 1



# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth2



auto eth2

```

---

### Post by claco on 2005-10-15
I still haven't been able to figure this out. Anyone?

---

### Post by Quirky on 2005-10-16
I don't know how useful this will be, I have Hoary and a completely different card, but my /etc/network/interfaces is as follows. The only differences I see is that auto is before and the key is in a different format:

```

auto ra0
iface ra0 inet dhcp
 wireless-essid quirky
 wireless-key restricted 10438b65cdbb0a9a7ee630443a0b

```

I couldn't get the card to work with WEP if I used the Gnome network interface. Well, it would work once when I ran it, but then not at boot. If you 'deactivate' it from there then restart network from the shell, does it work? i.e. running */etc/init.d/networking restart*? If not, perhaps this will at least be faster to test than rebooting.

---

### Post by loon on 2005-11-11
Been able to fix this yet?

-loon

---

### Post by trubblemaker on 2006-01-25
don't know how you got wireless to work, did you use NDISWRAPPER?  it might (guessing here) be trying to run it's own card, see what drivers are running for ndiswrapper:
```
ndiswrapper -l
```

also check out your folder /etc/network, look around in the files for the network card that "isn't there" but is appearing to be there, (I can't look up which file it is that screws up sometime [I'm on a windows box right now].)

what happens when you do ?```
iwconfig
``` 
what happens when you do ?
```
 ifconfig 
```
```
 sudo ifconfig eth1 down 
```
and then ```
 ifconfig 
```

hope some of this helps

---

### Post by hollinch on 2006-01-27
I have exactly the same problem.
IBM Thinkpad with Cisco Aironet 350 wireless PCMCIA card.
When the computer starts there are two interfaces: eth1 and eht2, both pointing to wifi0. eth1 is not able to retrieve a DHCP ethernet address, but eth2 can. The only thing is that the eth2 card by default remains deactivated, and I have to manually activate it.

Can it be the startup sequence? Are scripts in rcS.d executed before rc5.d? If so, PCMCIA is started when the network startup has already been done, and that may explain the behaviour.

Any other suggestions?

---

