---
title: "SSH when using wifi and not ethernet cable"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2013-09-05
For the sake of clarity, I have a computer (Ubuntu 12.04LTS) and a Raspberry PI. I call the comptuer, computer and the PI, a PI.

I have a Raspberry PI. To config it, I have to use ssh into the raspi-config.

And I cannot seem to find a way to get to:

192.168.0.101:8891 (tvheadend webgui)

but 192.168.0.101:8892 does come up on my computer.

is there a way to make the PI talk to my ubuntu 12.04 via wifi? Or can this computer, which itself has only 'net access via wifi make a network connection to the PI. Either wirelessly or by ethernet cable. 

Currently the PI has both a wifi adapter (known working) and it's ethenet port connects to a router. (It's a wifi router, but the wifi part is turned off).

When the PI has an ethernet cable, RaspBMC cannot find a networking MAC address. It find an IP, GW and DNS server however. If the cable connecting the router to the PI is removed, the

---

### Post by ian-weisser on 2013-09-06
The problem you describe seems to be on the PI's end.
Are you able to ssh into the PI wirelessly? Your post is unclear.

Is the application really using port 8891 on the PI?
Have you used the command **netstat -tulpn** on the pi to verify that the application is really using port 8891 (not some other application)?
Have you checked the firewall on the PI to ensure port 8891 is not being blocked?

---

### Post by Mark_in_Hollywood on 2013-09-06
"The problem you describe seems to be on the PI's end.

Are you able to ssh into the PI wirelessly? Your post is unclear.

[COLOR="#FF0000"]Answer: I cannot get into the PI via wifi that I know of. That is, I'm not enough of a computer geek to understand what to do.[/COLOR]

Is the application really using port 8891 on the PI?

[COLOR="#FF0000"]Answer #2: Yes, if I have the ethernet cable run between a router, this computer (for a webgui) and the PI, I can see some of 8891. (technically: 192.168.0.1:8891
[/COLOR]
Have you used the command netstat -tulpn on the pi to verify that the application is really using port 8891 (not some other application)?

[COLOR="#FF0000"]Answer #3 RaspBMC has no user interface (terminal emulator or terminal in Ubuntu speak) to commandline: netsate -tulpn.[/COLOR]

Have you checked the firewall on the PI to ensure port 8891 is not being blocked?

[COLOR="#FF0000"]Answer #3: is there a firewall? No. that has been turned off.[/COLOR]

---

### Post by ian-weisser on 2013-09-07
> **Mark_in_Hollywood said:**
> Are you able to ssh into the PI wirelessly? Your post is unclear.

[COLOR=#FF0000]Answer: I cannot get into the PI via wifi that I know of. That is, I'm not enough of a computer geek to understand what to do.[/COLOR]

So the PI cannot be used or connected to *at all* using wifi?
If true, then my check would be the wifi hardware connections. Perhaps it is not getting power, or has a hardware defect.

You are able to ssh into the PI using the ethernet cable?
If so, what OS is installed?
In that OS, when you check for hardware is the wifi detected? (equivalent to the **lshw** or **lspci** or **lsusb** commands in Ubuntu)
If detected, does the wifi connect to your router or gateway? (equivalent to the **ifconfig** command in Ubuntu)

---

