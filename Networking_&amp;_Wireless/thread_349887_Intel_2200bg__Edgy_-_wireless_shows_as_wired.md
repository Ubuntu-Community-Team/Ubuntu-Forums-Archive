---
title: "Intel 2200bg / Edgy - wireless shows as wired"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by Icarus3000 on 2007-01-30
Linux newb here...

I just installed Ubuntu 6.10 on my Dell Inspiron 700m laptop.  Everything seems to be working well so far, except I am having a strange problem with my wireless card.  I am able to connect to the internet somehow (don't have any idea whose internet connection I am on, since my own is WEP and I didn't enter any password), but according to the network settings, the wireless network interface is not configured, and I am using a "wired" connection.  According to the networking icon, I am connected through "eth1".

Any help would be appreciated!

Thanks,
Icarus3000

---

### Post by Floppyjoe on 2007-01-30
It is not uncommon for a wireless card to be given the eth1 interface name.  Is your computer connected via a network cable? My laptop had eth1 for its wireless extension untill I changed a config file to make it wlan0. Please open a terminal and post the out put of the following:
```
iwconfig
```
```
ifconfig
```

---

### Post by Icarus3000 on 2007-01-30
No network cable... completely wireless...

Anyway, I seem to have done something to screw up whatever good thing I had...  I was messing around with the synaptic manager thinking I had to install a network manager or something, and now I lost my internet connection.  Actually, it still says I have 94% signal strength, but I can't access any web sites (i'm writing this from my other computer).

For what it is worth, the output from iwconfig is now:

> 
lo  no wireless extensions
eth0 no wireless extensions
eth1  IEEE 802.11b ESSID:"SMC
Mode: managed Frequency: 2.437 GHz  Access Point: .... (let me know if you need more)
sit0  no wireless extension


from ifconfig:

too much to type, but it lists a hardware address for eth1 and says "UP BROADCAST RUNNING MULTICAST"

What am I looking for specifically?

Any idea how I can get my wireless back, and then how to get it working properly?

---

### Post by gottria on 2007-01-30
I have the same problem, my Dell wireless is coming up as eth1 instead of wlan0. I'm still booting from the live CD but I thinkI'm going to install it and give it a try. How would I go about changing this file?

Thanks Greg

---

### Post by Floppyjoe on 2007-01-30
Can you post your /etc/network/interfaces file?
```
sudo gedit /etc/network/interfaces
```
 I would uninstall network manager for now because that will not work with your wireless interface being eth1. There is a way to make eth1 wlan0 but I don't recall the name of the file that needs to be edited off hand.

Edit:
To change eth1 to show as wlan0 you need to enter the command:
```
sudo  gedit /etc/iftab
```
You will see something like:
> # This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0c:f1:85:97:Ff arp 1
eth1 mac 00:0c:f6:98:F7:Fe arp 1

You need to chnage the eth1 here to wlan0

---

### Post by Icarus3000 on 2007-01-30
>  	Can you post your /etc/network/interfaces file?

```

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

auto wlan0
iface wlan0 inet dhcp

```

How do i go about uninstalling network manager?

Thanks!

---

### Post by Floppyjoe on 2007-01-30
Maybe you should first try my fix to get Network manager to work by seeing the end of my previous post. Then reboot.

---

### Post by Icarus3000 on 2007-01-30
> **Floppyjoe said:**
> Maybe you should first try my fix to get Network manager to work by seeing the end of my previous post. Then reboot.

I guess I was a little over-eager... I figured out how to uninstall network-manager (sudo apt-get remove network-manager) and that brought me back to where I was when I first posted...  i.e.  I can connect to a wireless connection but it's not showing up properly in the networking settings.

Then I tried what you suggested (changing eth1 to wlan0) and rebooted.

At first, it wouldn't connect automatically, because somehow it is looking to eth1 first, but when I swith the connection name from "eth1" to "wlan0" in the connection properties window,  I am back in business.  However, I don't seem to be any further along than I was before, except that "eth1" is now called "wlan0".  Should I re-install network-manager now?

Thanks again!
Icarus3000

---

### Post by Floppyjoe on 2007-01-30
Scince you have deleted network manager, you have several choices.
1 reinstall network manager and see if it works
2 edit your /etc/network/interfaces file with the correct parameters to enable function.

What do you prefer?

---

### Post by Icarus3000 on 2007-01-30
> **Floppyjoe said:**
> Scince you have deleted network manager, you have several choices.
1 reinstall network manager and see if it works
2 edit your /etc/network/interfaces file with the correct parameters to enable function.

What do you prefer?

I'd probably learn more by editing the interfaces file myself... Please let me know how I should go about finding the correct parameters.

Thanks again!

---

### Post by Floppyjoe on 2007-01-30
You will need to edit your /etc/network/interfaces file:
```
sudo gedit /etc/network/interfaces
```
Find where it says:
> auto wlan0
iface wlan0 inet dhcp
and then add your specific setup details to get something like this:
> auto wlan0
iface wlan0 inet dhcp
wireless-essid YourNetworkEssid
wireless-mode managed
wireless-channel 7

Where your router channel is in there instead of 7.
You may also need another line for the wireless password in there.

---

### Post by Icarus3000 on 2007-01-30
> **Floppyjoe said:**
> You will need to edit your /etc/network/interfaces file:
```
sudo gedit /etc/network/interfaces
```
Find where it says:

and then add your specific setup details to get something like this:

Where your router channel is in there instead of 7.
You may also need another line for the wireless password in there.

What does that do exactly?  It seems like it is tying my wireless connection to one specific access point (ie: my router).  But what if I want to use my laptop at another location where I don't know the details of the access point?  Is there a way I can set it up to auto-detect wireless access points?  My objective is not to tie my internet access to my wireless router only.

Forgive me if I misunderstood what you are suggesting - this is all very new to me!

---

### Post by Floppyjoe on 2007-01-30
You are right. It is a setup for a home network. If you need one for frequent changing I would reconsider reinstalling network manager.
For Network manager to work you need to disable all your network interfaces after installing it and then reboot.

---

### Post by Icarus3000 on 2007-01-31
> **Floppyjoe said:**
> You are right. It is a setup for a home network. If you need one for frequent changing I would reconsider reinstalling network manager.
For Network manager to work you need to disable all your network interfaces after installing it and then reboot.

Success!  I installed network-manager-gnome and can now access my wifi router with my WEP password.  (Incidentally, I can also access my neighbour's unsecured wifi but I have no need to do that anymore!).

Thanks for your help,
Icarus3000

---

### Post by gottria on 2007-01-31
Thanks Floppjoe. I edited the interfaces file and now all my hotspots show up. And even connected my my own wireless with WPA enabled. One question does it store my WPA key or do I have to type it in when ever I connect?

---

### Post by Floppyjoe on 2007-01-31
> **gottria said:**
> Thanks Floppjoe. I edited the interfaces file and now all my hotspots show up. And even connected my my own wireless with WPA enabled. One question does it store my WPA key or do I have to type it in when ever I connect?
If you are using Network Manager then I think your password is stored for each different network you connect to. Network Manager uses a keyring to save your wireless passwords and will prompt you for your keyring password all the time. There is a way around this but your keyring password will have to be the same as your login password. The following URL shows how to do this:

[http://ubuntuforums.org/showthread.php?t=187874&highlight=nm-applet](http://ubuntuforums.org/showthread.php?t=187874&highlight=nm-applet)

If you are not using Network Manager then there are other steps to set up WPA supplicant.

---

