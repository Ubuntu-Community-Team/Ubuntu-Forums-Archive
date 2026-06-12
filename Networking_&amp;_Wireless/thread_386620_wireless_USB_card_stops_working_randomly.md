---
title: "wireless USB card stops working randomly"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by lerio on 2007-03-17
Hi everybody,

I have a belkin wireless USB card connected to a D-Link router. Everything is configured perfectly and works fine, except for the fact that sometimes, randomly, the network traffic stops and I need to restart my edgy box in order to make it work again.

What it should be, considering that on windows that problem haven't ever happened?

Thanks in advance to anyone who wants to help me on that! I want to make Ubuntu be my only OS, and solving this problem would make me uninstall windows forever!

---

### Post by lerio on 2007-03-17
I know I didn't give any details about it but if you ask for I can give any kind of information you need.

Thanks again!

---

### Post by Floppyjoe on 2007-03-17
This sounds like it might be a DNS problem. Check your DNS settings before and after the card stops working in System/Administration/Networking. If you use DHCP your resolv.conf file might periodically get rewritten. There is a way to prevent that at this link:

[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=15](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=15)

This may or may not be the problem.

---

### Post by lerio on 2007-03-17
Thanks for the reply. I don't think it's the DNS because when the networking freezes I can't ping even the router. Morevoer I don't use DHCP and the resolv.conf is just fine.
It looks like when the computer goes idle for some time the network (and only the network) stops working. I've even tried to "ifconfig rausb0 up" but only a system restart would make it work again.

pretty annoying huh?

---

### Post by Floppyjoe on 2007-03-17
Can you do a networking restart instead of rebooting the computer? I'm not sure if I have the right syntax here but:
```
sudo /etc/init.d/networking restart
```

---

### Post by lerio on 2007-03-17
ok, I'll try as soon as the network stops (soon enough I'm afraid)

---

### Post by lerio on 2007-03-18
Ok, I tried to restart the networking but didn't work. It hanged on "reconfiguring wlan0". That's strange cause my wireless device is rausb0

any clues?

---

### Post by lerio on 2007-03-19
Has anybody had a similar problem with a Belkin Wireless G USB Network Adapter so far?

---

### Post by steevz on 2007-03-20
I'm having a very similar problem on a SMC Wireless USC Adapter.. it works and then just randomly stops working and rebooting is the only way to make it work again. I'm dual booted with Windows XP and it works perfectly fine when I'm using Windows. No idea what to do..

---

### Post by torekiki on 2007-03-21
I have the same problem when I umount a USB pen drive (but sometime)

---

### Post by lerio on 2007-03-21
yes steevz, it's the exact same problem. I'm using Edgy's native drivers (rausb0) and I'm wondering if installing ndsiwrapper drivers will solve the problem.

---

### Post by steevz on 2007-03-22
Without using the Network Manager and just using System>Administration>Networking and disabling and then re-enabling it seems to be working for me. It's running perfectly, doesn't stop working anymore. When I was using the Network Manager it was stopping. I do also have it installed with ndiswrapper.

---

### Post by lerio on 2007-03-22
Steevz, I have few questions for you:

- Do u need to disable/reenable it every time it stops or u did it once and now it's not stopping anymore?

- How did u install and configure ndiswrapper? I mean, my usb wireless chipset is natively (but badly) supported by edgy. How do I tell the system to use the ndsiwrapper and discard the native ones?

- I've found a way to make the network work again without rebooting: all I have to do is to unplug the usb wireless card and plug it again. It's very annoying though to find out that it disconnected through the night. HOW DO I FIX THIS? IS THERE A WAY TO UNINSTALL WINDOWS ONCE FOR ALL????????

---

### Post by steevz on 2007-03-22
Sorry.. I don't understand what you're exactly trying to say. I think part of the reason my internet was stopping was because of the actual connection and not the adapter.

The way I setup ndiswrapper is like this:

```

1. Get the Windows driver for your USB adapter.

2. Unpack the driver somwhere like in home dir.



3. Install ndiswrapper (use terminal or synaptic package manager), and the windows driver through NDISWrapper

Im using the terminal:

sudo apt-get install ndiswrapper-utils-1.8

cd /where_you_unpacked_the_driver/ (if there's subfolder for OS go there, i used the WinXp folder)

sudo ndiswrapper -i <your driver>.inf (This should be the name of the Windows INF file in the folder)

sudo ndiswrapper -l (shows if the driver is installed) Mine looks like this "smc2862w driver installed, hardware present"

sudo modprobe ndiswrapper (this inserts the module in the kernel)

sudo ndiswrapper -m (this creates a default entry for ndiswrapper in /etc/modprobe.d/)

```
After that reboot (Ctrl+Alt+Backspace).

Then goto System>Administation>Networking. Now your wireless adapter should show up in here. Enable it and enter your network name. 

That's how I got mine to work, when it was stopping working I would just go into System>Administartion>Networking and just uncheck the wireless device, then re-check it and it works. 

Hope that might help you. But I'm a Linux newb like you too.

Steve

---

### Post by lerio on 2007-03-26
After googling around I found this post which describes what my problem is:
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=237&sid=88a6d748eda1a32fadd31cb9e06db520](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=237&sid=88a6d748eda1a32fadd31cb9e06db520)

ra2500usb driver disconnects under heavy network traffic (while using bittorrent, for example)
It seems there isn't a proper solution yet but guys there posted a couple of workarounds:
- either disabling usb2.0 feature on the port used my the wireless device
- or adding a new job in your crontab which checks the network status and in case is down, restarts it

All I said is described in detail in the link I posted

Of course, if anybody else has got a better solution than these two workarounds here... I'll be happy

---

