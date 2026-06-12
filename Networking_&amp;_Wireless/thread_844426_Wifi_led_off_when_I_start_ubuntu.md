---
title: "Wifi led off when I start ubuntu"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by Ihaveaproblem on 2008-06-29
Hi to all, please help me!
Everytime I turn on my notebook and start ubuntu, the small wifi led turn on. I using ADSL cable so everytime manually I turn off the wifi. I'd like to set off permanently my wifi so I've to turn on it just when I have to use an ADSL wifi (very few times!).
How can I do this?
Thank you very much!

---

### Post by pytheas22 on 2008-06-29
What is the output of:
```

lshw -C Network
```

That will tell us the interface name and the driver used by the device you want to disable.  Then you can either blacklist the driver or write a script to force down the interface, and the device will be disabled.

---

### Post by lswb on 2008-06-29
Some of the wireless adapter modules can accept parameters at load time to control various things. Once you know the module being loaded for your wireless adapter,
you can use the modinfo command to see if it accepts any parameters for controlling the default on/off state. For instance, I have an Intel Pro 2200 card that uses the ipw200 driver. Typing "modinfo ipw2200" in a terminal returns a few screens full of information, including:
  parm:           disable:manually disable the radio (default 0 [radio on]) (int)

so If I needed to, I could add this line to a file in /etc/modprobe.d:

   options ipw2200 disable=1

and the disable=1 parameter will automatically be used whenever the ipw2200 module is loaded. Sometimes the information provided by modinfo is not easily translated, you may have to do some googling to determine the correct syntax.

---

### Post by Ihaveaproblem on 2008-07-02
Thank you pytheas22, your > lshw -C Network I know my driver:

> driver=iwl3945

Thank you lswb for your reply. Just that, where I've to put the option?
> options ipw2200 disable=1

I tried in /etc/modprobe.d/options but didn't work!
Maybe in blacklist file?
Ok. I can try one by one file but I see 16 files and 2 subdirectory! Maybe you can help me to make easier my job...
:)
thank you very much!

---

### Post by chili555 on 2008-07-02
Isn't there a wireless switch or key combination on your laptop? Try turning it off.> options ipw2200 disable=1I believe he was using that as an example. This is the wrong option for your 3945ABG.

Hard-coding the wireless off certainly works, but it's then difficult to re-enable it when, on those few occaisions, you want to use wireless. That's why I suggest the switch.

---

### Post by pytheas22 on 2008-07-02
Since you know your driver, you can open the file /etc/modprobe.d/blacklist and add the line:
```

blacklist iwl3945
```

to the bottom and save the file.  Then either reboot or run:
```

sudo rmmod iwl3945
```

and the card will be permanently disabled until you remove its driver from the blacklist and run:
```

sudo modprobe iwl3945
```

to reactivate it.

That said, the solutions that others have suggested might be better (the switch is probably best if you do indeed have a switch for the card).  Any of these methods should work fine, but some may be more convenient than others depending on how often you do want to use the wireless.

---

### Post by Ihaveaproblem on 2008-07-02
Thank you chili555, but I prefer pytheas22's solution!
pytheas22, thank you for your wonderful post but...doesn't work :(

I wrote the command:
sudo gedit /etc/modprobe.d/blacklist

