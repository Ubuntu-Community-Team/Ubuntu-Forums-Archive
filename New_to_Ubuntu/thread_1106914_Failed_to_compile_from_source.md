---
title: "Failed to compile from source"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Bölvaður on 2009-03-26
Mission: To install Crack Attack (newest version)
Execution: compile from source
Failure: cannot make, fail at ./configure

untared it to : ~/Desktop/crack-attack-1.1.10
changed directories into it and went:
```

$ **./configure **
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
**checking for working makeinfo... missing**
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes[B]
checking whether the C compiler (gcc  ) is a cross-compiler... no[/B]
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes[B]
checking whether the C++ compiler (c++  ) is a cross-compiler... no[/B]
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking for a BSD compatible install... /usr/bin/install -c
checking how to run the C preprocessor... (cached) gcc -E
checking for ANSI C header files... (cached) yes
checking for limits.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/socket.h... (cached) yes
checking for sys/poll.h... (cached) yes
checking for netinet/in.h... (cached) yes
checking for netdb.h... (cached) yes
checking for arpa/inet.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for working const... (cached) yes
checking for inline... (cached) inline
checking for X... (cached) libraries , headers 
[B]checking for dnet_ntoa in -ldnet... (cached) no
checking for dnet_ntoa in -ldnet_stub... (cached) no[/B]
checking for gethostbyname... (cached) yes
checking for connect... (cached) yes
checking for remove... (cached) yes
checking for shmat... (cached) yes
checking for IceConnectionNumber in -lICE... (cached) yes
checking for socket... (cached) yes
checking for poll... (cached) yes
creating ./config.status
creating Makefile
creating src/Makefile
creating data/Makefile
creating doc/Makefile
creating src/config.h
**src/config.h is unchanged**

```

and ofcourse because of the failure before this happens.

```
**$ make**
Making all in src
make[1]: Entering directory `/home/gummi/Desktop/crack-attack-1.1.10/src'
c++ -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/crack-attack/"'    -O6 -s -c Attack.cxx
In file included from /usr/include/c++/4.2/sstream:588,
                 from TextureLoader.h:7,
                 from Attack.cxx:45:
/usr/include/c++/4.2/bits/sstream.tcc: In member function &#8216;virtual typename std::basic_stringbuf<_CharT, _Traits, _Alloc>::int_type std::basic_stringbuf<_CharT, _Traits, _Alloc>::overflow(typename _Traits::int_type)&#8217;:
/usr/include/c++/4.2/bits/sstream.tcc:116: error: expected unqualified-id before &#8216;(&#8217; token
make[1]: *** [Attack.o] Error 1
make[1]: Leaving directory `/home/gummi/Desktop/crack-attack-1.1.10/src'
make: *** [all-recursive] Error 1

```

I was unable to fix it my self :( feel lke a beginner, but then again I am not used to compile.

---

### Post by cariboo on 2009-03-26
From the looks of it you need to install **build-essentials**. Build-essentials are in the repositories and you can use synaptic to install it.

Jim

---

### Post by snova on 2009-03-26
> **Bölvaður said:**
> ```

[B]checking for working makeinfo... missing
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking for dnet_ntoa in -ldnet... (cached) no
checking for dnet_ntoa in -ldnet_stub... (cached) no
src/config.h is unchanged[/B]

```

Installing build-essential as cariboo907 suggested will probably help, but I wanted to mention that these are not failures. If it hadn't succeeded, configure wouldn't have generated Makefiles, and make would have complained about them being missing.

makeinfo is only useful if you are building a particular form of documentation.

Cross-compilers are only used in particular scenarios, and I would be more worried if it said Yes. :)

Those two dnet-related functions, I'm not entirely sure of, but it looks like it's a really really old networking API.

And that src/config.h isn't changed, I would guess means you ran ./configure more than once, and it saw no need to regenerate it.

---

### Post by Bölvaður on 2009-03-27
build-essential has already been installed.
I'm not really that green ;) and I have compiled successfully a program on this computer so that cannot be it.

```
# apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

I suspect there is an bug in the code, but didn't see a syntax error when I skimmed through the TextureLoader.h that was called from Attack.cxx and yes.. there are 2 funny lines, both exactly the same: ostringstream s;

So this is a compile error which I guess I'll have to report to the makers of this great game.
```
$ make
Making all in src
make[1]: Entering directory `/home/bölvaður/Desktop/crack-attack-1.1.10/src'
c++ -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/crack-attack/"'    -O6 -s -c Attack.cxx
In file included from Attack.cxx:45:
TextureLoader.h: In static member function ‘static void TextureLoader::buildLocalDataDirectoryName(char*)’:
**TextureLoader.h:30: error: aggregate ‘std::ostringstream s’ has incomplete type and cannot be defined**
TextureLoader.h: In static member function ‘static void TextureLoader::buildLocalDataFileName(const char*, char*)’:
**TextureLoader.h:42: error: aggregate ‘std::ostringstream s’ has incomplete type and cannot be defined**
make[1]: *** [Attack.o] Error 1
make[1]: Leaving directory `/home/bölvaður/Desktop/crack-attack-1.1.10/src'
make: *** [all-recursive] Error 1


```


Can anyone try to compile it and post the results?

---

### Post by snova on 2009-03-27
> **Bölvaður said:**
> I suspect there is an bug in the code, but didn't see a syntax error when I skimmed through the TextureLoader.h that was called from Attack.cxx and yes.. there are 2 funny lines, both exactly the same: ostringstream s;

No, it's not a syntax error...

> ```
[B]TextureLoader.h:30: error: aggregate &#8216;std::ostringstream s&#8217; has incomplete type and cannot be defined
TextureLoader.h:42: error: aggregate &#8216;std::ostringstream s&#8217; has incomplete type and cannot be 
```

Open TextureLoader.h and add this line at the top:

```
#include <sstream>
```

Try compiling again, I think that will fix it.

---

