---
title: "Problem installing tilp...? configure error"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by nene7 on 2010-03-26
hi, 
 I am tring to install tilp 6.81 in my mini 10v with ubuntu remix 9.10, i extract the .tar.gz file then i wrote in the terminal:
> ./configurebut is say configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
I copy the info of the "config.log" and creat a .txt file if help.
sorry i divide in two part because the file txt are more big of limite forum

---

### Post by mzalfres on 2010-03-26
Hi,

check if you have "g++" package installed. If not, install with all dependencies. Should help...

Regards.

---

### Post by gmargo on 2010-03-27
Install the **build-essential** package, which will pull in g++.

---

### Post by nene7 on 2010-03-30
I install the g++ with his dependencies and now i have other problem. 
> 
checking for ticables >= 3.8.0... Package ticables was not found in the pkg-config search path. Perhaps you should add the directory containing `ticables.pc' to the PKG_CONFIG_PATH environment variable No package 'ticables' found
configure: error: Library requirements (ticables >= 3.8.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


---

### Post by gmargo on 2010-03-30
Memorize that type of error message - it almost always means that you need a "-dev" package installed.  In this case you need the **libticables3-dev** package.

[http://packages.ubuntu.com/karmic/libticables3-dev](http://packages.ubuntu.com/karmic/libticables3-dev)

---

