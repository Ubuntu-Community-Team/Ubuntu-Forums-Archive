---
title: "SDL graphics library and g++"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by machdohvah on 2011-04-14
The attached screen shot shows that I am having a problem with an SDL library downloaded from the web. The include file clearly references the SDL_Init function, but at compile time, shown here, there is an error stating that the SDL_Init function is not there. Did not download the SDL library files correctly? Is there an installation step that is not documented? It has been my experience that there is lots of missing documentation about precisely how to do anything in g++. It seems to me that this "open" system is truly not. I am new to the Ubuntu scene, but have extensive experience in telephone billing. It is just that I am retired now and would like to do graphical things in C++ somehow, like an ancient card game called klondike that I had been developing since I was a teenager where it started in BASIC. :)

---

### Post by wep940 on 2011-04-14
Are you sure you got everything set up for the search paths, etc., for g++ to find the library?  Looks like you are using an IDE - which?

---

### Post by machdohvah on 2011-04-14
> **wep940 said:**
> Are you sure you got everything set up for the search paths, etc., for g++ to find the library?  Looks like you are using an IDE - which?

Geany 0.19.1

---

### Post by sandyd on 2011-04-14
> **machdohvah said:**
> The attached screen shot shows that I am having a problem with an SDL library downloaded from the web. The include file clearly references the SDL_Init function, but at compile time, shown here, there is an error stating that the SDL_Init function is not there. Did not download the SDL library files correctly? Is there an installation step that is not documented? It has been my experience that there is lots of missing documentation about precisely how to do anything in g++. It seems to me that this "open" system is truly not. I am new to the Ubuntu scene, but have extensive experience in telephone billing. It is just that I am retired now and would like to do graphical things in C++ somehow, like an ancient card game called klondike that I had been developing since I was a teenager where it started in BASIC. :)
Did you install libsdl-dev?
```

sudo apt-get install libsdl-dev
```

if yes, post output of
```

ls -l /usr/include/SDL/

```

---

### Post by machdohvah on 2011-04-15
> **sandyd said:**
> Did you install libsdl-dev?
```

sudo apt-get install libsdl-dev
```if yes, post output of
```

ls -l /usr/include/SDL/

```

Successfully installed libsdl-dev. Ran listing as requested. Here is the screen shot.

---

### Post by sandyd on 2011-04-16
> **machdohvah said:**
> Successfully installed libsdl-dev. Ran listing as requested. Here is the screen shot.
it *should* work now

---

### Post by machdohvah on 2011-04-16
> **sandyd said:**
> it *should* work now

As you can see by this screen shot, it did not.

---

### Post by wep940 on 2011-04-17
I noticed you are including only sdl.h. Did you check in the sdl.h file itself to see if SDL_init and SDL_quit are in that source header file or perhaps they are in another header file? Also, what directory are you in when you are compiling? From the looks of that code, it expects the following:
 
your program code directory
---> a sub directory of SDL which includes all of the SDL header files, etc.
 
EDIT:  Jeez do I feel stupid!  Must have been watching TV when I replied.  Of course everything is found via the default include path.

---

### Post by wep940 on 2011-04-17
Okay, just to try this out I installed the SDL development lib and it's dependencies and geany. I then entered the code which I believe is the same as yours without the leading comments. I did not configure geany in any way - just create a project "test" and saved the program as "test.cxx". The attachment is a screenshot from geany with the source and the result of the compile - mine went fine. EDIT: please note I did not install anything extra - only what was generated in synaptic package manager. Maybe you should skip the apt-get (you never did a build-dep I would guess) and instead go through synaptic package manager to install SDL. You can probably just reinstall via the package manager so that all of the dependencies are met.  As has been noted here many times - use the package manager to install things so that all the dependencies are met.  Not doing so means you will probably have to do apt-get -build-dep for the package as well.  Gets messy.

---

### Post by machdohvah on 2011-04-17
> **wep940 said:**
> I noticed you are including only sdl.h. Did you check in the sdl.h file itself to see if SDL_init and SDL_quit are in that source header file or perhaps they are in another header file?  Also, what directory are you in when you are compiling?  From the looks of that code, it expects the following:
 
