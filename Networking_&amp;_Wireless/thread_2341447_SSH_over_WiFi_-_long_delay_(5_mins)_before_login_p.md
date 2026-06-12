---
title: "SSH over WiFi - long delay (5 mins) before login possible"
date: 2016-10-28
forum: Networking &amp; Wireless
---

### Post by litening on 2016-10-28
Hi,

Im running Ubuntu server 16.04.1 LTS on an Intel NUC. I've configured my network settings with the help of network manager (nmcli). Everything seems to be working fine:

When I disconnect my ethernet the wifi takes over. If I connect ethernet that takes over etc.

My only problem is: when booting without ethernet (with only wifi) it takes around 5 minutes for SSH to start working. I can ping the computer instantly but SSH gives me "connection refused". After five minutes SSH starts working. If the ethernet cable has been connected after (or on) reboot then SSH over wifi (once ethernet is disconnected) works instantaneously. 

Anyone has any idea what the problem could be?

Thanks in advance.

---

### Post by TheFu on 2016-10-28
Name resolution or perhaps network manager doesn't automatically connect as quickly as you like?  Do all the machines know how to find each other regardless of the type of connection?  For example, I use DHCP reservations for my laptop - 1 for wired and a different 1 for wifi ... that is means the machine has two different hostnames on my home network.  cc3350 and cc3350w ... I don't use network-manager (actually purge it from the system) to manage networking. My networks are a little more complicated than most people's.

As a test, try pinging the machine. If ping can't figure out where the IP is, then ssh won't either.

You can also increase the verbose-ness of the ssh client and server.  **ssh -vvv server** to see what the issue is. Sometimes it is due to failures to negotiate a good encryption method.

And welcome to the forums.

---

### Post by litening on 2016-11-09
Hi,

Sorry for late reply. Ping works almost instantly. SSH takes 5-10 minutes. sshd is not listening on the port, I can't connect to the port with ssh or telnet.

This would be easier to solve if I had terminal access to the machine, but I haven't.

Any other tips? Make a script that restarts sshd when network interface changes are detected? Are there any sshd logs I could view?

---

### Post by litening on 2016-11-09
Solved it!

Changed [COLOR=#1D2129][FONT=San Francisco]TimeoutStartSec=5min to "1sec" in /etc/systemd/system/network-online.target.wants/networking.service.

My system was delaying boot with five minutes.[/FONT][/COLOR]

---

### Post by TheFu on 2016-11-09
Great!

a) Please mark the thread as SOLVED - "thread tools" above. It will be very helpful to others, since this is the 1st time I've heard that one in almost 25 yrs doing this stuff.

b) My only systemd box has that same setting - "5min", but I don't see this issue.  [https://www.freedesktop.org/software/systemd/man/systemd.service.html](https://www.freedesktop.org/software/systemd/man/systemd.service.html) has this:
> TimeoutStartSec=

    Configures the time to wait for start-up. If a daemon service does not signal start-up completion within the configured time, the service will be considered failed and will be shut down again. Takes a unit-less value in seconds, or a time span value such as "5min 20s". Pass "infinity" to disable the timeout logic. Defaults to DefaultTimeoutStartSec= from the manager configuration file, except when Type=oneshot is used, in which case the timeout is disabled by default (see systemd-system.conf(5)). 
So lowering it to 1 sec probably isn't really desirable.  OTOH, it is systemd and surprising whenever things WORK as expected.

---

