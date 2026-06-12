---
title: "Apache takes 100% cpu.."
date: 2009-01-15
forum: New to Ubuntu
---

### Post by mech7 on 2009-01-15
Does anybody know a way to log what is wrong? what scripts are taking many resources?

In the error log it says this, only some warnings and notice but I don't think this is the problem

Also restarting takes like 10 minutes
:

website@ns:~$ tail -f /var/log/apache2/error.log
[Fri Jan 16 10:21:07 2009] [warn] NameVirtualHost tnt.tntoffice.dev:0 has no VirtualHosts
[Fri Jan 16 10:21:07 2009] [warn] NameVirtualHost trc.tntoffice.dev:0 has no VirtualHosts
[Fri Jan 16 10:21:07 2009] [warn] NameVirtualHost trc2007.tntoffice.dev:0 has no VirtualHosts
[Fri Jan 16 10:21:07 2009] [warn] NameVirtualHost tripmagazine.tntoffice.dev:0 has no VirtualHosts
[Fri Jan 16 10:21:07 2009] [warn] NameVirtualHost usdathailand.tntoffice.dev:0 has no VirtualHosts
[Fri Jan 16 10:21:07 2009] [warn] NameVirtualHost voip.ela.tntoffice.dev:0 has no VirtualHosts
[Fri Jan 16 10:21:07 2009] [warn] NameVirtualHost voip.mofi.tntoffice.dev:0 has no VirtualHosts
[Fri Jan 16 10:21:07 2009] [warn] NameVirtualHost web.tntoffice.dev:0 has no VirtualHosts
[Fri Jan 16 10:21:07 2009] [notice] FastCGI: process manager initialized (pid 16589)
[Fri Jan 16 10:21:07 2009] [notice] Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_fastcgi/2.4.6 PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations

---

### Post by utnubuuser on 2009-01-16
Hi -- Wasn't there some issue with the fastcgi module?

---

### Post by mech7 on 2009-01-16
Am not sure? when i kill the process after it goes back to normal again... only starting takes like 10 minutes :confused: I never see apache start so slow on any config:confused:

---

