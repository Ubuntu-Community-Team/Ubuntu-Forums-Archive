---
title: "stream.h, iostream.h not found,but some ns2 header files include them."
date: 2009-06-16
forum: New to Ubuntu
---

### Post by sirene on 2009-06-16
Dear all,
I am a new Linux user.
I have the stream.h/iostream.h : No such file or directory problem.
I am using Ubuntu9.04. I am installing ns2.28 and 802.11e module ( available from TKN).
The header file mac-802_11e.cc contains "#include "stream.h" " and mac-802_11e.h contains "#include "iostream.h" ". When I try to MAKE, it gives me error stream.h/iostream.h :no such file or directory. 
I tried to search for the files separately, but they are not really present in my system. I found some zstream.h etc files in my system,but no stream.h and iostream.h.
Can anyone tell me,how can I MAKE the 802.11e module which contains those header files?
Thanks for your attention.

---

### Post by gsocker on 2009-06-16
GCC 4.3, which Jaunty uses, no longer includes the obsolete versions of the C++ header files. The C++ ones ending in .h have been deprecated since the 1998 C++ standard. Replace <iostream.h> with <iostream>, and add "using namespace std;" - without the qoutes - on the first line below the last #include. 
Your other option is to get the maintainer of the package to fix it.

---

### Post by sirene on 2009-06-23
Thank you very much gsocker.
I think it would solve my problem.

---

### Post by sirene on 2009-06-23
> **gsocker said:**
> GCC 4.3, which Jaunty uses, no longer includes the obsolete versions of the C++ header files. The C++ ones ending in .h have been deprecated since the 1998 C++ standard. Replace <iostream.h> with <iostream>, and add "using namespace std;" - without the qoutes - on the first line below the last #include. 
Your other option is to get the maintainer of the package to fix it.


Dear gsocker, should I change <stream.h> to <iostream> also?
Because there is no file name stream, I tried this.

---

