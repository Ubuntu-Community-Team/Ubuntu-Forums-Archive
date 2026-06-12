---
title: "Ubuntu tweak"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by spribo on 2010-01-24
I recently installed Ubuntu Tweak in my Ubuntu Karmic, but when attempting to access the templates module, the following error message appears:
```
 Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/ubuntutweak/mainwindow.py", line 390, in setup_notebook
    page = module()
  File "/usr/lib/pymodules/python2.6/ubuntutweak/modules/templates.py", line 126, in __init__
    self.set_description(_('Templates path is wrong! The current path is point to "%s".\nPlease reset it to a folder under your Home Folder.') % USER_DIR)
AttributeError: 'Templates' object has no attribute 'set_description'

```How can I fix that?

---

