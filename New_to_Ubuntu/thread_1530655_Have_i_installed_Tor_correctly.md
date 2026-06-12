---
title: "Have i installed Tor correctly?"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by Falc7 on 2010-07-13
Have i installed Tor correctly?
I got the source, and compiled

```
jamie@jamie-ku:~/Downloads/tor-0.2.1.26$ ./configure && make && src/or/tor
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
checking for libevent directory... configure: WARNING: Could not find a linkable libevent.  If you have it installed somewhere unusual, you can specify an explicit path using --with-libevent-dir
configure: WARNING: On Debian, you can install libevent using "apt-get install libevent-dev"
configure: error: Missing libraries; unable to proceed.
jamie@jamie-ku:~/Downloads/tor-0.2.1.26$ apt-get install libevent-dev
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jamie@jamie-ku:~/Downloads/tor-0.2.1.26$ apt-get install libevent-dev
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jamie@jamie-ku:~/Downloads/tor-0.2.1.26$ ./configure && make && src/or/tor
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
checking for openssl directory... configure: WARNING: Could not find a linkable openssl.  If you have it installed somewhere unusual, you can specify an explicit path using --with-openssl-dir
configure: WARNING: On Debian, you can install openssl using "apt-get install libssl"
configure: WARNING:    You will probably need libssl-dev too.
configure: error: Missing libraries; unable to proceed.
jamie@jamie-ku:~/Downloads/tor-0.2.1.26$ ./configure && make && src/or/tor
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
make[1]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26'
Making all in src
make[2]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/src'
Making all in common
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/src/common'
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT address.o -MD -MP -MF .deps/address.Tpo -c -o address.o address.c
mv -f .deps/address.Tpo .deps/address.Po
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT log.o -MD -MP -MF .deps/log.Tpo -c -o log.o log.c
mv -f .deps/log.Tpo .deps/log.Po
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT util.o -MD -MP -MF .deps/util.Tpo -c -o util.o util.c
mv -f .deps/util.Tpo .deps/util.Po
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT compat.o -MD -MP -MF .deps/compat.Tpo -c -o compat.o compat.c
mv -f .deps/compat.Tpo .deps/compat.Po
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT container.o -MD -MP -MF .deps/container.Tpo -c -o container.o container.c
mv -f .deps/container.Tpo .deps/container.Po
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT mempool.o -MD -MP -MF .deps/mempool.Tpo -c -o mempool.o mempool.c
mv -f .deps/mempool.Tpo .deps/mempool.Po
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT memarea.o -MD -MP -MF .deps/memarea.Tpo -c -o memarea.o memarea.c
mv -f .deps/memarea.Tpo .deps/memarea.Po
rm -f libor.a
ar cru libor.a address.o log.o util.o compat.o container.o mempool.o memarea.o  
ranlib libor.a
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT crypto.o -MD -MP -MF .deps/crypto.Tpo -c -o crypto.o crypto.c
mv -f .deps/crypto.Tpo .deps/crypto.Po
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT aes.o -MD -MP -MF .deps/aes.Tpo -c -o aes.o aes.c
mv -f .deps/aes.Tpo .deps/aes.Po
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT tortls.o -MD -MP -MF .deps/tortls.Tpo -c -o tortls.o tortls.c
mv -f .deps/tortls.Tpo .deps/tortls.Po
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT torgzip.o -MD -MP -MF .deps/torgzip.Tpo -c -o torgzip.o torgzip.c
mv -f .deps/torgzip.Tpo .deps/torgzip.Po
rm -f libor-crypto.a
ar cru libor-crypto.a crypto.o aes.o tortls.o torgzip.o 
ranlib libor-crypto.a
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/src/common'
Making all in or
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/src/or'
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT buffers.o -MD -MP -MF .deps/buffers.Tpo -c -o buffers.o buffers.c
mv -f .deps/buffers.Tpo .deps/buffers.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT circuitbuild.o -MD -MP -MF .deps/circuitbuild.Tpo -c -o circuitbuild.o circuitbuild.c
mv -f .deps/circuitbuild.Tpo .deps/circuitbuild.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT circuitlist.o -MD -MP -MF .deps/circuitlist.Tpo -c -o circuitlist.o circuitlist.c
mv -f .deps/circuitlist.Tpo .deps/circuitlist.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT circuituse.o -MD -MP -MF .deps/circuituse.Tpo -c -o circuituse.o circuituse.c
mv -f .deps/circuituse.Tpo .deps/circuituse.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT command.o -MD -MP -MF .deps/command.Tpo -c -o command.o command.c
mv -f .deps/command.Tpo .deps/command.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT config.o -MD -MP -MF .deps/config.Tpo -c -o config.o config.c
mv -f .deps/config.Tpo .deps/config.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT connection.o -MD -MP -MF .deps/connection.Tpo -c -o connection.o connection.c
mv -f .deps/connection.Tpo .deps/connection.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT connection_edge.o -MD -MP -MF .deps/connection_edge.Tpo -c -o connection_edge.o connection_edge.c
mv -f .deps/connection_edge.Tpo .deps/connection_edge.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT connection_or.o -MD -MP -MF .deps/connection_or.Tpo -c -o connection_or.o connection_or.c
mv -f .deps/connection_or.Tpo .deps/connection_or.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT control.o -MD -MP -MF .deps/control.Tpo -c -o control.o control.c
mv -f .deps/control.Tpo .deps/control.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT cpuworker.o -MD -MP -MF .deps/cpuworker.Tpo -c -o cpuworker.o cpuworker.c
mv -f .deps/cpuworker.Tpo .deps/cpuworker.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT directory.o -MD -MP -MF .deps/directory.Tpo -c -o directory.o directory.c
mv -f .deps/directory.Tpo .deps/directory.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT dirserv.o -MD -MP -MF .deps/dirserv.Tpo -c -o dirserv.o dirserv.c
mv -f .deps/dirserv.Tpo .deps/dirserv.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT dirvote.o -MD -MP -MF .deps/dirvote.Tpo -c -o dirvote.o dirvote.c
mv -f .deps/dirvote.Tpo .deps/dirvote.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT dns.o -MD -MP -MF .deps/dns.Tpo -c -o dns.o dns.c
mv -f .deps/dns.Tpo .deps/dns.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT dnsserv.o -MD -MP -MF .deps/dnsserv.Tpo -c -o dnsserv.o dnsserv.c
mv -f .deps/dnsserv.Tpo .deps/dnsserv.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT geoip.o -MD -MP -MF .deps/geoip.Tpo -c -o geoip.o geoip.c
mv -f .deps/geoip.Tpo .deps/geoip.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT hibernate.o -MD -MP -MF .deps/hibernate.Tpo -c -o hibernate.o hibernate.c
mv -f .deps/hibernate.Tpo .deps/hibernate.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
mv -f .deps/main.Tpo .deps/main.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT networkstatus.o -MD -MP -MF .deps/networkstatus.Tpo -c -o networkstatus.o networkstatus.c
mv -f .deps/networkstatus.Tpo .deps/networkstatus.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT onion.o -MD -MP -MF .deps/onion.Tpo -c -o onion.o onion.c
mv -f .deps/onion.Tpo .deps/onion.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT policies.o -MD -MP -MF .deps/policies.Tpo -c -o policies.o policies.c
mv -f .deps/policies.Tpo .deps/policies.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT reasons.o -MD -MP -MF .deps/reasons.Tpo -c -o reasons.o reasons.c
mv -f .deps/reasons.Tpo .deps/reasons.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT relay.o -MD -MP -MF .deps/relay.Tpo -c -o relay.o relay.c
mv -f .deps/relay.Tpo .deps/relay.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT rendcommon.o -MD -MP -MF .deps/rendcommon.Tpo -c -o rendcommon.o rendcommon.c
mv -f .deps/rendcommon.Tpo .deps/rendcommon.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT rendclient.o -MD -MP -MF .deps/rendclient.Tpo -c -o rendclient.o rendclient.c
mv -f .deps/rendclient.Tpo .deps/rendclient.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT rendmid.o -MD -MP -MF .deps/rendmid.Tpo -c -o rendmid.o rendmid.c
mv -f .deps/rendmid.Tpo .deps/rendmid.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT rendservice.o -MD -MP -MF .deps/rendservice.Tpo -c -o rendservice.o rendservice.c
mv -f .deps/rendservice.Tpo .deps/rendservice.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT rephist.o -MD -MP -MF .deps/rephist.Tpo -c -o rephist.o rephist.c
mv -f .deps/rephist.Tpo .deps/rephist.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT router.o -MD -MP -MF .deps/router.Tpo -c -o router.o router.c
mv -f .deps/router.Tpo .deps/router.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT routerlist.o -MD -MP -MF .deps/routerlist.Tpo -c -o routerlist.o routerlist.c
mv -f .deps/routerlist.Tpo .deps/routerlist.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT routerparse.o -MD -MP -MF .deps/routerparse.Tpo -c -o routerparse.o routerparse.c
mv -f .deps/routerparse.Tpo .deps/routerparse.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT eventdns.o -MD -MP -MF .deps/eventdns.Tpo -c -o eventdns.o eventdns.c
mv -f .deps/eventdns.Tpo .deps/eventdns.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT tor_main.o -MD -MP -MF .deps/tor_main.Tpo -c -o tor_main.o tor_main.c
mv -f .deps/tor_main.Tpo .deps/tor_main.Po
gcc  -g -O2 -Wall -g -O2 -fno-strict-aliasing   -o tor buffers.o circuitbuild.o circuitlist.o circuituse.o command.o config.o connection.o connection_edge.o connection_or.o control.o cpuworker.o directory.o dirserv.o dirvote.o dns.o dnsserv.o geoip.o hibernate.o main.o  networkstatus.o onion.o policies.o reasons.o relay.o rendcommon.o rendclient.o rendmid.o rendservice.o rephist.o router.o routerlist.o routerparse.o eventdns.o tor_main.o ../common/libor.a ../common/libor-crypto.a -lz -levent -lssl -lcrypto   -lpthread -ldl 
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT test_data.o -MD -MP -MF .deps/test_data.Tpo -c -o test_data.o test_data.c
mv -f .deps/test_data.Tpo .deps/test_data.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -DSHARE_DATADIR="\"/usr/local/share\"" -DLOCALSTATEDIR="\"/usr/local/var\"" -DBINDIR="\"/usr/local/bin\"" -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT test.o -MD -MP -MF .deps/test.Tpo -c -o test.o test.c
mv -f .deps/test.Tpo .deps/test.Po
gcc  -g -O2 -Wall -g -O2 -fno-strict-aliasing   -o test buffers.o circuitbuild.o circuitlist.o circuituse.o command.o config.o connection.o connection_edge.o connection_or.o control.o cpuworker.o directory.o dirserv.o dirvote.o dns.o dnsserv.o geoip.o hibernate.o main.o  networkstatus.o onion.o policies.o reasons.o relay.o rendcommon.o rendclient.o rendmid.o rendservice.o rephist.o router.o routerlist.o routerparse.o eventdns.o test_data.o test.o ../common/libor.a ../common/libor-crypto.a -lz -levent -lssl -lcrypto   -lpthread -ldl 
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/src/or'
Making all in tools
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/src/tools'
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT tor-resolve.o -MD -MP -MF .deps/tor-resolve.Tpo -c -o tor-resolve.o tor-resolve.c
mv -f .deps/tor-resolve.Tpo .deps/tor-resolve.Po
gcc  -g -O2 -Wall -g -O2 -fno-strict-aliasing   -o tor-resolve tor-resolve.o ../common/libor.a  -levent  -lpthread -ldl 
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT tor-gencert.o -MD -MP -MF .deps/tor-gencert.Tpo -c -o tor-gencert.o tor-gencert.c
mv -f .deps/tor-gencert.Tpo .deps/tor-gencert.Po
gcc  -g -O2 -Wall -g -O2 -fno-strict-aliasing   -o tor-gencert tor-gencert.o ../common/libor.a ../common/libor-crypto.a -lz  -levent -lssl -lcrypto   -lpthread -ldl 
gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/common     -g -O2 -Wall -g -O2 -fno-strict-aliasing -MT tor-checkkey.o -MD -MP -MF .deps/tor-checkkey.Tpo -c -o tor-checkkey.o tor-checkkey.c
mv -f .deps/tor-checkkey.Tpo .deps/tor-checkkey.Po
gcc  -g -O2 -Wall -g -O2 -fno-strict-aliasing   -o tor-checkkey tor-checkkey.o ../common/libor.a ../common/libor-crypto.a -lz  -levent -lssl -lcrypto   -lpthread -ldl 
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/src/tools'
Making all in win32
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/src/win32'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/src/win32'
Making all in config
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/src/config'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/src/config'
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/src'
make[2]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/src'
Making all in doc
make[2]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/doc'
Making all in design-paper
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/doc/design-paper'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/doc/design-paper'
Making all in spec
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/doc/spec'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/doc/spec'
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/doc'
make[2]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/doc'
Making all in contrib
make[2]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/contrib'
Making all in osx
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/contrib/osx'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/contrib/osx'
Making all in suse
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/contrib/suse'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/contrib/suse'
make[3]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26/contrib'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/contrib'
make[2]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26/contrib'
make[2]: Entering directory `/home/jamie/Downloads/tor-0.2.1.26'
make[2]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26'
make[1]: Leaving directory `/home/jamie/Downloads/tor-0.2.1.26'
Jul 14 10:30:19.982 [notice] Tor v0.2.1.26. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Jul 14 10:30:20.000 [notice] Configuration file "/usr/local/etc/tor/torrc" not present, using reasonable defaults.
Jul 14 10:30:20.015 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Jul 14 10:30:20.015 [notice] Opening Socks listener on 127.0.0.1:9050
Jul 14 10:30:20.082 [notice] OpenSSL OpenSSL 0.9.8k 25 Mar 2009 [9080bf] looks like it's older than 0.9.8l, but some vendors have backported 0.9.8l's renegotiation code to earlier versions, and some have backported the code from 0.9.8m or 0.9.8n.  I'll set both SSL3_FLAGS and SSL_OP just to be safe.
Jul 14 10:30:20.128 [notice] No current certificate known for authority moria1; launching request.
Jul 14 10:30:20.128 [notice] No current certificate known for authority tor26; launching request.
Jul 14 10:30:20.128 [notice] No current certificate known for authority dizum; launching request.
Jul 14 10:30:20.128 [notice] No current certificate known for authority ides; launching request.
Jul 14 10:30:20.128 [notice] No current certificate known for authority gabelmoo; launching request.
Jul 14 10:30:20.128 [notice] No current certificate known for authority dannenberg; launching request.
Jul 14 10:30:20.128 [notice] No current certificate known for authority urras; launching request.
Jul 14 10:30:20.128 [notice] Bootstrapped 5%: Connecting to directory server.
Jul 14 10:30:20.128 [notice] I learned some more directory information, but not enough to build a circuit: We have no network-status consensus.
Jul 14 10:30:41.128 [notice] No current certificate known for authority moria1; launching request.
Jul 14 10:30:41.128 [notice] No current certificate known for authority tor26; launching request.
Jul 14 10:30:41.128 [notice] No current certificate known for authority dizum; launching request.
Jul 14 10:30:41.128 [notice] No current certificate known for authority ides; launching request.
Jul 14 10:30:41.128 [notice] No current certificate known for authority gabelmoo; launching request.
Jul 14 10:30:41.128 [notice] No current certificate known for authority dannenberg; launching request.
Jul 14 10:30:41.128 [notice] No current certificate known for authority urras; launching request.
Jul 14 10:32:22.757 [notice] No current certificate known for authority moria1; launching request.
Jul 14 10:32:22.758 [notice] No current certificate known for authority tor26; launching request.
Jul 14 10:32:22.758 [notice] No current certificate known for authority dizum; launching request.
Jul 14 10:32:22.758 [notice] No current certificate known for authority ides; launching request.
Jul 14 10:32:22.758 [notice] No current certificate known for authority gabelmoo; launching request.
Jul 14 10:32:22.758 [notice] No current certificate known for authority dannenberg; launching request.
Jul 14 10:32:22.758 [notice] No current certificate known for authority urras; launching request.
Jul 14 10:38:28.694 [notice] No current certificate known for authority moria1; launching request.
Jul 14 10:38:28.694 [notice] No current certificate known for authority tor26; launching request.
Jul 14 10:38:28.694 [notice] No current certificate known for authority dizum; launching request.
Jul 14 10:38:28.694 [notice] No current certificate known for authority ides; launching request.
Jul 14 10:38:28.694 [notice] No current certificate known for authority gabelmoo; launching request.
Jul 14 10:38:28.694 [notice] No current certificate known for authority dannenberg; launching request.
Jul 14 10:38:28.694 [notice] No current certificate known for authority urras; launching request.
Jul 14 10:49:39.150 [notice] No current certificate known for authority moria1; launching request.
Jul 14 10:49:39.150 [notice] No current certificate known for authority tor26; launching request.
Jul 14 10:49:39.150 [notice] No current certificate known for authority dizum; launching request.
Jul 14 10:49:39.150 [notice] No current certificate known for authority ides; launching request.
Jul 14 10:49:39.150 [notice] No current certificate known for authority gabelmoo; launching request.
Jul 14 10:49:39.150 [notice] No current certificate known for authority dannenberg; launching request.
Jul 14 10:49:39.150 [notice] No current certificate known for authority urras; launching request.
Jul 14 10:50:00.147 [warn] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Connection timed out; TIMEOUT; count 10; recommendation warn)

```

