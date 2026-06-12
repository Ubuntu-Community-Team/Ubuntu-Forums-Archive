---
title: "Hardy loses wireless on T60 after SLEEP."
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by bliffle on 2008-08-17
When Hardy (8.04) was released I had Gutsy (7.10) working well on two laptops: Thinkpad T40 and thinkpad T60. I installed Hardy on the T60 to test it out, but wireless wouldn't work at all. With some help on this forum I got it working.

But now I have a problem when I go into SLEEP mode. When I re-awaken the computer it will do 2 or 3 network accesses and then quit. I tried the usual stunts of Disabling Network and Disabling Wireless, <Fn><F5>, etc., and it just won't come back.

I have to restart the Hardy to get wireless working again.

However, if I do HIBERNATE instead of sleep, then the wireless works fine. In fact, if I do a HIBERNATE after it becomes non-communicative upon re-awakening, it comes back, too!

Something is getting re-initialized, but I don't know what, or how to do it manually without a HIBERNATE.

Any ideas?

---

### Post by pytheas22 on 2008-08-17
Probably reinserting the driver after waking up would make the card work.  To figure out which driver you have, please post the output of:
```

lshw -C Network
```

Then we can write a script to reinsert the driver automatically when you wake the machine up.

---

### Post by bliffle on 2008-08-18
I went straight into HIBERNATE but couldn't get the network running when I awakened the system later.

Here's the lshw after I did a RESTART:

```

john@JHT60:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:4b:2b:28
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.3 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
john@JHT60:~$ 

```

Next time I'll do it while the net isn't working.

---

### Post by pytheas22 on 2008-08-18
Thanks for the information.  You're using the iwl3945 driver.  The next time you resume your machine from hibernate or suspend and the wireless isn't working, please run these commands:
```

sudo rmmod iwl3945
sudo modprobe iwl3945
sudo ifconfig eth1 up
```

and let me know if that fixes it.  If so, you can write a script to run those commands automatically whenever the machine wakes up.

---

### Post by bliffle on 2008-08-19
Thanks for the info.

Should I NOT be using the iwl3945 driver? 

I didn't make any conscious attempt to use iwl3945, but the T60 does have a 3945 in it. Altho I may install an Atheros since many people say they work better and further. So I suppose I'd have to change drivers then.

---

### Post by pytheas22 on 2008-08-19
iwl3945 is what you should be using...it's the native Linux driver for your wireless card, which has an Intel chipset.  There are other drivers (ipw, which is an older Intel Linux driver, or ndiswrapper, which lets you drive the card with Windows drivers) but iwl3945 is best and is used by default in Ubuntu 8.04.  The Atheros drivers (madwifi, ath5k, ath9k) are only for cards with Atheros chipsets, not Intel, so don't use an Atheros driver or it won't work.

I think that the reason you have issues with wireless after suspend/hibernate is because there's a problem waking the iwl3945 module back up--this happens with a lot of wireless cards and is not a big deal.  If that's what's happening, we can apply a simple workaround.  But in order to make sure that the iwl3945 module is really the issue here, please run these commands the next time you wake the computer back up and wireless doesn't work:
```

sudo rmmod iwl3945
sudo modprobe iwl3945
sudo ifconfig eth1 up
```

---

### Post by garethrichardadams on 2008-12-19
Hi,

I've had the same problem on my Acer Travelmate 2410. It uses an Atheros wireless card so the following commands fixed it for me:

sudo rmmod ath_pci
sudo modprobe ath_pci

I'm using Intrepid Ibex - can you help me write a script to run on wakeup? I'm a complete beginner so I'll need basic instructions I'm afraid...

Thanks

Gareth

---

### Post by pytheas22 on 2008-12-19
> I'm using Intrepid Ibex - can you help me write a script to run on wakeup? I'm a complete beginner so I'll need basic instructions I'm afraid...

Sure.  First, type this command:
```

gedit /etc/acpi/resume.sh
```

A file should open up (it's a script that gets run whenever your computer wakes back up from suspend).  Add these lines to the end of the file:
```

rmmod ath_pci
modprobe ath_pci
```

Then save and close the file and reboot your computer.  After it boots back up, suspend it, then wake it up again, and see if your wireless works automatically after the resume.  Does this work?  If not, we may need to try a few different things, but it shouldn't be too hard to get this working.

---

### Post by garethrichardadams on 2008-12-19
Hi,

No, that doesn't seem to work. I realised I'd missed out: sudo ifconfig ath0 up but that didn't help either. It seems to be executing the script as it managed to disable the wifi (usually it just keeps trying to reconnect and fails)

Does the script automatically run as root or should I put sudo into there?

Is there a way to put a delay in the script - I wonder if there needs to be a pause to allow the wifi to power up??

Thanks

Gareth

---

### Post by pytheas22 on 2008-12-19
Sorry that didn't quite do it.

> 
Does the script automatically run as root or should I put sudo into there?


The script should be running as root, but putting sudo in won't hurt anything, so you can try.

> 
Is there a way to put a delay in the script - I wonder if there needs to be a pause to allow the wifi to power up??

Yes; you can use the 'sleep' command.  Just type 'sleep' followed by the number of seconds that you want it to pause for; for example, to make the machine wait five seconds before running the modprobe commands, you would make it look like this:
```

sleep 5
rmmod ath_pci
modprobe ath_pci
ifconfig ath0 up
```

Also, in order to really make sure that this script is running, you may want to add this line to the bottom of it:
```

touch ~/Desktop/SCRIPT-RAN
```

If the script runs, it will create a blank file on your desktop called 'SCRIPT-RAN'.  You can do this once just to verify that the script is definitely running all the way through.

Let me know whether this leads to a solution...

---

### Post by garethrichardadams on 2008-12-20
Hi,

No, the script doesn't seem to be running at all, The entire script is shown below but no files are created on the desktop...

```
#!/bin/sh

touch ~/Desktop/SCRIPT-RAN1

test -f /usr/share/acpi-support/key-constants || exit 0

touch ~/Desktop/SCRIPT-RAN2

# Source from /etc/acpi/resume.d/
for SCRIPT in /etc/acpi/resume.d/*.sh; do
    if [ -x $SCRIPT ] ; then
        . $SCRIPT
    fi
done

sleep 5

sudo rmmod ath_pci
sudo modprobe ath_pci
sudo ifconfig ath0 up

touch ~/Desktop/SCRIPT-RAN3
```

---

### Post by pytheas22 on 2008-12-20
The reason it isn't working is that the /etc/apci stuff is now apparently deprecated, and the scripts there no longer do anything, according to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/205005").

In order to add the commands to the right script, please type:
```

sudo gedit /usr/lib/pm-utils/sleep.d/50modules
```

A script should open up.  Add your commands to the very bottom of it, save it and give it a try.

This is not the cleanest solution, but to be honest I don't really understand how the new resume scripts are supposed to work and can't find much documentation on them, but this should at least get the job done.

Also, for the command to test whether the script really ran, use this:
```

touch /home/YOUR-USER-NAME/Desktop/SCRIPT-RAN
```

If you just have 'touch ~/Desktop' it won't work, because the script is being run as root, and root doesn't have a Desktop...but the script wasn't running before anyway so this was irrelevant.

---

