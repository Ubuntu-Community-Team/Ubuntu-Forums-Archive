---
title: "scim google pinyin"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by YQ002lc2 on 2009-12-29
I am trying to install scim google pinyin.

[http://code.google.com/p/scim-googlepinyin/](http://code.google.com/p/scim-googlepinyin/)

I get down to the "make" step and get a bunch of errors. 

Anyone else having this problem?

Thanks,

jpinson

---

### Post by YQ002lc2 on 2009-12-29
This is my error on make




make  all-recursive
make[1]: Entering directory `/home/jpinson/scim-googlepinyin'
Making all in src
make[2]: Entering directory `/home/jpinson/scim-googlepinyin/src'
Making all in share
make[3]: Entering directory `/home/jpinson/scim-googlepinyin/src/share'
/bin/bash ../../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..    -Werror -g -O2 -MT libpinyinime_la-dictbuilder.lo -MD -MP -MF .deps/libpinyinime_la-dictbuilder.Tpo -c -o libpinyinime_la-dictbuilder.lo `test -f 'dictbuilder.cpp' || echo './'`dictbuilder.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-dictbuilder.lo -MD -MP -MF .deps/libpinyinime_la-dictbuilder.Tpo -c dictbuilder.cpp  -fPIC -DPIC -o .libs/libpinyinime_la-dictbuilder.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-dictbuilder.lo -MD -MP -MF .deps/libpinyinime_la-dictbuilder.Tpo -c dictbuilder.cpp -o libpinyinime_la-dictbuilder.o >/dev/null 2>&1
mv -f .deps/libpinyinime_la-dictbuilder.Tpo .deps/libpinyinime_la-dictbuilder.Plo
/bin/bash ../../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..    -Werror -g -O2 -MT libpinyinime_la-dictlist.lo -MD -MP -MF .deps/libpinyinime_la-dictlist.Tpo -c -o libpinyinime_la-dictlist.lo `test -f 'dictlist.cpp' || echo './'`dictlist.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-dictlist.lo -MD -MP -MF .deps/libpinyinime_la-dictlist.Tpo -c dictlist.cpp  -fPIC -DPIC -o .libs/libpinyinime_la-dictlist.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-dictlist.lo -MD -MP -MF .deps/libpinyinime_la-dictlist.Tpo -c dictlist.cpp -o libpinyinime_la-dictlist.o >/dev/null 2>&1
mv -f .deps/libpinyinime_la-dictlist.Tpo .deps/libpinyinime_la-dictlist.Plo
/bin/bash ../../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..    -Werror -g -O2 -MT libpinyinime_la-dicttrie.lo -MD -MP -MF .deps/libpinyinime_la-dicttrie.Tpo -c -o libpinyinime_la-dicttrie.lo `test -f 'dicttrie.cpp' || echo './'`dicttrie.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-dicttrie.lo -MD -MP -MF .deps/libpinyinime_la-dicttrie.Tpo -c dicttrie.cpp  -fPIC -DPIC -o .libs/libpinyinime_la-dicttrie.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-dicttrie.lo -MD -MP -MF .deps/libpinyinime_la-dicttrie.Tpo -c dicttrie.cpp -o libpinyinime_la-dicttrie.o >/dev/null 2>&1
mv -f .deps/libpinyinime_la-dicttrie.Tpo .deps/libpinyinime_la-dicttrie.Plo
/bin/bash ../../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..    -Werror -g -O2 -MT libpinyinime_la-lpicache.lo -MD -MP -MF .deps/libpinyinime_la-lpicache.Tpo -c -o libpinyinime_la-lpicache.lo `test -f 'lpicache.cpp' || echo './'`lpicache.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-lpicache.lo -MD -MP -MF .deps/libpinyinime_la-lpicache.Tpo -c lpicache.cpp  -fPIC -DPIC -o .libs/libpinyinime_la-lpicache.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-lpicache.lo -MD -MP -MF .deps/libpinyinime_la-lpicache.Tpo -c lpicache.cpp -o libpinyinime_la-lpicache.o >/dev/null 2>&1
mv -f .deps/libpinyinime_la-lpicache.Tpo .deps/libpinyinime_la-lpicache.Plo
/bin/bash ../../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..    -Werror -g -O2 -MT libpinyinime_la-matrixsearch.lo -MD -MP -MF .deps/libpinyinime_la-matrixsearch.Tpo -c -o libpinyinime_la-matrixsearch.lo `test -f 'matrixsearch.cpp' || echo './'`matrixsearch.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-matrixsearch.lo -MD -MP -MF .deps/libpinyinime_la-matrixsearch.Tpo -c matrixsearch.cpp  -fPIC -DPIC -o .libs/libpinyinime_la-matrixsearch.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-matrixsearch.lo -MD -MP -MF .deps/libpinyinime_la-matrixsearch.Tpo -c matrixsearch.cpp -o libpinyinime_la-matrixsearch.o >/dev/null 2>&1
mv -f .deps/libpinyinime_la-matrixsearch.Tpo .deps/libpinyinime_la-matrixsearch.Plo
/bin/bash ../../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..    -Werror -g -O2 -MT libpinyinime_la-mystdlib.lo -MD -MP -MF .deps/libpinyinime_la-mystdlib.Tpo -c -o libpinyinime_la-mystdlib.lo `test -f 'mystdlib.cpp' || echo './'`mystdlib.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-mystdlib.lo -MD -MP -MF .deps/libpinyinime_la-mystdlib.Tpo -c mystdlib.cpp  -fPIC -DPIC -o .libs/libpinyinime_la-mystdlib.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-mystdlib.lo -MD -MP -MF .deps/libpinyinime_la-mystdlib.Tpo -c mystdlib.cpp -o libpinyinime_la-mystdlib.o >/dev/null 2>&1
mv -f .deps/libpinyinime_la-mystdlib.Tpo .deps/libpinyinime_la-mystdlib.Plo
/bin/bash ../../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..    -Werror -g -O2 -MT libpinyinime_la-ngram.lo -MD -MP -MF .deps/libpinyinime_la-ngram.Tpo -c -o libpinyinime_la-ngram.lo `test -f 'ngram.cpp' || echo './'`ngram.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-ngram.lo -MD -MP -MF .deps/libpinyinime_la-ngram.Tpo -c ngram.cpp  -fPIC -DPIC -o .libs/libpinyinime_la-ngram.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-ngram.lo -MD -MP -MF .deps/libpinyinime_la-ngram.Tpo -c ngram.cpp -o libpinyinime_la-ngram.o >/dev/null 2>&1
mv -f .deps/libpinyinime_la-ngram.Tpo .deps/libpinyinime_la-ngram.Plo
/bin/bash ../../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..    -Werror -g -O2 -MT libpinyinime_la-searchutility.lo -MD -MP -MF .deps/libpinyinime_la-searchutility.Tpo -c -o libpinyinime_la-searchutility.lo `test -f 'searchutility.cpp' || echo './'`searchutility.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-searchutility.lo -MD -MP -MF .deps/libpinyinime_la-searchutility.Tpo -c searchutility.cpp  -fPIC -DPIC -o .libs/libpinyinime_la-searchutility.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-searchutility.lo -MD -MP -MF .deps/libpinyinime_la-searchutility.Tpo -c searchutility.cpp -o libpinyinime_la-searchutility.o >/dev/null 2>&1
mv -f .deps/libpinyinime_la-searchutility.Tpo .deps/libpinyinime_la-searchutility.Plo
/bin/bash ../../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..    -Werror -g -O2 -MT libpinyinime_la-spellingtable.lo -MD -MP -MF .deps/libpinyinime_la-spellingtable.Tpo -c -o libpinyinime_la-spellingtable.lo `test -f 'spellingtable.cpp' || echo './'`spellingtable.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-spellingtable.lo -MD -MP -MF .deps/libpinyinime_la-spellingtable.Tpo -c spellingtable.cpp  -fPIC -DPIC -o .libs/libpinyinime_la-spellingtable.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-spellingtable.lo -MD -MP -MF .deps/libpinyinime_la-spellingtable.Tpo -c spellingtable.cpp -o libpinyinime_la-spellingtable.o >/dev/null 2>&1
mv -f .deps/libpinyinime_la-spellingtable.Tpo .deps/libpinyinime_la-spellingtable.Plo
/bin/bash ../../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..    -Werror -g -O2 -MT libpinyinime_la-spellingtrie.lo -MD -MP -MF .deps/libpinyinime_la-spellingtrie.Tpo -c -o libpinyinime_la-spellingtrie.lo `test -f 'spellingtrie.cpp' || echo './'`spellingtrie.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-spellingtrie.lo -MD -MP -MF .deps/libpinyinime_la-spellingtrie.Tpo -c spellingtrie.cpp  -fPIC -DPIC -o .libs/libpinyinime_la-spellingtrie.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-spellingtrie.lo -MD -MP -MF .deps/libpinyinime_la-spellingtrie.Tpo -c spellingtrie.cpp -o libpinyinime_la-spellingtrie.o >/dev/null 2>&1
mv -f .deps/libpinyinime_la-spellingtrie.Tpo .deps/libpinyinime_la-spellingtrie.Plo
/bin/bash ../../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..    -Werror -g -O2 -MT libpinyinime_la-splparser.lo -MD -MP -MF .deps/libpinyinime_la-splparser.Tpo -c -o libpinyinime_la-splparser.lo `test -f 'splparser.cpp' || echo './'`splparser.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-splparser.lo -MD -MP -MF .deps/libpinyinime_la-splparser.Tpo -c splparser.cpp  -fPIC -DPIC -o .libs/libpinyinime_la-splparser.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-splparser.lo -MD -MP -MF .deps/libpinyinime_la-splparser.Tpo -c splparser.cpp -o libpinyinime_la-splparser.o >/dev/null 2>&1
mv -f .deps/libpinyinime_la-splparser.Tpo .deps/libpinyinime_la-splparser.Plo
/bin/bash ../../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..    -Werror -g -O2 -MT libpinyinime_la-userdict.lo -MD -MP -MF .deps/libpinyinime_la-userdict.Tpo -c -o libpinyinime_la-userdict.lo `test -f 'userdict.cpp' || echo './'`userdict.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -Werror -g -O2 -MT libpinyinime_la-userdict.lo -MD -MP -MF .deps/libpinyinime_la-userdict.Tpo -c userdict.cpp  -fPIC -DPIC -o .libs/libpinyinime_la-userdict.o
cc1plus: warnings being treated as errors
userdict.cpp: In member function ‘void ime_pinyin::UserDict::write_back()’:
userdict.cpp:1270: error: ignoring return value of ‘int ftruncate(int, __off_t)’, declared with attribute warn_unused_result
userdict.cpp: In member function ‘void ime_pinyin::UserDict::write_back_sync(int)’:
userdict.cpp:1285: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1286: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp: In member function ‘void ime_pinyin::UserDict::write_back_offset(int)’:
userdict.cpp:1294: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1296: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1298: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1300: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1302: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp: In member function ‘void ime_pinyin::UserDict::write_back_score(int)’:
userdict.cpp:1314: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1316: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1318: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp: In member function ‘void ime_pinyin::UserDict::write_back_lemma(int)’:
userdict.cpp:1331: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1333: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1335: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1337: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1339: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1341: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp: In member function ‘void ime_pinyin::UserDict::write_back_all(int)’:
userdict.cpp:1351: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1352: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1354: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1356: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1358: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
userdict.cpp:1360: error: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
make[3]: *** [libpinyinime_la-userdict.lo] Error 1
make[3]: Leaving directory `/home/jpinson/scim-googlepinyin/src/share'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jpinson/scim-googlepinyin/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jpinson/scim-googlepinyin'
make: *** [all] Error 2


Thanks, 

jpinson

---

### Post by stlsaint on 2009-12-29
Assuming your trying to compile something make sure you have all necessary build-tools installed: IE: build-essentials package
also try here for reference on compiling: [CompilingSoftware]("https://help.ubuntu.com/community/CompilingSoftware")

---

