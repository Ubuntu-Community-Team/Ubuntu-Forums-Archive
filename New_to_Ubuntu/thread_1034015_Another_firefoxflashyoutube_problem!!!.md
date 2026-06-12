---
title: "Another firefox/flash/youtube problem!!!"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2009-01-07
I have an acer 4530 running on nvidia 9100m graphics.  YouTube plays video but it grays out every 3 seconds while the audio goes in and out as well which makes watching videos unbearable. Ive already tried removing flash, clean, autoremove, and reinstalling as other post have suggested but to no avail.  I don't think it is a problem with audio, but rather just flash video.  Any other suggestions?  Thank you.

---

### Post by pytheas22 on 2009-01-07
Which flash plugin are you using?  Adobe's proprietary plugin is still the most reliable, unfortunately.  The others--SWF and gnash--won't be as reliable.  I would recommend that you uninstall them if they exist:
```

sudo apt-get remove --purge swfdec gnash flashplugin-nonfree
```

Then reinstall flashplugin-nonfree (which is Adobe's plugin):
```

sudo apt-get install flashplugin-nonfree
```

Also, are you on a 64-bit system?  If so, the use of flashplugin-nonfree is more complicated because Adobe until recently only released a 32-bit build, and there was a lot of buggy and dirty hacking involved in making it work on 64-bit systems.  However, last month Adobe finally released a beta 64-bit version of its plugin, which may be worth trying if none of the above helps (all versions of Ubuntu are still currently using the 32-bit version, even on 64-bit systems; you would have to install the 64-bit version manually from Adobe's site).

---

### Post by FAMUgolfer on 2009-01-09
Thank you for the reply, sorry I couldn't respond earlier but the site was down.  I am on a 32-bit system.  Gnash is not installed.  The problem still persist.  I've even tried deleting the xpti.dat file in /.mozilla/plugins as well.

---

### Post by pytheas22 on 2009-01-09
Can you run Firefox from a terminal (just open a terminal and type 'firefox') and post any output that you get when flash crashes?

---

