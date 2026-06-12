---
title: "Bluetooth mouse and keyboard won't stay connected."
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Raziekiel on 2008-12-23
I just did a fresh install of 8.1, and I can't get my bluetooth mouse and keyboard all fixed. Everytime I let them idle for more than ~5 minutes, I have to reconnect with with sudo hidd--search. I've looked around for a way to solve it, but no luck.

Here is what my /etc/default/bluetooth looks like:

# Defaults for bluez

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497)
HID2HCI_ENABLED=1
HID2HCI_UNDO=1
HIDD_ENABLED=1
HIDD_OPTIONS="-i --connect  00:12:5A:10:7A:7E --connect 00:12:5A:10:1E:7F --server"

---

### Post by startherepodcast on 2008-12-23
The quick and dirty approach I would take is to put something in the crontab that executes the reconnect command every 2 minutes. Instructions on how to do that are here:
[http://neeocis.wordpress.com/2008/07/08/crontab-every-five-minutes/](http://neeocis.wordpress.com/2008/07/08/crontab-every-five-minutes/)

Maybe you have something disrupting the communications between the devices, do the same issues occur in other operating systems, if there are any (like Windows?)

Hope that helped

Leon

---

### Post by Raziekiel on 2008-12-23
It's not an issue on windows XP, I don't think anything is disrupting the signal, it's more like the devices go into sleep after idling for a few minutes, and when I use them, they don't auto re-connect.
Also, I tried using contrab, but it didn't work :(

---

### Post by Raziekiel on 2008-12-24
/bump
Any ideas???

---

### Post by Law506 on 2008-12-24
You can try this page and see if there is anything additional on it you haven't tried yet.

[https://help.ubuntu.com/community/BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup")

Update #2: 
I decided to break back out my bluetooth stuff and give it a go once again.  Gave up on it a while back because I was switching alot between Windows and Linux at the time and couldn't get the bluetooth to transfer, but anyways, here is my /etc/default/bluetooth.

> # Defaults for bluez

# Defaults for bluez

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497)
HID2HCI_ENABLED=1
HID2HCI_UNDO=1
HIDD_ENABLED=1
HIDD_OPTIONS="--connect 00:07:61:4E:43:C2 --connect 00:07:61:4E:31:9F --server"


I got both my mouse and keyboard hooked up now and both come to life when I get to the login screen after a fresh boot up or restart.  I am also using Ubuntu 8.10.

---

### Post by HyRax on 2008-12-26
Next time your Bluetooth mouse/keyboard falls asleep, open a terminal and type in the following command (yes, I know this necessitates getting another keyboard!! ;) )

```

$ sudo hciconfig hci0 pscan

```

Wait a few seconds and start wiggling your mouse to see if it comes back to life. If it does, great - your Bluetooth adapter was not actively scanning for devices to reconnect.

Rebooting will lose this change, so until a permanent bugfix is made, just stick the command into your /etc/rc.local file before the "exit 0" line so it gets executed on every startup.

*NOTE ABOUT THIS WORKAROUND:* Depending on your Bluetooth devices, Ubuntu may still not connect to them if they already had a "connected" status, eg: when you reboot. The simplest way to get them to reconnect is to switch them off and on again and Ubuntu will then pick them up a few seconds later. You can power cycle right away rather than wait for Ubuntu to completely restart and they should be usable again even from the login screen.

---

### Post by Raziekiel on 2008-12-29
Alright, here is my current /etc/default/bluetooth

# Defaults for bluez

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497)
HID2HCI_ENABLED=1
HID2HCI_UNDO=1
HIDD_ENABLED=1
HIDD_OPTIONS="--connect 00:12:5A:10:7A:7E --connect 00:12:5A:10:1E:7F --server"

I tried the pscan command as well, but it didn't pick up my mouse or keyboard. 

I'm running 64bit if that matters. :( Any other ideas?

