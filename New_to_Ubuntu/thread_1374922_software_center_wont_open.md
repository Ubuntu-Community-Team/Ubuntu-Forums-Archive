---
title: "software center wont open"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by libihero on 2010-01-07
when putting software center in the terminal, i get this error:
```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 43, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 36, in <module>
    from softwarepane import SoftwarePane, wait_for_apt_cache_ready
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 38, in <module>
    from appdetailsview import AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 52, in <module>
    from widgets.wkwidget import WebkitWidget
  File "/usr/share/software-center/softwarecenter/view/widgets/wkwidget.py", line 27, in <module>
    import webkit
  File "/usr/lib/pymodules/python2.6/webkit/__init__.py", line 19, in <module>
    import webkit
ImportError: /usr/lib/libwebkit-1.0.so.2: undefined symbol: soup_content_decoder_get_type

```

---

### Post by slakkie on 2010-01-07
Could you post the all the output? We are not the developers, so a bit more context would be nice.

---

### Post by libihero on 2010-01-07
could u explain what u want me to post? i try opening it from the applications bar and it doesnt pop up, when i try opening it in terminal this is what i get

---

### Post by soro2005 on 2010-01-07
I think the webkit-team ppa has temporarily screwed up and installed a version of some packages that were a little ahead of their time. My solution is at [http://ubuntuforums.org/showpost.php?p=8626026&postcount=3](http://ubuntuforums.org/showpost.php?p=8626026&postcount=3)

---

