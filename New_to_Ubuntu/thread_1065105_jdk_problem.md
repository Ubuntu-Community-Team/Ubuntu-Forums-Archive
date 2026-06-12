---
title: "jdk problem"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by chf on 2009-02-09
hello,

i downloaded the java jdk6 in order to replace the open jdk environment.

the apt-get now always gives an error message```
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

```

i have downloaded the documentation and moved it to /tmp/ owned by root, but when i press return in order to try again nothing happns. does someone now how to solve the issue?

chf

---

### Post by tzulberti on 2009-02-10
There is already a bug in launchpad on that package[0], and it seems to have a solution (see one of the last answers).

[0] [https://bugs.launchpad.net/synaptic/+bug/151183](https://bugs.launchpad.net/synaptic/+bug/151183)

---

