---
title: "two different error message when trying to upgrade"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by steeny124 on 2009-04-23
So, I wanted to upgrade to 9.04 but I hadn't yet upgraded to 8.10 from 8.04 due to this error message:


Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 113M free space on disk '/boot'. Please free at least an additional 77.7M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.



  I've tried running apt-get clean, but to no avail.  I know this has been a common problem already posted on. But I've not really found a posting that's been very helpful in giving me instructions I can understand.  I'm not very savvy on ubuntu. 

While trying to upgrade today, I've gotten a mix of the former error message and this one: 


An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.


Any help would be much appreciated.

---

### Post by steeny124 on 2009-04-23
bump

---

### Post by steeny124 on 2009-04-23
bump

Seriously, even a link to another posting would be helpful.  I'd really appreciate it.

---

### Post by MDSmith2 on 2009-04-23
On the first error, could you paste the output of the command df?
For the second one I am not sure on.

---

### Post by JoshuaRL on 2009-04-23
You might need to trim your installed applications a little to get some extra space in your root folder.  Or if you have everything in the same partition, try deleting some extra stuff you have in /home.  Usually everyone has a little they can get rid of.

For the other one, do you have any extra repos?  Like maybe Wine or PPAs?  If so, go into /etc/apt/sources.list and comment them out (put a # in front of them) to make APT not see them.  After upgrading, you can either take that out, or with things like Wine that change repos for disto-upgrades, fix them to what they should be.  I'm pretty sure that's the problem.

---

### Post by steeny124 on 2009-04-23
Thanks so much for your replies.  I'll be sure to get back to you later tonight when I'm able to follow all of your instructions.

---

### Post by steeny124 on 2009-05-01
> **JoshuaRL said:**
> You might need to trim your installed applications a little to get some extra space in your root folder.  Or if you have everything in the same partition, try deleting some extra stuff you have in /home.  Usually everyone has a little they can get rid of.

For the other one, do you have any extra repos?  Like maybe Wine or PPAs?  If so, go into /etc/apt/sources.list and comment them out (put a # in front of them) to make APT not see them.  After upgrading, you can either take that out, or with things like Wine that change repos for disto-upgrades, fix them to what they should be.  I'm pretty sure that's the problem.


Solved!

I cut down the repositories to just the canonical-supported and community-maintained software.

I also cleared out a lot of my old kernels, which took care of the /boot space issue.

It's amazing how EASY it was, I just needed the right instruction.

Thanks for all your help!

---

### Post by JoshuaRL on 2009-05-01
Glad everything worked out man.

---

