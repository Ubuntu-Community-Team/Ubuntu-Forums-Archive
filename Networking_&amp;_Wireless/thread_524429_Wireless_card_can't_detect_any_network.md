---
title: "Wireless card can't detect any network"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by rikkeb on 2007-08-13
I have a problem with the wireless on my laptop an Acer Travelmate 292 LMi, with a Intel Pro / Wireless 2200BG card. I have been using the Wicd networkmanager, but the problem also occured with the default KNetworkManger in Kubuntu. I tried following the steps in the thread

[http://ubuntuforums.org/showthread.php?t=517228](http://ubuntuforums.org/showthread.php?t=517228)

But got stuck at the end, the difference being, that my laptop doesn't have a "push-button" to turn on the wireless, but a slider on the side. First the acerhk seemed promising, but I guess i ran into the problem stated on [www.cakey.de/acerhk/](www.cakey.de/acerhk/), saying that:

> The newer Travelmate series (starting with 290, 530, 650, 800) aren't supported very well, since Acer uses different hardware. 

If anyone could help me, I would be very thankful.

/ Rikke

---

### Post by moore.bryan on 2007-08-13
*what exactly is your problem?  can you connect sometimes/not all the time?  can you peruse connected computers but not acces the net?  more info, please!  ;-)*

---

