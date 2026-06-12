---
title: "Installing and using Tor and Tork"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by Falc7 on 2010-04-26
I have recently done a fresh install of lucid, and am trying to get Tor to work.
I installed Tor from source

```
jamie@jamie-ku:~/Downloads/tor-0.2.1.25$ ./configure && make && src/or/tor
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for win32... no
checking for MIPSpro compiler... no
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether byte ordering is bigendian... no
checking for library containing socket... none required
checking for library containing gethostbyname... none required
checking for library containing dlopen... -ldl
checking for library containing inet_aton... none required
checking for library containing pthread_create... -lpthread
checking for library containing pthread_detach... none required
checking for gettimeofday... yes
checking for ftime... yes
checking for socketpair... yes
checking for uname... yes
checking for inet_aton... yes
checking for strptime... yes
checking for getrlimit... yes
checking for strlcat... no
checking for strlcpy... no
checking for strtoull... yes
checking for getaddrinfo... yes
checking for localtime_r... yes
checking for gmtime_r... yes
checking for memmem... yes
checking for strtok_r... yes
checking for writev... yes
checking for readv... yes
checking for flock... yes
checking for prctl... yes
checking for mallinfo... yes
checking for malloc_good_size... no
checking for malloc_usable_size... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_create... yes
checking for sys/types.h... (cached) yes
checking for u_int64_t... yes
checking for u_int32_t... yes
checking for u_int16_t... yes
checking for u_int8_t... yes
checking for libevent directory... (system)
checking whether we need extra options to link libevent... (none)
checking for event_get_version... yes
checking for event_get_method... yes
checking for event_set_log_callback... yes
checking for struct event.min_heap_idx... yes
checking for openssl directory... (system)
checking whether we need extra options to link openssl... (none)
tor_cv_library_openssl_dir is (system)
checking for zlib directory... (system)
checking whether we need extra options to link zlib... (none)
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for unistd.h... (cached) yes
checking for string.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for sys/stat.h... (cached) yes
checking for sys/types.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/fcntl.h usability... yes
checking sys/fcntl.h presence... yes
checking for sys/fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking grp.h usability... yes
checking grp.h presence... yes
checking for grp.h... yes
checking sys/un.h usability... yes
checking sys/un.h presence... yes
checking for sys/un.h... yes
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking for stdint.h... (cached) yes
checking for sys/types.h... (cached) yes
checking for inttypes.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/limits.h usability... no
checking sys/limits.h presence... no
checking for sys/limits.h... no
checking for netinet/in.h... (cached) yes
checking for arpa/inet.h... (cached) yes
checking machine/limits.h usability... no
checking machine/limits.h presence... no
checking for machine/limits.h... no
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for sys/time.h... (cached) yes
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking for inttypes.h... (cached) yes
checking utime.h usability... yes
checking utime.h presence... yes
checking for utime.h... yes
checking sys/utime.h usability... no
checking sys/utime.h presence... no
checking for sys/utime.h... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking netinet/in6.h usability... no
checking netinet/in6.h presence... no
checking for netinet/in6.h... no
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking sys/syslimits.h usability... no
checking sys/syslimits.h presence... no
checking for sys/syslimits.h... no
checking malloc/malloc.h usability... no
checking malloc/malloc.h presence... no
checking for malloc/malloc.h... no
checking linux/types.h usability... yes
checking linux/types.h presence... yes
checking for linux/types.h... yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking malloc_np.h usability... no
checking malloc_np.h presence... no
checking for malloc_np.h... no
checking sys/prctl.h usability... yes
checking sys/prctl.h presence... yes
checking for sys/prctl.h... yes
checking for declaration of malloc_good_size... no
checking for net/if.h... yes
checking for net/pfvar.h... no
checking for linux/netfilter_ipv4.h... yes
checking for struct timeval.tv_sec... yes
checking for int8_t... yes
checking size of int8_t... 1
checking for int16_t... yes
checking size of int16_t... 2
checking for int32_t... yes
checking size of int32_t... 4
checking for int64_t... yes
checking size of int64_t... 8
checking for uint8_t... yes
checking size of uint8_t... 1
checking for uint16_t... yes
checking size of uint16_t... 2
checking for uint32_t... yes
checking size of uint32_t... 4
checking for uint64_t... yes
checking size of uint64_t... 8
checking for intptr_t... yes
checking size of intptr_t... 8
checking for uintptr_t... yes
checking size of uintptr_t... 8
checking for char... yes
checking size of char... 1
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 8
checking for long long... yes
checking size of long long... 8
checking for __int64... no
checking size of __int64... 0
checking for void *... yes
checking size of void *... 8
checking for time_t... yes
checking size of time_t... 8
checking for size_t... yes
checking size of size_t... 8
checking for uint... yes
checking for u_char... yes
checking for ssize_t... yes
checking for struct in6_addr... yes
checking for struct sockaddr_in6... yes
checking for sa_family_t... yes
checking for struct in6_addr.s6_addr32... yes
checking for struct in6_addr.s6_addr16... yes
checking for struct sockaddr_in.sin_len... no
checking for struct sockaddr_in6.sin6_len... no
checking for rlim_t... yes
checking whether time_t is signed... yes
checking for socklen_t... yes
checking size of socklen_t... 4
checking for cell_t... no
checking size of cell_t... 0
checking whether memset(0) sets pointers to NULL... yes
checking whether we can malloc(0) safely.... yes
checking whether we are using 2s-complement arithmetic... yes
checking whether to use dmalloc (debug memory allocation library)... no
checking for getresuid... yes
checking for getresgid... yes
checking for gethostbyname_r... yes
checking how many arguments gethostbyname_r() wants... 6
checking whether the C compiler supports __func__... yes
checking whether the C compiler supports __FUNC__... no
checking whether the C compiler supports __FUNCTION__... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating tor.spec
config.status: creating Doxyfile
config.status: creating contrib/tor.sh
config.status: creating contrib/torctl
config.status: creating contrib/torify
config.status: creating contrib/tor.logrotate
config.status: creating contrib/Makefile
config.status: creating contrib/osx/Makefile
config.status: creating contrib/osx/TorBundleDesc.plist
config.status: creating contrib/osx/TorBundleInfo.plist
config.status: creating contrib/osx/TorDesc.plist
config.status: creating contrib/osx/TorInfo.plist
config.status: creating contrib/osx/TorStartupDesc.plist
config.status: creating src/config/torrc.sample
config.status: creating doc/tor.1
config.status: creating src/Makefile
config.status: creating doc/Makefile
config.status: creating doc/design-paper/Makefile
config.status: creating doc/spec/Makefile
config.status: creating src/config/Makefile
config.status: creating src/common/Makefile
config.status: creating src/or/Makefile
config.status: creating src/win32/Makefile
config.status: creating src/tools/Makefile
config.status: creating contrib/suse/Makefile
config.status: creating contrib/suse/tor.sh
config.status: creating orconfig.h
config.status: orconfig.h is unchanged
config.status: executing depfiles commands
 /bin/bash ./config.status
config.status: creating Makefile
config.status: creating tor.spec
config.status: creating Doxyfile
config.status: creating contrib/tor.sh
config.status: creating contrib/torctl
config.status: creating contrib/torify
config.status: creating contrib/tor.logrotate
config.status: creating contrib/Makefile
config.status: creating contrib/osx/Makefile
config.status: creating contrib/osx/TorBundleDesc.plist
config.status: creating contrib/osx/TorBundleInfo.plist
config.status: creating contrib/osx/TorDesc.plist
config.status: creating contrib/osx/TorInfo.plist
config.status: creating contrib/osx/TorStartupDesc.plist
config.status: creating src/config/torrc.sample
config.status: creating doc/tor.1
config.status: creating src/Makefile
config.status: creating doc/Makefile
config.status: creating doc/design-paper/Makefile
config.status: creating doc/spec/Makefile
config.status: creating src/config/Makefile
config.status: creating src/common/Makefile
config.status: creating src/or/Makefile
config.status: creating src/win32/Makefile
config.status: creating src/tools/Makefile
config.status: creating contrib/suse/Makefile
config.status: creating contrib/suse/tor.sh
config.status: creating orconfig.h
config.status: orconfig.h is unchanged
config.status: executing depfiles commands
make  all-recursive
make[1]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25'
Making all in src
make[2]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/src'
Making all in common
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/src/common'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/src/common'
Making all in or
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/src/or'
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/src/or'
Making all in tools
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/src/tools'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/src/tools'
Making all in win32
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/src/win32'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/src/win32'
Making all in config
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/src/config'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/src/config'
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/src'
make[2]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/src'
Making all in doc
make[2]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/doc'
Making all in design-paper
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/doc/design-paper'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/doc/design-paper'
Making all in spec
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/doc/spec'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/doc/spec'
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/doc'
make[2]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/doc'
Making all in contrib
make[2]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/contrib'
Making all in osx
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/contrib/osx'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/contrib/osx'
Making all in suse
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/contrib/suse'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/contrib/suse'
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25/contrib'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/contrib'
make[2]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25/contrib'
make[2]: Entering directory `/home/jamie/Downloads/tor-0.2.1.25'
make[2]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25'
make[1]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.25'
Apr 26 15:16:40.832 [notice] Tor v0.2.1.25. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Apr 26 15:16:40.833 [notice] Configuration file "/usr/local/etc/tor/torrc" not present, using reasonable defaults.
Apr 26 15:16:40.833 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Apr 26 15:16:40.833 [notice] Opening Socks listener on 127.0.0.1:9050
Apr 26 15:16:40.909 [notice] OpenSSL OpenSSL 0.9.8k 25 Mar 2009 [9080bf] looks like it's older than 0.9.8l, but some vendors have backported 0.9.8l's renegotiation code to earlier versions.  I'll set SSL3_FLAGS just to be safe.
Apr 26 15:16:40.938 [notice] No current certificate known for authority moria1; launching request.
Apr 26 15:16:40.938 [notice] No current certificate known for authority tor26; launching request.
Apr 26 15:16:40.938 [notice] No current certificate known for authority dizum; launching request.
Apr 26 15:16:40.938 [notice] No current certificate known for authority ides; launching request.
Apr 26 15:16:40.938 [notice] No current certificate known for authority gabelmoo; launching request.
Apr 26 15:16:40.938 [notice] No current certificate known for authority dannenberg; launching request.
Apr 26 15:16:40.938 [notice] No current certificate known for authority urras; launching request.
Apr 26 15:16:40.938 [notice] Bootstrapped 5%: Connecting to directory server.
Apr 26 15:16:40.938 [notice] I learned some more directory information, but not enough to build a circuit: We have no network-status consensus.
^CApr 26 15:16:51.648 [notice] Interrupt: exiting cleanly.