*UPDATE*
I was looking around for other ideas and came across the /etc/bluetooth/input.conf file and found 
```
# Configuration file for the input service

# This section contains options which are not specific to any
# particular interface
[General]

# Set idle timeout (in minutes) before the connection will
# be disconnect (defaults to 0 for no timeout)
#IdleTimeout=30

```

I changed IdleTimeout to 0 so it won't time out anymore (hopefully).

// Changing the IdleTimeout didn't seem to matter...

---

### Post by HyRax on 2008-12-29
I'm running 64-bit as well - no dramas. My /etc/default/bluetooth is far simpler than yours:

```

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497
HID2HCI_ENABLED=1
HID2HCI_UNDO=1

```

The reason I don't have the HIDD_ENABLED and HIDD_OPTIONS lines is that I do not have the bluez-compat package installed that contains the *hidd* command, because it is not supposed to be part of Intrepid anymore.

Can I suggest as an experiment that you boot up on a LiveCD (or a VM) so that you have a fresh, default environment to work with, pair your mouse and keyboard as normal and then issue the *sudo hciconfig hci0 pscan* command and see how you go? I've now setup four machines with Intrepid and Bluetooth mice (cabled keyboards, though) and they are currently working perfectly with this workaround.

Also, the disconnection timeout is generally a function of the hardware, not software. The keyboard and mouse disconnect themselves to conserve battery when idle.

---

### Post by newore on 2009-02-09
using a microsoft bluetooth mouse 5000 on a lenovo s10 

under 8.10 I connected once but never again. pscan didn't seem
to make a difference. 

under 9.04 which has later bluez-gnome, pscan method makes no difference. the applet shows a connect button, but no function for
the mouse after using. removing the mouse device and reconnecting using the '+' button adds the mouse to the device list but does not show mouse function. the mouse flashes intermittant led signals like it is still trying to sync.

there is a bug open on this:
[https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/285007](https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/285007)

---

### Post by HyRax on 2009-02-09
> **newore said:**
> using a microsoft bluetooth mouse 5000 on a lenovo s10 

under 8.10 I connected once but never again. pscan didn't seem
to make a difference. 


Works perfectly for me under 8.10. Worse-case scenario is when I reboot - I just need to switch the mouse off and then on again and it reconnects a few seconds later without needing to redo the Bluetooth pairing. I've also never had any sleeping issues.

Can you enter just:
```

$ sudo hciconfig hci0

```
...and post up the output? It should look similar to this:

```

hci0:	Type: USB
	BD Address: 00:BB:CC:00:33:FF ACL MTU: 310:10 SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:766 acl:0 sco:0 events:34 errors:0
	TX bytes:401 acl:0 sco:0 commands:34 errors:0

$ 

```
If it does not show "UP RUNNING PSCAN", then your Bluetooth adapter is not actively scanning and the mouse will not auto reconnect.

---

### Post by newore on 2009-02-09
here 'tis:

bp@bp-ssdjacky:~$ hciconfig hci0
hci0:	Type: USB
	BD Address: 00:14:A4:FD:57:75 ACL MTU: 1017:8 SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN 
	RX bytes:1180 acl:0 sco:0 events:56 errors:0
	TX bytes:495 acl:0 sco:0 commands:56 errors:0

note that it's running both pscan and iscan. ran pscan only, at the first as you suggested. 'hciconfig noscan' not working for me.

msoft's mouse seems to start and fade rapidly, when i toggle the switch on off. i changed batteries just in case. this is 9.04.

---

### Post by newore on 2009-02-09
noting the difference in the aclmtu i tried:

sudo hciconfig aclmtu 310:10

but just got the same data as before the command. maybe it's hardwired
somewhere?

b

---

### Post by newore on 2009-02-09
taking a look at the mouse info

<code>
bp@bp-ssdjacky:~$ hcitool scan
Scanning ...
	00:1D:D8:96:AE:9B	Microsoft Bluetooth Notebook Mouse 5000
