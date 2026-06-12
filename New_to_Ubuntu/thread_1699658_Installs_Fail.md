---
title: "Installs Fail"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by Shortstraw8 on 2011-03-04
This is the message I receive when I try to install anything from the software center. Any ideas on what I did or what to do?



installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 200653 files and directories currently installed.)
Removing abs-guide ...
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...
Setting up php5-fpm (5.3.3-1ubuntu9.3) ...
update-rc.d: warning: php5-fpm stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)
 * Starting PHP5 FPM...
Mar 03 22:32:34.506156 [WARNING] [pool www] pm.start_servers is not set. It's been set to 20.
Mar 03 22:32:34.506173 [ERROR] [pool www] the chdir path '/var/www' does not exist or is not a directory
Mar 03 22:32:34.506176 [ERROR] failed to post process the configuration
   ...fail!
invoke-rc.d: initscript php5-fpm, action "start" failed.
dpkg: error processing php5-fpm (--configure):
 subprocess installed post-installation script returned error exit status 255
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 php5-fpm
Setting up php5-fpm (5.3.3-1ubuntu9.3) ...
update-rc.d: warning: php5-fpm stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)
 * Starting PHP5 FPM...
Mar 03 22:32:34.894292 [WARNING] [pool www] pm.start_servers is not set. It's been set to 20.
Mar 03 22:32:34.894310 [ERROR] [pool www] the chdir path '/var/www' does not exist or is not a directory
Mar 03 22:32:34.894313 [ERROR] failed to post process the configuration
   ...fail!
invoke-rc.d: initscript php5-fpm, action "start" failed.
dpkg: error processing php5-fpm (--configure):
 subprocess installed post-installation script returned error exit status 255

---

### Post by sikander3786 on 2011-03-04
Try removing the offensive 'php5-fpm' package.

Applications > Accessories > Terminal:

```
sudo apt-get remove --purge php5-fpm
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Shortstraw8 on 2011-03-07
Yeah that worked thank you.

---

