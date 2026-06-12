---
title: "How to make ndiswrapper stick"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by exsencon on 2008-02-06
Installed a Dual Boot between WinXP and Kubuntu 7.10 on my Dell Laptop Inspiron 1501
AMD Turion 64x2, 2GB of RAM, 120GB HD.
This is my first Linux Distribution install and it works perfectly. I've been running Ubuntu/Kubuntu live CD's for at least a week and I don't regret it!
Now, installing my wireless driver (Broadcom 1390) with ndiswrapper is not a problem. After a little tinkering and reading a lot in forums (and I really mean a lot!)it runs very well. 
I blacklist the native bcm43xx and then I add a line I found on a slackware forum:

modprobe -r bcm43xx
then I run the ndiswrapper as usual and I get a good wireless(54MB/s)
I usually have to disable Knetworkmanager because it keeps messing things up. I installed Kwifi and it gives me the essential data(speed, strength etc)

How do I keep this ndiswrapper configuration so my wireless springs up every time I boot instead of having to get it together every time?
I read Kevdog's tutorial and tried to do what he says but it doesn't work. My interface stubbornly remains eth1and won't change to wlan0.
When I run dmesg, here is what I get:

bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed. 

I get a lot of those, if it means the fwcutter is not there then it is correct of course

ndiswrapper version 1.45 loaded (smp=yes)
ndiswrapper: driver bcmwl5 (Broadcom,11/02/2005, 4.10.40.0) loaded
ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:05:00.0 to 64
ndiswrapper: using IRQ 18
wlan0: ethernet device 00:19:7d:33:0a:b4 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
**ndiswrapper: changing interface name from 'wlan0' to 'eth1'**
usbcore: registered new interface driver ndiswrapper  	

It looks OK except for the line 'changing interface name'
Why it keeps doing that I don't know
And naturally when i do lshw -C network it gives:

	*-network      
 
description: Wireless interface       
product: BCM94311MCG wlan mini-PCI      
vendor: Broadcom Corporation      
physical id: 0      
bus info: pci@0000:05:00.0      
**logical name: eth1    **  
version: 01      
serial: 00:19:7d:33:0a:b4      
width: 32 bits      
clock: 33MHz      
capabilities: bus_master cap_list ethernet physical wireless    configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,11/02/2005, 4.10.4 ip=192.168.1.102 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

How can I change this and then apply some codes to make ndiswrapper run my wireless at boot?
All suggestions are welcome!
running a linux OS is really an experience for my (Windows for 15 years) and I really love it!

---

### Post by luisromangz on 2008-02-06
I activate ndiswrapper adding the line

modprobe ndiswrapper

to the /etc/rc.local file, which is run at boot.

If you have blacklisted bcm43xx in /etc/modprobe.d/blacklist, you shouldn't need to remove the driver with modprobe -r bcm43xx.

---

### Post by Ayuthia on 2008-02-06
> **luisromangz said:**
> I activate ndiswrapper adding the line

modprobe ndiswrapper

to the /etc/rc.local file, which is run at boot.

If you have blacklisted bcm43xx in /etc/modprobe.d/blacklist, you shouldn't need to remove the driver with modprobe -r bcm43xx.

Another way to make the module load up at boot is to add the word 'ndiswrapper' without the quotes in /etc/modules.

---

### Post by wieman01 on 2008-02-06
See the last steps of my Ralink tutorial (signature). That should clear things up a bit.

---

### Post by exsencon on 2008-02-06
> **Ayuthia said:**
> Another way to make the module load up at boot is to add the word 'ndiswrapper' without the quotes in /etc/modules.

I checked, it's in there:

/etc/modules

fuse
lp
ndiswrapper

---

### Post by NullHead on 2008-02-06
ok what I would do is this ```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```and ```
echo 'blacklist bcm43xx' | tee -a /etc/modprobe.d/blacklist
```

---

### Post by exsencon on 2008-02-06
> **NullHead said:**
> ok what I would do is this ```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```and ```
echo 'blacklist bcm43xx' | tee -a /etc/modprobe.d/blacklist
```

Ok your second line I already did
What does your first line do?  echo 'ndiswrapper' | sudo tee -a /etc/modules

---

### Post by NullHead on 2008-02-06
> **exsencon said:**
> Ok your second line I already did
What does your first line do?  echo 'ndiswrapper' | sudo tee -a /etc/modules

It adds ndiswrapper to the /etc/modules file so ndiswrapper will load on bootup. :popcorn:

---

### Post by exsencon on 2008-02-06
> **NullHead said:**
> It adds ndiswrapper to the /etc/modules file so ndiswrapper will load on bootup. :popcorn:

Right,I did that already and I just rebooted now and I get no more error messages about the bcm43xx driver,it completely disappeared now AND ndiswrapper loads!
I just had to reset my connection to automatic and up it went!

Thanks to all of you,you're great and linux is fun:)

---

