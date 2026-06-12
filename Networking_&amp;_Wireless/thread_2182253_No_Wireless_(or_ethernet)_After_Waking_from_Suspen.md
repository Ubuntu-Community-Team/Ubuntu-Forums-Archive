---
title: "No Wireless (or ethernet) After Waking from Suspend"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by Gaboontoo on 2013-10-20
I've seen posts about this in the past (some going back to 2010) but nothing I've come across has worked. Simply, all networking is disabled after waking from suspend and re-enabling (at least via the network indicator) does nothing. At the moment, I'm most concerned about getting wireless to work after waking from suspend but I would of course like for the ethernet to be available as well if any fix is going to have to be permanent and not addressed through a bug fix.

As for what I've tried and has thus far not worked:
- Figuring out what wireless driver I'm using and creating files in: /etc/pm/config.d/
- Filenames have included: "config", "modules" and "unload_modules"
- Lines have included: SUSPEND_MODULES="$SUSPEND_MODULES rt2800pci" or just SUSPEND_MODULES="rt2800pci"

No combination of filename or line code above have worked and this problem did not exist before upgrading from 13.04 to 13.10. If it helps, this isn't a big box PC anymore as it's 8 years old and I've replaced everything but the motherboard and optical drive. I am running the 64-bit version of 13.10. I'm new here and though I'm OK with the terminal, I am far from having a substantial Linux background. So I appreciate any help that can be given with steps laid out fairly explicitly.

---

### Post by varunendra on 2013-10-23
Have you checked "/var/log/pm-suspend.log"? That or syslog may contain significant hints on what may be going wrong.

In syslog, the interesting part can be anywhere from the last instance of line "....**Command line: BOOT_IMAGE**..." upto where the resume suspend-resume cycle is completed. Would be easier to parse after a fresh boot (would still be hundreds of lines).

You can easily check the instance(s) of "**Command line**" lines by -
```
grep -n "Command line" /var/log/syslog
```
..command run after a fresh boot. The output will be prefixed with the no. of line(s) that is parsed, thus making it easy to find your starting point.

I would suggest to post both logs (only the above parsed part of syslog) at pastebin.ubuntu.com, and post back the pastebin link here. You may wish to examine the syslog part before posting to make sure there is no such data in it that you may consider sensitive.

---

### Post by marcinkowski on 2013-10-27
This seems to have solved the issue for me:

[http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153](http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153)

---

