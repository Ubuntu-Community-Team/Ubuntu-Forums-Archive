---
title: "Click Modular Router installing problem"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by 7up on 2007-01-09
I'm having a problem installing this Click Modular Router software.

tried:
```
./configure --prefix=$HOME/click/
make install
```

got:
```
click-elem2man: warning: category 'devices' begins with a lowercase letter (used in UMLSwitch)
click-elem2man: warning: category 'devices' begins with a lowercase letter (used in UMLSwitch)
cd .; ../missing makeinfo click.texi
WARNING: `makeinfo' is missing on your system. You should only need it if you modified a 
`.texinfo' file, or any other file indirectly affecting the aspect of the manual. The spurious 
call migh also be the consequence of using a buggy `make' (AIX, DU, IRIX). You might want 
to install the `Texinfo' package or the `GNU make' package. Grab either from any GNU 
archive site.
make[2]: *** [click.info] Error 1
make[2]: Leaving directory `/home/box/click-source/doc'
make[1]: *** [install-doc] Error 2
make[1]: Leaving directory `/home/box/click-source'
make: *** [install] Error 2
```

anyone knows what's happening here?
i tried both Dapper and Edgy + tried to install that 'texinfo', but still, it gave the same message.

I'd greatly appreciate any comments or suggestions

---

