---
title: "install tar.bz2"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by MelDJ on 2009-08-18
hi. i want to install vdrift. i downloaded the tar.bz2 file. but i cant install it. i tried looking around for ways but all i got was how to install the older releases of vdrift. hel pls

---

### Post by decoherence on 2009-08-18
> **MelDJ said:**
> hi. i want to install vdrift. i downloaded the tar.bz2 file. but i cant install it. i tried looking around for ways but all i got was how to install the older releases of vdrift. hel pls

Can you post the link to the specific tar.bz2 you're using pls?

---

### Post by MelDJ on 2009-08-18
edit build from source
here's the link [http://sourceforge.net/projects/vdrift/files/vdrift/vdrift-2009-06-15/vdrift-2009-06-15-src.tar.bz2/download](http://sourceforge.net/projects/vdrift/files/vdrift/vdrift-2009-06-15/vdrift-2009-06-15-src.tar.bz2/download)

---

### Post by Faud on 2009-08-18
You can try here if you have not looked here before.

[http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually](http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually)

---

### Post by arochester on 2009-08-18
Look at "How to install ANYTHING in Ubuntu!" on [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by decoherence on 2009-08-18
> **MelDJ said:**
> install from source

heh okay, nevermind my edits. I'll assume it is the one we get here

[http://sourceforge.net/projects/vdrift/files/vdrift/vdrift-2009-06-15/vdrift-2009-06-15-src.tar.bz2/download](http://sourceforge.net/projects/vdrift/files/vdrift/vdrift-2009-06-15/vdrift-2009-06-15-src.tar.bz2/download)

i'll try building it

---

### Post by MelDJ on 2009-08-18
when i try to install it, it says it does not have the ./configure file. i read the readme and it said that it install with a python script i think called scons..

---

### Post by MelDJ on 2009-08-18
> **Faud said:**
> You can try here if you have not looked here before.

[http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually](http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually)

didn't work...but thanks..bookmarked for future reference:KS

---

### Post by decoherence on 2009-08-18
I'm downloading it but it's pretty big. Says another hour to go.

In the mean time, you can get scons from Synaptic and see if the readme makes more sense.

You'll also no doubt have to install a bunch of -dev files.

Nice looking game!

---

### Post by MelDJ on 2009-08-18
i have got scons already. maybe i will take a deep breath and try installing it again and go through the readme carefully :lolflag:

---

### Post by MelDJ on 2009-08-18
when i did sudo scons install, this comes up:

mel@mel-laptop:~/Desktop/vdrift-2009-06-15$ sudo scons install
[sudo] password for mel: 
scons: Reading SConscript files ...
Checking for C++ header file asio.hpp... yes
Checking for C++ header file boost/bind.hpp... yes
Checking for C++ header file GL/gl.h... yes
Checking for C++ header file GL/glu.h... yes
Checking for C++ header file SDL/SDL.h... yes
Checking for C++ header file SDL/SDL_image.h... yes
Checking for C++ header file SDL/SDL_rotozoom.h... yes
Checking for C++ header file vorbis/vorbisfile.h... yes
Checking for C++ header file GL/glew.h... yes
sh: svnversion: not found
/bin/sh: sdl-config: not found
OSError: 'sdl-config --cflags --libs' exited 127:
  File "/home/mel/Desktop/vdrift-2009-06-15/SConstruct", line 563:
    SConscript('src/SConscript', build_dir='build', duplicate = 0)
  File "/usr/lib/scons/SCons/Script/SConscript.py", line 596:
    return apply(method, args, kw)
  File "/usr/lib/scons/SCons/Script/SConscript.py", line 533:
    return apply(_SConscript, [self.fs,] + files, subst_kw)
  File "/usr/lib/scons/SCons/Script/SConscript.py", line 256:
    exec _file_ in call_stack[-1].globals
  File "/home/mel/Desktop/vdrift-2009-06-15/src/SConscript", line 236:
    local_env.ParseConfig('sdl-config --cflags --libs')
  File "/usr/lib/scons/SCons/Environment.py", line 1288:
    return function(self, self.backtick(command))
  File "/usr/lib/scons/SCons/Environment.py", line 514:
    raise OSError("'%s' exited %d" % (command, status))


what does it mean?

---

### Post by MelDJ on 2009-08-18
it seems that i had to install some extra packages. i then di sudo scons install. it goes well but suddenly errors come up and it ends with
scons: *** [build/httpget.o] Error 1
scons: building terminated because of errors.

anybody????:confused:

---

### Post by decoherence on 2009-08-18
there's an Ubuntu specific command in the README that satisfies the dependencies

sudo apt-get install g++ scons libsdl-gfx1.2-dev libsdl-image1.2-dev libsdl-net1.2-dev libvorbis-dev libglew-dev libasio-dev

after running that I was able to do scons and scons install

---

### Post by MelDJ on 2009-08-18
i got the dependencies. but when i did scons install, i got the error in my earlier post

---

### Post by decoherence on 2009-08-18
> **MelDJ said:**
> i got the dependencies. but when i did scons install, i got the error in my earlier post

Based on the errors I would guess you also need to install libsdl1.2-dev and subversion.

---

### Post by MelDJ on 2009-08-18
i installed both and now i get this 

scons: Reading SConscript files ...
Checking for C++ header file asio.hpp... (cached) yes
Checking for C++ header file boost/bind.hpp... (cached) yes
Checking for C++ header file GL/gl.h... (cached) yes
Checking for C++ header file GL/glu.h... (cached) yes
Checking for C++ header file SDL/SDL.h... (cached) yes
Checking for C++ header file SDL/SDL_image.h... (cached) yes
Checking for C++ header file SDL/SDL_rotozoom.h... (cached) yes
Checking for C++ header file vorbis/vorbisfile.h... (cached) yes
Checking for C++ header file GL/glew.h... (cached) yes
scons: done reading SConscript files.
scons: Building targets ...
g++ -o build/httpget.o -c -Wall -Wextra -Wno-unused-parameter -pthread -g3 -march=athlon64 -D_GNU_SOURCE=1 -D_REENTRANT -Iinclude -Ibullet -I/usr/include/SDL src/httpget.cpp
In file included from /usr/include/asio.hpp:62,
                 from include/httpget.h:7,
                 from src/httpget.cpp:1:
/usr/include/asio/read_until.hpp:23:27: error: boost/regex.hpp: No such file or directory
In file included from /usr/include/asio.hpp:62,
                 from include/httpget.h:7,
                 from src/httpget.cpp:1:
/usr/include/asio/read_until.hpp:211: error: expected unqualified-id before ‘&’ token
/usr/include/asio/read_until.hpp:211: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/asio/read_until.hpp:242: error: expected unqualified-id before ‘&’ token
/usr/include/asio/read_until.hpp:242: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/asio/read_until.hpp:441: error: expected unqualified-id before ‘&’ token
/usr/include/asio/read_until.hpp:441: error: expected ‘,’ or ‘...’ before ‘&’ token
In file included from /usr/include/asio/read_until.hpp:448,
                 from /usr/include/asio.hpp:62,
                 from include/httpget.h:7,
                 from src/httpget.cpp:1:
/usr/include/asio/impl/read_until.ipp:196: error: expected unqualified-id before ‘&’ token
/usr/include/asio/impl/read_until.ipp:196: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/asio/impl/read_until.ipp: In function ‘size_t asio::read_until(SyncReadStream&, asio::basic_streambuf<Allocator>&)’:
/usr/include/asio/impl/read_until.ipp:199: error: ‘expr’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp: At global scope:
/usr/include/asio/impl/read_until.ipp:206: error: expected unqualified-id before ‘&’ token
/usr/include/asio/impl/read_until.ipp:206: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/asio/impl/read_until.ipp:207: error: redefinition of ‘template<class SyncReadStream, class Allocator> size_t asio::read_until(SyncReadStream&, asio::basic_streambuf<Allocator>&)’
/usr/include/asio/impl/read_until.ipp:196: error: ‘template<class SyncReadStream, class Allocator> size_t asio::read_until(SyncReadStream&, asio::basic_streambuf<Allocator>&)’ previously declared here
/usr/include/asio/impl/read_until.ipp: In function ‘size_t asio::read_until(SyncReadStream&, asio::basic_streambuf<Allocator>&)’:
/usr/include/asio/impl/read_until.ipp:222: error: ‘match_results’ is not a member of ‘boost’
/usr/include/asio/impl/read_until.ipp:222: error: expected primary-expression before ‘>’ token
/usr/include/asio/impl/read_until.ipp:222: error: ‘match_results’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:223: error: ‘regex_search’ is not a member of ‘boost’
/usr/include/asio/impl/read_until.ipp:223: error: ‘expr’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:224: error: ‘match_default’ is not a member of ‘boost’
/usr/include/asio/impl/read_until.ipp:224: error: ‘match_partial’ is not a member of ‘boost’
/usr/include/asio/impl/read_until.ipp:229: error: ‘ec’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:247: error: ‘ec’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:254: error: ‘ec’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp: At global scope:
/usr/include/asio/impl/read_until.ipp:583: error: expected unqualified-id before ‘&’ token
/usr/include/asio/impl/read_until.ipp:583: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/asio/impl/read_until.ipp:657: error: ‘regex’ in namespace ‘boost’ does not name a type
/usr/include/asio/impl/read_until.ipp: In constructor ‘asio::detail::read_until_expr_handler<AsyncReadStream, Allocator, ReadHandler>::read_until_expr_handler(AsyncReadStream&, asio::basic_streambuf<Allocator>&)’:
/usr/include/asio/impl/read_until.ipp:587: error: class ‘asio::detail::read_until_expr_handler<AsyncReadStream, Allocator, ReadHandler>’ does not have any field named ‘expr_’
/usr/include/asio/impl/read_until.ipp:587: error: ‘expr’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:588: error: ‘next_search_start’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:589: error: ‘handler’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp: In member function ‘void asio::detail::read_until_expr_handler<AsyncReadStream, Allocator, ReadHandler>::operator()(const asio::error_code&, size_t)’:
/usr/include/asio/impl/read_until.ipp:617: error: ‘match_results’ is not a member of ‘boost’
/usr/include/asio/impl/read_until.ipp:617: error: expected primary-expression before ‘>’ token
/usr/include/asio/impl/read_until.ipp:617: error: ‘match_results’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:618: error: ‘regex_search’ is not a member of ‘boost’
/usr/include/asio/impl/read_until.ipp:618: error: ‘expr_’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:619: error: ‘match_default’ is not a member of ‘boost’
/usr/include/asio/impl/read_until.ipp:619: error: ‘match_partial’ is not a member of ‘boost’
/usr/include/asio/impl/read_until.ipp: At global scope:
/usr/include/asio/impl/read_until.ipp:693: error: expected unqualified-id before ‘&’ token
/usr/include/asio/impl/read_until.ipp:693: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/asio/impl/read_until.ipp: In function ‘void asio::async_read_until(AsyncReadStream&, asio::basic_streambuf<Allocator>&)’:
/usr/include/asio/impl/read_until.ipp:707: error: ‘match_results’ is not a member of ‘boost’
/usr/include/asio/impl/read_until.ipp:707: error: expected primary-expression before ‘>’ token
/usr/include/asio/impl/read_until.ipp:707: error: ‘match_results’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:708: error: ‘regex_search’ is not a member of ‘boost’
/usr/include/asio/impl/read_until.ipp:708: error: ‘expr’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:709: error: ‘match_default’ is not a member of ‘boost’
/usr/include/asio/impl/read_until.ipp:709: error: ‘match_partial’ is not a member of ‘boost’
/usr/include/asio/impl/read_until.ipp:716: error: ‘handler’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:734: error: ‘handler’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:743: error: ‘expr’ was not declared in this scope
/usr/include/asio/impl/read_until.ipp:743: error: ‘handler’ was not declared in this scope
scons: *** [build/httpget.o] Error 1
scons: building terminated because of errors.

lol

---

### Post by decoherence on 2009-08-18
Good grief! :lolflag:

do you have libboost-regex-dev installed?

---

### Post by MelDJ on 2009-08-18
nope..getting it now

---

### Post by MelDJ on 2009-08-18
IT WORKS!!!
thanks [decoherence]("http://ubuntuforums.org/member.php?u=156618")!!! 5 stars for you! :KS:KS:KS:KS:KS:lolflag:

---

### Post by decoherence on 2009-08-18
YAY glad I could help!

apt-file was my secret weapon. For instance the first error in that output you posted was

"/usr/include/asio/read_until.hpp:23:27: error: boost/regex.hpp: No such file or directory"

```
$ sudo apt-file search boost/regex.hpp
libboost-regex-dev: /usr/include/boost/regex.hpp
libboost-regex1.35-dev: /usr/include/boost/regex.hpp
libboost-regex1.37-dev: /usr/include/boost/regex.hpp

```

you'll have to run "sudo apt-file update" before you can search. also, not sure if it is installed by default, but it is in the repository (of course!)

cheers,

---

### Post by sky net on 2010-03-29
i have the same problem after installin all the packages you said !!
scons: *** [build/vdrift] Error 1
scons: building terminated because of errors.

anyone can help ?

the errors are :
sh: svnversion: command not found

scons: warning: The env.Copy() method is deprecated; use the env.Clone() method instead.


i installed svnversion successfully !! but i still get this error : scons: warning: The env.Copy() method is deprecated; use the env.Clone() method instead.

help ???

---

