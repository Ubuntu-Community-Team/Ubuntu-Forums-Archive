---
title: "No dhcpoffers recieved"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by hdensley on 2007-06-24
I'm about to throw in the towel, and possibly the computer.  I've had a rough row with Ubuntu 7.04 with major networking issues, both wired and wireless.  Currently I cannot connect to the internet at all, even with a fresh install, via a wired network.

When I run /etc/init.d/networking restart, all I get is 'no dhcpoffers recieved' can anybody assist - for lack of detailed networking knowledge, should I be using another linux distro?

:(

---

### Post by a1unix529 on 2007-06-24
Can you, please, post the output of the command line:
```
sudo /etc/init.d/networking restart
```I have the same issue.

Mine looks like this:
```
user@computer:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6043
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/ *# MAC address snipped!*
Sending on   LPF/wlan0/ *# MAC address snipped!*
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.254 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/ *# MAC address snipped!*
Sending on   LPF/wlan0/ *# MAC address snipped!*
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
user@computer:~$

```

---

### Post by kevdog on 2007-06-24
Either of you with this problem please post the output of 
dmesg

You may need to upload this as a file attachment.

---

### Post by hdensley on 2007-06-25
Attachment includes both dmesg and /etc/init.d/networking restart output.

Here's what else I can tell you about my problem
1) For some reason, ethernet is working this morning
2) Yesterday, both wired and wireless flaked out, I had wireless a few installs ago, and it worked after much effort, at one point in time
3) Wireless is Belkin F5D7000

Thanks for your help

---

### Post by hdensley on 2007-06-25
attachment, as per above.  Had to ZIP due to forum size limitations

---

### Post by Julolidine on 2007-06-25
For whatever reason if I do

```
sudo ifdown wlan0
sudo rm /var/run/dhclient.wlan0.pid
sudo ifup wlan0

```

Everything works, otherwise, I receive no DHCP offers.  Maybe somebody can help out.  I think its another process thats not properly cleaning up after itself.

---

### Post by hdensley on 2007-06-25
I think you're onto something... I think I see something about a PID in an error message (etc/... restart) that there's already a PID

---

### Post by a1unix529 on 2007-06-25
> **Julolidine said:**
> For whatever reason if I do

```
sudo ifdown wlan0
sudo rm /var/run/dhclient.wlan0.pid
sudo ifup wlan0

```Everything works, otherwise, I receive no DHCP offers.  Maybe somebody can help out.  I think its another process thats not properly cleaning up after itself.
This works for me as well! Finally! Yes! Woohoo!

So why is that file the culprit here?

Is this a bug in dhclient?

EDIT: Nevermind, it worked once but not anymore. I must have done something different this time. Does it still work for you?

---

### Post by hdensley on 2007-06-26
I might resort to Fedora 7, it's a lesser sin than Windows.  It's a real shame that Ubuntu doesn't have more stable networking.  If anyone figures this problem out, please post!

---

### Post by dgifford on 2007-06-27
i get this on wired (eth0) as well, no joy on dhcp.

looking for any work arounds

---

