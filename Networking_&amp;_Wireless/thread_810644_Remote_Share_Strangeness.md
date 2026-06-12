---
title: "Remote Share Strangeness"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by ColdFusionEESG on 2008-05-28
Hey All,

OK...so here's how things worked for me on Gutsy in Nautilus...

1) Browse network:///
2) See workgroups listed
3) select workgroup of remote machine I'm after
4) see a list of shared folders on that remote machine
5) click the folder I want and enter user/pass and away I go
6) see the folder contents I was after

Here's how it doesn't work in HARDY...

1) Browse network:///
2) See workgroups listed
3) select workgroup of remote machine I'm after
4) DO NOT see a list of shared folders on that remote machine
5) manually add shared folder to location bar
6) enter user/pass and away I go
7) see the folder contents I was after

I know there is trouble with hosts and with workgroups in HARDY, but no idea what to do about them.  BTW in case it's not clear it's step 4 on HARDY that is bugging me.

BTW I also noticed that once authenticated on the remote machine, the shared folder is auto-mounted in HARDY (that never happened in GUTSY).  Where the heck does it get mounted....can't see it in /media??

TIA for any help

Sorry if it's been asked and answered....I did a fair amount of Googling before landing here ;-)

BTW...my searching mentioned setting the workgroup manually in /etc/smb.conf.....problem is I don't have that file.  I could add one, but shouldn't it be there by default??

Cheers

---

### Post by jimv on 2008-05-28
I'm having the same issue.  When I browse to a computer over the network, I cannot see the shares.  I can access them if I type the name though.  Anybody have any ideas?

---

### Post by ColdFusionEESG on 2008-05-28
> **jimv said:**
> I'm having the same issue.  When I browse to a computer over the network, I cannot see the shares.  I can access them if I type the name though.  Anybody have any ideas?

Good to know I'm not alone ;-)

BTW...in case it matters...

My HARDY install was an upgrade from Gutsy and not  afresh install

Cheers

---

### Post by jimv on 2008-05-28
Mine's a fresh install, and I can't see shares at home on my workgroup, or at work on the domain.  I can see all the computers and subdomains at work though.

---

### Post by jimv on 2008-05-28
I found two interesting posts that might help...but I can't test until I get home tonight.

> I had been experiencing the same symptoms describe in a number of threads about issues accessing Windows shares. I solved of my problems accessing Windows shares by...

    * Go to System>Administration>Network
    * Select the General Tab of the Network Settings window.
    * Set Domain Name to be the same as your home network workgroup name.


I can now browse all of my machines and their shared folders through Places>Network

AND
> 
I have successfully solved my problem. It had to do with the fact that I was using OpenDNS namerservers. I had to add my network name as an exception. on the OpenDNS dashboard. I noticed that the address being pinged was 208.67.217.130 and that it was close to the actual OpenDNS nameservers;

nameserver 208.67.222.222
nameserver 208.67.220.220

So I went to the OpenDNS site and poked around until I found the dashboard exceptions page, added my network name and now I can browse my network and all shared folders from any of my computers to any other computer.

It certainly was a strange problem that only affected my Linux computers on my network. I sincerely appreciate the help I received.

---

### Post by ColdFusionEESG on 2008-05-28
> **jimv said:**
> I found two interesting posts that might help...but I can't test until I get home tonight.



AND

FIRST FINDING
Well the first one is a known issue in HARDY and caused me some serious grief with package managers and terminal.  I tried that "fix" before posting and it recreates the initial problem I had.

When adding an entry for "Domain", it automatically adds the domain/workgroup to one of my HOST entries causing termianl and package managers to outright fail.  The entry is IP 127.0.0.1 with host name of bryan-laptop.  When I add a domain entry, that host entry gets changed to bryan-laptop.FUTURAMA (FUTURAMA being my workgroup).  When the domain entry is in place, I still get the same bad behavior from Nautilus.

SECOND FINDING
Well I don't use OpenDNS, so I doubt that's the issue for me ;-)


Cheers

---

### Post by jimv on 2008-05-29
Bump

---

