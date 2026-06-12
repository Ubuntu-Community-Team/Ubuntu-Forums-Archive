---
title: "Installing Linux for the 1st time"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by cruggeri on 2009-02-12
Hello,

Brand new to Forum/Linux. I have had a server in my closet for quite awhile now meaning to do something with it. Of course, only working in the windows world and having absolutely no linux experience whatsoever until last night, the obvious thing to do was to download and attempt to install Ubunto Desktop version 8.1on this Dell Poweredge 2400. So, of course the story goes, it did not work( failed on File copy and referenced no FAT Partition in the log).
 So, aside from R'ingTFM (already have about 1000pgs of reading sitting on my desk that needs to come before that), is it feasible to believe I could easily accomplish this install. It will boot and run from the CD and I did check the disk for errors?

Not looking for someone to do this for me, but, could I get it done and read later (goal is to use VMWare in this environment for starters).

Regards,

Chris

---

### Post by Dr Small on 2009-02-12
> **cruggeri said:**
> Not looking for someone to do this for me, but, could I get it done and read later (goal is to use VMWare in this environment for starters).

Without the willingness to learn, later never comes.

---

### Post by donkyhotay on 2009-02-12
So the download itself failed? Where were you downloading from? If you're familiar with VM's then definitely use that to learn, but ubuntu can be installed with wubi which allows you to boot into ubuntu natively but it's installed within your windows partition as a linux program. If you want to uninstall you just boot windows and go to add/remove programs. This is my recommendation as you don't have the oddities VM's can occasionally give you and also don't have the risk of messing up windows that dual-booting can sometimes have.

//edit: if the problem wasn't with the download then let us know more clearly what you were doing during the install.

---

### Post by alphacrucis2 on 2009-02-12
> **cruggeri said:**
> Hello,

Brand new to Forum/Linux. I have had a server in my closet for quite awhile now meaning to do something with it. Of course, only working in the windows world and having absolutely no linux experience whatsoever until last night, the obvious thing to do was to download and attempt to install Ubunto Desktop version 8.1on this Dell Poweredge 2400. So, of course the story goes, it did not work( failed on File copy and referenced no FAT Partition in the log).
 So, aside from R'ingTFM (already have about 1000pgs of reading sitting on my desk that needs to come before that), is it feasible to believe I could easily accomplish this install. It will boot and run from the CD and I did check the disk for errors?

Not looking for someone to do this for me, but, could I get it done and read later (goal is to use VMWare in this environment for starters).

Regards,

Chris

Not enough detail to figure out exactly what problem you are having. However, the Poweredge presumably has a hardware RAID controller. You may have to use the Dell setup software to configure the RAID controller before you can proceed with the Ubuntu install. I installed CentOS on one of those last year and I vaguely recall having to do the above.

---

### Post by cruggeri on 2009-02-13
Thanks to all for replies and apologies on delayed response.

 I wanted to get to a point where I could give you some specific feedback as to what problems I was having...which led me a log file...leading to wanting to try something else ...which led to me getting it installed...fyi...and apologies for not really have good detail on how...but the log said something along the lines of not finding a FAT partition. I found an app...Gparted of some flavor that allowed me to format partitions and complete the installation successfully.

Thanks Again
Chris

---

### Post by Kain000 on 2009-02-13
> **cruggeri said:**
> Thanks to all for replies and apologies on delayed response.

 I wanted to get to a point where I could give you some specific feedback as to what problems I was having...which led me a log file...leading to wanting to try something else ...which led to me getting it installed...fyi...and apologies for not really have good detail on how...but the log said something along the lines of not finding a FAT partition. I found an app...Gparted of some flavor that allowed me to format partitions and complete the installation successfully.

Thanks Again
Chris

Glad you got up and running, 

[CENTER][SIZE="6"]welcome home to Ubuntu[/SIZE][/CENTER]

---

