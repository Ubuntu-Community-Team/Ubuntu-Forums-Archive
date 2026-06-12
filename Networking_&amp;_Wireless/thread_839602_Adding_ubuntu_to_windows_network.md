---
title: "Adding ubuntu to windows network"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by Dawgwalker on 2008-06-24
I installed 8.04 on a HP Pavilion that was running W2K and printer sharing to my Windows network.

How do I network 8.04 to the windows network so there is printer sharing on 8.04 to the windows pcs.

Do I use samba or is there a better solution?

What are step-by-step instructions please.

---

### Post by plewisfdx on 2008-06-24
First,

1. Make sure the printer works on Ubuntu, and each computer that will be printing has the correct drivers for their respective operating system.

Then, try one of these, in this order...

2a. System->Administration->Printing --- Server Settings
-- make sure "Share published printers connected to this system" is **checked** then click "apply".

**or**, if that doesn't work,


2b.[http://ubuntuguide.org/wiki/Dapper#How_to_print_on_remote_Ubuntu_machine_via_samba]("http://ubuntuguide.org/wiki/Dapper#How_to_print_on_remote_Ubuntu_machine_via_samba").

---

### Post by michwill on 2008-06-24
Not to confuse the issue, but you might also look into Webmin:


[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by Dawgwalker on 2008-06-24
The printer is now working from my Windows network and I am not sure what corrected the problem.  

I installed samba from some not very clear instructions.  Samba installed easily but I wasn't sure I had a user installed.

Verified that the printer was shared per suggestion above.

Went to Windows and saw the network printer as it appeared when served by a Windows server.  Had not seen before.  Was dual booting the computer it slaved to.

Could not print so reinstalled network printer under current name and everything worked.

Where is good documentation for samba?

Was samba the solution?

---

### Post by Dawgwalker on 2008-06-24
> **plewisfdx said:**
> First,

1. Make sure the printer works on Ubuntu, and each computer that will be printing has the correct drivers for their respective operating system.

Then, try one of these, in this order...

2a. System->Administration->Printing --- Server Settings
-- make sure "Share published printers connected to this system" is **checked** then click "apply".

**or**, if that doesn't work,


2b.[http://ubuntuguide.org/wiki/Dapper#How_to_print_on_remote_Ubuntu_machine_via_samba]("http://ubuntuguide.org/wiki/Dapper#How_to_print_on_remote_Ubuntu_machine_via_samba").
Running Hardy Herron 8.04.  Is there and equivalent quide?

---

### Post by plewisfdx on 2008-06-24
> **Dawgwalker said:**
> Running Hardy Herron 8.04.  Is there and equivalent quide?

Those steps should all be the same.  

There is one here: [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

It doesn't have the printing instructions yet.  They build it little by little, and the release is only 2 months old, so check back.

---

### Post by plewisfdx on 2008-06-24
> **Dawgwalker said:**
> Verified that the printer was shared per suggestion above.

Went to Windows and saw the network printer as it appeared when served by a Windows server.  Had not seen before.  Was dual booting the computer it slaved to.

Could not print so reinstalled network printer under current name and everything worked.

Where is good documentation for samba?

Was samba the solution?

I'm not sure, but I think the "sharing" of the printer you did via the "system->administration->printing" sets up samba (or cups) for you.  Since its meant to be windows friendly, I imagine it sets up the samba config for you and shares it that way.

Read this thread for some samba help. [http://ubuntuforums.org/showthread.php?t=365326](http://ubuntuforums.org/showthread.php?t=365326)

Somewhere on there it leads you to an ubuntuguide.org for edgy, a previous release.  Samba instructions will most likely not change much from release to release, so don't be afraid to read up on any info like this.  Ubuntu is the key, other distro samba info may not work for you. (Unless its debian)

---

