---
title: "NetMate make error"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by bison0927 on 2009-10-08
Hi all, I am a newbie to linux, and my os is ubuntu9.04(jaunty), I am trying to install netmate-0.9.4, I download the .gz packages, and the required linraries, install them and also their -dev versions to get .h files, but there are still errors, so anyone please help me out? 

Thank you very much!
///////////////
 In file included from testexp.cc:31:
../../src/include/stdincpp.h:46:22: error: multimap.h: No such file or directory
../../src/include/stdincpp.h:47:22: error: hash_map.h: No such file or directory
../../src/include/stdincpp.h:58:21: error: iomanip.h: No such file or directory
../../src/include/stdincpp.h:59:23: error: streambuf.h: No such file or directory
testexp.cc: In function 'char* getErrorMsg(int)':
testexp.cc:121: warning: deprecated conversion from string constant to 'char*'
testexp.cc: In function 'char* getModuleInfo(int)':
testexp.cc:127: warning: deprecated conversion from string constant to 'char*'
make[3]: *** [testexp.lo] Error 1
make[3]: Leaving directory `/home/gzou/netmate-0.9.4/src/export_modules'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/gzou/netmate-0.9.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gzou/netmate-0.9.4'
make: *** [all] Error 2

---