and I wrote in blacklist file: blacklist iwl3945.
Well, I saved and I closed gedit.
After I turned off my notebook and I turned on again after few seconds.
Well, after grub, when ubuntu begin to load, this damn wifi led turned on again!!!  (sigh!) :(
Why???

ok. this is "lshw -C Network" command:

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:2b:12:63
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

I think your solution is very good, but I don't understand why doesn't work!
Some ideas?
Thank to all

---

### Post by pytheas22 on 2008-07-02
> I think your solution is very good, but I don't understand why doesn't work!
Some ideas?

Sorry it didn't work; that's strange.

What if you (without rebooting or anything) run the command:
```

sudo rmmod iwl3945
```

Does the light turn off immediately?

If not, what happens with:

```
sudo ifconfig wmaster0 down
```

---

### Post by Ihaveaproblem on 2008-07-03
Hi pytheas22,

> What if you (without rebooting or anything) run the command:
Code:

sudo rmmod iwl3945

Does the light turn off immediately?

No :( light continuing on...

> If not, what happens with:

Code:

sudo ifconfig wmaster0 down



```
pepito@pepitoshome:~$ sudo ifconfig wmaster0 down
wmaster0: ERROR while getting interface flags: No such device
pepito@pepitoshome:~$
```

Strange? Any idea? :confused:

---

### Post by chili555 on 2008-07-03
> Thank you chili555, but I prefer pytheas22's solution!
pytheas22, thank you for your wonderful post but...doesn't work Are you starting to like mine better now?

---

### Post by Ihaveaproblem on 2008-07-03
> **chili555 said:**
> Isn't there a wireless switch or key combination on your laptop? Try turning it off.I believe he was using that as an example. This is the wrong option for your 3945ABG.

Hard-coding the wireless off certainly works, but it's then difficult to re-enable it when, on those few occaisions, you want to use wireless. That's why I suggest the switch.

Hi chili555, I hope didn't offend you! Sorry :( Just I liked the other solution because everytime I turn on my notebook and launch ubuntu I've to switch off the wifi!!
Just that.
I'd like to set it off permanently by software, and when I need wifi (really very few times) set it on!
Why you wrote:
> Hard-coding the wireless off certainly works, but it's then difficult to re-enable it when, on those few occaisions, you want to use wireless. That's why I suggest the switch.
Really in the magic world of Linux doesn't exist a "switch software" to do that? :confused:

---

### Post by pytheas22 on 2008-07-03
I think that by the switch, chili means either a physical button to turn your wifi on and off, or possibly a function-key that would do the same.  That's probably why it is the easiest solution, if you have a switch like that.  There's no guarantee that you do, however.

As for my commands, I'm puzzled as to why they're not working.  If lshw says that your driver=iwl3945, then removing that module should make the card invisible.  I don't know why it's not working.

It might work to:
```

sudo ifconfig wlan0 down
```

That should also make the wireless turn off, and it could be put into a script if that's the case.

---

### Post by chili555 on 2008-07-03
> I hope didn't offend you! Not at all, I just like the solution that works better than the one that doesn't.  

First, remove *iwl3945* from your blacklist so this all works as expected when you do want to use your wireless. Next, *sudo gedit /etc/modprobe.d/iwl3945*. It will open a new file. Add two lines:```
alias wlan0 iwl3945
options iwl3945 disable=1
```Proofread, save and close. When you reboot, your wireless should be off.

When you want to use the wireless again, do:```
sudo mv /etc/modprobe.d/iwl3945 /etc/modprobe.d/iwl3945.bak
```Disable it again with the reverse; that is:```
sudo mv /etc/modprobe.d/iwl3945.bak /etc/modprobe.d/iwl3945
```Let us know.

---

### Post by lswb on 2008-07-03
Hello Chili555,
Fortunately my ipw2200 works without needing any module loading options, so I've never tested it, but please correct me if I'm wrong: I was under the impression that the disable parameter just set the initial state of the wireless adapter at boot, and that it could subsequently be turned back on with the switch. I might try this later just to satisfy my curiosity.

---

### Post by chili555 on 2008-07-04
> the disable parameter just set the initial state of the wireless adapter at boot, and that it could subsequently be turned back on with the switch.Theoretically, yes. It depends, however, how well the keys map in the software. There are all kinds of posts here that deal with the rf_kill switch and it's obvious that some function perfectly and some don't work very well at all.

My Thinkpad T60 has a physical slide switch on the front that turns the wireless radio off and on, although the network sometimes doesn't come up automatically. If I were going to be connected by ethernet for any appreciable time, I'd simply leave the switch in the off position.

I haven't tried 'disable=1' myself, however, I will and I will report for the benefit of the searchers.

---

### Post by Ihaveaproblem on 2008-07-04
> **pytheas22 said:**
> I think that by the switch, chili means either a physical button to turn your wifi on and off, or possibly a function-key that would do the same.  That's probably why it is the easiest solution, if you have a switch like that.  There's no guarantee that you do, however.

As for my commands, I'm puzzled as to why they're not working.  If lshw says that your driver=iwl3945, then removing that module should make the card invisible.  I don't know why it's not working.

It might work to:
```

sudo ifconfig wlan0 down
```

That should also make the wireless turn off, and it could be put into a script if that's the case.

Led continue turn on... :(

> **chili555 said:**
> Not at all, I just like the solution that works better than the one that doesn't.  

First, remove *iwl3945* from your blacklist so this all works as expected when you do want to use your wireless. Next, *sudo gedit /etc/modprobe.d/iwl3945*. It will open a new file. Add two lines:```
alias wlan0 iwl3945
options iwl3945 disable=1
```Proofread, save and close. When you reboot, your wireless should be off.

When you want to use the wireless again, do:```
sudo mv /etc/modprobe.d/iwl3945 /etc/modprobe.d/iwl3945.bak
```Disable it again with the reverse; that is:```
sudo mv /etc/modprobe.d/iwl3945.bak /etc/modprobe.d/iwl3945
```Let us know.

Led continue turn on... :(

> My Thinkpad T60 has a physical slide switch on the front that turns the wireless radio off and on
My notebook too!

---

### Post by chili555 on 2008-07-05
> 
[QUOTE]
My Thinkpad T60 has a physical slide switch on the front that turns the wireless radio off and on
My notebook too![/QUOTE]Now I am really confused! You mean if you slide the switch to 'off' and leave it there and boot up the notebook, the LED and wireless come ***on***?

---

### Post by Ihaveaproblem on 2008-07-05
> Now I am really confused! You mean if you slide the switch to 'off' and leave it there and boot up the notebook, the LED and wireless come on?

Yes! absolutely. everytime.

My switch type is a spring type. I've to press, with my finger, on the left side to turn on/off wifi and when I leave my finger the switch go back alone to the right side.

Strange, when (very very few times...) I start up windows vista preinstalled on my notebook, wifi led is off!
If I need to use wifi with vista, I launch acer network tool and only in this case the led switch from off to on lighting!
For this reason I'm sure it's a software setting and not hardware!

---

### Post by lswb on 2008-07-05
Are you SURE that your wireless card is in Intel 3945? What does lspci show? Does operating the switch have no effect, or does the wireless in fact actually turn on & off with the switch? You can "tail -f /var/log/syslog" in a terminal while operating the switch to see if anything is happening.

---

### Post by Ihaveaproblem on 2008-07-05
> **lswb said:**
> Are you SURE that your wireless card is in Intel 3945? What does lspci show?

from terminal: lspci
> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
**05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)**
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

> Does operating the switch have no effect, or does the wireless in fact actually turn on & off with the switch? 

Switch on -> wifi on
Switch off -> wifi off

> You can "tail -f /var/log/syslog" in a terminal while operating the switch to see if anything is happening.

With wifi on:

> pepito@pepitoshome:~/Desktop$ tail -f /var/log/syslog
Jul  5 16:29:09 pepitoshome NetworkManager: <debug> [1215268149.248146] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_119fbd78ad'). 
Jul  5 16:29:15 pepitoshome NetworkManager: <debug> [1215268155.322901] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_119fbd78ad'). 
Jul  5 16:29:15 pepitoshome hcid[19381]: link_key_request (sba=00:11:67:42:3E:38, dba=00:11:9F:BD:78:AD)
Jul  5 16:30:01 pepitoshome /USR/SBIN/CRON[19636]: (pepito) CMD (sh /home/pepito/.xplanet/earth)
Jul  5 16:40:01 pepitoshome /USR/SBIN/CRON[20174]: (pepito) CMD (sh /home/pepito/.xplanet/earth)
Jul  5 16:50:01 pepitoshome /USR/SBIN/CRON[20722]: (pepito) CMD (sh /home/pepito/.xplanet/earth)
Jul  5 16:51:43 pepitoshome hcid[19381]: Default passkey agent (:1.2521, /org/bluez/passkey) registered
Jul  5 16:51:43 pepitoshome hcid[19381]: Default authorization agent (:1.2521, /org/bluez/auth) registered
Jul  5 17:00:01 pepitoshome /USR/SBIN/CRON[21323]: (pepito) CMD (sh /home/pepito/.xplanet/earth)
Jul  5 17:10:01 pepitoshome /USR/SBIN/CRON[21864]: (pepito) CMD (sh /home/pepito/.xplanet/earth)

At this time I switched off the wifi button

> 
Jul  5 17:12:11 pepitoshome kernel: [ 8646.165509] iwl3945: Radio Frequency Kill Switch is On:
Jul  5 17:12:11 pepitoshome kernel: [ 8646.165513] Kill switch must be turned off for wireless networking to work.
Jul  5 17:12:16 pepitoshome NetworkManager: <info>  Wireless now disabled by radio killswitch 
Jul  5 17:12:16 pepitoshome NetworkManager: <info>  Deactivating device wlan0. 

After 2 minutes about, I turned on again wifi (always using physical button)
> 
Jul  5 17:14:29 pepitoshome NetworkManager: <info>  Wireless now enabled by radio killswitch 
Jul  5 17:14:31 pepitoshome kernel: [ 8714.895607] ADDRCONF(NETDEV_UP): wlan0: link is not ready 

That's all

---

### Post by lswb on 2008-07-05
Well, if it's any consolation, at least you now know that the switch is working OK, even though the led is not. I did a little googling & searching on this and found several references to the iwl3945 module not properly supporting the led function on some systems. Some people stated they got it working by adding hardy backports to their repositories and using the modules supplied from there. Others installed the older ipw3945 module and claimed success. 

It might be worthwhile trying out the backports module. The other solution, using the older ipw3945 module (someone correct me if there's another way) would be kind of a pain; You'd have to compile it from source against your kernel, not that it's terribly difficult, but every time there's a kernel update, you'd need recompile. run depmod, etc. And you would have to blacklist the iwl3945 module or delete it. The backports method (if it did in fact work) should be a one-time thing. 

You also might just put up with it for the time being, perhaps an update will correct this problem. Personally, though I really like some of the new things in hardy, there's lots of times I wonder why I ever upgraded from dapper!

---

### Post by Ihaveaproblem on 2008-07-20
Well I studied better the problem.
I wrote the wifi module "iwl3945" into /etc/blacklist
Now my wifi is off but...
But wifi led is on!!! It's incredible!
When I turn on my notebook, ubuntu starts, wifi module (iwl3945) didn't load but wifi led turn on!!
Why?
I'm so sed!!
:.(

---

### Post by pytheas22 on 2008-07-20
> Now my wifi is off but...
But wifi led is on!!! It's incredible!

Another Intel wireless module could be causing the light to come on even though it can't drive the card.  Does adding:
```

blacklist iwl4965
```

to /etc/modprobe.d/blacklist make a difference?

---

### Post by Ihaveaproblem on 2008-07-21
blacklist iwl4965 added to my /etc/modprobe.d/blacklist

Nothing happened!
I turned off my notebook. I turned on again after 10seconds and...the damned led turned on again!
It becoming a stupid nightmare for me...
:(

Other advice, please?

---

### Post by lswb on 2008-07-21
You know, I have a notebook where the led come on all the time ,even when there was NO CARD INSTALLED!

---

### Post by Ihaveaproblem on 2008-07-21
> **lswb said:**
> You know, I have a notebook where the led come on all the time ,even when there was NO CARD INSTALLED!

INCREDIBLE!!! I didn't know this!
I'd like to create my personal notebook...
;)

Ok. But when I start up winvista led remain off!!
So, in ONLY this case, vista is better than ubuntu! :D

I found in this file (/etc/acpi/start.d/**60-asus-wireless-led.sh**) the led status control:

```
#!/bin/sh
. /usr/share/acpi-support/state-funcs
if isAnyWirelessPoweredOn ; then
    setLEDAsusWireless 1
else
    setLEDAsusWireless 0
fi

```

So I read the file **state-funcs**:
```
#!/bin/sh
# Paul Sladen, 2006-03-28, 2007-03-26
# Library functions to check/change status of wireless

# Return 0 if there is, allowing you to write   if isAnyWirelessPoweredOn; then ...
isAnyWirelessPoweredOn()
{
    for DEVICE in /sys/class/net/* ; do
	if [ -d $DEVICE/wireless ]; then
	    # if any of the wireless devices are turned on then return success
	    if [ -r $DEVICE/device/power/state ] && [ "`cat $DEVICE/device/power/state`" -eq 0 ]
	    then
		return 0
	    fi
	    if [ -r $DEVICE/device/rf_kill ] && [ "`cat $DEVICE/device/rf_kill`" -eq 0 ]
	    then
		return 0
	    fi
	fi
    done
    # otherwise return failure
    return 1
}

# Takes no parameters, toggles all wireless devices.
# TODO: Should possible toggle all wireless devices to the state of the first one.
# Attempts to use 'rf_kill' first, and then tries 'power/state', though that
# will fail on >=2.6.18 kernels since upstream removed the functionality...
toggleAllWirelessStates()
{
    for DEVICE in /sys/class/net/* ; do
	if [ -d $DEVICE/wireless ] ; then
	    # $DEVICE is a wireless device. Check if it's powered on:
	    ON=0
	    OFF=1  # 1 for rf_kill, 2 for power/state
	    for CONTROL in $DEVICE/device/rf_kill $DEVICE/device/power/state ; do
		if [ -w $CONTROL ] ; then
		    # We have a way of controlling the device, lets try
		    if [ "`cat $CONTROL`" = 0 ] ; then
			# It's powered on. Switch it off.
			if echo -n $OFF > $CONTROL ; then 
			    break
			else
			    OFF=2 # for power/state, second time around
			fi
		    else
			# It's powered off. Switch it on.
			if echo -n $ON > $CONTROL ; then
			    break
			fi
```

What you think about? I think ubuntu, at start up, read the blacklist file after other wifi-files like **state-funcs**. For this reason, **state-funcs** find a wifi in my notebook and the file **60-asus-wireless-led.sh** turn on the led! I'd like to know what **state-funcs** find!!

One more think: if I write in a terminal: *lshw -C network*
I can read:

>   *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:b3:c9:5b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.64 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

Well, this last network information is my ethernet, so...it's ok, but...first network, UNCLAIMED, says me...*Network controller*
Maybe I disabled the wifi card but not the controller and I need to switch off the controller also (or only the controller?)

---

### Post by pytheas22 on 2008-07-23
You could try editing the /etc/acpi/start.d/60-asus-wireless-led.sh script to something like:

```

#!/bin/sh
. /usr/share/acpi-support/state-funcs
#if isAnyWirelessPoweredOn ; then
#    setLEDAsusWireless 1
#else
    setLEDAsusWireless 0
fiscript
```

That way it should turn the wireless light off no matter what.

---

### Post by Ihaveaproblem on 2008-07-24
@pytheas22
good idea!! I did it but...doesn't work!! This fu...ing led turned on immediatey after grub boot!!
Maybe there's an other REAL file where this control is checked!!
Believe me, this apparently stupid problem knacking out me!!!
:...((
Other ideas?

---

### Post by pytheas22 on 2008-07-25
That's strange...maybe editing /usr/share/acpi-support/state-funcs would help?  You could try to make the isAnyWirelessPoweredOn function always return 0 by editing it to something like:

```
isAnyWirelessPoweredOn()
{
    for DEVICE in /sys/class/net/* ; do
	if [ -d $DEVICE/wireless ]; then
	    # if any of the wireless devices are turned on then return success
	    if [ -r $DEVICE/device/power/state ] && [ "`cat $DEVICE/device/power/state`" -eq 0 ]
	    then
		return 0
	    fi
	    if [ -r $DEVICE/device/rf_kill ] && [ "`cat $DEVICE/device/rf_kill`" -eq 0 ]
	    then
		return 0
	    fi
	fi
    done
    # otherwise return failure
    **return 0**
}
```

It's a dirty solution but it should make it always think that no wireless device is on, I think.

Also, I can't tell where the 'setLEDAsusWireless' call comes from.  It's not a function that appears in the scripts you've pasted here (and I don't have an Asus board to check myself), as far as I can tell.  Do you know where it's getting that from, and if so, could you paste it here?  Maybe there's a way to force setLEDAsusWireless to never actually turn the light on.

---

### Post by zoly on 2008-07-30
HI! Wait for the next Ubuntu version: I've tried the Intrepid Ibex Alpha 3 live CD and the wifi LED works fine :) (not working on Hardy Heron, but worked on any previous versions) I think it is a kernel problem, while Intrepid has newer kernel.

---

### Post by Ihaveaproblem on 2008-08-02
@zoly GOOD NEW!!! I'll wait for... Intrepid! Of course! my nightmares will finish!! :)
But in the meantime...in full Linux spirit...I trying to understand the problem.
I post below the **full** /usr/share/acpi-support/state-funcs file (in my previous post I posted a partial!) please see the end of this file...

```
#!/bin/sh
# Paul Sladen, 2006-03-28, 2007-03-26
# Library functions to check/change status of wireless

# Return 0 if there is, allowing you to write   if isAnyWirelessPoweredOn; then ...
isAnyWirelessPoweredOn()
{
    for DEVICE in /sys/class/net/* ; do
	if [ -d $DEVICE/wireless ]; then
	    # if any of the wireless devices are turned on then return success
	    if [ -r $DEVICE/device/power/state ] && [ "`cat $DEVICE/device/power/state`" -eq 0 ]
	    then
		return 0
	    fi
	    if [ -r $DEVICE/device/rf_kill ] && [ "`cat $DEVICE/device/rf_kill`" -eq 0 ]
	    then
		return 0
	    fi
	fi
    done
    # otherwise return failure
    return 1
}

# Takes no parameters, toggles all wireless devices.
# TODO: Should possible toggle all wireless devices to the state of the first one.
# Attempts to use 'rf_kill' first, and then tries 'power/state', though that
# will fail on >=2.6.18 kernels since upstream removed the functionality...
toggleAllWirelessStates()
{
    for DEVICE in /sys/class/net/* ; do
	if [ -d $DEVICE/wireless ] ; then
	    # $DEVICE is a wireless device. Check if it's powered on:
	    ON=0
	    OFF=1  # 1 for rf_kill, 2 for power/state
	    for CONTROL in $DEVICE/device/rf_kill $DEVICE/device/power/state ; do
		if [ -w $CONTROL ] ; then
		    # We have a way of controlling the device, lets try
		    if [ "`cat $CONTROL`" = 0 ] ; then
			# It's powered on. Switch it off.
			if echo -n $OFF > $CONTROL ; then 
			    break
			else
			    OFF=2 # for power/state, second time around
			fi
		    else
			# It's powered off. Switch it on.
			if echo -n $ON > $CONTROL ; then
			    break
			fi
		    fi
		fi
	    done
	fi
    done
}

# Pass '1' to blink suspending LED and '0' to stop LED
setLEDThinkpadSuspending()
{
    action=`test "$1" -ne 0 && echo blink || echo off`
    test -w /proc/acpi/ibm/led && echo -n 7 "$action" > /proc/acpi/ibm/led
}

# Pass '1' to light LED and '0' to dark LED
setLEDAsusWireless()
{
    action=`test "$1" -ne 0 && echo 1 || echo 0`
    test -w /proc/acpi/asus/wled && echo -n "$action" > /proc/acpi/asus/wled
    test -w /sys/devices/platform/asus-laptop/wlan && echo -n "$action" > /sys/devices/platform/asus-laptop/wlan
}
```

That's strange!! These last two tests are for imb-thinkpad and asus. Nothing test for acer!!!!!
In fact, I haven't /proc/acpi/ibm... neither /proc/acpi/asus... directories, of course!
I've /proc/acpi/acer/ directory with inside these files:
[I]brightness
interface
threeg
version
wireless[/I]

And if I do in a terminal: cat /proc/acpi/acer/wireless
Linux replies me:
0

Because I wrote the wireless module (iwl3945) in /etc/modprobe.d/blacklist (in fact my problem is the led on, my wireless is always off now!)
So there isn't test for acer wireless! Consequently linux can't control my wifi led on/off!
Maybe is this the problem?

Other doubt: in 8-11th lines of this file, if I understood well, linux search in /sys/class/net/* any wireless device, it's correct?
Well, in /sys/class/net/* there isn't wireless file (because I put it in blacklist..), in fact there are only:
[I]eth0 (link)
lo (link)
ppp0 (link)[/I]
So I looked for */device/power/state* on my linux...doesn't exist!! (maybe I put it in blacklist, but I'm not sure!)
Last question: if there isn't acer wireless test file, why linux at start up turn on the led instead let it off?
:confused:

---

### Post by Ichido on 2008-08-04
Please forgive me for 'jumping in' here but I have a problem.
My 2 Dell Inspirons 1525n, with Hardy and the 3945 Wireless Mini-Card, Wireless worked great until 4 days ago when I did the usual Updates.
Now I have two laptops without Wifi!
I suspect the "Updates" Killed both of my laptop's wifi

output from "dmesg | tail" from one of my 2 laptops:

[ 70.924157] sky2 eth1: enabling interface
[ 70.930385] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 73.048413] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 73.048555] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[ 73.049623] iwl3945: Radio disabled by HW RF Kill switch
[ 73.049741] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[ 86.438315] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 86.438458] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[ 86.439560] iwl3945: Radio disabled by HW RF Kill switch
[ 86.439678] ACPI: PCI interrupt for device 0000:0b:00.0 disabled

What is a "Kill Switch"?
How do I "Un-Kill" my Wifi?
Can I "Un-Update"?

Can anyone help?

---

### Post by pytheas22 on 2008-08-04
> Please forgive me for 'jumping in' here but I have a problem.
My 2 Dell Inspirons 1525n, with Hardy and the 3945 Wireless Mini-Card, Wireless worked great until 4 days ago when I did the usual Updates.
Now I have two laptops without Wifi!
I suspect the "Updates" Killed both of my laptop's wifi

output from "dmesg | tail" from one of my 2 laptops:

[ 70.924157] sky2 eth1: enabling interface
[ 70.930385] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 73.048413] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 73.048555] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[ 73.049623] iwl3945: Radio disabled by HW RF Kill switch
[ 73.049741] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[ 86.438315] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 86.438458] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[ 86.439560] iwl3945: Radio disabled by HW RF Kill switch
[ 86.439678] ACPI: PCI interrupt for device 0000:0b:00.0 disabled

