---
title: "Disabling weaker of two wireless adapters"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by ricardisimo on 2009-10-06
I have two wireless connections:
[LIST]
[*]An Atheros AR928X PCI-Express card;
[*]and a D-Link System DWA-140 USB adapter.
[/LIST]
The first is rather not bad, but just happens not to be strong enough most of the time, what with the location of my office. Being an internal PCI-Express, it seems to be treated as the "default" connection by Ubuntu (9.04).

The second is fantastic, but I regularly pull it out to use on my laptop or my wife's computer.

The problem is that when the PCI card ***does*** pick up the nearby signal which I use, it's dreadfully slow and I'm stuck with the weaker connection, even though the USB adapter is connected and showing a strong, fast signal.

Is there an easy way for me to toggle the PCI connection on and off when needed? Thanks in advance.

---

### Post by mikeyphi on 2009-10-07
I'm using Hardy - so these instructions might look slightly different under 9.4

Open System-Administration-Network
enter your password - to access
select the appropriate wireless connection then select properties.
deselect 'roaming mode' 

you should now be left with one wireless connection in Roaming mode - that can connect, and the deselected connection will be inactive.
It's possible you may need to input some random manual domain for the deselected connection.

---

### Post by 3rdalbum on 2009-10-07
I'm sure there is a nicer way to do this, but I don't know it. So here's the method I'd use.

First you'll have to find out the device name of your internal wifi card - you can find out in Connection Information in Network Manager (it's in brackets next to Interface, it's probably wlan0 or ath0).

Then, you'll need to add this command to your /etc/rc.local file, before the "exit" line:

```
iwconfig wlan0 txpower off &
```

