---
title: "No network connectivity on reboot"
date: 2016-08-16
forum: Networking &amp; Wireless
---

### Post by John Chambers on 2016-08-16
I've been trying to fix the setup of a new Ubuntu server box, and one problem is that when it's rebooted, it comes up with no network connectivity.  I've done a lot of googling, and the result is a lot of confusion.  Is there somewhere a coherent description of the "latest, greatest" setup stuff.

One problem is that we can't even convince ourselves that we know what release of Ubuntu is on the box.  Typing "uname -a" gives:

Linux kendy 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

However, nearly all the docs use OS version numbers starting with "16-".  We suspect it's 16-4 (or maybe 16-6?), but nowhere do we find anything that gives a 16-* number.  What are we missing?  Where is this documented?

Also, ifconfig gives the result for the known ethernet port (en01):

```
eno1      Link encap:Ethernet  HWaddr 00:1f:c6:9b:c6:a4
          inet addr:10.0.1.107  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe9b:c6a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104079 errors:0 dropped:1 overruns:0 frame:0
          TX packets:93976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22393411 (22.3 MB)  TX bytes:34647244 (34.6 MB)
          Interrupt:16 Memory:dc200000-dc220000

```
One thing that looks wrong is that the /etc/network/interfaces file says:

```
iface eno1 inet static
	address 10.0.1.17/8
	gateway 10.0.1.1
```

That's not the address that ifconfig shows, and "ls -lu" shows that /etc/network/interfaces wasn't read after the reboot.  So, despite all the helpful docs saying to put the info in /etc/network/interfaces, that info is apparently not used during a boot.  Or is it?  I discovered the "ip address" command, which gives:

2:```
 eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:1f:c6:9b:c6:a4 brd ff:ff:ff:ff:ff:ff
    inet 10.0.1.107/24 brd 10.0.1.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet 10.0.1.17/8 brd 10.255.255.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::21f:c6ff:fe9b:c6a4/64 scope link
       valid_lft forever preferred_lft forever

```
So it appears that en01 has 2 IPv4 addresses, 10.0.1.107 and 10.0.1.17.    

