---
title: "google gagdets error"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by cybuss on 2009-10-20
Selecting previously deselected package google-gadgets.
(Reading database ... 211714 files and directories currently installed.)
Unpacking google-gadgets (from google-gadgets_0.10.5-1~getdeb2_i386.deb) ...
dpkg: dependency problems prevent configuration of google-gadgets:
 google-gadgets depends on flex; however:
  Package flex is not installed.
dpkg: error processing google-gadgets (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Errors were encountered while processing:
 google-gadgets


i have no comment other then how do i fix lol

---

### Post by martrn on 2009-10-20
```
sudo apt-get install flex
```

Install the flex package and/or other necessary dependencies first.

---

### Post by cybuss on 2009-10-20
thanks, that fixed it lol

---