What is a "Kill Switch"?
How do I "Un-Kill" my Wifi?
Can I "Un-Update"?

Can anyone help?

It seems that the Intel iwl drivers have a great knack for breaking via Ubuntu updates...this is the fifth or sixth case I've seen in two weeks...what's going on?  Why don't these updates get tested better???  It's pretty embarrassing to tell someone to choose between keeping her system up-to-date or having a working wireless card on Ubuntu.

Actually it seems that other distributions have similar issues with Intel wireless, so I guess the iwl people are at fault more than Ubuntu, but we should still be testing these things thoroughly before we push them out through updates!

Anyway, does this help:
```

rmmod -f iwl3945
modprobe iwl3945 disable_hw_scan=1
```

Run that command and wait a few seconds and see if you can connect again, and post your results.

Also, you may want to start a new thread, since I think your issue doesn't have to do with the original poster's problem, other than being related to the iwl drivers.  If you start a new thread, let us know the URL.

@Ihaveaproblem: sorry, but I'm out of suggestions for your issue.  I hope someone else will still be able to think of why you can't get your LED to turn off, though, or that it will be fixed in Intrepid.

---

### Post by chili555 on 2008-08-05
> [ 86.439560] iwl3945: Radio disabled by HW RF Kill switch
[ 86.439678] ACPI: PCI interrupt for device 0000:0b:00.0 disabled

