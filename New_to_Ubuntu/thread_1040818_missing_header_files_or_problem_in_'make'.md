---
title: "missing header files or problem in 'make'"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by shehroz on 2009-01-15
Hello,
I am trying to install a package called netmate-0.0.4 on ubuntu 8.10. While doing a 'make' it gave me these errors [I am doing installation using sudo -i]

In file included from testexp.cc:31:
../../src/include/stdincpp.h:46:22: error: multimap.h: No such file or directory
../../src/include/stdincpp.h:47:22: error: hash_map.h: No such file or directory
../../src/include/stdincpp.h:58:21: error: iomanip.h: No such file or directory
../../src/include/stdincpp.h:59:23: error: streambuf.h: No such file or directory
testexp.cc: In function 'char* getErrorMsg(int)':
testexp.cc:121: warning: deprecated conversion from string constant to 'char*'
testexp.cc: In function 'char* getModuleInfo(int)':
testexp.cc:127: warning: deprecated conversion from string constant to 'char*'
make[2]: *** [testexp.lo] Error 1
make[2]: Leaving directory `/home/shehroz/Documents/netAI-0.1/install/netmate-0.9.4/src/export_modules'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/shehroz/Documents/netAI-0.1/install/netmate-0.9.4/src'
make: *** [install-recursive] Error 1

In order to get the missing .h file, I did apt-get install build-essential and apt-get install linux-headers-2.6.27-7-generic (my kernel name), but still I dont get the missing .h files.

Now the question is :
1. How do i get those missing .h file (multimap.h, hashmap.h, iomanip.h, and streambuf.h)
2. Is make really failing bcoz of these errors? Can anyone throw some light.

Any help will be appreciated.
Regards
Shrz

---

### Post by shehroz on 2009-01-15
Hello,
I am trying to install a package called netmate-0.0.4 on ubuntu 8.10. While doing a 'make' it gave me these errors

In file included from testexp.cc:31:
../../src/include/stdincpp.h:46:22: error: multimap.h: No such file or directory
../../src/include/stdincpp.h:47:22: error: hash_map.h: No such file or directory
../../src/include/stdincpp.h:58:21: error: iomanip.h: No such file or directory
../../src/include/stdincpp.h:59:23: error: streambuf.h: No such file or directory
testexp.cc: In function 'char* getErrorMsg(int)':
testexp.cc:121: warning: deprecated conversion from string constant to 'char*'
testexp.cc: In function 'char* getModuleInfo(int)':
testexp.cc:127: warning: deprecated conversion from string constant to 'char*'
make[2]: *** [testexp.lo] Error 1
make[2]: Leaving directory `/home/shehroz/Documents/netAI-0.1/install/netmate-0.9.4/src/export_modules'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/shehroz/Documents/netAI-0.1/install/netmate-0.9.4/src'
make: *** [install-recursive] Error 1

In order to get the missing .h file, I did apt-get install build-essential and apt-get install linux-headers-2.6.27-7-generic (my kernel name), but still I dont get the missing .h files.

Now the question is :
1. How do i get those missing .h file (multimap.h, hashmap.h, iomanip.h, and streambuf.h)
2. Is make really failing bcoz of these errors? Can anyone throw some light.

Any help will be appreciated.
Regards
Shrz

---

### Post by overdrank on 2009-01-15
Hi and please do not create multiple threads on the same issue. Threads merged :)

---

### Post by baruch60610 on 2009-01-15
I'm not sure exactly what you're trying to compile, but you may need to find the program with a '-dev' suffix.  That '-dev' suffix indicates a development version, which contains the headers.  However, as I said, I'm not sure which program is looking for those headers.

Since netmate isn't in the repository, you may need to go back to where you got it, and see whether they offer a set of header files among the source.  HTH.

---

### Post by bison0927 on 2009-10-08
> **shehroz said:**
> Hello,
I am trying to install a package called netmate-0.0.4 on ubuntu 8.10. While doing a 'make' it gave me these errors [I am doing installation using sudo -i]

In file included from testexp.cc:31:
../../src/include/stdincpp.h:46:22: error: multimap.h: No such file or directory
../../src/include/stdincpp.h:47:22: error: hash_map.h: No such file or directory
../../src/include/stdincpp.h:58:21: error: iomanip.h: No such file or directory
../../src/include/stdincpp.h:59:23: error: streambuf.h: No such file or directory
testexp.cc: In function 'char* getErrorMsg(int)':
testexp.cc:121: warning: deprecated conversion from string constant to 'char*'
testexp.cc: In function 'char* getModuleInfo(int)':
testexp.cc:127: warning: deprecated conversion from string constant to 'char*'
make[2]: *** [testexp.lo] Error 1
make[2]: Leaving directory `/home/shehroz/Documents/netAI-0.1/install/netmate-0.9.4/src/export_modules'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/shehroz/Documents/netAI-0.1/install/netmate-0.9.4/src'
make: *** [install-recursive] Error 1

In order to get the missing .h file, I did apt-get install build-essential and apt-get install linux-headers-2.6.27-7-generic (my kernel name), but still I dont get the missing .h files.

Now the question is :
1. How do i get those missing .h file (multimap.h, hashmap.h, iomanip.h, and streambuf.h)
2. Is make really failing bcoz of these errors? Can anyone throw some light.

Any help will be appreciated.
Regards
Shrz

Did you fix this problem? In fact, I am slo trying to install NetMate0.9.4, and meet the same problems, I download the required packages and also the -dev version, but I got the same error message, could you please help me out?

Thanks

---

