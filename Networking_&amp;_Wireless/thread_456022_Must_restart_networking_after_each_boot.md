---
title: "Must restart networking after each boot"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by Dzenhax on 2007-05-27
Can anyone tell me why I have to restart my networking service after each reboot of my computer?

This is a weird one for me.  I'm not changing anything in any file or configuration but when I reboot I can't ping my gateway or any other host until I:

/etc/init.d/networking restart

My one interface is a wireless that works fine after the restart.  Is there a log I might check?

I've written a script to speed up the process, but I'd rather just have it work.  And in case I don't figure it out how do I make the script run at boot instead of me manually running it after login.

Thanks,

---

### Post by zek725 on 2007-05-27
I had to restart samba for it to work when I resume from hibernation. any other clues? 	:confused:

---

### Post by Rui Pais on 2007-05-27
> **Dzenhax said:**
> Can anyone tell me why I have to restart my networking service after each reboot of my computer?

This is a weird one for me.  I'm not changing anything in any file or configuration but when I reboot I can't ping my gateway or any other host until I:

/etc/init.d/networking restart

My one interface is a wireless that works fine after the restart.  Is there a log I might check?

I've written a script to speed up the process, but I'd rather just have it work.  And in case I don't figure it out how do I make the script run at boot instead of me manually running it after login.

Thanks,

Hi,
you can add your script path (or the script commands) to /etc/rc.local.

About the main problem. Are you sure that your network is been started? 
Check the following:
```
ls /etc/rcS.d/S*network*
```
should give something like:
```
/etc/rcS.d/S40networking
```
Check too /var/log/messages for any messages related to network failure.

Do you have the module for network loaded after boot and before running the command manually or with your script? dmesg command report any error?

Do you have a static or an dynamic IP. Maybe changing the one you use by the other... 
Once, when  i used dynamic IPs, something related with slow dhcp assignment of IP create a situation liek that. I had to restart network manually 1 or 2 times before get one.

---

### Post by Dzenhax on 2007-05-28
Thanks for the responses,

Rui Pais

When I run ls /etc/rcS.d/S*network*

I get /etc/rcS.d/S40networking

So I'm guessing I'm good there.

/var/log/messages gives me

May 27 16:34:32 morgan kernel: [  610.440000] eth1: remaining active for wake-on-lan
May 27 16:34:32 morgan kernel: [  610.520000] ADDRCONF(NETDEV_UP): ath0: link is not ready
May 27 16:34:34 morgan kernel: [  612.564000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
May 27 16:34:34 morgan kernel: [  612.924000] eth1: DSPCFG accepted after 0 usec.
May 27 16:34:34 morgan kernel: [  612.928000] ADDRCONF(NETDEV_UP): eth1: link is not ready

Which doesn't look too suspicious to me.  eth1 is not hooked up, so no surprise there.  ath0 becomes ready so on to dmesg

[  610.440000] eth1: remaining active for wake-on-lan
[  610.520000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[  612.564000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  612.924000] eth1: DSPCFG accepted after 0 usec.
[  612.928000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  623.396000] ath0: no IPv6 routers present

Not running v6, not a big deal.  Still doesn't look bad to me.

QUOTE=Rui Pais;2730390]
Do you have the module for network loaded after boot and before running the command manually or with your script? dmesg command report any error?
[/QUOTE]

I don't know how to check this or know where it is running.

I get error messages on the broadcom card, which I'm not using (because I still can't get it to work)

[  112.512000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  137.404000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  162.356000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  187.304000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  312.208000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  437.108000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.

But the interface had worked fine until the feisty upgrade when I didn't have this problem, so don't think that's it.

QUOTE=Rui Pais;2730390]
Do you have a static or an dynamic IP. Maybe changing the one you use by the other... 
[/QUOTE]

I have static ips.  This is because my dhcp server is a wireless router that has not option to direct clients to my dns server.  I run an internal dns server and the router wants to send clients to the internet for dns.  This also was the situation when the card worked fine.

The only thing that has really changed, is that I upgraded to feisty.  After the upgrade, the system became unstabel, so I backed up my data and did a fresh install.  After that, I had this problem.

zek725,

The only other clues are that until I restart networking, my programs load like windows programs.  Really slow, 15 to 20 seconds to start evolution, firefox or a terminal.  After restarting the network they load in the normal 3-5 seconds.

lastly,

If I need to make my script part of startup by copying it into /etc/rc.local, just for convienience sake, how to I get the script to run as root so I don't have to type a password in?

Thanks again for any help.

---

### Post by Rui Pais on 2007-05-28
Hi, 
> **Dzenhax said:**
> [QUOTE=Rui Pais;2730390]
Do you have the module for network loaded after boot and before running the command manually or with your script? dmesg command report any error?


