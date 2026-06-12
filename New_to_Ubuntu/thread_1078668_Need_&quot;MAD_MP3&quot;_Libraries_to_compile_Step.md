---
title: "Need &quot;MAD MP3&quot; Libraries to compile Step Mania from Source"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-02-23
```
configure: error: A working installation of MAD could not be found, which is
required for MP3 support.  If you really want to compile without MP3 support,
pass the "--without-mp3" flag to configure.
```

I poked around online but could not find the package I need to get MAD working, any idea where I can get the 64bit one for ubuntu?

Thanks,
~Jeff

---

### Post by t0p on 2009-02-23
I can't help you directly, but I can suggest you read [this guide]("https://help.ubuntu.com/community/CompilingEasyHowTo") on compiling.  This should show you how to locate dependencies.

---

### Post by snova on 2009-02-23
Try installing the **libmad0-dev** package, I think that's it.

---

### Post by beastrace91 on 2009-02-23
> **snova said:**
> Try installing the **libmad0-dev** package, I think that's it.

That was the one I needed! How ever upon running sudo make I now get this error: ```
HighScore.h: In member function ‘void HighScore::Unset()’:
HighScore.h:42: error: ‘memset’ was not declared in this scope
make[2]: *** [Screen.o] Error 1
make[2]: Leaving directory `/home/jeff/Desktop/StepMania-3.9-src/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/jeff/Desktop/StepMania-3.9-src/src'
make: *** [all-recursive] Error 1

``` Anyone have any idea what that means? It looks like an error in the source to me :/

~Jeff

---

### Post by snova on 2009-02-23
> **beastrace91 said:**
> ```

HighScore.h: In member function &#8216;void HighScore::Unset()&#8217;:
HighScore.h:42: error: &#8216;memset&#8217; was not declared in this scope
make[2]: *** [Screen.o] Error 1
make[2]: Leaving directory `/home/jeff/Desktop/StepMania-3.9-src/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/jeff/Desktop/StepMania-3.9-src/src'
make: *** [all-recursive] Error 1

```

Anyone have any idea what that means? It looks like an error in the source to me :/

It is, however an easily fixed one. Open src/HighScore.h, and at the top, add this line:

```
#include <string.h>
```

And run make again.

Also, make doesn't need to be run with sudo- only make install. At this point, however, it may be best to continue using sudo, or have to to start the process over again.

---

### Post by beastrace91 on 2009-02-23
Ugg this source is all jacked up it appears... (I wonder if they ever tested it...) getting this now: ```
jeff@jeff-ubuntu:~/Desktop/StepMania-3.9-src$ make
Making all in src
make[1]: Entering directory `/home/jeff/Desktop/StepMania-3.9-src/src'
make  all-am
make[2]: Entering directory `/home/jeff/Desktop/StepMania-3.9-src/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I. -I/usr/include/lua50 -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -finline-limit=300   -Wall -W -Wno-unused -Wno-switch -O3 -MT Screen.o -MD -MP -MF ".deps/Screen.Tpo" \
	  -c -o Screen.o `test -f 'Screen.cpp' || echo './'`Screen.cpp; \
	then mv -f ".deps/Screen.Tpo" ".deps/Screen.Po"; \
	else rm -f ".deps/Screen.Tpo"; exit 1; \
	fi
In file included from Actor.h:7,
                 from ActorFrame.h:6,
                 from Screen.h:6,
                 from Screen.cpp:2:
ActorCommands.h:20: warning: type qualifiers ignored on function return type
ActorCommands.h:21: warning: type qualifiers ignored on function return type
ActorCommands.h:22: warning: type qualifiers ignored on function return type
In file included from Grade.h:6,
                 from GameState.h:9,
                 from Screen.cpp:4:
RageUtil.h:145: error: ‘INT_MAX’ was not declared in this scope
In file included from Screen.cpp:4:
GameState.h:88: error: extra qualification ‘GameState::’ on member ‘GetRandomCharacter’
GameState.h:89: error: extra qualification ‘GameState::’ on member ‘GetDefaultCharacter’
In file included from Screen.cpp:7:
ThemeManager.h:114: warning: type qualifiers ignored on function return type
ThemeManager.h:123: warning: type qualifiers ignored on function return type
ThemeManager.h:132: warning: type qualifiers ignored on function return type
make[2]: *** [Screen.o] Error 1
make[2]: Leaving directory `/home/jeff/Desktop/StepMania-3.9-src/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/jeff/Desktop/StepMania-3.9-src/src'
make: *** [all-recursive] Error 1
```

Its too bad, was a good piece of software on windows.

~JEff

---

### Post by snova on 2009-02-23
You know, they have a Linux binary...

> **beastrace91 said:**
> ```
jeff@jeff-ubuntu:~/Desktop/StepMania-3.9-src$ make
RageUtil.h:145: error: &#8216;INT_MAX&#8217; was not declared in this scope

