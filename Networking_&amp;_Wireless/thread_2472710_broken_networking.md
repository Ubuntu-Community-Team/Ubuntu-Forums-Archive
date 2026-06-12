---
title: "broken networking"
date: 2022-03-09
forum: Networking &amp; Wireless
---

### Post by itheemonk on 2022-03-09
I have a PC that happily ran Ubuntu 10.04 for about 8 years, then I decided it was a good idea to upgrade it to a current LTS version...
So I progressively upgraded it to 12.04, 14.04, 16.04 and finally to 18.04. 

Now it is really upset. The main issue is the networking is totally stuffed up, it still gets an an address from the DHCP server, but nothing can communicate with it, and it can't communicate with anything (including itself!)

The really strange part is I have a bunch of VMs on the server and their networking continues to work fine.
The PC has 4x NICs that are bonded with LACP and bridges setup to various VLANs, the VMs networking is set to "bridged adapter" and then assigned to the various bridges on the host so they can only access one VLAN each.

The host can't ping anything: local router, its own IP or even localhost. The worst part is this means I can't access the web interface for the 3ware array controller, and I can't get alarms about potential issues with the array. 
I'm planning to replace the box and start again in the near future, but I'd really like to fix the networking so I can at least check the array status and get the 10Tb of data off the array.

I have no idea where to start diagnosing this issue, any help would be greatly appreciated.

---

### Post by TheFu on 2022-03-09
Upgrading more than 1 LTS often leaves too much cruft behind which leaves incompatible configurations behind as different infrastructure tools are added over time.  Networking has changed drastically since systemd was added in 2016.  Troubleshoot all you want, but almost nobody will recall the issues from 3+ yrs ago now to be able to help.

I'd strongly suggest doing a fresh 20.04 install.  In 20.04, netplan is the method used to control Ubuntu networking on servers. The old interfaces file is deprecated and will probably just cause confusion to you for which config system is actually being used.  I know that netplan had issues with bridges in the early releases of 18.04, but eventually, those were corrected.  18.04 can use either netplan or the interfaces file, so just be certain which is being used on your system if you insist on troubleshooting something.  The 18.04 install should be less than 15 minutes and restoring the applications and personal config files should take less than 30 minutes more, after a fresh install.  When I did an 18.04 upgrade from 16.04, it took over 2.5 hrs and broke not just networking, but a few other things that took me about 3 hrs to research and correct.  FYI.  

I still have a few systems on 18.04, but plans are to move to 20.04 as soon as my testing of our backup tool finishes on a new backup system.  The backup tool we use broke client-server compatibility with the 20.04 release because it is now based on python3 and serialization is broken between python 2/3 clients and servers. On disk, the backup sets use the same formats, so, for now, we'll have pre-20.04 backups on 1 system and 20.04+ backups on another.  I did port the python2 version of the backup tool to 20.04 and that has been working on some non-production systems for over year just fine, but it is time to move everything I can forward.

Anyway, hopefully my thought process is of some help to your situation.  Running a system that is out of support for years after support ended is a very bad idea.  I think moving from LTS-LTS in 4 yr periods is probably the best solution for stable, supported, systems. Of course, other people will have different opinions based on their needs and history.

---