I don't know how to check this or know where it is running.[/QUOTE]

You can check this with lsmod os lspci. Do, before running your script:
```
 lsmod |grep <module_name_of_your_netcard>
```
or 
```
lspci | grep net
```

Another thing to do would be running lsmod before your script, then run the script till you got connection, then run the lsmod command again and check if some module as been added to the list. 
You can do this with dmesg too and check what is been add to dmesg after running the script.
Since you got normal connection after the script there is no really problem... it's just some configuration that seems to be incorrect.  

btw do you min to post yours:
cat /etc/network/interfaces
and
cat /etc/hosts
please.

> 
lastly,

If I need to make my script part of startup by copying it into /etc/rc.local, just for convienience sake, how to I get the script to run as root so I don't have to type a password in?

/ets/rc.local will be running as a boot service (the last one) so it's at root/admin level. You don't need to worry with sudo or passwords :)

---

### Post by Dzenhax on 2007-05-28
I'll reboot and try it, but check this out.  The lines:

May 27 16:34:32 morgan kernel: [ 610.440000] eth1: remaining active for wake-on-lan
May 27 16:34:32 morgan kernel: [ 610.520000] ADDRCONF(NETDEV_UP): ath0: link is not ready
May 27 16:34:34 morgan kernel: [ 612.564000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
May 27 16:34:34 morgan kernel: [ 612.924000] eth1: DSPCFG accepted after 0 usec.
May 27 16:34:34 morgan kernel: [ 612.928000] ADDRCONF(NETDEV_UP): eth1: link is not ready

always were the last lines in messages.  I rebooted and checked messages BEFORE the script and there is nothing at all referencing ath0.  So I'm thinking networking is not getting loaded at all.  I wonder how that would happen on a default feisty install?

Anyway, I'll reboot and check the other now.

---

### Post by Dzenhax on 2007-05-28
OK, Here's what I got,

root@morgan:/home/dzenhax# lsmod | grep ath0
root@morgan:/home/dzenhax# lspci | grep net
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

I made a file for lsmod and pulled this stuff out:

Module                  Size  Used by

wlan_wep                7936  1 
wlan_scan_sta          14976  1 
ath_rate_sample        14080  1 
ath_pci                97312  0 
wlan                  204484  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
pcmcia                 39212  0 
bcm43xx               126824  0 
ieee80211              34760  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
ipv6                  268960  8 

But I don't know what this tells me.

Any suggestions?

---

### Post by hartz on 2007-05-28
Do you have an entry in the /etc/hosts file for your computer pointing to its own (correct) IP address?

---

### Post by Dzenhax on 2007-05-28
Just the standard

127.0.0.1 localhost

But I'm not sure why that would affect it.  On the restart of services I'm still using the same hosts and interfaces files, so if that were the case, I'd think it'd fail again.

---

### Post by Rui Pais on 2007-05-28
> **Dzenhax said:**
> Just the standard

127.0.0.1 localhost

But I'm not sure why that would affect it.  On the restart of services I'm still using the same hosts and interfaces files, so if that were the case, I'd think it'd fail again.

hosts file used to have a different format. Some people report a strange slowness of application start up that disappear when old format was put it back. I mentioned cause you said before some application take a long ime to start before you got connected (it shouldn't has nothing to do with your main problem) here what you can change on /etc/hosts:
> 127.0.0.1 localhost ***<your_box_name>***
127.0.1.1 <your_box_name>
where <your_box_name> must be replaced by... that (morgan according to your logs).

 > always were the last lines in messages. I rebooted and checked messages BEFORE the script and there is nothing at all referencing ath0. So I'm thinking networking is not getting loaded at all.
you may try to add manually the modules for your card to the file /etc/modules to ensure they will be loaded when network service starts... may help.

Some things change from old kernels to the ones feisty uses. There is a lot of posts related to wireless cards... may you have one of those affected...

good luck.


***edit***:
 Check your /etc/network/interfaces to ensure that is ok and all cards have the correct static IP.

---

### Post by Dzenhax on 2007-05-28
Actually I remember the old

127.0.1.1  I didn't realize it went away.  I'll put it back and see if it helps.

---

### Post by Rui Pais on 2007-05-28
> **Dzenhax said:**
> Actually I remember the old

127.0.1.1  I didn't realize it went away.  I'll put it back and see if it helps.

Oops i made a typo (you probably get it, but nevertheless...) 
i put the name of my computer on the lines of /etc/hosts of my previous post. :oops: Sorry. 
It's corrected now. 

Please note that the change should be:
> 127.0.0.1 localhost
to:
> 127.0.0.1 localhost ***<your_box_name>***
and of course 
127.0.1.1 <your_box_name>
should exist too.

good luck

---

### Post by Dzenhax on 2007-05-28
No prob.

It did speed up my progs, but I still have to use the script to start networking.  It's strange to me that using the script also sped up the programs too.  I wouldn't think they were related.

In any case I'm glad to get one problem fixed.

---

### Post by Rui Pais on 2007-05-28
> **Dzenhax said:**
> No prob.

It did speed up my progs, but I still have to use the script to start networking.  It's strange to me that using the script also sped up the programs too.  I wouldn't think they were related.

In any case I'm glad to get one problem fixed.

Oh well, too bad your main problem isn't solve :(

Try to add ath_pci and wlan to your /etc/modules and see if tit works (i don't have much hope on that too, i confess). 
I don't have much more ideas... maybe  mean time someone else may suggest something better.

Good luck, Dzenhax.

---

### Post by Rui Pais on 2007-05-28
hi again, just one more thing.
I don't have wireless network so have no idea about they specific problems... but not connect at start up seems to be a frequent problem. (Seems to be something related with NetworkManager, that some prefer to remove).

[Here is an app (wicd)]("http://wicd.sourceforge.net/pages/features.php") that tries to make life easy for wireless users, among features:
> automatically connect at boot - no user intervention required, even for encrypted networks
(Although your script should do the same anyway...)

---

### Post by Dzenhax on 2007-05-28
I'll try it.  Network manager is lousy and I have been looking for a good replacement.  I've used wlassistant, but it lacks some functionality.

Thanks!!

---

### Post by hartz on 2007-05-29
Put an entry into your hosts file with your IP address and your host name.  Then test again.

Example
```
192.168.3.5   morgan
```

I just noticed some other suggestion for 127.0.1.1 into your hosts file.  Don't put two entries with the same name (like morgan).  Put only an entry with your real host name and real IP address.

Also don't remove the localhost entry from the file.

Programs start up faster because they can find out where to put their display faster.  Network setup (at boot time) also sometimes depends on resolving the hostname (back to an IP address) in order to allocate an address and subsequently configure the interface.  Can you please display this file /etc/network/interfaces

---

### Post by Rui Pais on 2007-05-29
> **hartz said:**
> ...
I just noticed some other suggestion for 127.0.1.1 into your hosts file.  Don't put two entries with the same name (like morgan).  Put only an entry with your real host name and real IP address.

Also don't remove the localhost entry from the file.

...

Hi hartz,
i wish i understand that subject better... 
My suggestion to use a 127.0.1.1 is because i have one and usually any reference to /etc/hosts i read had one too (but i never suggested using two entries for the same name or to remove localhost ;)) 

My point was that recently seems that hosts file is been set with the line 127.0.0.1 with localhost name only and some people seems to find a speed up (on apps starts) when alias is present on that line (i don't note any difference, but anyway...).
(*EDIT:* [here a bug report]("http://lists.debian.org/debian-boot/2005/06/msg01047.html") on debian list mention that it's better not have it in fact... but all my Ubuntu installations made one.)

[Here is the a bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048") for that and [here a thread ]("http://ubuntuforums.org/showthread.php?t=388765")on the subject.


About the issue on network auto startup... didn't add the line you suggested, "192.168.3.5   morgan", just make the alias morgan available for that IP? Could be that information missing the cause for the non automatic start of the network?

I'm more inclined to suspect that something is not correct at /etc/network/interfaces files...

---

### Post by hartz on 2007-05-29
> **Rui Pais said:**
> Hi hartz,
i wish i understand that subject better... 
My suggestion to use a 127.0.1.1 is because i have one and usually any reference to /etc/hosts i read had one too (but i never suggested using two entries for the same name or to remove localhost ;)) 

Yes, the reason why I said don't have two entries with the same name is because I worried that the OP might follow both your solution AND my solution.  I've never seen a 127.0.1.1 address before.  EVER.  In Unix or on Linux.  And that includes a LOT of boxen.  So I have no idea what it would do...

Of course the whole 127.*.*.* A-class net is devoted to loopback.  

I did a search on 127.0.1.1 and ... still don't see the need for it.   Maybe someone on this list can clarify that.

> **Rui Pais said:**
> My point was that recently seems that hosts file is been set with the line 127.0.0.1 with localhost name only and some people seems to find a speed up (on apps starts) when alias is present on that line (i don't note any difference, but anyway...).
(*EDIT:* [here a bug report]("http://lists.debian.org/debian-boot/2005/06/msg01047.html") on debian list mention that it's better not have it in fact... but all my Ubuntu installations made one.)

[Here is the a bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048") for that and [here a thread ]("http://ubuntuforums.org/showthread.php?t=388765")on the subject.

About the issue on network auto startup... didn't add the line you suggested, "192.168.3.5   morgan", just make the alias morgan available for that IP? Could be that information missing the cause for the non automatic start of the network?

It also provides reverse lookup, and Yes, this is why I asked that he check for the presense of a hostname entry in the hosts file in the first place.  Which is important inside the X-Windows server stack.  This is why X-apps open up slowly (or not at all) if they open up at all it means that the client found another way to reverse lookup the IP, eg via DNS, hence the delay.  Also login sessions often try to resolve the hostname for record keeping in utmp/wtmp databases, and x-sessions sometimes perform an implicit login.  This reverse-lookup will timeout after 60 seconds and if there is no name found, it then allows the connection and records the IP in stead of the hostname.

> **Rui Pais said:**
> I'm more inclined to suspect that something is not correct at /etc/network/interfaces files...

Me too, which is why I asked the OP to show the file :-)

---

### Post by Rui Pais on 2007-05-29
hartz,
thanks for your (excellent detailed) answer.

> **hartz said:**
> Yes, the reason why I said don't have two entries with the same name is because I worried that the OP might follow both your solution AND my solution.  I've never seen a 127.0.1.1 address before.  EVER.  In Unix or on Linux.  And that includes a LOT of boxen.  So I have no idea what it would do...

Of course the whole 127.*.*.* A-class net is devoted to loopback.  

I did a search on 127.0.1.1 and ... still don't see the need for it.   Maybe someone on this list can clarify that.


thats weird... all my ubuntus installations have that line. Most links to issues with loopbacks or topics involving /etc/hosts the examples showed lists a 127.0.1.1 line ([here ]("https://answers.launchpad.net/ubuntu/+question/4419") another one on Ubuntu launchpad answers, and the person who answers gives exactly the same suggestion, again referring that 2nd IP).

But you are right, at least here seems not needed; i commented mine and rebooted and no problem at all. Besides man hosts don't mention any .1.1 
I wonder if it isn't some old requirement of hosts file...

---

### Post by hartz on 2007-05-29
I've just read up a bit more carefully on 127.0.1.1

1) You need your hostname (as produced by the hostname command) in your /etc/hosts file.  This allows apps to lookup the name/address they get when they check the host (eg as produced by the "hostname" command)

2) In terms of application startup performance, I doesn't matter whether the hostname is on a line that reads 127.0.0.1, 127.anything, or your real IP address, **as long as it is in the hosts file ONCE**.  This prevents unnecessarily going out on the network to try to do a lookup.  If you find that it does perform faster one way or the other, you have found a bug in the Linux IP networking.

3) If you have a static IP, the "correctest" way is to use that one as the entry for your hostname.

4) The various suggestions to put the hostname entry on multiple lines are incorrect.  If you DO do that, you can get one of several behaviors:
a) You may get that the resolver returns the various IPs in a round-robin fashion.
b) The resolver might just simply always return the first entry found.
c) You could get undocumented undefined behavior.

