---
title: "Networking Mystery of the CENTURY!"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by Cyorxamp on 2006-07-23
p.s. I use xubuntu in this, but it is also tried with ubuntu

I kid you not with this title, this is a real mind boggler of a problem.

I have been asking around on IRC and 6 people so far have given up on this, so I thought i'd give the forum ago... the last guy who helped me (neo0h) was great but went offline at the end of our chat (just when things were getting interesting)

I have included a veeeery cut down version of the chat we had here so you know what I have and have not tried so far.... please please please don't skip the log as it does outline important things, it was 8 times longer so it's cut down.

The situation summerized is this...
On my box... Xubuntu LiveCD has internet access automatically...
... Windows on the same box has automatic internet too
... When installing xubuntu via the alternate text installer... it can resolve dhcp fine.

BUT! When xubuntu is finally on the HDD... nothing! no internet, not even an IP assigned, and the settings look identical to that of the LiveCD.

p.s. I have tried the DHCP server from a Netgear Router, a 3COM ADSL Modem, and finally WinXP Internet Connection Sharing - same results with all 3 (even re-installed xubuntu after changing from one to the other)... I am using the 3Com at the moment.

Here is my log
--------------------

1:15am <neo0h> ill try and help
1:16am <neo0h> go ahead
1:16am <Cyorxamp> I have a normal ethernet lan... and this box I want linux on
1:16am <Cyorxamp> I have tried three different dhcp servers (one from the ICS on WinXP, one from a Netgear Router, and one from a 3COM ADSL modem)
1:16am <Cyorxamp> When using the LiveCD of my distro on this box with all three dhcp variations... i get internet access
1:17am <Cyorxamp> When installing linux... it can resolve dhcp fine when installing
1:17am <Cyorxamp> I must also say that windows on the same box works
1:17am <Cyorxamp> But when linux is finally on the HDD.... nothing!
1:17am <Cyorxamp> after every dhcp server 'change' I have reinstalled it too
1:17am <neo0h> but eth0 is there and has an ip?
1:17am <Cyorxamp> eth0 is there but no IP
1:17am <neo0h> and you are running ubuntu
1:17am <Cyorxamp> yeah Xubuntu
1:22am <neo0h> ifconfig eth0 up
1:23am <Cyorxamp> it returns nothing
1:24am <neo0h> dsl/cable modem?, wireless?
1:24am <Cyorxamp> no wireless
1:24am <Cyorxamp> just wired ethernet to an ADSL modem (the 3com one atm) that has dhcp switched on
1:27am <Cyorxamp> theres no router/wiring/card problem
1:27am <Cyorxamp> since the LiveCD of the same distro works, and windows on the box works
1:29am <neo0h> ifconfig eth0 down
1:29am <neo0h> then bring it back up and do this....
1:29am <neo0h> netstat
1:30am <Cyorxamp> i see lots of things, none of them say dhcp in them
1:30am <Cyorxamp> others have told me to run 'netstat -r' in the past... which returns nothing
1:31am <neo0h> ping [www.google.com](www.google.com)
1:31am <Cyorxamp> theres no IP on ifcongfig and ping fails
1:33am <Cyorxamp> LiveCD uses the same settings as the hdd one did (automatic DHCP as before)
1:33am <Cyorxamp> and I have tried static ip
1:33am <Cyorxamp> still doesn't work
1:33am <Cyorxamp> like I said, this is a puzzler
1:33am <Cyorxamp> i've now had 6 people unable to tell me what is wrong
1:34am <neo0h> you have the right to be confused and weirded out
1:34am <Cyorxamp> I even went on about it in #xubuntu
1:34am <Cyorxamp> they just accused me of trolling and booted me
1:35am <neo0h> give me 15-20 min
1:42am <neo0h> ok, well I suggest making sure.....that ur using the same kernel that the live cd was using
1:42am <Cyorxamp> whats the command I need to check kernel version ?
1:42am <neo0h> uname -a
1:43am <Cyorxamp> 2.6.15-23-386
1:43am <Cyorxamp> thats HDD
1:43am <Cyorxamp> -reboots-
1:49am <Cyorxamp> ok im in :P
1:49am <neo0h> ifconfig it for me
1:49am <Cyorxamp> internet works :P
1:49am <neo0h> whats the Bcast?
1:49am <Cyorxamp> ive got an IP address
1:49am <Cyorxamp> 192.168.200.2
1:50am <neo0h> uname -a
1:50am <Cyorxamp> 2.6.15-23-386 - exactly the same as the hdd one
1:50am <neo0h> dhcp is running
1:51am <Cyorxamp> yup
1:58am <neo0h> nmap -sT localhost
1:58am <neo0h> dont tell me
1:58am <neo0h> just make sure your nmap output is the same once ur on the hdd
2:00am <Cyorxamp> ok i've recorded what nmap said
2:00am <neo0h> koool
2:12am <Cyorxamp> shall I reboot now ?
2:13am <Cyorxamp> I've saved those 'outputs' as a text file on the hdd
2:20am <neo0h> cd /etc on the livecd
2:21am <neo0h> dhcp3 discover.conf discover.d
2:22am <neo0h> those files
2:22am <Cyorxamp> ok, copy to hdd?
2:22am <neo0h> over write those files from the livcd to the hdd ones in /etc
2:24am <Cyorxamp> discover.conf is file that exists
2:24am <Cyorxamp> discover.d is a dir that exists
2:25am <Cyorxamp> dhcp3 is a dir that exists
2:25am <neo0h> over write them with the ones that work from the cd
2:25am <Cyorxamp> done
2:26am <neo0h> great
2:26am <Cyorxamp> restart?
2:26am <neo0h> yup
2:26am <Cyorxamp> booting up...
2:29am <Cyorxamp> logging in...
2:30am <Cyorxamp> no internet access

