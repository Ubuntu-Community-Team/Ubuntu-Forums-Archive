---
title: "Watching youtube (and other blocked sites) in China"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by Falc7 on 2010-03-26
I am in China and i want to watch videos on youtube. I have done some research on the topic, i was advised to use proxies, (so i tried dave proxy and google translate) and these worked for text and images, but not videos. I was also advised to try youtube download sites, i tried a whole bunch of those but none of them seemed to work. Can someone help?

---

### Post by cgroza on 2010-03-26
In China they don't allow you to watch [www.youtube.com](www.youtube.com) ?? :o:o

---

### Post by Mykk on 2010-03-26
Dont use the google translate as a proxy.

Go to google and search something along the lines of "free proxy site".

I _think_ that there is a good one called fire proxy or something to that effect.

---

### Post by liam.lah on 2010-03-26
Try [openvpn]("http://openvpn.net/index.php/open-source.html"), you can make youtube think you are in another country, similar to a proxy, the only problem being it may be slow for looking at movies. Either that... or move to hong kong

Good luck getting past the filter.

---

### Post by liam.lah on 2010-03-26
> **Mykk said:**
> Dont use the google translate as a proxy.

Go to google and search something along the lines of "free proxy site".

I _think_ that there is a good one called fire proxy or something to that effect.

Unless google results are no longer filtered in China, the chances of finding a proxy site via search is low. i am not sure what the current situation is, chinese citizens may be being directed to google hong kong, but i doubt the government is going to let that go on for very long

---

### Post by _h_ on 2010-03-26
> **cgroza said:**
> In China they don't allow you to watch [www.youtube.com]("http://www.youtube.com") ?? :o:o

Not just Youtube, they have like half the internet blocked. lol