This is implementation specific and depends on your nsswitch configuration and the actual lookup routine/dns client in use.

My suggestion:

Keep it clean and tidy:
a) 127.0.0.1 localhost <- this entry is a MUST HAVE
b) If you have a static address, specify that together with your (FQHN) hostname.
c) If you don't, feel free to add your (FQHN) hostname to either the 127.0.0.1 line, OR create a new loopback entry, like 127.0.1.1, whichever rocks your boat.
d) Don't have multiple hosts lines with the same name - you're bound to one day discover some unexpected behaviour.
e) If you are using a fully qualified hostname (check what the hostname command returns), then put that name into the hosts file, but feel free to then ALSO list the unqualified hostname in the hosts file, on the same line, as an alias (Note: Aliases comes after canonical entries - example:)

```
127.0.0.1  localhost
192.168.5.3 hartz.mydomain.com hartz # Static IP, FQHN and alias
```

*I must grant that from a practical point of view, it doesn't matter whether you give the unqualified hostname or the qualified hostname first.  The first one will be considered "canonical", the other one an alias.  Both will work equally well, irrespective of which is the canonical name.... **HOWEVER**... reverse lookups will return the Canonical Name.  Commands like netstat and lsof will produce "**nicer**" output if you put the shorter name first.*

---

### Post by Dzenhax on 2007-05-31
Guys,

     Thanks for the additional info.  I've been out of town and am just getting back.  I have an early day but will look over your notes the weekend.  Thanks.

---

