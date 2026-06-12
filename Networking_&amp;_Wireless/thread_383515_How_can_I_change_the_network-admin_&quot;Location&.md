---
title: "How can I change the network-admin &quot;Location:&quot; from a script?"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by RichardBronosky on 2007-03-13
I like doing things from the command line.  I like writing shell scripts to perform mundane tasks that require lots of steps/clicks when done manually.  I like writing /etc/init.d scripts that tweak things after checking dmesg and other indicators to decide where I am and what I am booting my laptop for.  I cannot figure out how to do this for my network settings.

Right now, every time I boot my laptop in a new location (back and forth between home and office) I have to launch network-admin, authenticate, chose the desired Location preset, open the properties for the wireless interface, check the enable box, click ok to the properties box, click the apply button, and close the network-admin

Can this not be done from the command line?

I love Linux as a server, but this desktop Linux makes me struggle.  All tasks should be scriptable, should they not?

---

### Post by alexlzl on 2007-03-21
Every time you change network location, there is a different version of "/etc/network/interfaces" file gets written. What I did was keep a copy of each file with different suffix, e.g. interfaces.office, interfaces.home, then write a script to copy them over

```

#!/bin/sh
profile=$1
sudo ifdown eth0
sudo ifdown eth1
sudo cp ~/interfaces.$profile /etc/network/interfaces
sudo ifup eth0
sudo ifup eth1

```

One extra thing to take care if you need manual DNS suffix. If you use DHCP, The /etc/resolv.conf will be wiped out every time you bring the interface up, to overcome that, just change your /etc/dhcp3/dhclient.conf, add:

```

supercede mydomain.com;  

```

---

### Post by RichardBronosky on 2007-03-22
Thanks for the advice.  I decided to try:
1. tar up my entire /etc folder
2. change locations
3. repeat for all locations in a cycle twice over getting 2 tars for each location

I then diff'ed the contents to see what was changing.  There were a few files that would change.  Some locations, being more complex than others, would change more files.  So I built a list of all the files that any location effects and will try taring a version for each location.

What I didn't know was if there were:
1. any changes to files outside of the /etc folder
2. any changes to files inside the /etc folder which may also receive changes via some other activity for some other purpose which would be harmed by overwriting the file versus altering it on a per line basis
3. any commands that need to be ran to causes the results that I currently get from making changes via the network-admin GUI  (Your explanation of using ifup and ifdown are helpful.  I just wonder if there are others.)

One of the things I do is disable the wireless device if I am not in a location where I know I want to use wireless.  So, I don't think I want to call "ifup eth1" every time.

To make this solution more robust and safe for the general user, there could be some checking implemented.  Put all of the tars in a folder, like ${P_DIR}.  When changing profiles (as you call them) get a list of contents from ${profile}.tar.  Then for each file in ${profile}.tar, check each tar in ${P_DIR} to see if any of them contain the exact copy of the file.  If so, you are fine to overwrite, otherwise copy the file to ${P_DIR}/backups/${cur_file}.$(date +%Y%m%d%H%M%S) before overwriting.

Go and do that then you'd have something to put on sf.net and open up to the community.  Maybe I should do that.

If I want this to happen at boot, before the fstab mounts happen, I can put this in the proper /etc/rc*N*.d folder.

I already do a similar thing with a script that detects my rotated LCD and calls xrandr.  But, I have it in my System>Preferences>Sessions>Startup_Programs which means I get a sideways login screen.  I need to get this script called as soon as X starts so that it always looks right.  I realize that is a digression.  Any ideas?  I'll create a new thread for this if you do.

---

