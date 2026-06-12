---
title: "Why 'v' twice in 'man tar' examples (i.e. 'tar -xvvzf foo.tar.gz')?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by tnek on 2009-01-24
Hi,

Why is 'v' specified twice in the examples of the man pages of tar command? I know -v is verbose, as it says in the man page. But specifying 'v' twice, is that an error or does it actually set some kind of functionality?

From 'man tar':
> 
EXAMPLES
       tar -xvvf foo.tar
              extract foo.tar

       tar -xvvzf foo.tar.gz
              extract gzipped foo.tar.gz

       tar -cvvf foo.tar foo/
              tar contents of folder foo in foo.tar


---

### Post by Paqman on 2009-01-24
It just makes it more verbose, IIRC.

---

### Post by Iowan on 2009-01-24
_V_ery _v_erbose? :-k

---

### Post by tnek on 2009-01-24
If that's the case, why is it not documented in the man page? :confused:

---

### Post by tnek on 2009-01-24
It was documented in the *source code*, I didn't think to look there, doh! ;)

From the source (starting at line 288 )
```
src/common.h-288-/* Count how many times the option has been set, multiple setting yields
src/common.h-289-   more verbose behavior.  Value 0 means no verbosity, 1 means file name
src/common.h-290-   only, 2 means file name and all attributes.  More than 2 is just like 2.  */
```

---

