---
title: "NetBios Naming issues with NAS device"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by Pontifex on 2008-09-21
[Semi-experience user converting from Windows]
[Using ReadyNAS appliance, running Linux]
[Running Linux in VMWare during conversion]

**_Caveat_**

Forgive me if I come across as hostile in my post.  I am extremely irritated that I am unable to do something as simple as connecting to my network NAS device.  Please bear with me.

**_Problem Description_**
I'm attempting to connect to my NAS device from linux, but linux will not resolve the name of the device (in this case 'colossus').

I can connect to it via the "Connect to Server.." dialog with its IP address, but this is obviously not an optimal solution.

I followed this guide "[HOWTO: Resolve Netbios hostname system-wide]("http://ubuntuforums.org/showthread.php?t=88206")", but it plainly didn't work.  I installed _winbind_ and edited the _nsswitch.conf_ as instructed, but I could not resolve the hostname of my NAS regardless.

As I'm using VMWare to run Linux at the moment I'm on a different subnet than my Windows computer, which may be related to the problem.  But the Ubuntu network browser can see my main PC so I should at least be able to see my NAS which is in the same workgroup and subnet.

The DNS server my Linux computer is using is different than the one my Windows computer is using (my router).  So that may effect things.  Though really VMWare **should** be able to figure out the hostname of my NAS by checking with the router.  But I can't assume things that **should** work **will** at the moment.

I also suspect I may have to adjust my workgroup settings in Linux to match my Windows configuration.

But I am unable to adjust any of my network settings at the moment as the networking tool will not allow me to "unlock" it to adjust the settings.

**_Questions:_**

_How can I get my Linux machine to see / mount / browse / use my NAS device via DNS / WINS / NetBIOS or some other naming service?_
_How can I "unlock" my network settings configuration utility so that I can use it to make adjustments?_

I would like it very much if the answer were something other than editing hidden configuration files, going to the command line or installing new software; I'm shooting for simplicity with setting up.

--Pontifex

---

### Post by dmizer on 2008-09-22
The guide you linked to makes one serious mistake. It says that the "hosts" line should look like this:
```
hosts: files dns wins
```
But that can cause problems with a number of DNS servers.

The problem here is that the order of these DOES matter, and that wins should be before dns like so:
```
hosts: files [COLOR="Red"]wins[/COLOR] dns
```
Correct this and see if that resolves your name resolution problem.

---

### Post by Pontifex on 2008-09-27
Nope, it still doesn't work.

/etc/nsswitch.conf

```
hosts:          files wins dns
```

I finally got my Network Settings widget working and adjusted my DNS settings like so (See attached).

Also, I'm able to ping my Windows machine by name (see attached).

So, I'm out of ideas.  Something with Samba would work, I'm sure.  Any ideas?

--Pontifex

---

