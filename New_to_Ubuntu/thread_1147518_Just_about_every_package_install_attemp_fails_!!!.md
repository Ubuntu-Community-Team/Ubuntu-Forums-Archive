---
title: "Just about every package install attemp fails !!!"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by k6mkf on 2009-05-03
I upgraded to Ubuntu 9.04.  Gnome seems to be working, but just about every package I try to install: Sun Java; compiz, etc. bombs out in dpkg like this:

mike@mike-ubuntu7:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up unixodbc (2.2.11-16build3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing unixodbc (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java6-bin:
 sun-java6-bin depends on unixodbc; however:
  Package unixodbc is not configured yet.
dpkg: error processing sun-java6-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on sun-java6-bin (= 6-13-1) | ia32-sun-java6-bin (= 6-13-1); however:
  Package sun-java6-bin is not configured yet.
  Package ia32-sun-java6-bin is not installed.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
Setting up postfix (2.5.5-1.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: numeric hostname: 04
newaliases: fatal: file /etc/postfix/main.cf: parameter mydomain: bad parameter value: 04
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 75
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-fonts:
 sun-java6-fonts depends on sun-java6-jre (>= 6-13-1); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-fonts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-13-1); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          ldconfig deferred processing now taking place
Errors were encountered while processing:
 unixodbc
 sun-java6-bin
 sun-java6-jre
 postfix
 bsd-mailx
 sun-java6-fonts
 sun-java6-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@mike-ubuntu7:~$ 

Tried searching the forums/bugs for unixodbc references, but they're all over the map.

[B]Could somebody please take pity on a newbie and point me in the right direction?

Thanks![/B]  :confused:

---

### Post by AdmiralAdama on 2009-05-03
i put this up earlier on another thread, see if it helps explain what i did to get it working. 

 Smile  Re: 8.10 to 9.04 Upgrade hesitation
I upgraded to 9.04 NBR from 8.10 NBR using the automated method and it seemed smooth but took a very long time.

However, the system behaved erratically soon afterwards. I was unable to apt-get install certain well known packages like eee-control (from greg.geekmind.org) on the new OS.

It almost seemed that the unit was rebooting as 9.04 but still had some 8.10 in it. Upon closer examination and remembering that I previously made many attempts to get eee-control (my favorite fan control package) working I realized that a long time ago I installed some kernel patches or enhancements that were required (perhaps not, not sure) to get the fan control module to work. This involved learning about ACPI systems and trying different packages (and many uninstalls of them) to finally end up with eee-control working on my eeePC 1000.

Yes, therefore it seems I ended up with a 8.10 install that was modified to a point where the 9.04 process could not fully take over.

So, I decided to do a full fresh install via flash drive boot and it only took about 3 hours to get the new system to the point where everything is just the way I like it with all of my home stuff restored.

This includes the following:

reformat partition via install utility
overlay home mount with second SSD drive using utility
emacs-snapshot
emacs-goodies-el
firefox multimedia add-ins
eee-control
restore all custom software (only Komodo)
restore home directory with all my settings for emacs and browser bookmarks
reset bluetooth mouse settings and internet access

Overall, 3 hours for a complete system re-install is acceptable considering any Windows update can take several days to get it to the same point.

Some would ask why is the eee-control package so important for me? With the 8+32 GB SSD drives in the eeepc 1000, smart fan control can allow the netbook to operate nearly silently most of the time. If you take the netbook outside and it's cooler, sometimes the fan doesn't run at all. The smart part of the fan control just uses the ability of the fan to run at different speeds to cool the unit down according to the internal temperature of the CPU. The default ACPI controls seem to just overuse the full speed too much. Also, this should conserve battery usage as well.

---

### Post by k6mkf on 2009-05-03
Thanks, Admiral !!

A complete re-installation seems a lot for me to tackle.  My Ubuntu 8.10 was standard vanilla, and the upgrade went very smoothly.

My problems seem to be all around this:

Setting up unixodbc (2.2.11-16build3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing unixodbc (--configure):
 subprocess post-installation script returned error exit status 2

This is the consistent failure mode, so I guess I'll keep looking around for this specific problem.  Thanks!!  :)

---

### Post by k6mkf on 2009-05-03
I finally removed postfix, java and unixodbc completely, then installed unixodbc.  unixodbc installed correctly, so I'll reinstall java later. :P

---