I feel bad for OP. :(

---

### Post by Ghost|BTFH on 2010-03-26
[www.secure-tunnel.com](www.secure-tunnel.com)
[www.stayinvisible.com](www.stayinvisible.com)

Another person suggested:

iptables -A INPUT -p tcp --tcp-flags
RST RST -j DROP

Some other proxies include:

ohnu.info
pr4xy.info

They include ssl capacity.

If the OP needs more than that, drop me a note, there's only about 11 pages of proxies out there available.

---

### Post by Mykk on 2010-03-26
I don't know how they work but I have read up on:

Privoxy + Tor - both applications which you can install and supposedly browse the internet anonymously.

Might be something worth looking into.

---

### Post by Ghost|BTFH on 2010-03-26
Opening up your synaptic package manager and doing a search for anon-proxy might also be a big help...if they don't restrict encrypted data streams, that will allow you to fetch pretty much anything, anywhere.

Cheers,
Ghost|BTFH

---

### Post by donkyhotay on 2010-03-26
> **liam.lah said:**
> Unless google results are no longer filtered in China, the chances of finding a proxy site via search is low. i am not sure what the current situation is, chinese citizens may be being directed to google hong kong, but i doubt the government is going to let that go on for very long

Google just went completely unfiltered in china, google china now goes through google hong kong. Of course the chinese government has (partially) blocked them because of it. Details can be found here:
[http://www.eff.org/deeplinks/2010/03/google-stops-its-chinese-censorship](http://www.eff.org/deeplinks/2010/03/google-stops-its-chinese-censorship)

---

### Post by Falc7 on 2010-03-26
> **cgroza said:**
> In China they don't allow you to watch [www.youtube.com](www.youtube.com) ?? :o:o
**Nope, nor facebook, or many image hosting sites**

> **Mykk said:**
> Dont use the google translate as a proxy.

Go to google and search something along the lines of "free proxy site".

I _think_ that there is a good one called fire proxy or something to that effect.

**Blocked unfortunately**

> **liam.lah said:**
> Try [openvpn]("http://openvpn.net/index.php/open-source.html"), you can make youtube think you are in another country, similar to a proxy, the only problem being it may be slow for looking at movies. Either that... or move to hong kong

Good luck getting past the filter.
**It looks kinda complicated but i'll give it a go**

> **Mykk said:**
> I don't know how they work but I have read up on:

Privoxy + Tor - both applications which you can install and supposedly browse the internet anonymously.

Might be something worth looking into.

**I have heard about Tor but its blocked, i've also tried Tor button with FF, but couldn't get it to work**

> **Ghost|BTFH said:**
> Opening up your synaptic package manager and doing a search for anon-proxy might also be a big help...if they don't restrict encrypted data streams, that will allow you to fetch pretty much anything, anywhere.

Cheers,
Ghost|BTFH

**I've just dl'ed that, it didn't add anything to my programs menu but i'll do a search for info on how to use it if you say its good**

> **Ghost|BTFH said:**
> [www.secure-tunnel.com](www.secure-tunnel.com)
[www.stayinvisible.com](www.stayinvisible.com)

Another person suggested:

iptables -A INPUT -p tcp --tcp-flags
RST RST -j DROP

Some other proxies include:

ohnu.info
pr4xy.info

They include ssl capacity.

If the OP needs more than that, drop me a note, there's only about 11 pages of proxies out there available.

**I'll drop you a note about the iptables configuring, those proxies you recommended did the same as the other ones i've tried, it works for texts and images, but not videos or youtube**

---

### Post by liam.lah on 2010-03-26
If you have windows too,[ hotspot shield]("http://hotspotshield.com/") is as easy as installing an .exe and flicking it on and off.

---

### Post by hatalar205 on 2010-03-26
> **Falc7 said:**
> I am in China and i want to watch videos on youtube. I have done some research on the topic, i was advised to use proxies, (so i tried dave proxy and google translate) and these worked for text and images, but not videos. I was also advised to try youtube download sites, i tried a whole bunch of those but none of them seemed to work. Can someone help?

Did you try opendns?
[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by Falc7 on 2010-03-26
> **liam.lah said:**
> If you have windows too,[ hotspot shield]("http://hotspotshield.com/") is as easy as installing an .exe and flicking it on and off.

**Thanks i'll try that as well on windows**

> **hatalar205 said:**
> Did you try opendns?
[http://www.opendns.com/](http://www.opendns.com/)

**I've just signed up for opendns, and followed all their instructions exactly, but it still says i am not using open dns yet. hmmm, thats annoying, it looked promising**

---

### Post by hatalar205 on 2010-03-26
> **Falc7 said:**
> **Thanks i'll try that as well on windows**



**I've just signed up for opendns, and followed all their instructions exactly, but it still says i am not using open dns yet. hmmm, thats annoying, it looked promising**


It is not dificult. Write click Network Manager applet
**Edit Connections > choose yours > IPV4 Settings > Change the default one to "Only automatic (DHCP) adresses" **

In the **DNS servers** box write **208.67.222.222, 208.67.220.220** 
Save and quit.

---

### Post by Falc7 on 2010-03-26
> **hatalar205 said:**
> It is not dificult. Write click Network Manager applet
**Edit Connections > choose yours > IPV4 Settings > Change the default one to "Only automatic (DHCP) adresses" **

In the **DNS servers** box write **208.67.222.222, 208.67.220.220** 
Save and quit.

Yep done that
[http://www.ubuntu-pics.de/bild/49050/screenshot_003_f0iGjV.png](http://www.ubuntu-pics.de/bild/49050/screenshot_003_f0iGjV.png)

But all tests tell me i am not using it yet

---

### Post by mangurt on 2010-03-26
You could try secure-tunnel (used them, they are great) or you can try vyprvpn (golden frog).  I don't know if you can connect to a VPN in china or not.  OPENDNS my work also.

---

### Post by NightwishFan on 2010-03-26
Be careful whatever you do, and good luck.

---

### Post by hatalar205 on 2010-03-26
You must disconnect and connect again. If not reboot your computer.

---

### Post by Falc7 on 2010-03-28
> **hatalar205 said:**
> You must disconnect and connect again. If not reboot your computer.

Yep done that too, still says i am not using it

---

### Post by Doctor Mike on 2010-03-28
use any linux distro. any open source browser. go to: [http://hidemyass.com/](http://hidemyass.com/)

will work for most video content... no software or changes to be detected... online free http proxy. select specific link to video first then drop into box. then hide my a**...

also works in canada for blocked content...

---

### Post by Falc7 on 2010-03-31
> **Doctor Mike said:**
> use any linux distro. any open source browser. go to: [http://hidemyass.com/](http://hidemyass.com/)

will work for most video content... no software or changes to be detected... online free http proxy. select specific link to video first then drop into box. then hide my a**...

also works in canada for blocked content...

That site is blocked here :(

---

### Post by Chronon on 2010-03-31
I wonder if bridges could help to access TOR:
[https://www.torproject.org/bridges](https://www.torproject.org/bridges)

---

### Post by Falc7 on 2010-03-31
> **liam.lah said:**
> If you have windows too,[ hotspot shield]("http://hotspotshield.com/") is as easy as installing an .exe and flicking it on and off.

Thanks this works great for windows, now if only i could get it working on ubuntu

> **Chronon said:**
> I wonder if bridges could help to access TOR:
[https://www.torproject.org/bridges](https://www.torproject.org/bridges)

I can access the Tor website now using a proxy, but i can't install their software because when i add it to my software sources it is blocked, and Tor dosen't seem to be in the ubuntu repos. I need to find some way of installing Tor, is it a deb somewhere?

---

### Post by Falc7 on 2010-04-01
> **Ghost|BTFH said:**
> Opening up your synaptic package manager and doing a search for anon-proxy might also be a big help...if they don't restrict encrypted data streams, that will allow you to fetch pretty much anything, anywhere.

Cheers,
Ghost|BTFH

I've installed this, and i can see it starts when i turn the computer on. But it dosen't seem to effect what sites i can see at all

I've just about given up on getting open dns to work, i've done everything it says but still no luck

I am going to keep looking for a Tor deb

---

### Post by mcoleman44 on 2010-04-01
Im not sure if it will work or not, but you could try installing Hotspot shield using wine in Ubuntu. No guarantees though. Good luck.

---

### Post by Andavane on 2010-04-01
Can't help technically, but just sending best wishes & moral support.
So sorry you're being censored! :-(

Regards

John

---

### Post by The Real Dave on 2010-04-01
It won't let you watch Youtube, but your welcome to use my proxy if it helps.

[cyrix.comoj.com]("http://cyrix.comoj.com/")

Just click the big W to get to the site.

---

### Post by Martje_001 on 2010-04-01
Try changing your DNS settings. Open /etc/resolv.conf with admin right, by entering the following in a terminal:
```
gksudo gedit /etc/resolv.conf
```
Add the following:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```
And reboot. Is it blocked now?

[http://code.google.com/intl/nl/speed/public-dns/](http://code.google.com/intl/nl/speed/public-dns/)

---

### Post by Chronon on 2010-04-01
> **Falc7 said:**
> 
I can access the Tor website now using a proxy, but i can't install their software because when i add it to my software sources it is blocked, and Tor dosen't seem to be in the ubuntu repos. I need to find some way of installing Tor, is it a deb somewhere?

Can you download the source tarball?  If you can get that then you can compile TOR on your machine.

---

### Post by Falc7 on 2010-04-02
> **The Real Dave said:**
> It won't let you watch Youtube, but your welcome to use my proxy if it helps.

[cyrix.comoj.com]("http://cyrix.comoj.com/")

Just click the big W to get to the site.

**hhmm, It still says sites like youtube/facebook/imageshack are blocked**

> **Martje_001 said:**
> Try changing your DNS settings. Open /etc/resolv.conf with admin right, by entering the following in a terminal:
```
gksudo gedit /etc/resolv.conf
```
Add the following:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```
And reboot. Is it blocked now?

[http://code.google.com/intl/nl/speed/public-dns/](http://code.google.com/intl/nl/speed/public-dns/)

**I did that, then rebooted, but youtube and others are still blocked. Also, when i put the code in again, i noticed that it had reverted to how it was before i added the extra lines**

> **Chronon said:**
> Can you download the source tarball?  If you can get that then you can compile TOR on your machine.

[B]I've managed to get the source tarball! :D
I read the read me, and it says to put this into terminal
```
./configure; make; make install
``` so i did, but i get the error message:
```
...................
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'tor' '/usr/local/bin/tor'
/usr/bin/install: cannot create regular file `/usr/local/bin/tor': Permission denied
make[3]: *** [install-binPROGRAMS] Error 1
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src'
make: *** [install-recursive] Error 1
jamie@jamie-kubuntu:~/Desktop/tor-0.2.1.25$ 

``` 
[/B]

---

### Post by @rizz on 2010-04-02
[COLOR=Green]**Here is a Trick!!!!**[/COLOR]

**How to bypass YouTube Region Filtering ?**
 YouTube uses your computer IP address to determine your physical location / country. In order to bypass these country-specific restrictions on YouTube, try this trick:
 If the URL of the YouTube video is [http://www.youtube.com/watch?v=yEwD36Dk1jw](http://www.youtube.com/watch?v=yEwD36Dk1jw) – just replace the /watch?v= part with /v so your new URL becomes [http://www.youtube.com/v/yEwD36Dk1jw](http://www.youtube.com/v/yEwD36Dk1jw)

 Let us know if it works!

---

### Post by Chronon on 2010-04-02
> **Falc7 said:**
> 
[B]I've managed to get the source tarball! :D
I read the read me, and it says to put this into terminal
```
./configure; make; make install
``` so i did, but i get the error message:
```
...................
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'tor' '/usr/local/bin/tor'
/usr/bin/install: cannot create regular file `/usr/local/bin/tor': Permission denied
make[3]: *** [install-binPROGRAMS] Error 1
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src'
make: *** [install-recursive] Error 1
jamie@jamie-kubuntu:~/Desktop/tor-0.2.1.25$ 

``` 
[/B]
Did you do this bit first?
> If you're building from source, first install libevent, and make sure you have openssl and zlib (including the -devel packages if applicable). 

---

### Post by Falc7 on 2010-04-02
> **Chronon said:**
> Did you do this bit first?

Yep i have versions of those packages, it prompted me to install several packages during the process, all of which i did, but i have zlib1g instead of zlib, if that is important.

I must say i am a little confused however, when following the instructions included in the tar ball, i do/get this:
```
jamie@jamie-kubuntu:~/Desktop/tor-0.2.1.25$ ./configure; make; make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
make[1]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25'
Making all in src
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src'
Making all in common
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/common'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/common'
Making all in or
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
Making all in tools
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/tools'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/tools'
Making all in win32
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/win32'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/win32'
Making all in config
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/config'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/config'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src'
Making all in doc
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/doc'
Making all in design-paper
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/doc/design-paper'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/doc/design-paper'
Making all in spec
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/doc/spec'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/doc/spec'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/doc'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/doc'
Making all in contrib
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/contrib'
Making all in osx
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/contrib/osx'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/contrib/osx'
Making all in suse
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/contrib/suse'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/contrib/suse'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/contrib'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/contrib'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/contrib'
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25'
make[1]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25'
Making install in src
make[1]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src'
Making install in common
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/common'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/common'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/common'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/common'
Making install in or
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'tor' '/usr/local/bin/tor'
/usr/bin/install: cannot create regular file `/usr/local/bin/tor': Permission denied
make[3]: *** [install-binPROGRAMS] Error 1
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src'
make: *** [install-recursive] Error 1
jamie@jamie-kubuntu:~/Desktop/tor-0.2.1.25$ 

```

But there are different instructions on the Tor website, which i am unable to follow, the instructions are here
[http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)

I get stuck here
```
jamie@jamie-kubuntu:~$ sudo apt-get source tor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for tor
jamie@jamie-kubuntu:~$ 

```

> **@rizz said:**
> [COLOR=Green]**Here is a Trick!!!!**[/COLOR]

**How to bypass YouTube Region Filtering ?**
 YouTube uses your computer IP address to determine your physical location / country. In order to bypass these country-specific restrictions on YouTube, try this trick:
 If the URL of the YouTube video is [http://www.youtube.com/watch?v=yEwD36Dk1jw](http://www.youtube.com/watch?v=yEwD36Dk1jw) &#8211; just replace the /watch?v= part with /v so your new URL becomes [http://www.youtube.com/v/yEwD36Dk1jw](http://www.youtube.com/v/yEwD36Dk1jw)

 Let us know if it works!

Already tried that, no luck, thanks anyway

---

### Post by undecim on 2010-04-02
> **Falc7 said:**
> [B]I've managed to get the source tarball! :D
I read the read me, and it says to put this into terminal
```
./configure; make; make install
``` so i did, but i get the error message:
```
...................
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'tor' '/usr/local/bin/tor'
/usr/bin/install: cannot create regular file `/usr/local/bin/tor': Permission denied
make[3]: *** [install-binPROGRAMS] Error 1
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src'
make: *** [install-recursive] Error 1
jamie@jamie-kubuntu:~/Desktop/tor-0.2.1.25$ 

``` 
[/B]

You need to run the "make install" part as root. It looks like everything else went fine, so you should just be able to go back to that directory and run:
```
sudo make install
```

---

### Post by Falc7 on 2010-04-02
> **undecim said:**
> You need to run the "make install" part as root. It looks like everything else went fine, so you should just be able to go back to that directory and run:
```
sudo make install
```

I get this, but no .deb file appears in the directory, some files do appear however
Screenshot:
[[img]http://www.ubuntu-pics.de/thumb/50182/screenshot_002_65mymK.png[/img]](http://www.ubuntu-pics.de/bild/50182/screenshot_002_65mymK.png)

```
jamie@jamie-kubuntu:~/Desktop/tor-0.2.1.25$ sudo make install
Making install in src
make[1]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src'
Making install in common
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/common'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/common'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/common'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/common'
Making install in or
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'tor' '/usr/local/bin/tor'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/or'
Making install in tools
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/tools'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/tools'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'tor-resolve' '/usr/local/bin/tor-resolve'
  /usr/bin/install -c 'tor-gencert' '/usr/local/bin/tor-gencert'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/tools'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/tools'
Making install in win32
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/win32'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/win32'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/win32'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/win32'
Making install in config
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/config'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src/config'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/etc/tor" || /bin/mkdir -p "/usr/local/etc/tor"
 /usr/bin/install -c -m 644 'torrc.sample' '/usr/local/etc/tor/torrc.sample'
test -z "/usr/local/share/tor" || /bin/mkdir -p "/usr/local/share/tor"
 /usr/bin/install -c -m 644 'geoip' '/usr/local/share/tor/geoip'
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/config'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src/config'
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/src'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src'
make[1]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/src'
Making install in doc
make[1]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/doc'
Making install in design-paper
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/doc/design-paper'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/doc/design-paper'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/doc/design-paper'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/doc/design-paper'
Making install in spec
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/doc/spec'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/doc/spec'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/doc/spec'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/doc/spec'
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/doc'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/doc'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './tor.1' '/usr/local/share/man/man1/tor.1'
 /usr/bin/install -c -m 644 './tor-resolve.1' '/usr/local/share/man/man1/tor-resolve.1'
 /usr/bin/install -c -m 644 './tor-gencert.1' '/usr/local/share/man/man1/tor-gencert.1'
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/doc'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/doc'
make[1]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/doc'
Making install in contrib
make[1]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/contrib'
Making install in osx
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/contrib/osx'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/contrib/osx'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/contrib/osx'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/contrib/osx'
Making install in suse
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/contrib/suse'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/contrib/suse'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/contrib/suse'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/contrib/suse'
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/contrib'
make[3]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25/contrib'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c 'torify' '/usr/local/bin/torify'
test -z "/usr/local/etc/tor" || /bin/mkdir -p "/usr/local/etc/tor"
 /usr/bin/install -c -m 644 'tor-tsocks.conf' '/usr/local/etc/tor/tor-tsocks.conf'
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './torify.1' '/usr/local/share/man/man1/torify.1'
make[3]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/contrib'
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/contrib'
make[1]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25/contrib'
make[1]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25'
make[2]: Entering directory `/home/jamie/Desktop/tor-0.2.1.25'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25'
make[1]: Leaving directory `/home/jamie/Desktop/tor-0.2.1.25'
jamie@jamie-kubuntu:~/Desktop/tor-0.2.1.25$ 

```

---

### Post by undecim on 2010-04-02
> **Falc7 said:**
> I get this, but no .deb file appears in the directory, some files do appear however

You don't get .deb files when you compile software. According to the output you gave me, tor is now installed on your system.

You should be able to run it with "tor", and then use the SOCKS proxy on localhost port 9050

---

### Post by Chronon on 2010-04-02
Good catch, undecim!

---

### Post by Falc7 on 2010-04-03
> **undecim said:**
> You don't get .deb files when you compile software. According to the output you gave me, tor is now installed on your system.

You should be able to run it with "tor", and then use the SOCKS proxy on localhost port 9050

Ah yes you are right, it is installed now, how do i use the SOCKS proxy on local host port 9050?

I had a play around with Vidalia, and after using some bridges got it sucessfully connected to the Tor network, but blocked websites still wouldn't load

---

### Post by Chronon on 2010-04-03
You have completed step 1.  Now do the rest of the steps here:
[http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)

---

### Post by undecim on 2010-04-03
> **Falc7 said:**
> Ah yes you are right, it is installed now, how do i use the SOCKS proxy on local host port 9050?

I had a play around with Vidalia, and after using some bridges got it sucessfully connected to the Tor network, but blocked websites still wouldn't load

In firefox, you can go to preferences, Advanced section, network tab and click the settings button.

You can also get an add on like TorButton or FoxyProxy. Just make sure you either use OpenDNS, Google's DNS servers (8.8.8.8 and 8.8.4.4) or have your browser set up to route DNS queries through the proxy as well as web request. I know this can be done with FoxyProxy, but I'm not sure about TorButton or Firefox's default proxy setup.

I personally recommend FoxyProxy, if for nothing more than the patterns feature - You can specify only blocked sites to use the proxy on, and that will keep you from loading, for example, advertisements from another domain through tor.

You might also want to look into Tork. It's a graphical frontend to Tor's configuration and runtime functions. To use it, you will need to add (or uncomment if they are already there somewhere) these lines to /etc/tor/torrc:
```
ControlPort 9051
HashedControlPassword 16:B7248B7E9EC72993600381B404EFC1BE7EAD85343168CB37D1955CF426
```

You will need to replace 16:B7248B7E9EC72993600381B404EFC1BE7EAD85343168CB37D1955CF426 with the hash generated from "tor --hash-password password" where password is the password you want to use.

Then, you can configure Tork to connect to a local tor instance at control port 9051, with whatever password you chose.

---

### Post by Chronon on 2010-04-04
> **undecim said:**
> 
You might also want to look into Tork. It's a graphical frontend to Tor's configuration and runtime functions. To use it, you will need to add (or uncomment if they are already there somewhere) these lines to /etc/tor/torrc:
```
ControlPort 9051
HashedControlPassword 16:B7248B7E9EC72993600381B404EFC1BE7EAD85343168CB37D1955CF426
```

You will need to replace 16:B7248B7E9EC72993600381B404EFC1BE7EAD85343168CB37D1955CF426 with the hash generated from "tor --hash-password password" where password is the password you want to use.

Then, you can configure Tork to connect to a local tor instance at control port 9051, with whatever password you chose.

That's a nice little tidbit.  Thanks!  :guitar:

---

### Post by undecim on 2010-04-04
Also, I forgot to mention it, but Tork keeps on eye on your tor and normal traffic and alerts you of things such as DNS leaks, unencrypted connections, etc.

---

### Post by Falc7 on 2010-04-04
> **undecim said:**
> In firefox, you can go to preferences, Advanced section, network tab and click the settings button.

You can also get an add on like TorButton or FoxyProxy. Just make sure you either use OpenDNS, Google's DNS servers (8.8.8.8 and 8.8.4.4) or have your browser set up to route DNS queries through the proxy as well as web request. I know this can be done with FoxyProxy, but I'm not sure about TorButton or Firefox's default proxy setup.

I personally recommend FoxyProxy, if for nothing more than the patterns feature - You can specify only blocked sites to use the proxy on, and that will keep you from loading, for example, advertisements from another domain through tor.

You might also want to look into Tork. It's a graphical frontend to Tor's configuration and runtime functions. To use it, you will need to add (or uncomment if they are already there somewhere) these lines to /etc/tor/torrc:
```
ControlPort 9051
HashedControlPassword 16:B7248B7E9EC72993600381B404EFC1BE7EAD85343168CB37D1955CF426
```

You will need to replace 16:B7248B7E9EC72993600381B404EFC1BE7EAD85343168CB37D1955CF426 with the hash generated from "tor --hash-password password" where password is the password you want to use.

Then, you can configure Tork to connect to a local tor instance at control port 9051, with whatever password you chose.

Awesome its working now! Thanks alot :D
I am using tor button atm. Before i move onto playing with other ways of connecting, (such as foxy proxy and Tork) i wanted to have a quick play at getting it to work in chrome. So i installed a proxy extension (switchy), copied in the network settings from Tor button, but it didn't work, anyone know what i am doing wrong?
[[img]http://www.ubuntu-pics.de/thumb/50551/screenshot_001_kKchP4.png[/img]](http://www.ubuntu-pics.de/bild/50551/screenshot_001_kKchP4.png)

---

### Post by Nisal on 2010-04-04
use some good proxies u know right how to configure them in a browser ?

---

### Post by undecim on 2010-04-04
> **Falc7 said:**
> Awesome its working now! Thanks alot :D
I am using tor button atm. Before i move onto playing with other ways of connecting, (such as foxy proxy and Tork) i wanted to have a quick play at getting it to work in chrome. So i installed a proxy extension (switchy), copied in the network settings from Tor button, but it didn't work, anyone know what i am doing wrong?
[[img]http://www.ubuntu-pics.de/thumb/50551/screenshot_001_kKchP4.png[/img]](http://www.ubuntu-pics.de/bild/50551/screenshot_001_kKchP4.png)

I don't see anything wrong there. Are you sure you are using the new profile? And I assume Polipo is listening on port 8118 and routing traffic through tor.

Also, Tork isn't a way of connecting to tor. It does make Konqueror use tor, but it's also a graphical manager for tor that lets you change identity with a button click, or choose which exit server you would like to use. It also is a good way to keep privacy intact while browsing. I don't know what kind of trouble you can get into for circumventing the internet blocks in China, but if you can get arrested for it or have your computer taken, etc., I recommend that you use it.

---

### Post by Falc7 on 2010-04-04
> **undecim said:**
> I don't see anything wrong there. Are you sure you are using the new profile? And I assume Polipo is listening on port 8118 and routing traffic through tor.

Also, Tork isn't a way of connecting to tor. It does make Konqueror use tor, but it's also a graphical manager for tor that lets you change identity with a button click, or choose which exit server you would like to use. It also is a good way to keep privacy intact while browsing. I don't know what kind of trouble you can get into for circumventing the internet blocks in China, but if you can get arrested for it or have your computer taken, etc., I recommend that you use it.

Okay thanks i will definitely look closely at Tork in that case.
Would it be that i have to set up Polipo for use in chrome separately?

---

### Post by undecim on 2010-04-04
> **Falc7 said:**
> Would it be that i have to set up Polipo for use in chrome separately?

No. If it's listening for HTTP requests, it would work for any browser that uses HTTP (i.e. any browser)
Try taking the HTTP IP and port out of the chrome configuration. It should fall back on the SOCKS proxy, which will use tor directly.

---

### Post by Falc7 on 2010-04-05
Done that, still no luck.
Here is a screenshot, one is FF with tor button and it can connect to youtube. On the other side of the screen, is chrome, it won't connect to youtube, but it shows the SOCKS settings and that profile Tor is selected. Quite confused as to why it isen't working
[[img]http://www.ubuntu-pics.de/thumb/50557/screenshot_003_bu631r.png[/img]](http://www.ubuntu-pics.de/bild/50557/screenshot_003_bu631r.png)


Also, i was looking to use Tork, but there isen't a folder here:
/etc/tor/torrc

---

### Post by undecim on 2010-04-05
> **Falc7 said:**
> Done that, still no luck.
Here is a screenshot, one is FF with tor button and it can connect to youtube. On the other side of the screen, is chrome, it won't connect to youtube, but it shows the SOCKS settings and that profile Tor is selected. Quite confused as to why it isen't working
[[img]http://www.ubuntu-pics.de/thumb/50557/screenshot_003_bu631r.png[/img]](http://www.ubuntu-pics.de/bild/50557/screenshot_003_bu631r.png)


Also, i was looking to use Tork, but there isen't a folder here:
/etc/tor/torrc

It may be that Chrome is using blocked DNS entries. Try setting the version to SOCKS v4 in the Switchy configuration.

Also, about torrc, see if you have a .torrc in your home directory. If not, then you will have to create /etc/tor/torrc

---

### Post by Yvan300 on 2010-04-05
This made my day for sure!

---

### Post by Falc7 on 2010-04-07
> **undecim said:**
> It may be that Chrome is using blocked DNS entries. Try setting the version to SOCKS v4 in the Switchy configuration.

Also, about torrc, see if you have a .torrc in your home directory. If not, then you will have to create /etc/tor/torrc

Switching to SOCKS v4 didn't help either, if necessary i will just use FF for youtube and stuff, its not a big deal, i was just curious why is wasent working with chrome

---

### Post by life-on-mars on 2010-07-07
Since last year, using tor has become a bit tricky. If you can bootstrap to 10% (see /var/tor/log/tor.log) it should work, but it might take some time (up to a few hours) to build a circuit. If tor cannot connect to a directory server, you'll need to add bridges (using vidalia, tork or editing torrc). If you want to make tor available any time you might need to run it on a server box that is up 24h a day. For laptops you can sync /var/lib/tor to speed up bootstrapping. The more often and longer you use tor, the faster the bootstrapping process.

If you use polipo, you'll probably have to configure it to use tor via Socks5. Polipo uses port 8123 by default.

If you don't use polipo or privoxy, you will probably need to change your DNS server, as using tor directly does not tunnel DNS requests.

---

### Post by mayta on 2010-07-22
Hi! I may have a solution.. :D
I'm in China too, and months ago i found good alternative to HSS, it's called FreeU from dynaweb. 
Obviously Dynaweb is blocked but if you have Windows and HSS can connect with that and download it.

It works in ubuntu, you have to open it with WINE. 

It's slow sometimes, better than nothing, right? ;)

---