I really hope someone has an idea to this bizzare problem, I have installed xubuntu some 20 odd times now and I am getting desperate!!!

---

### Post by Cyorxamp on 2006-07-23
p.s. I use xubuntu in this, but it is also tried with ubuntu

I kid you not with this title, this is a real mind boggler of a problem.

I have been asking around on IRC and 6 people so far have given up on this, so I thought i'd give the forum ago... the last guy who helped me (neo0h) was great but went offline at the end of our chat (just when things were getting interesting)

I have included a veeeery cut down version of the chat we had here so you know what I have and have not tried so far.... please please please don't skip the log as it does outline important things, it was 8 times longer so it's cut down.

The situation summerized is this...
On my box... Xubuntu LiveCD has internet access automatically...
... Windows on the same box has automatic internet too
... When installing xubuntu via the alternate text installer... it can resolve dhcp fine.

BUT! When xubuntu is finally on the HDD... nothing! no internet, not even an IP assigned, and the settings look identical to that of the LiveCD.

p.s. I have tried the DHCP server from a Netgear Router, a 3COM ADSL Modem, and finally WinXP Internet Connection Sharing - same results with all 3 (even re-installed xubuntu after changing from one to the other)... I am using the 3Com at the moment.

Here is my log
--------------------

1:15am <neo0h> ill try and help
1:16am <neo0h> go ahead
1:16am <Cyorxamp> I have a normal ethernet lan... and this box I want linux on
1:16am <Cyorxamp> I have tried three different dhcp servers (one from the ICS on WinXP, one from a Netgear Router, and one from a 3COM ADSL modem)
1:16am <Cyorxamp> When using the LiveCD of my distro on this box with all three dhcp variations... i get internet access
1:17am <Cyorxamp> When installing linux... it can resolve dhcp fine when installing
1:17am <Cyorxamp> I must also say that windows on the same box works
1:17am <Cyorxamp> But when linux is finally on the HDD.... nothing!
1:17am <Cyorxamp> after every dhcp server 'change' I have reinstalled it too
1:17am <neo0h> but eth0 is there and has an ip?
1:17am <Cyorxamp> eth0 is there but no IP
1:17am <neo0h> and you are running ubuntu
1:17am <Cyorxamp> yeah Xubuntu
1:22am <neo0h> ifconfig eth0 up
1:23am <Cyorxamp> it returns nothing
1:24am <neo0h> dsl/cable modem?, wireless?
1:24am <Cyorxamp> no wireless
1:24am <Cyorxamp> just wired ethernet to an ADSL modem (the 3com one atm) that has dhcp switched on
1:27am <Cyorxamp> theres no router/wiring/card problem
1:27am <Cyorxamp> since the LiveCD of the same distro works, and windows on the box works
1:29am <neo0h> ifconfig eth0 down
1:29am <neo0h> then bring it back up and do this....
1:29am <neo0h> netstat
1:30am <Cyorxamp> i see lots of things, none of them say dhcp in them
1:30am <Cyorxamp> others have told me to run 'netstat -r' in the past... which returns nothing
1:31am <neo0h> ping [www.google.com](www.google.com)
1:31am <Cyorxamp> theres no IP on ifcongfig and ping fails
1:33am <Cyorxamp> LiveCD uses the same settings as the hdd one did (automatic DHCP as before)
1:33am <Cyorxamp> and I have tried static ip
1:33am <Cyorxamp> still doesn't work
1:33am <Cyorxamp> like I said, this is a puzzler
1:33am <Cyorxamp> i've now had 6 people unable to tell me what is wrong
1:34am <neo0h> you have the right to be confused and weirded out
1:34am <Cyorxamp> I even went on about it in #xubuntu
1:34am <Cyorxamp> they just accused me of trolling and booted me
1:35am <neo0h> give me 15-20 min
1:42am <neo0h> ok, well I suggest making sure.....that ur using the same kernel that the live cd was using
1:42am <Cyorxamp> whats the command I need to check kernel version ?
1:42am <neo0h> uname -a
1:43am <Cyorxamp> 2.6.15-23-386
1:43am <Cyorxamp> thats HDD
1:43am <Cyorxamp> -reboots-
1:49am <Cyorxamp> ok im in :P
1:49am <neo0h> ifconfig it for me
1:49am <Cyorxamp> internet works :P
1:49am <neo0h> whats the Bcast?
1:49am <Cyorxamp> ive got an IP address
1:49am <Cyorxamp> 192.168.200.2
1:50am <neo0h> uname -a
1:50am <Cyorxamp> 2.6.15-23-386 - exactly the same as the hdd one
1:50am <neo0h> dhcp is running
1:51am <Cyorxamp> yup
1:58am <neo0h> nmap -sT localhost
1:58am <neo0h> dont tell me
1:58am <neo0h> just make sure your nmap output is the same once ur on the hdd
2:00am <Cyorxamp> ok i've recorded what nmap said
2:00am <neo0h> koool
2:12am <Cyorxamp> shall I reboot now ?
2:13am <Cyorxamp> I've saved those 'outputs' as a text file on the hdd
2:20am <neo0h> cd /etc on the livecd
2:21am <neo0h> dhcp3 discover.conf discover.d
2:22am <neo0h> those files
2:22am <Cyorxamp> ok, copy to hdd?
2:22am <neo0h> over write those files from the livcd to the hdd ones in /etc
2:24am <Cyorxamp> discover.conf is file that exists
2:24am <Cyorxamp> discover.d is a dir that exists
2:25am <Cyorxamp> dhcp3 is a dir that exists
2:25am <neo0h> over write them with the ones that work from the cd
2:25am <Cyorxamp> done
2:26am <neo0h> great
2:26am <Cyorxamp> restart?
2:26am <neo0h> yup
2:26am <Cyorxamp> booting up...
2:29am <Cyorxamp> logging in...
2:30am <Cyorxamp> no internet access