bp@bp-ssdjacky:~$ hcitool info 00:1D:D8:96:AE:9B
Requesting information ...
Can't create connection: Operation not permitted
bp@bp-ssdjacky:~$ sudo hcitool info 00:1D:D8:96:AE:9B
Requesting information ...
	BD Address:  00:1D:D8:96:AE:9B
	LMP Version: 2.0 (0x3) LMP Subversion: 0x5cb2
	Manufacturer: Infineon Technologies AG (9)
	Features: 0xbc 0x02 0x04 0x38 0x18 0x00 0x00 0x00
		<encryption> <slot offset> <timing accuracy> <role switch> 
		<sniff mode> <RSSI> <power control> <enhanced iscan> 
		<interlaced iscan> <interlaced pscan> <AFH cap. slave> 
		<AFH class. slave> 

</code>

---

### Post by newore on 2009-03-17
problem has returned with recent bluez upgrade... 4.32-0ubuntu1

microsoft mouse had been syncing automatically upon boot. now
back to momentary connection icon on pairing, with no further connections..


 sudo hciconfig hci0
[sudo] password for bp: 
hci0:	Type: USB
	BD Address: 00:14:A4:FD:57:75 ACL MTU: 1017:8 SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:1097 acl:0 sco:0 events:44 errors:0
	TX bytes:434 acl:0 sco:0 commands:44 errors:0

VERY annoying.

---

### Post by newore on 2009-03-17
kernel version is now 2.26.10.10 generic  for bluez problem with microsoft mouse

sudo hcitool scan shows NO output, although the mouse is showing in the preferences device display.

perhaps it's user error on hcitool. It does see the mouse, if I put it in 'pairing' mode.
00:1D:D8:96:AE:9B	Microsoft Bluetooth Notebook Mouse 5000

just nothing in regular operating mode for the mouse.

 lsusb
Bus 005 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 005 Device 002: ID 5986:0241 Acer, Inc 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by olaoni on 2009-04-30
Hi Group,

As anyone been able to use the bluetooth mouse successfully in ubuntu 9.04.
I am using the HP Bluetooth PC card mouse. This worked correctly in ubuntu 8.10.

I initially tried the built in Ubuntu (9.04) Bluetooth stack. I am able to pair the mouse with my laptop (HP-TC1100) successfully. And after this I can use the mosue without a problem. 

The problem manifest itself when I power down the mouse or the laptop or I don't use mouse for a few minutes. 
To get the mouse to work again, I have to remove the mouse from the list of bluetooth device and then go through the whole pairing process again.

After trying to get the mouse to work correctly for a couple of hours. I decided to do a google search for better bluetooth stack support.

I came across the blueman bluetooth stack which I was able to install without much effort. [http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html]("http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html")

Unfortunately after pairing the laptop and the mouse everything behaved the same.

Any help will be highly appreciated.

---

### Post by HyRax on 2009-04-30
Well, you're one better than me - Bluetooth mice under Jaunty doesn't appear to work for me at all now. Worked fine with the pscan workaround under Intrepid!

In your case, when your mouse goes to sleep, try the following command in a terminal and see if your mouse suddenly wakes up after a second or so:

```

sudo hciconfig hci0 pscan

```

---

### Post by olaoni on 2009-04-30
Sorry for the delay in responding. I have partially gone back to windows (Which I dislike). Unfortunately I have too much stuff are not working on my laptop at the moment and I begining to get fed up spending too much time trying to get things to work.

---

### Post by olaoni on 2009-04-30
Hi HyRax,

Sorry I missed your request in my last post. 
The command didn't make a difference.

Just a silly thought have you tried using Blueman bluetooth package.
See if that makes a difference.

---

### Post by fwendt on 2009-07-15
As a side note - I've been listening to music using a SonyEricsson headset since 7.10. Since January this year I've used an Acer Aspire One 110L with a new USB adapter/dongle and it's been running perfectly OK with Ubuntu 8.10. BUT, with 9.04 the playback is choppy and it sounds like the bluetoothd daemon doesn't get enough CPU time in order to transfer the data. It sounds just like it did with 8.10 when I got too far away from the laptop, and then returned (it speeds up/skips frames to get back in sync).

