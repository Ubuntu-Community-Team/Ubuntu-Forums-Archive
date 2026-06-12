---
title: "AutoFS with NIS broken in 14.04 LTS?"
date: 2014-04-29
forum: Networking &amp; Wireless
---

### Post by Stefan_Knig on 2014-04-29
Hello Forum,

I have several machines using NIS and autoFS in 12.04 LTS.
in nsswitch.conf automount is set to get its maps via nis (auto.master and auto.home) and this works great.

However, after an ugrade to 14.04 LTS this is broken. NIS is still working and serves the maps (e.g. "ypcat auto.master" or "ypcat auto.home") but autoFS does not seem to "understand".
Restarting autoFS does not solve the problem, so I guess it is not the old problem of pre 12.04 releases....

For testing purposes I tried a clean, new install of 14.04 LTS with the same results.
Any ideas or hints are appreciated!

thanks and regards
Stefan

---

### Post by copperhat on 2014-06-28
I am having the same problem. I should know better than to upgrade.

I added the following line to /etc/nsswitch.conf:
automount:      files nis

and then
    sudo /etc/init.d/autofs restart
and it seems to work.

However, after reboot, I have to do the restart again. In a previous version there was some pre-start mumbo jumbo based on statd that worked but statd doesn't exist in the stock 14.04. Will update if I have any progress.

I'm tired of dealing with nfs/autofs issues **everytime** I upgrade. Is it so unusual?

---

### Post by DoubelD on 2015-04-25
> **copperhat said:**
> 
I added the following line to /etc/nsswitch.conf:
automount:      files nis

and then
    sudo /etc/init.d/autofs restart
and it seems to work.

I have been having this problem too - I have a tried bunch of things and reinstalled it a multitude of times (server and client) with the same results - It just doesn't work.  As someone said on this forum Fedora just works, whats up with ubuntu 

On the clients if I add auto.home and or auto.xxx to the auto.master file and populate those files then it works. BUT whats the point of autoFS if I have to do that. Make on change to a auto.xxx file and I have to push the changes to all the clients manually ????

I just rebuild the NIS/AutoFS server again so I can start fresh . 

Is there a how to  on installing NIS/AutoFS for both Client and Server ? 

I'll have to try adding automout: files nis to the nsswitch.conf file and see what happens - do you do this on teh NIS/AutoFS server thr client or both ?

---

