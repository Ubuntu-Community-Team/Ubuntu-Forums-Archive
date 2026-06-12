---
title: "make/make install failed? (aircrack-ng)"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by northconnor on 2010-08-13
I have been having trouble trying to get the program "aircrack-ng" to install from the source. I had previously installed it through "sudo apt-get install aircrack-ng", but it did not compile with sqlite support for databases. I learned that to fix this I had to uninstall aircrack and use the commands: make clean;./configure;make sqlite=true;make sqlite=true install. However, when I try these I get the output:


root@connor:~/Desktop/aircrack-ng-1.1# make clean;./configure;make sqlite=true;make sqlite=true install
make -C src clean
make[1]: Entering directory `/home/connor/Desktop/aircrack-ng-1.1/src'
make -C osdep clean
make[2]: Entering directory `/home/connor/Desktop/aircrack-ng-1.1/src/osdep'
make -C radiotap clean
make[3]: Entering directory `/home/connor/Desktop/aircrack-ng-1.1/src/osdep/radiotap'
rm -f *.o
make[3]: Leaving directory `/home/connor/Desktop/aircrack-ng-1.1/src/osdep/radiotap'
rm -f libosdep.a  *.o .os.*
make[2]: Leaving directory `/home/connor/Desktop/aircrack-ng-1.1/src/osdep'
rm -f aireplay-ng airodump-ng airserv-ng airtun-ng airbase-ng aircrack-ng airdecap-ng packetforge-ng ivstools kstats makeivs-ng airdecloak-ng aircrack-ng-opt-prof_gen aircrack-ng-opt aircrack-ng-opt-prof prof/* airolib-ng *.o wesside-ng tkiptun-ng easside-ng buddy-ng
make[1]: Leaving directory `/home/connor/Desktop/aircrack-ng-1.1/src'
bash: ./configure: No such file or directory
make -C src all
make[1]: Entering directory `/home/connor/Desktop/aircrack-ng-1.1/src'
make -C osdep
make[2]: Entering directory `/home/connor/Desktop/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/connor/Desktop/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -I/usr/local/include -DHAVE_SQLITE -fPIC -I..    -c -o osdep.o osdep.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -I/usr/local/include -DHAVE_SQLITE -fPIC -I..    -c -o network.o network.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -I/usr/local/include -DHAVE_SQLITE -fPIC -I..    -c -o linux.o linux.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -I/usr/local/include -DHAVE_SQLITE -fPIC -I..    -c -o linux_tap.o linux_tap.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -I/usr/local/include -DHAVE_SQLITE -fPIC -I..    -c -o radiotap/radiotap-parser.o radiotap/radiotap-parser.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -I/usr/local/include -DHAVE_SQLITE -fPIC -I..    -c -o common.o common.c
ar cru libosdep.a  osdep.o network.o linux.o linux_tap.o radiotap/radiotap-parser.o common.o
ranlib libosdep.a 
touch .os.Linux
make[3]: Leaving directory `/home/connor/Desktop/aircrack-ng-1.1/src/osdep'
make[2]: Leaving directory `/home/connor/Desktop/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -I/usr/local/include -DHAVE_SQLITE -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:65:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
In file included from aircrack-ng.c:69:
sha1-sse2.h: In function ‘calc_4pmk’:
sha1-sse2.h:140: error: implicit declaration of function ‘HMAC’
sha1-sse2.h:140: error: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c: In function ‘crack_wpa_thread’:
aircrack-ng.c:3934: error: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/connor/Desktop/aircrack-ng-1.1/src'
make: *** [all] Error 2
make -C src install
make[1]: Entering directory `/home/connor/Desktop/aircrack-ng-1.1/src'
make -C osdep
make[2]: Entering directory `/home/connor/Desktop/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/connor/Desktop/aircrack-ng-1.1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/connor/Desktop/aircrack-ng-1.1/src/osdep'
make[2]: Leaving directory `/home/connor/Desktop/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -I/usr/local/include -DHAVE_SQLITE -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:65:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
In file included from aircrack-ng.c:69:
sha1-sse2.h: In function ‘calc_4pmk’:
sha1-sse2.h:140: error: implicit declaration of function ‘HMAC’
sha1-sse2.h:140: error: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c: In function ‘crack_wpa_thread’:
aircrack-ng.c:3934: error: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/connor/Desktop/aircrack-ng-1.1/src'
make: *** [install] Error 2

Any ideas? I compiled openSSL from the source (just in case) and got no error messages, so I don't know why it says there is no such file or directory for that. Any help would be GREATLY appreciated. Thank you! :grin:

---

### Post by Paul820 on 2010-08-13
Read through all of the output until you get to the first error. Your first error is here
> crypto.h:12:26: error: openssl/hmac.h: No such file or directory
What does that tell you? To me it says it can't find hmac.h that is part of openssl. So, you need the development headers for openssl installed on your system. There should be a readme file that comes with all source (well, most) code that will tell you what needs to be installed on your system so you can compile the code.

---

### Post by northconnor on 2010-08-13
Thank you! Saved me a LOT of time and frustration :smile: and not being very good in linux I thought all those "-Werror"s were errors.

---