What is a "Kill Switch"?
How do I "Un-Kill" my Wifi?The kill switch is the switch or key combination, Fn+F2 perhaps, that allows a laptop to turn off the wireless radio to lower power consumption while playing solitaire (but pretending to work up your expense report) in the airport. You computer believes the switch is set to 'off.' It is this that has killed your wireless, evidently, rather than an update. Find it and press it!

---

### Post by Ichido on 2008-08-06
> **pytheas22 said:**
> It seems that the Intel iwl drivers have a great knack for breaking via Ubuntu updates...this is the fifth or sixth case I've seen in two weeks...what's going on?  Why don't these updates get tested better???  It's pretty embarrassing to tell someone to choose between keeping her system up-to-date or having a working wireless card on Ubuntu.

Actually it seems that other distributions have similar issues with Intel wireless, so I guess the iwl people are at fault more than Ubuntu, but we should still be testing these things thoroughly before we push them out through updates!

Anyway, does this help:
```

rmmod -f iwl3945
modprobe iwl3945 disable_hw_scan=1
```

Run that command and wait a few seconds and see if you can connect again, and post your results.

Also, you may want to start a new thread, since I think your issue doesn't have to do with the original poster's problem, other than being related to the iwl drivers.  If you start a new thread, let us know the URL.

@Ihaveaproblem: sorry, but I'm out of suggestions for your issue.  I hope someone else will still be able to think of why you can't get your LED to turn off, though, or that it will be fixed in Intrepid.

Still no Wifi, Wifi Light or Signal.
Moved my problem to New Post: **dell 1525 laptop & iwl3945 nightmare**


thanks anyway.

---