Another sign of the confusion is that a "route -n" command right now gives:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.1.1        0.0.0.0         UG    0      0        0 eno1
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eno1
10.0.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
```

This gets even more reactions.  What's this 10.0.1.1 gateway, and where did it come from?  That string isn't in any config file that I can find.  And where did the 169.254.0.0 address come from? What is doing this setup, and how to we fix it?

Anyway, we're looking for a bit of guidance in making sense of this mess, so we can get the server up and running sanely.  (Googling the problems isn't getting us anywhere. ;-)

(We're convinced that some big changes have been made somewhere.  Part of the evidence is that I tried copying the network setup from a machine just down the wire that's been running for a few years, changing only the last field of the IP addresses to 17 for this machine.  The result was an earlier version of the failure you see above.  But part of the evidence is also that "ls -lu" tells us that some of the config files weren't even read after a boot.)

(And I did find references to network-manager, which I tried disabling using some instructions that google found, but that didn't seem to change anything at all, so it may not be the problem.)

(And points to anyone who can name the sci-fi novel that the machine's name came from. ;-)

---

### Post by John Chambers on 2016-08-16
Quick followup of something curious I've discovered.  All the documentation on networking uses the usual eth0, eth1, ... for interface names, but the box in question calls its ethernet port "eno1".  I didn't think anything of this when I saw it, because it's just a char string, and can be anything.  But in looking around in /var/log/syslog, I started noticing references to eth0 after a boot.  Then I spotted the following:

...
```
Aug 15 13:20:07 kendy kernel: [    2.884408] e1000e 0000:00:1f.6 eth0: registered PHC clock
Aug 15 13:20:07 kendy kernel: [    2.884412] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) 00:1f:c6:9b:c6:a4
Aug 15 13:20:07 kendy kernel: [    2.884414] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
Aug 15 13:20:07 kendy kernel: [    2.884511] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: FFFFFF-0FF
Aug 15 13:20:07 kendy kernel: [    2.887299] e1000e 0000:00:1f.6 eno1: renamed from eth0
...
```

So the interface starts out as eth0, and during startup something renames it as eno1.  

Is this normal?  Or is this throwing a monkey wrench into the network initialization?  If other code expects it to be the initial eth0, that could explain why the interface doesn't come up properly.  When I then type my setup commands using the eno1 name, the network does come to life.  But I won't always be around after a power failure or flipped circuit breaker reboots the machine, and I'm not sure I want to do all the setup by hand every time it's rebooted.

It's just a thought, and I'm wondering whether I should spend time investigating it.  There could be some very reasonable explanation of what's going on, which I'm not seeing.

The other real curiosity is I keep reading advice to edit  /etc/network/interface, which I've done and works.  But when I do a reboot, "ls -lu" tells me that  /etc/network/interface wasn't read during the startup.  I've found no clue about which program is supposed to read it.

Back to digging around in various forums and install guides ...

---

### Post by wildmanne39 on 2016-08-16
In 16.04 it is normal for the device to be named eno1 for an ethernet connection so you must be affected by the network manager bug that thinks wireless is ethernet, I had that issue for a short time but it was fixed quickly with an update and it did not cause connection issues.

Have you updated ubuntu? when you installed ubuntu did you do a fresh install? I imagine you did an upgrade otherwise I do not believe we would see the name change show up.

Please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 

The only time you mess with
```
/etc/network/interfaces
```
is when you are not using network manager like if you are running a server, otherwise network manager will over write that file at every reboot.
Thanks

---

### Post by wildmanne39 on 2016-08-16
*Thread moved to **Networking & Wireless**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by John Chambers on 2016-08-17
> **Wild Man said:**
> In 16.04 it is normal for the device to be named eno1 for an ethernet connection so you must be affected by the network manager bug that thinks wireless is ethernet, I had that issue for a short time but it was fixed quickly with an update and it did not cause connection issues.

Note that I didn't mention "wireless" in my original message.  The box does have a "wlp3s0" interface, which I googled, and it does appear to be wireless, but I'm not trying to deal with it (yet if at all).  But it's useful to hear that the renaming of eth0 to eno1 is normal.  The question then is why doesn't the startup code call it "eno1" from the start.  Why give it a different name, and then rename it?  Was that a kludge to avoid fixing code that has "eth0" hard-coded, or something equally bizarre?

> Have you updated ubuntu? when you installed ubuntu did you do a fresh install? I imagine you did an upgrade otherwise I do not believe we would see the name change show up.

I didn't install ubuntu on the machine.  I'm just tasked with getting it to work as a new server.  In fact, I've got a lot of things up and running (via the ethernet interface eno1).  This includes apache2 and bind9, which work fine.  The problem is that when the machine is rebooted, it comes up without any networking at all.  It only talks to its keyboard/mouse/display.  I can start it by hand, but that's not acceptable for a machine that's supposed to run unattended as a server.  

I've done a bit of asking around, and nobody has any objection to upgrading everything.  It's a new(ish) machine just being brought online, so  there's no worry about preserving anything that was there before.  As far as I can tell, it was a clean install, and nothing of value has been done on it.  Except that I did copy over a few things for testing, and added a few more debug/log messages to them.  But I've also copied those back to the archive on another machine.  ;-)

> Please click on the wireless script in my signature and follow the directions for running the script and posting the results here.

That's all about wireless, and I'm NOT trying to get that working.  Maybe later, after the server is up and running over ethernet (which is probably a lot faster than wireless). 

> The only time you mess with
```
/etc/network/interfaces
```
is when you are not using network manager like if you are running a server, otherwise network manager will over write that file at every reboot.
Thanks

I do see that ps says there's a process " /usr/sbin/NetworkManager --no-daemon" on the machine, so I'm guessing that NetworkManager is running.  However, it doesn't overwrite /etc/network/interfaces at boot.  According to "ls -l" and "ls -lu", nobody reads or writes that file after a boot.  But /usr/sbin/NetworkManager does get started.  I've been doing a bit of digging to find info about NetworkManager. So far all I've found is high praise for it, but not much useful documentation.  I have read instructions for NetworkManager telling me to edit /etc/network/interfaces and restart NetworkManager.  Is that wrong?  I am tempted to try to disable (or uninstall) it, and see what effect that has. But I don't even know how to tell if is actually doing anything at all.

I wonder what's the best way to just disable NetworkManager, so it won't get restarted after a reboot?  Either that, or is there a tutorial on configuring NetworkManager to work on a server?

(And what's the reason for putting CODE tags around just the file name?  The result certainly looks clumsy, and doesn't impart any additional information that I can see.  But I'm a novice at ubuntuforums, and don't understand the customs here.  It's hard enough just finding information.)

---