But in synaptic, i don't see any package called Tor, Tork cant find my Tor installation, and i get this in the terminal:

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

---

### Post by adamjkok on 2010-07-14
Try installing the TORBUTTON Firefox extension or point any SOCKS-Compatible application at "127.0.0.1" on port 9050 (alternatively, "localhost" on port 9050). If you can connect, you're good. TOR does not magically protect your activities online; the application in question must be pointed to the server on port 9050 for TOR to work. The proxy runs in the background and starts automatically.

---

### Post by Paqman on 2010-07-14
Last time I checked Tor had Ubuntu .debs available. You'll also need to install privoxy and the torbutton extension from the Ubuntu repos. Full instructions on setting up privoxy are [here]("http://ubuntuforums.org/showthread.php?p=2702743").

Once you're set up, you can visit [https://check.torproject.org/](https://check.torproject.org/) to confirm you have Tor switched on. The other way to check would be visit any site, if it's so slow as to be incredibly annoying and completely unusable, you're probably using Tor ;)

---

### Post by bodhi.zazen on 2010-07-14
> **Falc7 said:**
> Have i installed Tor correctly?
I got the source, and compiled

```
jamie@jamie-ku:~/Downloads/tor-0.2.1.26$ ./configure && make && src/or/tor
....

< clip >

 ...


```But in synaptic, i don't see any package called Tor, Tork cant find my Tor installation, and i get this in the terminal:
[/CODE]

That does not even look close to how most people install Tor

See : [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

If you prefer, download the Linux portable Tor package, it is very easy to use and IMO very nice :

[Tor Browser Bundle]("http://www.torproject.org/torbrowser/") 

Why are you compiling Tor from source ?

---

### Post by Falc7 on 2010-07-21
Hhm, that tor browser bundle does seem good, i've downloaded it, and unpacked it, but when i click on the 'start tor browser' script nothing happens. The script is listed as executable though

So i tried through terminal
jamie@jamie-ku:~/tor-browser_en-US$ start-tor-browser
start-tor-browser: command not found

---

### Post by bodhi.zazen on 2010-07-21
You are getting that error because it is not on your path.

Use the full path to the script.

```
/home/your_user/tor-browser_en-US/start-tor-browser
```

Make a custom launcher ;)

---

### Post by Falc7 on 2010-07-27
Oh yeah! That did it thanks, 

Now vidalia starts up, i've added a few bridges, but it still takes ages to get enough directory information to build a circuit, is there anything i can do about this?

---

