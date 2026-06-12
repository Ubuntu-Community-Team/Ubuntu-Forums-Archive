---
title: "Need help installing VMplayer"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by dorin.roseti on 2010-11-15
Hi.New to this forum and relativly new to linux.I currently have Ubuntu 10.10 instaled and i wish to install VMware Player.I went to this link [https://www.vmware.com/tryvmware/p/activate.php?p=player&lp=default](https://www.vmware.com/tryvmware/p/activate.php?p=player&lp=default) and downloaded tht bundle for linux 64bit.Didn't know what to do with it so i googled the issue.1st thing that popped out was a suggestion that said "sudo sh path-to-bundle" so i did that.I received this error message 
"VMware-Player-3.1.2-301548.x86_64.bundle: 110: Syntax error: newline unexpected".What next? I wish to install VM Player as soon as posible Thx

---

### Post by 2un@ on 2010-11-15
I'm the same as you...new.... & its a big headacke.
Taken me like several days to get VMware working - will try find some links for you OR 
Try Virtual box will be much easier & quicker

For Vmware installing on Ubuntu 10.10: i thrashed around the below:
1)Check your file downloaded from VMware's site isn't just a plain text file - i eventually found the link from VMware site was  not the right file unless i used the manual download link.
2)Follow here - [http://ubuntuguide.net/how-to-install-vmware-player-in-ubuntu-9-10](http://ubuntuguide.net/how-to-install-vmware-player-in-ubuntu-9-10)
read the readers comments also helps if your new and dumb like me..

Once you got it that far once the GUI appears you need to also patch the kernel as it gives "unable to build kernel modules" error
that link for fix here: [http://communities.vmware.com/thread/286119](http://communities.vmware.com/thread/286119)
how to install that here:[http://communities.vmware.com/thread/291915?tstart=15](http://communities.vmware.com/thread/291915?tstart=15)

Then maybe it works
  I'd guess alot of us newbies to Linux need to bring some Windows babies with us (enter Vmware) - the drama above as a 1st intro to Linux(altho its not really Linux's issues)i'm sure chases people back to Windows quite easily - i'd never used a UnIx terminal ever.

---

