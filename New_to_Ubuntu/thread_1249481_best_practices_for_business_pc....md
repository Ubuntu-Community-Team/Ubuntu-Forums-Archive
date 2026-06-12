---
title: "best practices for business pc..."
date: 2009-08-25
forum: New to Ubuntu
---

### Post by pablolie on 2009-08-25
well, i have preached the merits of Ubuntu (and its combination with Software as a Service offerings) so passionately among my friends that 2 of them, who are about to open small businesses (more power to them in this business climate), have decided to base their small supporting computer infrastructure on Ubuntu.

now to make sure these are utterly stable installs. i love ubuntu, but regular updates sometimes cause hickups - i have seen the taskbar in xubuntu obliterate itself and desktop effects in ubuntu inexplicably disappear. that would not be acceptable.

so my gutfeel is to recommend that they go for one clean install, an update, and then leave it like that, stable. then a strict backup schedule, and updates can be tested on a quarterly schedule or whenever they have time on *one* machine that is not business critical. then bring the others into the fray. immediately fall back if required.

i just would not recommend the auto-update feature to people running their business off Ubuntu - does this overall sound like a decent suggestion? perhaps some guys you out there have ITIL certifications and can chime in. :-)

---

### Post by Hogosha on 2009-08-25
that is the basics for all mission critical machines no matter the OS they are running, in my opinion. 

Security updates are a bit different cause they are rather important but they should always be tested.

I always have a machine just for testing updates and new software.

---

### Post by snowpine on 2009-08-25
I highly recommend Ubuntu 8.04 Hardy Heron, the current LTS (long term support) release. It will be supported through April 2011 with minimal updates (just security patches and bug fixes). It is the most stable currently-supported Ubuntu release.

---

### Post by slakkie on 2009-08-25
What are we talking about?
Workstations or servers?

First of all, back ups are mandatory, financial data needs to be stored for several years (7 in my home country), so you need a propper backup solution.

[http://linux.about.com/od/softbackup/Linux_Software_Backup_Solutions.htm](http://linux.about.com/od/softbackup/Linux_Software_Backup_Solutions.htm)

I don't have much experience with the mentioned solutions, at work we use a commercial tool ([http://www.symantec.com/business/netbackup](http://www.symantec.com/business/netbackup)). 

You may want to have a single server where all the data gets stored and perhaps the homedirs of users are stored. That decreases the risk of data loss when a workstations goes down.

Workstations can be backed up by one of the tools or manual backups can be taken with clonezilla (which also has a remote backup procedure, but no experience with that).

As for updating your machines.

I'm running karmic on a laptop which I need 24/7 for work. I have backups of 8.04/9.04/9.10, so any error can be recovered from within 15 minutes.

For servers I would recommend 8.04 (since it is LTS). For workstations you could just follow the release cycle of Ubunt, maybe add some delays, eg 3 months after release X comes out you upgrade. But it all depends on how good your backups are.

I think everything depends on your backup solution, if you have a propper solution and you can restore within an hour or so, you can enable all kinds of repo's. Since going back is easy. However, I would not let normal users do upgrades on machines. One or two admins maintain the machines.

You might want to look into puppet, for centralized management of your workstations and servers. And Nagios for monitoring. You want your boxes to be the same. Also puppet sort of makes your backup life easier, since a newly installed box with puppet can be setup within minutes.

You mention ITIL, I don't know how big the company is, but I doubt small companies will benefit from ITIL (some processes could work in smaller scale, but don't get carried away with it, common sense applies :)).

---

### Post by pablolie on 2009-08-25
thanks a lot for the replies!

i will check the update option settings to acquaint myself with those more - on my machines i've let updates roam free until now, a practise i probably need to revise (the 9.04 updated obliterated my dual boot installation on a RAID based machine, which was a shame, because since i can only run Vista on that main machine).

---

