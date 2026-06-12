---
title: "Wireless wake on lan (WOL) works in XP but not Ubuntu Edgy ?"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by Glenn Coombs on 2007-04-16
Hi,

I've just installed Ubuntu Edgy on my new laptop (a Dell Inspiron 9400) and the only thing I can't get to work is the wake on lan (WOL) functionality.  The laptop is using the intel wireless 3945 chipset to connect wirelessly and I know that the hardware is okay because it works under XP on the same machine.

Under XP I just select the NIC in the device manager and tick the box labelled "Allow this device to bring the computer out of sleep mode" on the power management tab.  Then, so long as the laptop is running on AC power I can put it into sleep mode (power light pulses periodically) and it can be woken up using etherwake on another computer.

Is this possible in Ubuntu Edgy ?  I see that for wired ethernet NICs you have to run "ethtool -s eth0 wol g" to enable the WOL functionality before shutting down.  Is there something similar I can run that will work for eth1 (my wireless interface) ?  Or is this something that just isn't supported in the current ipw3945 drivers ?  Anybody know if it is addressed in the Feisty release ?

The reason I really want to get WOL working is because I run SlimServer on my laptop to drive my SlimDevices Squeezebox downstairs and it is a right pain having to run upstairs and reboot the laptop every time you want to listen to some music.  If the last time I used the laptop was in XP then the Squeezebox just wakes it up and starts playing music in less than 5 seconds.  If the last time I used the laptop was in Ubuntu however...

---

### Post by StewD on 2007-04-24
Discovered my initial questions...and hopefully more! are answered in:

[http://ubuntuforums.org/showthread.php?t=360901&highlight=ethtool](http://ubuntuforums.org/showthread.php?t=360901&highlight=ethtool)

(HOW TO: power on remotely with WakeOnLan (WOL))

Worth a read!!

Stewart

---

### Post by Glenn Coombs on 2007-04-28
Yes, I have already seen that article.  It talks about using the "ethtool -s eth0 wol g" command to enable wol for a particular device.  I have successfully used that on a desktop machine but on my laptop it doesn't work.  If I run "ethtool -s eth1 wol g" it says:

Cannot get current wake-on-lan settings: Operation not supported
  not setting wol

Even running "ethtool eth1" only prints:

Settings for eth1:
        Link detected: yes

which makes me suspect that ethtool doesn't really work that well with wireless devices like the intel 3945 chipset.  Has anyone figured out the appropriate magic incantations to get this to work yet ?

---

### Post by p2im0 on 2007-05-14
I know this may seem farr too obvious but you are using "sudo" correct?

Forgive me, I had to ask.

---

### Post by Glenn Coombs on 2007-05-16
Yes, I am running all my commands as root so it is not a permissions problem.

---