(That's assuming that your device is "wlan0").

(I think "rate off" also works as well as "txpower off")

When you reboot, your internal device will be deactivated, and Network Manager will be forced to run the other device.

---

### Post by ricardisimo on 2009-10-07
> **mikeyphi said:**
> I'm using Hardy - so these instructions might look slightly different under 9.4

Open System-Administration-Network
enter your password - to access
select the appropriate wireless connection then select properties.
deselect 'roaming mode' 

you should now be left with one wireless connection in Roaming mode - that can connect, and the deselected connection will be inactive.
It's possible you may need to input some random manual domain for the deselected connection.

No, thanks but no. Jaunty has no "Network" under System >> Administration. I very much wanted your solution to work, as it looks much simpler than the following one. Uggh. On to the next one.

---

### Post by ricardisimo on 2009-10-07
> **3rdalbum said:**
> I'm sure there is a nicer way to do this, but I don't know it. So here's the method I'd use.

First you'll have to find out the device name of your internal wifi card - you can find out in Connection Information in Network Manager (it's in brackets next to Interface, it's probably wlan0 or ath0).

Then, you'll need to add this command to your /etc/rc.local file, before the "exit" line:

```
iwconfig wlan0 txpower off &
```

(That's assuming that your device is "wlan0").

(I think "rate off" also works as well as "txpower off")

When you reboot, your internal device will be deactivated, and Network Manager will be forced to run the other device.

I'll try it now... but how do I turn it back on? I wish there were a simpler way to do this (and I think there was under Dapper, Edgy, etc.) Thanks.

---

### Post by walt.smith1960 on 2009-10-08
Perhaps something to try--I'm a newb running Karmic on an Asus HA1005 which uses the Atheros 9XXX Wireless.  Network manager was indicating about 40-50% signal strength in Network Manager. I enabled Linux Backports for the appropriate kernel in Synaptic. I'm now showing 65-75% signal strength in Network Manager same location. If that helps perhaps you wouldn't need the second adapter.

---

### Post by ricardisimo on 2009-10-08
No, it really is the position of the comp... If anything I get a better signal than most of my coworkers positioned similarly. Thanks though.

---

### Post by Peter09 on 2009-10-08
Is there no option in your BIOS to disable that card?

---

### Post by 3rdalbum on 2009-10-08
> **Peter09 said:**
> Is there no option in your BIOS to disable that card?

Hahahaha... I knew there would be a cleaner, simpler way to do it! I forgot about disabling the card in the BIOS.

To make the internal card work again, the command:

```
sudo iwconfig wlan0 txpower auto
```

should work, or you can remove the line from /etc/rc.local and restart.

My way isn't actually hard, it's just a bit of a hack :-)

---

### Post by ricardisimo on 2009-10-14
```
:~$ sudo iwconfig wmaster0 txpower off &
[1] 8051
sectre@ricardo-desktop:~$ Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wmaster0 ; Operation not supported.
```
And now the terminal is just blinking at me. The card in question is still working, so far as I can tell... Do I need to reboot before any change takes effect? Thanks.

---

### Post by ricardisimo on 2009-10-14
The iwconfig code didn't work, so far as I can tell.

I checked BIOS, and there is some boot option with LAN, and I'm assuming that means "Local Area Network", and is therefore directly or roundabout what I am looking for. However, it appears to just toggle "enable" or "disable". Is this where I should start?

Any clues? What should I be looking for?

---

### Post by ricardisimo on 2009-10-14
Wait a second... aren't there GUIs for just this sort of problem? Would Wifi-radar or some other application do the trick here?

---

### Post by ricardisimo on 2009-10-15
Can anyone recommend Wifi-Radar for this purpose? Can it (or some other GUI) shut down and turn back on my wireless adapters? Thanks.

---

### Post by ricardisimo on 2009-10-15
By the way, I cannot tell you just how annoying this situation is... I have to hope and pray that the internal card will fail, because that's the only way to get the USB to work. If the internal logs in successfully, it lasts for only a second and is then worthless the rest of the way out. I have to browse in bursts, trying to log in with the USB, and taking advantage of the 30-seconds it takes for the wmaster to reconnect. Awful.

---

### Post by 73ckn797 on 2009-10-15
I was having a weak signal on a different wireless card that was 10 feet from the router. In Synaptic Package Manager I installed "ndisgtk". Using that graphical program I installed the Windows driver for XP. That solved the problem and the computer is now at the other end of the house and picking up very well.

---

### Post by ricardisimo on 2009-10-16
Thanks for the tip, but this isn't really a driver issue. No one else' machine gets a very good signal either - I have by far the two best adapters of everyone, one of mine significantly better than the other - and everyone else is on Windows or Mac.

---

### Post by 73ckn797 on 2009-10-16
> **ricardisimo said:**
> Thanks for the tip, but this isn't really a driver issue. No one else' machine gets a very good signal either - I have by far the two best adapters of everyone, one of mine significantly better than the other - and everyone else is on Windows or Mac.

Router time!

---

### Post by ricardisimo on 2009-10-16
D'oh!

---

### Post by 73ckn797 on 2009-10-18
> **ricardisimo said:**
> D'oh!

I would assume that is the common denominator.

---

### Post by 3rdalbum on 2009-10-18
> **ricardisimo said:**
> ```
:~$ sudo iwconfig wmaster0 txpower off &
[1] 8051
sectre@ricardo-desktop:~$ Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wmaster0 ; Operation not supported.
```
And now the terminal is just blinking at me. The card in question is still working, so far as I can tell... Do I need to reboot before any change takes effect? Thanks.

Sorry for not replying earlier... I never saw your follow-up.

I don't think "wmaster0" will work; it should be wlan0 or ath0 or something like that.

If the "txpower" bit of the command doesn't work, then possibly "rate" will work.

---

### Post by ricardisimo on 2009-10-20
I'll give it a try tomorrow. "wmaster0" is indeed the logical name of the adapter. Thanks again for your help.

---

### Post by ricardisimo on 2009-10-21
I tried it two different ways, sudo and non-superuser. Interestingly, the sudo never asked for a login, which I didn't think was possible. Here's what I got from both:
```
~$ sudo iwconfig wmaster0 rate off &
[1] 5095
```
and...
```
~$ iwconfig wmaster0 rate off &
[2] 5098

[1]+  Stopped                 sudo iwconfig wmaster0 rate off
~$ Error for wireless request "Set Bit Rate" (8B20) :
    invalid argument "off".
```
Why didn't I get a password prompt? What are those code numbers I'm getting back (5095 & 5098)?

The "Stopped..." part looks promising, but then the error that followed negated that, it seems. That, and the fact that I can still see the weak signal dominating on my machine. Any clue as to what is going on? I'm going to reboot now to see if that makes a difference.

---

### Post by ricardisimo on 2009-10-21
I'm not sure if it worked or not... I'm on the stronger connection right now, which is good, but the Atheros AR928X is clearly visible when I click on the NetworkManager Applet on the upper panel. I'm assuming that it should have been removed completely as an option, or no?

Let's assume, however, that it did work... do I need to know some way to re-activate it when I do need it?

---

### Post by falconindy on 2009-10-21
I'd go at this from a different angle... Are the two NICs using different driver modules? You can check with: `lshw -C network`. The module will be listed in the last line, for example:
```
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: wmaster0
       version: 01
       serial: 00:22:b0:6e:b3:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=168 maxlatency=28 mingnt=10 module=**ath5k** multicast=yes wireless=IEEE 802.11bg
```
The module for this particular wireless NIC is bolded. If you indeed find that the interfaces are using different modules, just blacklist the bad one! You can do this temporarily with `sudo modprobe -r ath5k`, replacing ath5k with your module name. The change can be made permanant by adding a line to your /etc/modprobe.d/blacklist file. Edit it with sudo and add a line `blacklist ath5k`, again with your module in place of ath5k. Even after a reboot, the driver module will not be loaded.

If you ever find yourself in need of the card again, remove the line from your blacklist file and execute `sudo modprobe ath5k`.

---

### Post by ricardisimo on 2009-10-22
And the clouds parted, and the valley was green, and all was goodness and light, and soft drinks were sweetened with real sugar instead of that high-fructose corn syrup stuff, and all homes and workplaces were clothing-optional...

You've made my little corner of the world right, my friend. Let's here a shout-out for falconindy, everybody. Woo-hoo! Thank you very much.

---

### Post by ricardisimo on 2009-10-30
Ugggh... That lasted exactly one week, and now 9.10 can't use the USB connection for some reason. I'm assuming that if it's a Koala bug with USB adapters, that there's already a thread for it... or several. Has anyone run across a particularly helpful thread?

---

