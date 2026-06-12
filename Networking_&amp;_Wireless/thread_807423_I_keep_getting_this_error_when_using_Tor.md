---
title: "I keep getting this error when using Tor"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by borkborkbork on 2008-05-25
```

Exception in sandbox evaluation. Date hooks not applied:
[Exception... "Not enough arguments"  nsresult: "0x80570001 (NS_ERROR_XPC_NOT_ENOUGH_ARGS)"  location: "JS frame :: chrome://torbutton/content/torbutton.js :: anonymous :: line 1722"  data: no]

```
and ideas?

---

### Post by noksagt on 2008-05-30
torbutton doesn't work with the firefox 3 that is shipped with ubuntu yet.  You can uncheck "hook dangerous javascript (crucial)" in the security preferences of the extension to not see the warning.  But note that you will be less private than if you used torbutton on a supported browser (such as firefox 2) with that setting turned on.  You may want to restrict javascript in some other way or this might not be crucial to you or you may want to firefox 2 until torbutton is updated.

---