I really hope someone has an idea to this bizzare problem, I have installed xubuntu some 20 odd times now and I am getting desperate!!!

---

### Post by simonn on 2006-07-23
First things first.

Forget about the internet for the time being. You seem to be unable to get a IP address via DHCP so this is the logical place to start.

Start with a static ip address on the same subnet, turn any firewalling off completely. Can you ping the router?

---

### Post by kagashe on 2006-07-23
This may look a silly question but I am asking since I faced some problems during Ubuntu 5.04 to 5.10 upgrade.

Are you using /home from a previous Linux installation?

kagashe

---

### Post by DJ Scribblinni on 2006-07-23
Just out of curiosity post the ```
sudo dhclient
``` or whichever command xubuntu uses to grab in ip

and... is it possible to try using another dhcp client that would configure your network, perhaps dhcpcd or pump,,,thats all off the top of my head.

---

### Post by mips on 2006-07-24
Will it work with a static config ?

---

### Post by Cyorxamp on 2006-07-24
> **mips said:**
> Will it work with a static config ?
> **simonn said:**
> You seem to be unable to get a IP address via DHCP so this is the logical place to start.  Start with a static ip address on the same subnet, turn any firewalling off completely. Can you ping the router?


As the chat log says...
1:33am <Cyorxamp> and I have tried static ip
1:31am <Cyorxamp> theres no IP on ifcongfig and ping fails

