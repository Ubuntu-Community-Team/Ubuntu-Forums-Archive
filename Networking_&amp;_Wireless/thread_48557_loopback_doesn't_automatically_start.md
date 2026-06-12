---
title: "loopback doesn't automatically start"
date: 2005-07-13
forum: Networking &amp; Wireless
---

### Post by fizgig on 2005-07-13
Anyone know why I have to execute **sudo ifup lo** every time I start to get the loopback interface up?

Here's my /etc/network/interfaces in case it's useful (I don't understand what it means)

# The loopback network interface
auto lo
iface lo inet loopback

Thanks!

---

### Post by varunus on 2005-07-13
Next time you reboot, try running "sudo /etc/init.d/networking restart" in a terminal.

Does this do the same thing?  If it does, then your startup scripts are having problems.

---

### Post by fizgig on 2005-07-13
Even if you don't know exactly what's wrong, any information you can provide about the script that should bring lo up (like, what's its name and location is) would be helpful in my quest.

edit: Wow that was weird!  Guess we entered our posts at the same time.  I'll give your suggestion a shot when I get home.

---

### Post by varunus on 2005-07-13
Haha, that's what I just did...guess we posted at the same time.

/etc/init.d/networking is supposed to bring up lo.

---

### Post by fizgig on 2005-07-14
OK.  What I was doing wrong was hitting ctrl-C during the "Configuring network interfaces" step.  I always did this before and I'd have eth0 and wlan0 come up just fine but I guess lo doesn't come up if I do that.

Bummer.  I hate waiting during that step but I guess I need to if I want lo to come up.

---

### Post by gruepig on 2005-07-14
Why are you hitting control-C during boot?  Is it because /etc/init.d/networking is taking a long time to run?  What is in your /etc/network/interfaces file?  Specifically, which interfaces have 'auto' lines (that is, which interfaces should be brought up automatically on boot)?  It sounds like you might be having a problem with one of those interfaces.  One way you could test this would be to comment out auto lines (but not the one for the loopback interface) and see if your boot time (or the time to run '/etc/init.d/networking restart') is still slow.  Also, try bringing up your interfaces manually one at a time ('ifup eth0', 'ifup eth0', etc.) and check for errors (either on the console or in the logs).

---

### Post by fizgig on 2005-07-14
Yeah, I'm hitting Ctrl-C because it's taking a long time to run the networking script and it didn't seem to have any adverse effects until now.

I'm pretty sure I have eth0 in the auto line of my networking file. I didn't know that meant it brought it up automatically - as obvious as it sounds now. As soon as I get home I'll edit the file and see what happens. I'll report back here.

edit:
I first removed eth0 from the auto line but that didn't make a difference - bootup still took a long time at the networking config step.

So, I next commented out the **iface eth0 inet dhcp **line and that made the difference.

---

### Post by vinceb on 2005-07-23
I've been getting the same issue and it appears to be knocking on in other services. The loopback doesn't come up. I can bring it up manually but when I do I get:

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I've only really discovered it trying to track down cups problems. Bizarrely my wireless card using ndiswrapper is working fine (although it isn't coming up automatically either). I've tried:

sudo /etc/init.d/networking restart

And I got a message saying fail. I don't seem to get any useful clues in /var/log/messages (should I be looking somewhere else)

Any Ideas? SHould I be starting a new post for this?

CHeers

Vince

---

### Post by kkass on 2005-08-29
Hi I am having a similar problem which seemed to occur suddenly.

**Background:**
My networking worked fine as of Thursday Aug 18th, and I installed NFS Kernel Server, TFTP Server, and DHCP Server for a work project on my laptop.  These all worked correctly thursday.

Thursday evening when i powered up my laptop, I started noticing some odd behavior.  Most notably that Firefox took up to 5 minutes to start.  I did not look into the issue.

Friday morning when I powered the system up I realized NFS was not working.  (The kernel service fails during startup, and will not start after the system is running.)  After several hours of research and attempts to debug the problem, I happened to notice that my loopback interface was missing from the ifconfig output.

I issued the command 'sudo ifconfig lo up' and it comes up, but without an assigned address.  I then issued the command 'sudo ifconfig lo 127.0.0.1 netmask 255.0.0.0'.  Now the loopback adapter is up with an address.

Once the loopback adapter is fixed the NFS kernel service properly starts, and Firefox no longer takes 5 minutes to start.

**Current Issue:**
When the system boots, the loopback interface does not come up.  If I issue the command 'sudo ifconfig lo 127.0.0.1 netmask 255.0.0.0', it comes up.

If I instead issue the command 'sudo ifup lo', it fails with the following error:
```
/etc/network/interfaces:19: too few parameters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

If I instead attempt to restart the networking service, it fails.
```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                     [fail]
```

**Reference:**

```
$ ls -l /etc/network/interfaces
-rw-r--r--  1 root root 534 2005-08-26 15:02 /etc/network/interfaces


$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
address 192.168.50.172
netmask 255.255.255.0

iface wlan0 inet
address 10.10.12.172
netmask 255.255.0.0

auto eth0

$ cat /etc/iftab
# This file assigns persistent names to network interfaces.  See iftab(5).
eth0 mac 00:0d:56:eb:fe:29

$ cat /etc/network/ifstate  ## This is empty

```

---

