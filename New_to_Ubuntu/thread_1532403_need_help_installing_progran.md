---
title: "need help installing progran"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by gamepanther on 2010-07-16
Hi I am relatively new to ubuntu and am running 10.04 64-bit.
I have installed other programs in the past but cannot make sense of the readme file for abgx360 I can get halway through and then the commands dont work or im not doing it right. can anyone please help me to install this program [http://www.abgx360.net/download.html](http://www.abgx360.net/download.html)

---

### Post by drpjkurian on 2010-07-16
hi
First open the terminal by navigating to Accessories->Terminal

1.type the command ```
sudo apt-get install libcurl4-openssl-dev zlib1g-dev
``` this is to install the dependencies. type password when prompted.

2.extract the downloaded folder to desktop by double clicking the folder.

3. type the command```
cd Desktop
``` in terminal

4. type the command ```
cd abgx360-1.0.2
```in terminal

5. type the command ```
./configure
make
sudo make install
```

reboot the machine, it should work

---

### Post by gamepanther on 2010-07-16
sorry i realise this is probobly a noob question but for instruction 5 why are the 3 commands on different lines is there something i need to do when there on different lines? thanks for your earlier speedy response

---

### Post by emoguitarist06 on 2010-07-16
> **gamepanther said:**
> sorry i realise this is probobly a noob question but for instruction 5 why are the 3 commands on different lines is there something i need to do when there on different lines? thanks for your earlier speedy response

Basically it just means first run
```
./configure
```
once that's completed run
```
make
```
once that's completed run
```
sudo make install
```

---

### Post by gamepanther on 2010-07-16
I tried that and this comes up

fergal@fergal-laptop:~/Desktop/abgx360-1.0.2$ make
make  all-am
make[1]: Entering directory `/home/fergal/Desktop/abgx360-1.0.2'
make[1]: Leaving directory `/home/fergal/Desktop/abgx360-1.0.2'
fergal@fergal-laptop:~/Desktop/abgx360-1.0.2$ sudo make install
[sudo] password for fergal: 
make[1]: Entering directory `/home/fergal/Desktop/abgx360-1.0.2'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'abgx360' '/usr/local/bin/abgx360'
make[1]: Nothing to be done for `install-data-am'.
make[1]: Leaving directory `/home/fergal/Desktop/abgx360-1.0.2'
fergal@fergal-laptop:~/Desktop/abgx360-1.0.2$ ^C
fergal@fergal-laptop:~/Desktop/abgx360-1.0.2$

---

### Post by gamepanther on 2010-07-16
any suggestions on what went wrong?

---

### Post by drpjkurian on 2010-07-17
Hi
First check out whether the programme is installed.

Second Ensure that you have used the command ```
./configure
```
It is not seen in your post.

Third Try by typing all the commands together (Step 5) in the terminal. The computer will execute it one after the other

---

### Post by gamepanther on 2010-07-17
its not installed. I tried adding all the compands together but it still didnt work. fergal@fergal-laptop:~$ cd Desktop
fergal@fergal-laptop:~/Desktop$ cd abgx360-1.0.2
fergal@fergal-laptop:~/Desktop/abgx360-1.0.2$ ./configure make sudo make installconfigure: WARNING: you should use --build, --host, --target
configure: WARNING: you should use --build, --host, --target
configure: WARNING: you should use --build, --host, --target
configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for make-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking for crc32 in -lz... yes
checking for gawk... (cached) gawk
checking for curl-config... /usr/bin/curl-config
checking for the version of libcurl... 7.19.7
checking for libcurl >= version 7.7.2... yes
checking whether libcurl is usable... yes
checking for curl_free... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking curl/curl.h usability... yes
checking curl/curl.h presence... yes
checking for curl/curl.h... yes
checking fnmatch.h usability... yes
checking fnmatch.h presence... yes
checking for fnmatch.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking stdlib.h usability... yes
checking stdlib.h presence... yes
checking for stdlib.h... yes
checking string.h usability... yes
checking string.h presence... yes
checking for string.h... yes
checking strings.h usability... yes
checking strings.h presence... yes
checking for strings.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking unistd.h usability... yes
checking unistd.h presence... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for working volatile... yes
checking for size_t... yes
checking for off_t... yes
checking for int32_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for ptrdiff_t... yes
checking whether closedir returns void... no
checking for working alloca.h... yes
checking for alloca... yes
checking for mbstate_t... yes
checking for working POSIX fnmatch... yes
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking whether lstat dereferences a symlink specified with a trailing slash... no
checking whether stat accepts an empty string... yes
checking for error_at_line... yes
checking for vprintf... yes
checking for _doprnt... no
checking for atexit... yes
checking for gettimeofday... yes
checking for memset... yes
checking for strcasecmp... yes
checking for strerror... yes
checking for strncasecmp... yes
checking for strtol... yes
checking for strtoul... yes
checking for strstr... yes
checking for mkdir... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
fergal@fergal-laptop:~/Desktop/abgx360-1.0.2$ ^C

---

### Post by da burger on 2010-07-17
Those commands do need to be separate. However if you want there is a way to put them on one line.

```
make && sudo make install
```

should do the trick.

---

### Post by gamepanther on 2010-07-17
Tried that but its still not working

fergal@fergal-laptop:~$ cd Desktop
fergal@fergal-laptop:~/Desktop$ cd abgx360-1.0.2
fergal@fergal-laptop:~/Desktop/abgx360-1.0.2$ ./configurechecking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking for crc32 in -lz... yes
checking for gawk... (cached) gawk
checking for curl-config... /usr/bin/curl-config
checking for the version of libcurl... 7.19.7
checking for libcurl >= version 7.7.2... yes
checking whether libcurl is usable... yes
checking for curl_free... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking curl/curl.h usability... yes
checking curl/curl.h presence... yes
checking for curl/curl.h... yes
checking fnmatch.h usability... yes
checking fnmatch.h presence... yes
checking for fnmatch.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking stdlib.h usability... yes
checking stdlib.h presence... yes
checking for stdlib.h... yes
checking string.h usability... yes
checking string.h presence... yes
checking for string.h... yes
checking strings.h usability... yes
checking strings.h presence... yes
checking for strings.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking unistd.h usability... yes
checking unistd.h presence... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for working volatile... yes
checking for size_t... yes
checking for off_t... yes
checking for int32_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for ptrdiff_t... yes
checking whether closedir returns void... no
checking for working alloca.h... yes
checking for alloca... yes
checking for mbstate_t... yes
checking for working POSIX fnmatch... yes
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking whether lstat dereferences a symlink specified with a trailing slash... no
checking whether stat accepts an empty string... yes
checking for error_at_line... yes
checking for vprintf... yes
checking for _doprnt... no
checking for atexit... yes
checking for gettimeofday... yes
checking for memset... yes
checking for strcasecmp... yes
checking for strerror... yes
checking for strncasecmp... yes
checking for strtol... yes
checking for strtoul... yes
checking for strstr... yes
checking for mkdir... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
fergal@fergal-laptop:~/Desktop/abgx360-1.0.2$ make && sudo make install
make  all-am
make[1]: Entering directory `/home/fergal/Desktop/abgx360-1.0.2'
make[1]: Leaving directory `/home/fergal/Desktop/abgx360-1.0.2'
[sudo] password for fergal: 
make[1]: Entering directory `/home/fergal/Desktop/abgx360-1.0.2'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'abgx360' '/usr/local/bin/abgx360'
make[1]: Nothing to be done for `install-data-am'.
make[1]: Leaving directory `/home/fergal/Desktop/abgx360-1.0.2'
fergal@fergal-laptop:~/Desktop/abgx360-1.0.2$

---

### Post by gamepanther on 2010-07-17
does anybody know why this is happening? cause i really need this program i love ubuntu but this program is make or break for me to decide staying with it

---

### Post by gamepanther on 2010-07-18
sorry noob mistake i did do it all correctly but i expected to find ab icon in applications but you had to either run from turmunal or download a gui and use it to run it. thanks very much my Ubuntu is now perfect

---

### Post by drpjkurian on 2010-07-21
Hi
Hmm
 Sorry for missing the last point in instructing you. Anyway I am happy that your problem is solved

---

### Post by drpjkurian on 2010-07-21
Hi
Please mark your problem solved

---

