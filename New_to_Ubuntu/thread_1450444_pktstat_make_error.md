---
title: "pktstat make error??"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by nitstorm on 2010-04-09
i just downloaded *pktstat-1.8.3.tar.gz   *from *[http://www.adaptive-enterprises.com.au/~d/software/pktstat/](http://www.adaptive-enterprises.com.au/~d/software/pktstat/)*

then extracted it with [I]tar xzpf pktstat-1.8.3.tar.gz
[/I]then moved into the folder with the *cd *command
and then typed in *./configure  *lots of output but then the last line said [I]
configure: error: Cannot proceed without a packet capture library[/I]

What do I do? How do I proceed???

here is the full output of ./configure 
```

nits@nits-workstation:~/Downloads/pktstat-1.8.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for library containing socket... none required
checking for library containing gethostbyname... none required
checking for library containing pcap_open_live... no
checking for library containing exp... -lm
checking for library containing tgoto... no
checking for library containing initscr... no
checking for library containing nanosleep... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking whether time.h and sys/time.h may both be included... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/queue.h usability... yes
checking sys/queue.h presence... yes
checking for sys/queue.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking for sys/types.h... (cached) yes
checking sys/signal.h usability... yes
checking sys/signal.h presence... yes
checking for sys/signal.h... yes
checking ncurses.h usability... no
checking ncurses.h presence... no
checking for ncurses.h... no
checking curses.h usability... no
checking curses.h presence... no
checking for curses.h... no
checking err.h usability... yes
checking err.h presence... yes
checking for err.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for inttypes.h... (cached) yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking net/ppp_defs.h usability... yes
checking net/ppp_defs.h presence... yes
checking for net/ppp_defs.h... yes
checking sys/ppp_sys.h usability... no
checking sys/ppp_sys.h presence... no
checking for sys/ppp_sys.h... no
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/ether.h usability... yes
checking netinet/ether.h presence... yes
checking for netinet/ether.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/in_systm.h usability... yes
checking netinet/in_systm.h presence... yes
checking for netinet/in_systm.h... yes
checking netinet/tcp.h usability... yes
checking netinet/tcp.h presence... yes
checking for netinet/tcp.h... yes
checking netinet/udp.h usability... yes
checking netinet/udp.h presence... yes
checking for netinet/udp.h... yes
checking netipx/ipx.h usability... yes
checking netipx/ipx.h presence... yes
checking for netipx/ipx.h... yes
checking pcap.h usability... no
checking pcap.h presence... no
checking for pcap.h... no
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking for string.h... (cached) yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking for net/if.h... yes
checking for netinet/if_ether.h... yes
checking for netinet/ip.h... yes
checking for netinet/ip_icmp.h... yes
checking for netinet/ip6.h... yes
checking whether termios.h defines TIOCGWINSZ... no
checking whether sys/ioctl.h defines TIOCGWINSZ... yes
checking return type of signal handlers... void
checking for size_t... yes
checking for struct timeval... yes
checking whether byte ordering is bigendian... no
checking for an ANSI C-conforming const... yes
checking for working volatile... yes
checking for unsigned short... yes
checking size of unsigned short... 2
checking for unsigned int... yes
checking size of unsigned int... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking for working memcmp... yes
checking for exp... yes
checking for pcap_open_live... no
configure: error: Cannot proceed without a packet capture library

```

---

### Post by slooow on 2010-04-09
Have you got libpcap installed?

---

### Post by gmargo on 2010-04-09
First of all, there is no need to compile this yourself, as you can simply install the **pktstat** package from the repository, using your favorite package manager.  The version in the Karmic repository is 1.8.4, newer than the one you downloaded.

[http://packages.ubuntu.com/karmic/pktstat](http://packages.ubuntu.com/karmic/pktstat)

If you insist on compiling however, you will first need to install the following packages:[SIZE=2]** libncurses5,**[/SIZE][SIZE=2]** libncurses5-dev,**[/SIZE][SIZE=2]** libpcap0.8,**[/SIZE][SIZE=2]** libpcap0.8-dev**.[/SIZE][SIZE=2]
[/SIZE]

---

### Post by nitstorm on 2010-04-27
Thanks and sorry for the late reply..

---

