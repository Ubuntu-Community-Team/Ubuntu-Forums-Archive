---
title: "Setting Ubuntu to Full Duplex Mode"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by riverkarl on 2007-09-01
I know there have been several posts on here concerning this question, but I still can't seem to solve this problem.  I recently installed Ubuntu on one of my pc's and for some reason it automatically sets my NIC to half duplex mode. I know this computer is capable of full-duplex mode because I dual boot XP which sets it to full. Another note on this is that I don't have a graphical start up screen, and as  a result I am able see the boot up command line process as it happens and I noticed that this half-duplex mode thing is something that is set right from boot.

Any help I can get with this would be much appreciated.

---

### Post by noob12 on 2007-09-01
It's not clear what you've tried so far.  The thing is that you have to override/turn off autonegotiation, and as a result you should also set both speed and duplex and turn autonegotiation off in one swoop.  

Assuming your device is eth0 and the link will support 100mbps full duplex, this would be the command.
```

sudo ethtool -s eth0 speed 100 duplex full autoneg off

```


Putting this in your /etc/network/interfaces in the **iface** stanza for eth0 would make it run just before bringing up the interface each time.
```

pre-up /usr/sbin/ethtool -s eth0 speed 100 duplex full autoneg off

```

---

### Post by riverkarl on 2007-09-02
I tried the "sudo ethtool -s eth0 speed 100 duplex full autoneg off" command in terminal and nothing happened. I checked my connection information and it still says its running at 10mbps.

"Putting this in your /etc/network/interfaces in the iface stanza for eth0 would make it run just before bringing up the interface each time.
Code:

pre-up /usr/sbin/ethtool -s eth0 speed 100 duplex full autoneg off"

I wanted to try this as well, but I couldn't figure out exactly where you wanted that code placed when you said "iface stanza."

---

### Post by anjilslaire on 2007-09-02
Try the following, It's what I use:
create a script as follows:

[I]$ sudo vi /etc/init.d/100Mbs
Append following lines:
#!/bin/sh
ETHTOOL="/usr/sbin/ethtool"
DEV="eth0"
SPEED="100 duplex full autoneg off"
case "$1" in
start)
echo -n "Setting eth0 speed 100 duplex full...";
$ETHTOOL -s $DEV speed $SPEED;
echo " done.";;
stop)
;;
esac
exit 0[/I]

Save and close the file. Setup executable permission:
# chmod +x /etc/init.d/100MbsOR$ sudo chmod +x /etc/init.d/100Mbs

Now run script when Ubuntu Linux boots up. Use update-rc.d command install System-V style init script links:
# sudo update-rc.d 100Mbs defaultsOutput:

 Adding system startup for /etc/init.d/100Mbs ...
   /etc/rc0.d/K20100Mbs -> ../init.d/100Mbs
   /etc/rc1.d/K20100Mbs -> ../init.d/100Mbs
   /etc/rc6.d/K20100Mbs -> ../init.d/100Mbs
   /etc/rc2.d/S20100Mbs -> ../init.d/100Mbs
   /etc/rc3.d/S20100Mbs -> ../init.d/100Mbs
   /etc/rc4.d/S20100Mbs -> ../init.d/100Mbs
   /etc/rc5.d/S20100Mbs -> ../init.d/100Mbs

Reboot the system to take effect or just type scrit name:
$ sudo /etc/init.d/100Mbs start

---

### Post by noob12 on 2007-09-02
Are you sure the other side of the link (the switch or hub into which you are plugging your Ubuntu host) supports 100mbps?  

You want to achieve the desired situation manually, then set it to be automated.

You can read **man interfaces** for a description of the structure of the /etc/network/interfaces file.

Here's a stanza that assumes many things: eth0 is the interface, that you want it brought up automatically at boot, that it is configured with an address via dhcp and that you want to run this pre-up command.  But I expect you can generalize to analogous things from that:

```

auto eth0
iface eth0 inet dhcp
pre-up /usr/sbin/ethtool -s eth0 speed 100 duplex full autoneg off

```

---

### Post by riverkarl on 2007-09-02
Thanks for the responses guys.

Anjilslaire, I created the script like you told me. When I run " sudo /etc/init.d/100Mbs start" the response I get from the terminal goes as follows:  Setting eth0 speed 100 duplex full... done. But I know my NIC hasn't actually been set to these settings for the following reasons: The indicator light on my router is still showing me orange (10mbs) rather than green (100mbs), when I look at my connection information in Ubuntu it tells me eth0 is still running at 10mbs. 

I have also noticed that even while my computer is being restarted and put through bios mode, the  indicator light on my router is still showing me orange (10mbs) for this computer. But if I boot into XP it is switched to green. 

What are my options now?

---

### Post by riverkarl on 2007-09-02
Okay, I fixed it. I decided to switch out my ethernet card for a newer d-link one I had stored away. Problem must have been something to do with the default settings of the ethernet card. Thanks for the help!

---

