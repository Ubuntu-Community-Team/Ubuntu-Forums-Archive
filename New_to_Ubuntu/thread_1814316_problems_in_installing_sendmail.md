---
title: "problems in installing sendmail"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by ram@iitr on 2011-07-29
i m new at ubuntu ,every time when i tried to install sendmail using _sudo apt-get install sendmail_, i found the following errors:(Please help)
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
(Reading database ... 295344 files and directories currently installed.)
Preparing to replace bandwidthd 2.0.1 (using .../bandwidthd_2.0.1+cvs20090917-3_i386.deb) ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by aeiah on 2011-07-29
it looks like the initiation file for the bandwidth daemon (/etc/init.d/bandwidthd) is corrupt. perhaps the whole package.


first id try and remove bandwidthd completley either through synaptic, or apt-get --purge remove

if that fails, safest thing would probably be to move the init.d script and see if that lets things go through
```

mv /etc/init.d/bandwidthd /etc/init.d/bandwidthd.old

```

if not, i would probably move it back and try and force the install

---

### Post by HermanAB on 2011-07-29
Hmmm, you are new and want to install sendmail - I sense a dissonance in the time-space continuum, as if ten billion butterflies suddenly took flight at once...

Sendmail is the kind of thing that will cause guru bearded UNIX administrators to run away screaming.  

My guess is that you probably should rather install Postfix or Citadel, not Sendmail.

---

