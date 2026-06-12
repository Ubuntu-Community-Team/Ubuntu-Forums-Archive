---
title: "gam_server, trackerd, nautilus  nfs homes terabytes of transfer."
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by eylisian on 2008-01-29
gam_server under 7.10 (or trackerd or nautilus) seems to be trying to poll even after being explicitly directed to use 'none' in /etc/gamin/gaminrc;
fsset nfs none 0

I have have a cronjob in place to kill gam_server every 40 min as I have read it starts on the hour. This may be helping but Ubuntu clients are still moving way more data than their CentOS counterparts. Last weekend the network was chunrned by a client to the tune of 2.7TB, the fileserver only has a 450GB combination of shares! 

I catch Nautilus running after users log out and find it's still ticking away at 6 percent of proc, nibbling at memory when the user isn't even sitting at the machine, they are gone and have been for hours (days!)... doing it's part to contribute to obfuscate troubleshooting =)

Have done my best to make sure Naut is not used as the defualt file tool, going so far as to install gtweakUI and disabling Naut from drawing the desktop. No avail.

Have installed the patch mentioned here; [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/44836](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/44836)
And have some hopes that user home directories will be at least un-mounted when they log off, know more about that later today.

Reason I am posting here? I'd like to roll Ubuntu Hardy eventually on the network for nfs clients. users like it better than CentOS, and so do I. I have a mirror set up for it (well, Gutsy right now) and have been devoting considerable resources to moving client desktops to Ubuntu. This issue will be a showstopper, period. We don't need workstations stress testing their subnet all the time and backups can't run on time due to clients trying to index or update themselves to the current state of the filesystem... 2.7 TB has been the record so far, but it's a common thing to see 200 - 500G of traffic churn over a weekend with the Ubuntu clients. My boss, the RedHat/CentOS guy... to him this is another reason why 'real' deployments don't roll Ubuntu. I am doing my best to prove him wrong but this looks like it's it for the experiment... I'm getting tired of it myself... checking ntop every hour, every day drags.

If anyone can offer up some solid advise on any of the above, thanks in advance. If more detail is needed, I am willing to provide that either here or a pastebin.

Cheers,
Robert

---

### Post by eylisian on 2008-02-09
I seem to have gotten it calmed down by a mix of the things that I have listed above, mileage varies between hosts (identical hardware, go figure). Since I have an Ubuntu mirror local, I might as well add Xubuntu and Kubuntu to it and see how they fair. At least my boss is understanding of the limited packaging in CentOS (even though he still loathes .deb distros... weird), so I have a reprieve in which to try Xubuntu out.

Which brings me to FAI... ;) But I'll start that somewhere else.

peas,
eylisian

---

