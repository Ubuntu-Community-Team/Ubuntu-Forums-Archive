---
title: "Sdl-1.2.14"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by Etchasketch on 2009-11-30
I am trying to get SDL-1.2.14 to install via the terminal but I get an error at the end while making it install.

Generating dependencies for ./src/timer/unix/SDL_systimer.c
/bin/bash build-scripts/mkinstalldirs /usr/local/bin
/usr/bin/install -c -m 755 sdl-config /usr/local/bin/sdl-config
/usr/bin/install: cannot remove `/usr/local/bin/sdl-config': Permission denied
make: *** [install-bin] Error 1

What do I need to do to fix this? I have tried to remove the sdl-config file manually from usr/local/bin/ but it tells me its a write-protected file and gives me this response:

james@james-laptop:/usr/local/bin$ rm sdl-config 
rm: remove write-protected regular file `sdl-config'? yes
rm: cannot remove `sdl-config': Permission denied

I am still new to this all and would appreciate any help!

---

### Post by Virtual Liberty on 2009-11-30
```
sudo <command>
```

Almost everything that's located outside your home directory is owned by root.

---

### Post by 3rdalbum on 2009-11-30
What do you need SDL 1.2.14 for?

There's 1.2.13 in the repositories; seeing as it's a minor point release difference you'd think that most software should compile or work with 1.2.13.

---

### Post by Etchasketch on 2009-11-30
I am trying to run an emulator script for Visualboy Advance and while installing that I get an error when it tries to make it install in the SDL directory.

Making install in sdl
make[2]: Entering directory `/home/james/Downloads/VisualBoyAdvance-1.7.2/src/sdl'
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"VisualBoyAdvance\" -DVERSION=\"1.7.2\" -DYYTEXT_POINTER=1 -DHAVE_LIBZ=1 -DHAVE_LIBPNG=1 -DHAVE_LIBPTHREAD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_MALLOC_H=1 -DHAVE_STRINGS_H=1 -DHAVE_UNISTD_H=1 -DHAVE_ARPA_INET_H=1 -DHAVE_NETINET_IN_H=1  -I. -I.  -I../../src -DSDL -DSYSCONFDIR=\"/usr/local/etc\"  -fno-exceptions -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -g -O2 -DPROFILING -DMMX -DDEV_VERSION -MT GBA.o -MD -MP -MF ".deps/GBA.Tpo" \
      -c -o GBA.o `test -f '../GBA.cpp' || echo './'`../GBA.cpp; \
    then mv -f ".deps/GBA.Tpo" ".deps/GBA.Po"; \
    else rm -f ".deps/GBA.Tpo"; exit 1; \
    fi
../GBA.cpp: In function ‘bool CPUWriteMemState(char*, int)’:
../GBA.cpp:677: warning: deprecated conversion from string constant to ‘char*’
../GBA.cpp: In function ‘bool CPUReadMemState(char*, int)’:
../GBA.cpp:820: warning: deprecated conversion from string constant to ‘char*’
../GBA.cpp: In function ‘bool CPUReadGSASnapshot(const char*)’:
../GBA.cpp:931: warning: ignoring return value of ‘size_t fread(void*, size_t, size_t, FILE*)’, declared with attribute warn_unused_result
../GBA.cpp:934: warning: ignoring return value of ‘size_t fread(void*, size_t, size_t, FILE*)’, declared with attribute warn_unused_result
../GBA.cpp:936: warning: ignoring return value of ‘size_t fread(void*, size_t, size_t, FILE*)’, declared with attribute warn_unused_result
../GBA.cpp:938: warning: ignoring return value of ‘size_t fread(void*, size_t, size_t, FILE*)’, declared with attribute warn_unused_result
../GBA.cpp:941: warning: ignoring return value of ‘size_t fread(void*, size_t, size_t, FILE*)’, declared with attribute warn_unused_result
../GBA.cpp:945: warning: ignoring return value of ‘size_t fread(void*, size_t, size_t, FILE*)’, declared with attribute warn_unused_result
../GBA.cpp: In function ‘bool CPUIsZipFile(const char*)’:
../GBA.cpp:1133: error: invalid conversion from ‘const char*’ to ‘char*’
../GBA.cpp: In function ‘bool CPUIsGBAImage(const char*)’:
../GBA.cpp:1148: error: invalid conversion from ‘const char*’ to ‘char*’
../GBA.cpp: In function ‘bool CPUIsGBABios(const char*)’:
../GBA.cpp:1172: error: invalid conversion from ‘const char*’ to ‘char*’
../GBA.cpp: In function ‘bool CPUIsELF(const char*)’:
../GBA.cpp:1192: error: invalid conversion from ‘const char*’ to ‘char*’
make[2]: *** [GBA.o] Error 1
make[2]: Leaving directory `/home/james/Downloads/VisualBoyAdvance-1.7.2/src/sdl'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/james/Downloads/VisualBoyAdvance-1.7.2/src'
make: *** [install-recursive] Error 1

---

### Post by Etchasketch on 2009-11-30
> **Virtual Liberty said:**
> ```
sudo <command>
```Almost everything that's located outside your home directory is owned by root.


Even with the sudo it gives me the same error.

---

### Post by James Paige on 2009-12-14
> **3rdalbum said:**
> What do you need SDL 1.2.14 for?

There's 1.2.13 in the repositories; seeing as it's a minor point release difference you'd think that most software should compile or work with 1.2.13.

Choice quotes from the libsdl 1.2.14 changelog:

> SDL 1.2.14 is a significant bug fix release and a recommended update.

...
    * Fixed crash in SDL_SetGammaRamp()
    * Fixed freeze in SDL_memset() with 0 length when assembly code is disabled.
...
    * Fixed a threading crash when a few threads are rapidly created and complete.
...
    * Fixed crash loading BMP files saved with the scanlines inverted.
...
    * Fixed potential memory corruption due to assembly bug with SDL_revcpy()
    * Fixed crashes trying to detect SSE features on x86_64 architecture.
...
    * Fixed crash in SDL_Quit() when a joystick has been unplugged. 


And those are just the crashers...

---

### Post by Etchasketch on 2009-12-14
So why am I receiving that error? I went through and removed everything I installed for the emulator and am going to go through the setup process again. Maybe this time it will work??

---

