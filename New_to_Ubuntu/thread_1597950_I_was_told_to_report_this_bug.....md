---
title: "I was told to report this bug...."
date: 2010-10-15
forum: New to Ubuntu
---

### Post by samw5 on 2010-10-15
p, li { white-space: pre-wrap; } Hello,
complete noobie here reporting as "told" when my laptop's being udpated:
I have Kubuntu Lucid 10.04....



Error Type: 
Error Value: coercing to Unicode: need string or buffer, exceptions.SystemError found
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2216, in 
main()
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2213, in main
run(args, options.single)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2175, in run
backend.dispatcher(args)
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 699, in dispatcher
self.dispatch_command(args[0], args[1:])
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 606, in dispatch_command
self.refresh_cache(force)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 202, in _locked_cache
func(*args, **kwargs)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1498, in refresh_cache
format_string(error.message))
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 723, in format_string
txt = unicode(text, encoding, errors='replace')




Now what?


Thanks

---

### Post by 73ckn797 on 2010-10-15
You need to go to: [https://bugs.launchpad.net/](https://bugs.launchpad.net/) and create an account and submit the info there.

---