> **kagashe said:**
> Are you using /home from a previous Linux installation?

Nope, /home exists on it's own ext3 partition which is formatted everytime I try a new install.

> **DJ Scribblinni said:**
> Just out of curiosity post the ```
sudo dhclient
```

(After a few attempts)
No DHCPOFFERS received
No working leases in persistant database - sleeping.

---

### Post by Cyorxamp on 2006-07-24
> **mips said:**
> Will it work with a static config ?
> **simonn said:**
> You seem to be unable to get a IP address via DHCP so this is the logical place to start.  Start with a static ip address on the same subnet, turn any firewalling off completely. Can you ping the router?


As the chat log says...
1:33am <Cyorxamp> and I have tried static ip
1:31am <Cyorxamp> theres no IP on ifcongfig and ping fails

> **kagashe said:**
> Are you using /home from a previous Linux installation?

Nope, /home exists on it's own ext3 partition which is formatted everytime I try a new install.

> **DJ Scribblinni said:**
> Just out of curiosity post the ```
sudo dhclient
```

(After a few attempts)
No DHCPOFFERS received
No working leases in persistant database - sleeping.

---

### Post by mips on 2006-07-24
What LAN adapter/chipset do you have ?

---

### Post by Cyorxamp on 2006-07-24
> **mips said:**
> What LAN adapter/chipset do you have ?

Davicom	DM9102A 
... please keep in mind that the LiveCD works perfectly and automatically under the same hardware conditions.

---

### Post by mips on 2006-07-24
> **Cyorxamp said:**
> Davicom    DM9102A 
... please keep in mind that the LiveCD works perfectly and automatically under the same hardware conditions.

Please post the output of lspci -v (just the network part) as I think I know whats wrong but need to confirm first.

---

### Post by mips on 2006-07-24
I dunno if your card uses the tulip chipset but have a look.

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by shultzjr on 2006-07-24
Have you tried other livecd's like:
Knoppix
SLAX
Kanotix
MEPIS
to determine a hw/sw config that works?  It seems that the live configuration of XUbuntu has the correct combination of drivers and networking subsystems that just works.  

You also mentioned Windows.  Is this a multiboot machine?  If so, get a separate hd and do a clean install with XUbuntu with it and see if that works.  If not post hw/software config and any error messages and we can go from there.

---

### Post by Cyorxamp on 2006-07-24
Hi folks,

I ran the command you asked for mips...

0000:00:09.0 Ethernet Controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip c$
    Subsystem: Davicom Semiconductor Inc.: Unknown Device 8212
    Flags: bus master, medium devsel, latency 32, IRQ 10
    I/O ports at d800 [size=256]
    Memory at eb000000 (32bit, non-prefetchable) [size=256]
    Expansion ROM at 30000000 [disabled] [size=256]
    Capabilities: <available only to root>

If like you say this is something to do with 'tulip' then how come it works fine on the LiveCD!

---

### Post by Cyorxamp on 2006-07-24
Update.......

I tried the solution at the link you gave and it works...

Since Ubuntu 5.10 worked and the Xubuntu 6.06 LiveCD works... surely this is a bug??  Any way of knowing if it has been flagged up for the next release?

---

### Post by mips on 2006-07-24
Cyorxamp,

Glad to see that it works.

Why dont you search launchpad and see if their is a bug report for it, if not then log one.

I don't know why it works with the livecd and not the installed version, it seems to be a common problem though.

I personally dont regard ubuntu as the  most stable distro out there. things that worked in Breezy does not always work in dapper which is sad.

---