your program code directory
---> a sub directory of SDL which includes all of the SDL header files, etc.

Here is the file SDL.h located in /usr/include/SDL directory where all the other include files for SDL reside.

```
/*
    SDL - Simple DirectMedia Layer
    Copyright (C) 1997-2009 Sam Lantinga

    This library is free software; you can redistribute it and/or
    modify it under the terms of the GNU Lesser General Public
    License as published by the Free Software Foundation; either
    version 2.1 of the License, or (at your option) any later version.

    This library is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
    Lesser General Public License for more details.

    You should have received a copy of the GNU Lesser General Public
    License along with this library; if not, write to the Free Software
    Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

    Sam Lantinga
    slouken@libsdl.org
*/

/** @file SDL.h
 *  Main include header for the SDL library
 */

#ifndef _SDL_H
#define _SDL_H

#include "SDL_main.h"
#include "SDL_stdinc.h"
#include "SDL_audio.h"
#include "SDL_cdrom.h"
#include "SDL_cpuinfo.h"
#include "SDL_endian.h"
#include "SDL_error.h"
#include "SDL_events.h"
#include "SDL_loadso.h"
#include "SDL_mutex.h"
#include "SDL_rwops.h"
#include "SDL_thread.h"
#include "SDL_timer.h"
#include "SDL_video.h"
#include "SDL_version.h"

#include "begin_code.h"
/* Set up for C function definitions, even when using C++ */
#ifdef __cplusplus
extern "C" {
#endif

/** @file SDL.h
 *  @note As of version 0.5, SDL is loaded dynamically into the application
 */

/** @name SDL_INIT Flags
 *  These are the flags which may be passed to SDL_Init() -- you should
 *  specify the subsystems which you will be using in your application.
 */
/*@{*/
#define    SDL_INIT_TIMER        0x00000001
#define SDL_INIT_AUDIO        0x00000010
#define SDL_INIT_VIDEO        0x00000020
#define SDL_INIT_CDROM        0x00000100
#define SDL_INIT_JOYSTICK    0x00000200
#define SDL_INIT_NOPARACHUTE    0x00100000    /**< Don't catch fatal signals */
#define SDL_INIT_EVENTTHREAD    0x01000000    /**< Not supported on all OS's */
#define SDL_INIT_EVERYTHING    0x0000FFFF
/*@}*/

/** This function loads the SDL dynamically linked library and initializes 
 *  the subsystems specified by 'flags' (and those satisfying dependencies)
 *  Unless the SDL_INIT_NOPARACHUTE flag is set, it will install cleanup
 *  signal handlers for some commonly ignored fatal signals (like SIGSEGV)
 */
extern DECLSPEC int SDLCALL SDL_Init(Uint32 flags);

/** This function initializes specific SDL subsystems */
extern DECLSPEC int SDLCALL SDL_InitSubSystem(Uint32 flags);

/** This function cleans up specific SDL subsystems */
extern DECLSPEC void SDLCALL SDL_QuitSubSystem(Uint32 flags);

/** This function returns mask of the specified subsystems which have
 *  been initialized.
 *  If 'flags' is 0, it returns a mask of all initialized subsystems.
 */
extern DECLSPEC Uint32 SDLCALL SDL_WasInit(Uint32 flags);

/** This function cleans up all initialized subsystems and unloads the
 *  dynamically linked library.  You should call it upon all exit conditions.
 */
extern DECLSPEC void SDLCALL SDL_Quit(void);

/* Ends C function definitions when using C++ */
#ifdef __cplusplus
}
#endif
#include "close_code.h"

#endif /* _SDL_H */
```

---

