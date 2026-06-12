---
title: "Gwibber Problem"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Azhtabak on 2009-09-11
I'm having a problem installing gwibber. I've installed it and tried to run it and it spits out the following error:

```

/usr/lib/python2.6/dist-packages/gwibber/microblog/support/facelib.py:47: DeprecationWarning: the md5 module is deprecated; use hashlib instead                   
  import md5                                                                     
The messenger is now down                                                        
Segmentation fault

```

I mv hashlib.py and hashlib.pyc into that folder and now get the following error instead:

```

Traceback (most recent call last):                                              
  File "/usr/bin/gwibber", line 55, in <module>                                 
    from gwibber.client import GwibberClient                                    
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 8, in <module>
    import time, os, threading, logging, mx.DateTime, hashlib                   
ImportError: No module named hashlib
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 38, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 21, in <module>
    import fileutils
  File "/usr/lib/python2.6/dist-packages/apport/fileutils.py", line 16, in <module>
    from packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 18, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 7, in <module>
    from apt.package import Package
  File "/usr/lib/python2.6/dist-packages/apt/package.py", line 27, in <module>
    import urllib2
  File "/usr/lib/python2.6/urllib2.py", line 91, in <module>
    import hashlib
ImportError: No module named hashlib

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 55, in <module>
    from gwibber.client import GwibberClient
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 8, in <module>
    import time, os, threading, logging, mx.DateTime, hashlib
ImportError: No module named hashlib

```

Any ideas? :confused:

---

