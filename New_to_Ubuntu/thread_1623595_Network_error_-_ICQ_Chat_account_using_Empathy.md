---
title: "Network error - ICQ Chat account using Empathy"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by wstay on 2010-11-16
I got my ICQ Chat account set up using Empathy 2.30.2.
When I try to connect my Chat account, I cannot get it to connect and it keeps on having Network Error message.
Please refer to the attachment and is there any setting I should do or change to get my ICQ Chat account to connect?
Can someone please help.

---

### Post by TiloBunt on 2010-11-17
have the same, played around with different Server but same results:

Here part of the debug:

```
startOSCARSession response was missing something: <?xml version="1.0" encoding="UTF-8"?>
<response xmlns="http://developer.aim.com/xsd/aim.xsd"><statusCode>200</statusCode><statusText>Ok</statusText><data><ts>1289969011</ts><host>205.188.0.96</host><port>443</port><cookie>
....
```

might be related to:
[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/95d96265ca682e4d/dfd652b7284d9ac1?show_docid=dfd652b7284d9ac1&pli=1](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/95d96265ca682e4d/dfd652b7284d9ac1?show_docid=dfd652b7284d9ac1&pli=1)

---

### Post by TiloBunt on 2010-11-18
here the bug reports for it.

[https://bugs.launchpad.net/empathy/+bug/676060](https://bugs.launchpad.net/empathy/+bug/676060)

[https://bugzilla.gnome.org/show_bug.cgi?id=634984](https://bugzilla.gnome.org/show_bug.cgi?id=634984)

---

