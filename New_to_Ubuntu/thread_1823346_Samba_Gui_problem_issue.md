---
title: "Samba Gui problem issue"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by tonix15 on 2011-08-11
Guys can't remove system-config-samba..help me out..

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
(Reading database ... 227982 files and directories currently installed.)
Removing system-config-samba ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2327, in <module>
    main()
  File "/usr/bin/pycentral", line 2321, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1673, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.5
dpkg: error processing system-config-samba (--remove):
 subprocess installed pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2327, in <module>
    main()
  File "/usr/bin/pycentral", line 2321, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1493, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.5
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 system-config-samba

---