...

GameState.h:88: error: extra qualification &#8216;GameState::&#8217; on member &#8216;GetRandomCharacter&#8217;
GameState.h:89: error: extra qualification &#8216;GameState::&#8217; on member &#8216;GetDefaultCharacter&#8217;

```

At the top of src/RageUtil.h, add this line:

```
#include <limits.h>
```

Then open src/GameState.h and scroll down to line 88, where we see:

[PHP]
	Character* GameState::GetRandomCharacter();
	Character* GameState::GetDefaultCharacter();
[/PHP]

Replace with:

[PHP]
	Character* GetRandomCharacter();
	Character* GetDefaultCharacter();
[/PHP]

And hopefully that'll fix it. Try to compile again.

---

### Post by beastrace91 on 2009-02-24
Wow more error trying to run make: ```
In file included from RageDisplay.h:9,
                 from ScreenBookkeeping.cpp:13:
ModelTypes.h: In member function ‘int msAnimation::FindBoneByName(const char*) const’:
ModelTypes.h:122: error: ‘strcmp’ was not declared in this scope
ScreenBookkeeping.cpp: In member function ‘virtual void ScreenBookkeeping::MenuLeft(PlayerNumber)’:
ScreenBookkeeping.cpp:77: warning: dereferencing type-punned pointer will break strict-aliasing rules
ScreenBookkeeping.cpp: In member function ‘virtual void ScreenBookkeeping::MenuRight(PlayerNumber)’:
ScreenBookkeeping.cpp:84: warning: dereferencing type-punned pointer will break strict-aliasing rules
make[2]: *** [ScreenBookkeeping.o] Error 1
make[2]: Leaving directory `/home/jeff/Desktop/StepMania-3.9-src/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/jeff/Desktop/StepMania-3.9-src/src'
make: *** [all-recursive] Error 1

```

I tried the binaries but they throw this error when I try to ./stepmania (thats the main file it has) ```
jeff@jeff-ubuntu:~/Desktop/StepMania-3.9$ ls
Announcers    Copying.txt  GtkModule.so  README-FIRST.html  Visualizations
BGAnimations  Courses      NEWS          Songs
CDTitles      Data         NoteSkins     stepmania
Characters    Docs         RandomMovies  Themes
jeff@jeff-ubuntu:~/Desktop/StepMania-3.9$ ./stepmania
./stepmania: error while loading shared libraries: libvorbisfile.so.3: cannot open shared object file: No such file or directory

```

Thanks for all your help thus far :) hope to get this working.

~Jeff

---

### Post by 3rdalbum on 2009-02-24
I'd suggest running the binary instead of compiling from source.

The binary is reporting that it needs the "libvorbisfile.so.3" file and that it can't find it. This one is easy fixed: Go into Synaptic Package Manager and install the "libvorbisfile3" package. Now try running the program. If it complains about another missing library, just follow the same procedure, rinse and repeat.

Finding dependencies in Synaptic is much easier than debugging someone's source code.

---

### Post by beastrace91 on 2009-02-24
I cannot find a "libvorbisfile.so.3" in synaptic... is this package called something else?...

~Jeff

---

### Post by snova on 2009-02-24
> **beastrace91 said:**
> I cannot find a "libvorbisfile.so.3" in synaptic... is this package called something else?...

```
$ apt-file search libvorbisfile.so.3
**libvorbisfile3**: /usr/lib/libvorbisfile.so.3
libvorbisfile3: /usr/lib/libvorbisfile.so.3.2.0

```

There you go.

---

### Post by beastrace91 on 2009-02-24
I already had those files apparently... any ideas why the binaries would throw the above error then?

~Jeff

---

### Post by opensourcethis on 2009-04-02
i'm having the exact same problem.  i'm still getting the 

"error while loading shared libraries: libvorbisfile.so.3: cannot open shared object file: No such file or directory"

any suggestions?

:EDIT:
as an alternative i tried running the windows version in wine and it works great. except it doesn't play any of the music.  but it does play most of the other sound effects.

---

### Post by opensourcethis on 2009-04-02
nevermind, i figured it all out.  i'll write a tutorial tonight.

-o

---

