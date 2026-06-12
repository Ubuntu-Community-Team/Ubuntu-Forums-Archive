---
title: "init.d issue after installing 3ware-3dm2-binary"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by scribbles on 2008-12-03
After installing 3ware-3dm2-binary from the repo's all went well but I got this message ```
update-rc.d: warning: /etc/init.d/3dm2 missing LSB style header
Starting 3ware 3DM 2 Disk Management Utility: 3dm2.
``` I can log into the utility via Firefox just fine and everything is working. I can even ```
sudo /etc/init.d/3dm2 restart
``` without error. Is there something I should be concerned with? I do not know what a LSB style header is...

What does update-rc.d do?

---

### Post by Titan8990 on 2008-12-03
> What does update-rc.d do?

It adds the program to the startup list (prior to user log in).

---

### Post by Michael.Godawski on 2008-12-03
There is a comparable bug in the TimeVault application:
[https://bugs.staging.launchpad.net/timevault/+bug/298222](https://bugs.staging.launchpad.net/timevault/+bug/298222)

Perhaps you can also file a bug report, see here how:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by scribbles on 2008-12-03
```
sudo ubuntu-bug 3ware-3dm2-binary
``` gave me ```
modinfo: could not open cdrom: No such device
modinfo: could not open cdrom: No such device
kfmclient(9769) ClientApp::doIt: Creating ClientApp
Launched ok, pid = 9774

``` which took me to [this website]("https://bugs.launchpad.net/ubuntu/+source/3ware-3dm2-binary-i386/+filebug/mAjjD4Q1RV8zLpFTlMmBJ52Jwja?").

Is there a different command for kubuntu or is this portion the same?

---

### Post by scribbles on 2008-12-03
This might've come from a debian repo instead of an ubuntu repo, I did add one recently...

---

### Post by scribbles on 2008-12-03
What should I do to make this start on boot since this failed?

---

### Post by dean123 on 2008-12-04
> **scribbles said:**
> What should I do to make this start on boot since this failed?


You should copy 3dm2 to /usr/sbin then modify your rc.local
to include this command

/usr/sbin/3dm2

3dm2 is a deamon, not a startup script. Hope it helps.

---

### Post by scribbles on 2008-12-06
```
exec /usr/sbin/3dm2 boot
```
???

I just ran /etc/init.d/3dm2 restart, it restarted without error but now the mgmt page doesnt show up at localhost:888 like it did previously...

---

### Post by scribbles on 2008-12-17
I rebooted after a big adept update and localhost:888 still wasn't available so I tried ```
sudo /usr/sbin/3dm2 start
``` and got ```
Starting 3ware 3DM 2 Disk Management Utility: Usage: /etc/init.d/3dm2 {start|stop|restart|force-reload}
``` and another prompt. The web interface is still not available. Surely there's documentation on issues like this?

---

### Post by scribbles on 2008-12-18
bump

---

### Post by scribbles on 2008-12-19
No one?

---

### Post by scribbles on 2008-12-30
bump.

---