Any ideas on what I can try to fix this is greatly welcome. (Kernel schedulers, renicing banshee, bluetoothd, pulseaudio, ...)

---

### Post by olaoni on 2009-09-01
Hey HyRax,

Out of curiousity. Did you manage to solve the bluetooth issue on your ubuntu 9.04 system?

I am still have the same issues I tend to visit the forums from time to time hoping to find a solution but nothing has worked so far. Very fraustrating I must admit.

Regards

Ola

---

### Post by HyRax on 2009-09-01
> **olaoni said:**
> 
Out of curiousity. Did you manage to solve the bluetooth issue on your ubuntu 9.04 system?
As a matter of fact, I did! I wrote about it [here](http://www.serenux.com/2009/08/howto-get-a-microsoft-bluetooth-notebook-5000-mouse-working-under-ubuntu-jaunty/). :)

---

### Post by olaoni on 2009-09-01
> **HyRax said:**
> As a matter of fact, I did! I wrote about it [here](http://www.serenux.com/2009/08/howto-get-a-microsoft-bluetooth-notebook-5000-mouse-working-under-ubuntu-jaunty/). :)

It seems you guys with the Microsoft bluetooth mouse are in luck. The process you described in your link was the same process I tried back in April 2009.

Out of curiosity I removed my setup and followed your tutorial just in case I missed something back then.

The result was the same. I can pair and use the mouse. The problem with my mouse arises when I turn it off and on.

After this point the pc no longer detects the mouse, even though it is in the blueman bluetooth device list and bonded. To get things working again. I will have to remove it from the bluetooth device list and then re-pair before I can get it to work again.

For the record, Just in case someone out there has a similar setup and has thing completely working I am using HP bluetooth mouse see [http://h18000.www1.hp.com/products/quickspecs/12618_div/12618_div.HTML]("http://h18000.www1.hp.com/products/quickspecs/12618_div/12618_div.HTML")

And my PC is the HP TC1100 (using built in bluetooth module) running ubuntu 9.04 32 bits.

Thanks for your time.

Regards

Ola

---

### Post by blue928 on 2010-11-01
> **HyRax said:**
> Next time your Bluetooth mouse/keyboard falls asleep, open a terminal and type in the following command (yes, I know this necessitates getting another keyboard!! ;) )

```

$ sudo hciconfig hci0 pscan

```Wait a few seconds and start wiggling your mouse to see if it comes back to life. If it does, great - your Bluetooth adapter was not actively scanning for devices to reconnect.

Rebooting will lose this change, so until a permanent bugfix is made, just stick the command into your /etc/rc.local file before the "exit 0" line so it gets executed on every startup.

*NOTE ABOUT THIS WORKAROUND:* Depending on your Bluetooth devices, Ubuntu may still not connect to them if they already had a "connected" status, eg: when you reboot. The simplest way to get them to reconnect is to switch them off and on again and Ubuntu will then pick them up a few seconds later. You can power cycle right away rather than wait for Ubuntu to completely restart and they should be usable again even from the login screen.

This thread is a little old, but hopefully someone is still checking it.

I am using an IOGEAR gbu421 bluetooth dongle on unbuntu 10.04.  I'm connecting my motorola h12 headset to it for use with Google Voice.  When I use the GUI to find my headset, it works perfect, and the combination for voice chat works better than expected.

However, after the headset goes idle, I lose the 'connected' status in the bluetooth device GUI screen.  When I switch the headset off and then back on, the connected icon beside the device name shows up briefly and disappears.  In other words, after the first use, the headset will not stay connected, and I have to "Remove" the device in the GUI and rediscover it.

Can someone tell me how to have this reconnect and stay connected each time? This is for voice calls through Google Voice, but obviously receiving calls is going to be impossible if I have to spend 20 seconds setting it up for each phone call.

Thanks!

Blue

---

