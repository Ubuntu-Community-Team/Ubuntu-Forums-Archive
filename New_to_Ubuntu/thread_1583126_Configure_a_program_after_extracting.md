---
title: "Configure a program after extracting"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Townley89 on 2010-09-27
Hey all,

I downloaded joy2key, a way to make your keyboard chorded, and I'm very excited about the prospect, but since it wasn't available in the ubuntu software center, I downloaded it from here [http://sourceforge.net/projects/joy2chord/files/joy2chord/](http://sourceforge.net/projects/joy2chord/files/joy2chord/) and extracted the file to desktop, but I'm a bit of a newbie and I'm not sure what to do with the extracted file to get the program running. 

Any help would be greatly appreciated.

Edit: Got it! For those looking for what to do with non-ubuntu software center programs, here's a great little link :) 

[http://www.wikihow.com/Compile-a-Program-in-Linux](http://www.wikihow.com/Compile-a-Program-in-Linux)

Sorry for the silly question.

---

### Post by amauk on 2010-09-27
You'll need to compile it

first get the essential utilities needed to compile stuff
```
sudo apt-get install build-essential
```

Extract the archive

cd to the extracted files
```
cd /path/to/files
```

then run the autogen.sh file
```
./autogen.sh
```

Then, compile the source
```
./configure; make; sudo make install
```

---

### Post by Townley89 on 2010-09-27
thanks for the response. I seem to be caught at the autogen.sh step. I extracted to desktop and ran ./autogen.sh and got the following: 

robert@Robert-laptop:~/Desktop/joy2chord-0.2$ ./autogen.sh
./autogen.sh: 2: aclocal: not found
./autogen.sh: 3: autoreconf: not found
./autogen.sh: 4: automake: not found
./autogen.sh: 5: autoreconf: not found
robert@Robert-laptop:~/Desktop/joy2chord-0.2$ 

whereas ./configure returns 

robert@Robert-laptop:~/Desktop/joy2chord-0.2$ ./configure
bash: ./configure: No such file or directory
robert@Robert-laptop:~/Desktop/joy2chord-0.2$ 

Any thoughts?

---

### Post by lykeion on 2010-09-27
Try this: sudo apt-get install automake

This is a better compile guide:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by amauk on 2010-09-27
basically, if you get anything "not found", search for it in synaptic / software centre and install

Because you're compiling, you'll most likely need to install the "-dev" packages for dependencies as well

---

### Post by Townley89 on 2010-09-28
The "not found" hint is very useful, I see that often, so thanks, that's very helpful advice.

Any suggestions about what's going wrong now? I think dependencies are solved, and the lack of errors makes me think the ./configure step went well. 


robert@Robert-laptop:~$ cd ~/Desktop/joy2chord-0.2
robert@Robert-laptop:~/Desktop/joy2chord-0.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
robert@Robert-laptop:~/Desktop/joy2chord-0.2$ make
make  all-recursive
make[1]: Entering directory `/home/robert/Desktop/joy2chord-0.2'
Making all in src
make[2]: Entering directory `/home/robert/Desktop/joy2chord-0.2/src'
g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT joy2chord.o -MD -MP -MF .deps/joy2chord.Tpo -c -o joy2chord.o joy2chord.cpp
joy2chord.cpp: In member function ‘int joy2chord::open_joystick()’:
joy2chord.cpp:131: error: ‘exit’ was not declared in this scope
joy2chord.cpp: In member function ‘void joy2chord::ioctl_wrapper(int, int, int)’:
joy2chord.cpp:171: error: ‘exit’ was not declared in this scope
joy2chord.cpp: In member function ‘int joy2chord::setup_uinput_device()’:
joy2chord.cpp:192: error: ‘exit’ was not declared in this scope
joy2chord.cpp:227: error: ‘exit’ was not declared in this scope
joy2chord.cpp:221: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
joy2chord.cpp: In member function ‘void joy2chord::send_click_events()’:
joy2chord.cpp:857: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
joy2chord.cpp:861: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
joy2chord.cpp:865: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
joy2chord.cpp:873: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
joy2chord.cpp:877: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
joy2chord.cpp:885: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
joy2chord.cpp:889: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
joy2chord.cpp: In member function ‘void joy2chord::send_key_down(__u16)’:
joy2chord.cpp:900: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
joy2chord.cpp:904: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
joy2chord.cpp: In member function ‘void joy2chord::send_key_up(__u16)’:
joy2chord.cpp:915: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
joy2chord.cpp:919: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
joy2chord.cpp: In member function ‘void joy2chord::main_loop(std::map<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, short unsigned int, std::less<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::pair<const std::basic_string<char, std::char_traits<char>, std::allocator<char> >, short unsigned int> > >)’:
joy2chord.cpp:968: error: ‘exit’ was not declared in this scope
joy2chord.cpp: In function ‘int main(int, char**)’:
joy2chord.cpp:1213: error: ‘exit’ was not declared in this scope
joy2chord.cpp:1230: error: ‘atoi’ was not declared in this scope
joy2chord.cpp:1267: error: ‘exit’ was not declared in this scope
make[2]: *** [joy2chord.o] Error 1
make[2]: Leaving directory `/home/robert/Desktop/joy2chord-0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/robert/Desktop/joy2chord-0.2'
make: *** [all] Error 2
robert@Robert-laptop:~/Desktop/joy2chord-0.2$

---

### Post by lykeion on 2010-09-29
I also failed to compile (tried both 0.2 src download and svn).
I suggest you contact the author either in the sourceforge help forum here:

[http://sourceforge.net/projects/joy2chord/forums/forum/799775](http://sourceforge.net/projects/joy2chord/forums/forum/799775)

Or if it's inactive contact the author directly. There's a mail address on the bottom of the homepage:

[http://joy2chord.sourceforge.net/](http://joy2chord.sourceforge.net/)

---