```

But when i enter 'tor' in terminal it dosen't seem to work
```
jamie@jamie-ku:~$ tor
No command 'tor' found, did you mean:
 Command 'tora' from package 'tora' (universe)
 Command 'tr' from package 'coreutils' (main)
 Command 'tork' from package 'tork' (universe)
 Command 'tdr' from package 'devtodo' (universe)
 Command 'sor' from package 'pccts' (universe)
 Command 'top' from package 'procps' (main)
 Command 'tob' from package 'tob' (universe)
 Command 'toe' from package 'ncurses-bin' (main)
 Command 'tar' from package 'tar' (main)
tor: command not found

```

Also, Tork cant see where Tor is installed and is asking for the location, but i don't know where it is installed either.

---

### Post by Chronon on 2010-04-26
> **Falc7 said:**
> I have recently done a fresh install of lucid, and am trying to get Tor to work.
I installed Tor from source

```
jamie@jamie-ku:~/Downloads/tor-0.2.1.25$ ./configure && make && **src/or/tor**

```



That bolded bit seems a bit suspect.  Usually, I would expect to call "make install" to install the compiled bits to the desired location.  My main tor binary seems to be in /usr/sbin.

---

### Post by Falc7 on 2010-04-26
It told me to do that bit on tor project website under Installation and Configuration instructions for installing from tar balls

---

### Post by mkvnmtr on 2010-04-26
If you go to the tor site it has a great tutorial for installing tor and popilo and using tor button. It is a deb file and I just had to double click and gdebi installed it with all the other packages required. Works great. Their tutorial is better than anything I could give you on the spur of the moment here.

---