### Post by exsencon on 2008-02-08
Well, I thought I had it all under control but not yet.
Today when i started my laptop it was booting slower than usual and when it finally got there I couldn't connect wireless.
So I ran iwconfig and I only got lo and eth0, no eth1 (my interface)
The radio button is off and I can't get it on with Fn-F2 keys (the usual combination)

Running dmesg I get this (relevant parts):

ndiswrapper (NdisWriteErrorLogEntry:192): log: C000138B, count: 1, return_address: f8b65937
[ 19.964000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x9
[ 19.964000] ndiswrapper (mp_init:263): couldn't initialize device: C0000001
[ 19.964000] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)
[ 19.964000] ndiswrapper (mp_halt:305): device dfd17500 is not initialized - not halting
[ 19.964000] ndiswrapper: device eth%d removed
[ 19.964000] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[ 19.964000] ndiswrapper: probe of 0000:05:00.0 failed with error -22

and after that I got a lot of:

atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 134.440000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 139.468000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 139.468000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 144.596000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 144.596000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 147.416000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 147.416000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.


And a lot more of those.I suppose that's why I could'n use the Fn-F2 keys although the Fn-F3 combination did work.

So what I did was:

sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5 (my driver)
sudo ndiswrapper -i path of driver
ndiswrapper -l (everything OK)
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m (alias already there)
sudo iwconfig eth1 essid (my essid)

After that I can turn on my radio button and I get I wireless.
I don't know what happened here,everything was working just fine.
Now everytime I reboot I have to do the same thing because my wireless interface is gone, radio button blocked.
What can I do?:(

---

### Post by NullHead on 2008-02-08
You can try my script I've just constructed.
Note: I haven't tested it yet.

---

### Post by exsencon on 2008-02-08
> **NullHead said:**
> You can try my script I've just constructed.
Note: I haven't tested it yet.

Hmm...and where should I put it?

---

### Post by NullHead on 2008-02-08
Oh well you need to run it every time you boot, but it'll do every thing you need it to do ... such as the commands you listed earlier. It does require user input ... so it'll ask you where bcmwl5.inf is and what you're essid is.

---

### Post by NullHead on 2008-02-09
Does the script work for you?

---

### Post by exsencon on 2008-02-10
> **NullHead said:**
> Does the script work for you?

Didn't try it yet. Changing from Kubuntu back to ubuntu. I really think there is a problem at boot and for some reason ndiswrapper doesn't load or doesn't load properly,hence the error messages. Linux is not always fun,but I won't give up anytime soon.:(

---

### Post by exsencon on 2008-02-11
Follow up. I moved to Ubuntu 7.10 Gutsy. It's the same problem really. Sometimes it boots correctly and I have my wireless,sometimes it does not and the wifi button of my laptop is stuck. I can put it back on by doing:

sudo modprobe -r ndiswrapper
sudo modbrobe ndiswrapper

My wifi card button lghts up then and I have my wireless.
Very strange

---

### Post by NullHead on 2008-02-11
> **exsencon said:**
> Follow up. I moved to Ubuntu 7.10 Gutsy. It's the same problem really. Sometimes it boots correctly and I have my wireless,sometimes it does not and the wifi button of my laptop is stuck. I can put it back on by doing:

sudo modprobe -r ndiswrapper
sudo modbrobe ndiswrapper

My wifi card button lghts up then and I have my wireless.
Very strange

I would download the source and compile it. That might fix your problems, but there is no guarantee.

---

### Post by exsencon on 2008-02-15
Follow up:
I finally got it.
I went into /usr/share/hotkey-setup/ (don't ask me why I went there!) and there are different set ups for different computer brands. So I chose mine(Dell) and I saw:

# Dell Laptops
					# Fn+Esc	Standby (ACPI)
setkeycodes	e00a	$KEY_SUSPEND	# Fn+F1		Hibernate (e00a)
#setkeycodes	e008	$KEY_	             # Fn+F2		Wireless (e008)
setkeycodes	e007	$KEY_BATTERY	# Fn+F3		Battery (e007)
setkeycodes	e00b	$KEY_VIDEOOUT	# Fn+F8		CRT/LCD (e00b)
setkeycodes	e009	$KEY_EJECTCD	# Fn+F10	EjectCD (e009)
setkeycodes	e005	$KEY_BRIGHTNESSDOWN # Fn+Down	Brightness Down (e005)
setkeycodes	e006	$KEY_BRIGHTNESSUP # Fn+Up	Brightness Up (e006)
setkeycodes	e012	$KEY_MEDIA	# MediaDirect	Load Media Player (e012)

You  see the second line has that inactive # before it,why I don't know. I edited that in:

setkeycodes	e008	$KEY_WIRELESS	    # Fn+F2	Wireless (e008)

and...ALL SET! I booted and rebooted about 15 times and all is working perfectly now. I get my wireless automatically from the start.
Those little things...Moving on to configure my network printer now.
Thanks for your support

---