### Post by machdohvah on 2011-04-17
> **wep940 said:**
> Okay, just to try this out I installed the SDL development lib and it's dependencies and geany. I then entered the code which I believe is the same as yours without the leading comments. I did not configure geany in any way - just create a project "test" and saved the program as "test.cxx". The attachment is a screenshot from geany with the source and the result of the compile - mine went fine. EDIT: please note I did not install anything extra - only what was generated in synaptic package manager. Maybe you should skip the apt-get (you never did a build-dep I would guess) and instead go through synaptic package manager to install SDL. You can probably just reinstall via the package manager so that all of the dependencies are met.  As has been noted here many times - use the package manager to install things so that all the dependencies are met.  Not doing so means you will probably have to do apt-get -build-dep for the package as well.  Gets messy.

I have looked at your screen shot and noticed that you only compiled the file. The problem is generated when you build the project. The program then generates errors as I have posted previously. Therefore, the program is not executable in any fashion.

---

### Post by wep940 on 2011-04-17
I was going by your screen shot that showed "compiling" and then the errors.  I'm not familiar at all with geany or SDL - just installed them to try and see if I could find anything to help you.  Guess I'll just delete them and get on with my life.

lotsa luck.

---

### Post by wep940 on 2011-04-18
Sorry about my last post - I was having some problems with some people here and my frustration endd up in post.
 
Here's your solution:
 
I searched the web for threads with geany and SDL in them. I found some that showed this problem on other SDL functions. I tried the various suggestions, starting in CodeBlocks since one of the examples was using that IDE, and it worked. So, I knew the problem was missing link libraries in geany. It took a while to find where the heck geany "hid" the arguments.
 
The sdl libraries need to be added to the build arguments and -LSDL needs to be added to the compile and build argements. In geany, look for the build icon - looks like a brick. Next to it is a down arrow - click on it and go to Set Includes and Arguments and:
 
- change the Compile line to: g++ -Wall -c "%f" -lSDL
- change the Build line to: g++ -Wall -o "%e" "%f" -lSDL -LlibSDLmain.a -LlibSDL.a
 
This is what I did then did a build with success - see the screen shot. Whether these are the only ones needed or not I have no clue, as I know squat about SDL. I just know this worked for me using Build.
 
EDIT: JUST FOUND OUT THAT AT LEAST FOR ME JUST HAVING THE -lSDL ON THE END OF THE COMPILE LINE AND THE BUILD LINE IS ALL IT TAKES TO GET IT TO WORK - I think it's simply telling it to use the SDL libraries.

---

### Post by machdohvah on 2011-04-18
> **wep940 said:**
> Sorry about my last post - I was having some problems with some people here and my frustration endd up in post.
 
Here's your solution:
 
I searched the web for threads with geany and SDL in them. I found some that showed this problem on other SDL functions. I tried the various suggestions, starting in CodeBlocks since one of the examples was using that IDE, and it worked. So, I knew the problem was missing link libraries in geany. It took a while to find where the heck geany "hid" the arguments.
 
The sdl libraries need to be added to the build arguments and -LSDL needs to be added to the compile and build argements. In geany, look for the build icon - looks like a brick. Next to it is a down arrow - click on it and go to Set Includes and Arguments and:
 
- change the Compile line to: g++ -Wall -c "%f" -lSDL
- change the Build line to: g++ -Wall -o "%e" "%f" -lSDL -LlibSDLmain.a -LlibSDL.a
 
This is what I did then did a build with success - see the screen shot. Whether these are the only ones needed or not I have no clue, as I know squat about SDL. I just know this worked for me using Build.
 
EDIT: JUST FOUND OUT THAT AT LEAST FOR ME JUST HAVING THE -lSDL ON THE END OF THE COMPILE LINE AND THE BUILD LINE IS ALL IT TAKES TO GET IT TO WORK - I think it's simply telling it to use the SDL libraries.

[SOLVED] Thank very much for your solution.

---

### Post by wep940 on 2011-04-18
After getting this to work, I wondered "just what the heck is SDL"?  So, I went looking, and found they actually have an online guide for it, and wouldn't you know, the -lSDL thing is right there!
 
I'm just glad it works for you!  Again, I really apologize for my 1 response - a bad day that rolled over to my post - it had absolutely nothing to with you!

---