### Post by noob12 on 2007-08-13
[COLOR="Red"]UPDATE 9/3/2007:  The meat of this thread has been converted to a HOWTO here: [http://ubuntuforums.org/showthread.php?t=541953](http://ubuntuforums.org/showthread.php?t=541953)[/COLOR]


As I understand from your post on the other thread, you are having a problem with an ipw2200 always seeing the RF kill switch on (radio off), and you are on the Acer 292.

First ** make sure the BIOS settings have wireless enabled and your hardware switch is in the wireless ON position**:

NOTE:  This assumes you installed the acerhk module following the instructions in the other thread.

Then try this sequence:
```

sudo /etc/init.d/networking stop
sudo modprobe -r ipw2200
sudo modprobe -r acerhk
sudo modprobe acerhk force_series=290 usedritek=1 verbose=1
echo 1 | sudo tee /proc/driver/acerhk/wirelessled
sudo modprobe ipw2200 led=1
sudo /etc/init.d/networking start

```
If this works (for the rf-kill-switch problem), let me know and I can tell you how to set the right flags at boot-time.

This tip is based on info from [http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix) which is referenced from links on the ipw driver sites on sourceforge.

I'll try to start a HOWTO for acerhk on ubuntu based on the other thread, but not having one of these laptops myself, I'm flying blind.

---

### Post by rikkeb on 2007-08-14
Thanks, it works! Now turning on and off the switch actually has an effect, although it takes a bit of time to execute the last line

```
sudo /etc/init.d/networking start
```

This is the output written on screen when executing all the lines as a bashscript:

```
rikkeb@rikkeb:~$ ./wireless.sh
 * Deconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5746
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:02:3f:19:86:cd
Sending on   LPF/eth0/00:02:3f:19:86:cd
Sending on   Socket/fallback
                                                                         [ OK ]
1
 * Configuring network interfaces...                                            There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:02:3f:19:86:cd
Sending on   LPF/eth0/00:02:3f:19:86:cd
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ OK ]

```

The place where it says sleeping, it actually sleeps for about 15 seconds. To me it seems as if it is doing a lot of unnessecary things, since my wireless network is eth1, and all it mentions is eth0 and eth2.

But thank you so much, just getting it to work is great.

/ Rikke

---

### Post by noob12 on 2007-08-14
OK.  That was just to test what things we might need to do to get things working.   You do not have to write a script to do this. You can set this up to run at boot while the modules are loading initially.

The long time to start networking and the many error lines about devices not existing is because you have these interfaces all specified in /etc/network/interfaces, but some of them don't actually exist.  You will want to take out the stanzas for all of the interfaces you don't actually have: eth2, ath0, wlan0.  You have only  lo (the loopback interface), eth0 and eth1, and if you put these in roaming mode in the NetworkManager, they will be removed from /etc/network/interfaces as well.  I would suggest that you do put the wireless interface in roaming mode.  If you are not always plugged in with eth0, I would put that in roaming mode as well.

Let's get back to finishing your rf-kill-switch setup properly.  The script should not be needed.

**Load ipw2200 with led=1 option**

This process will lead you through a few reboots so that we will eliminate things you do not need. I suspect in your situation you may only need the led=1 option on the ipw2200 module.

```

xhost +
sudo gedit /etc/modules

```

This will bring up the file /etc/modules in the text editor gedit.  See if you have a line that says **acerhk** here.  If so please remove that line, save and exit.  If you don't have an acerhk line, you can just exit without saving.

```

echo "options ipw2200 led=1" | sudo tee -a /etc/modprobe.d/options

```
This tells the system to load ipw2200 with the led=1 option when it normally loads.

[COLOR="Red"]EDIT 8/15/2007 15:41 UTC:[/COLOR] I'm not sure this is necessary, but with this device being an ethernet device on the pci bus, it may be getting initialized in initrd.  So do this as well.
```

sudo update-initramfs -u

```

Now reboot.  Don't run your special script.  Just reboot and see if wireless works.  If it does you are done.  This means you don't need acerhk and things should continue to work this way for you.  Please let me know. 

**Setting up acerhk to load at boot with your options**

If the wireless didn't work when you tried the preceding test without acerhk, follow these steps to add the acerhk module.

Note that this is a similar command but is a different file from the previous one.  So copy and paste from the box below.  Also, this assumes that you removed all lines for acerhk from the /etc/modules file in the earlier step.
```

echo "acerhk force_series=290 usedritek=1" | sudo tee -a /etc/modules

```

Reboot.  See if things work.  If so, you are done.  Let me know you didn't need the final step.
Otherwise proceed to the last step.

**Setting the wirelessled state manually via procfs at boot**

```

xhost +
sudo gedit /etc/init.d/acerhkwireless

```
Put the following content verbatim in this file
```

#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          acerhkwireless
# Required-Start:    mountkernfs $local_fs
# Required-Stop:    $local_fs
# Default-Start:     S
# Default-Stop:      0 6
### END INIT INFO
case "$1" in
start|restart|force-reload)
    /bin/echo "1"  > /proc/driver/acerhk/wirelessled
    ;;
stop)
   /bin/echo "0"  > /proc/driver/acerhk/wirelessled
   ;;
*)
   echo "Usage: /etc/init.d/acerhkwireless start|stop|restart|force-reload"
   exit 1
   ;;
esac

exit 0

```

Save the file and exit.  Then run

```

sudo chmod a+x /etc/init.d/acerhkwireless
sudo ln -s /etc/init.d/acerhkwireless /etc/rcS.d/S39acerhkwireless

```

Now reboot.   This script will normally run before networking.  If you always intend to keep the wireless in roaming mode, a much simpler approach is possible:  just edit the file /etc/rc.local and put the command **echo 1 > /proc/driver/acerhk/wirelessled** somewhere in that script.

Please let me know how all this goes.

---

### Post by rikkeb on 2007-08-17
Hi

I had to go all the way through all the steps, but now it's working :). The only "weird" thing was with the 
```
xhost +
```
I got 
```
access control disabled, clients can connect from any host
```
but everything works all the same. 

Thank you so much, Rikke

---

### Post by noob12 on 2007-08-17
Great to hear  rikkeb.  Thanks for the feedback.

The message about the access control was the expected output after the **xhost +**.   [Explanation for the curious: I've had trouble when I instruct users to use gksudo and variants before editing a root-owned file; gksudo doesn't always work.  Rather than rathole on X access control issues, I now just tell them to disable access control on their X server before the regular sudo using **xhost +**.  This lasts for the X session; it's reenabled next time you login.  You can reenable access control with **xhost -** if you want. By default your X server is only listening on loopback and typically users are on single-user machines, so it isn't a big issue.]

I still believe you may be able to do without the **acerhkwireless** boot script I provided. If you again edit the /etc/modules file using those commands and you add the option **autowlan=1** to the acerhk line, you may find that you no longer need to use that (acerhkwireless) boot script.  It would be useful to know before I write a HOWTO, but I expect some reader will eventually tell me; you are probably tired of experimenting.

---

### Post by rikkeb on 2007-08-18
Hi again.

I'm just greatful that you are putting this much work into this. So I removed the symbolic link to the acerhkwireless script and added the option to /etc/modules, so it now looks like this

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2

acerhk force_series=290 usedritek=1 autowlan=1

```

Unfortunately that didn't work. After rebooting the wireless wasn't working, and the switch on the side of my computer didn't work.

If you have more ideas, just let me now, and I'll try them out.

/ Rikke

---

### Post by noob12 on 2007-08-18
OK.  Thank you.  That's very useful feedback.  It sounds like we've found that the minimial solution for your laptop requires all three of the steps in the earlier guide posting.  I will be writing a HOWTO based on this for other users with a similar laptop after I return to the forum in about a week.  In the meantime, users who stumble on this can use all three steps in _[posting #5 ]("http://ubuntuforums.org/showpost.php?p=3188388&postcount=5")_ on this thread after following the instructions for building the acerhk module in _[the other thread]("http://ubuntuforums.org/showthread.php?t=517228.")  _

---

