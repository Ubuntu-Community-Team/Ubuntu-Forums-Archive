---
title: "Unfinished upgrade, impossible to install or remove any software"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by FaithlessPath on 2011-02-02
While I was upgrading from Lucid Lynx to Maverick Meerkat, my computer froze and it was impossible to continue the installation, so I had to restart it. 

Of course, I tried to re-continue the installation using the Update Manager and I got this message: Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

When I tried to use the Synaptic package manager: E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Then, I tried to manually run "sudo dpkg --configure -a" on the terminal, it said that "dpkg: parse error, in file '/var/lib/dpkg/updates/0070' near line 0:
 EOF after field name `' "

I really don't know what to do. I couldn't install even the Adobe Flash Player. 

I would be very grateful if someone could help me.

---

### Post by ajgreeny on 2011-02-02
The first thing to do, if you haven't already got backups, is run a live CD or USB and backup all your user files in /home/*username* to an external disk or DVDs just to make sure you don't loose them.

It could then be worth trying a rename of the file that dpkg is complaining about with ```
sudo mv /var/lib/dpkg/updates/0070 /var/lib/dpkg/updates/0070.bak
``` I have nothing in that folder on my system, so wonder if it is a temporary file that is made until the distro upgrade has finished, so it may even be worth trying to move it somewhere else entirely, then trying the update again.

However, I fear it is possible that you may have to start again from scratch, as it could be impossible for either anybody, or your system, to work out where the update had got to before it crashed.

---

### Post by Gotlieb on 2011-05-03
Hi,

You can do I had the same problem but to fix it I had to delete a config file in Filesystem > tmp > aptdemon folder (delete whole folder) 

If that works, please change thread status :)

---

