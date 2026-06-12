---
title: "Installing a .tar file?!?!?"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by ctyonahl on 2011-04-26
I know this question has been posted many times, but how to you install a .tar file? The only thing that disappoints me about Linux is the royal pain it is to install programs.

I have extracted it (Right click-->Extract), but I'm very confused on where to go from there. In this case I'm trying to install a game (it is NOT in the Software Center). Here is what the README.txt file says:

```
Galcon Fusion
(c) 2010 Phil Hassey

http://www.galcon.com/fusion/

To run:
./run_me

Dependencies:
- SDL
- SDL_image
- GL
- GLU

You must have a supported 3D card for Galcon Fusion to run at any sort of
reasonable speed :)

Have fun!
-Phil
```

I know how to work the command line a little, but please, don't refrain from step-by-step instructions! :P

---

### Post by dniMretsaM on 2011-04-26
try this: ```
cd /directory/to/game/file
```then ```
./run_me
```The run_me file is an installation script (or possibly just a file to run the game, but most likely not). by executing it, it will install the game for you and then you can play it. It's kind of an alternative to compiling the source code manually.

---

### Post by ctyonahl on 2011-04-26
I did exactly what you said, but the Terminal threw this error:

```
./sdlapp: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory
```

What did I do wrong?

---

### Post by dniMretsaM on 2011-04-26
Missing libraries. Search for "libsdl" in Synaptic Package Manager and install the libsdsl packages (maybe only the libsdsl-dev packages, not sure).

---

### Post by trollger on 2011-04-26
Do you have the dependencies that the readme has in it. It looks like you are missing some.
[EDIT] 
We just posted at the same time lol

sudo apt-get install libsdl

should do the trick
[/EDIT]

---

### Post by dniMretsaM on 2011-04-26
Yeah lol. That can be annoying.

---

### Post by ctyonahl on 2011-04-26
> **dniMretsaM said:**
> Missing libraries. Search for "libsdl" in Synaptic Package Manager and install the libsdsl packages (maybe only the libsdsl-dev packages, not sure).

ALL of the packages that begin with "libsdl"? That's a lot!

---

### Post by dniMretsaM on 2011-04-26
I'm really not sure (no experience with that game). Just do what trollger said (sudo apt-get install libsdl) and you should be fine.

---

### Post by ctyonahl on 2011-04-26
> **trollger said:**
> Do you have the dependencies that the readme has in it. It looks like you are missing some.
[EDIT] 
We just posted at the same time lol

sudo apt-get install libsdl

should do the trick
[/EDIT]

```
E: Unable to locate package libsdl
```

What now?

---

### Post by trollger on 2011-04-26
sorry I must have given you the wrong package name try 

sudo apt-get install libsdl-dev

---

### Post by dniMretsaM on 2011-04-26
Install them via Synaptic.

Edit: Posted at the same time again. Lol

100th post BTW!!!

---

### Post by ctyonahl on 2011-04-26
OK, so I installed libsdsl. I navigate to my extracted folder with the terminal, then execute ./run_me

I get this error:

```
josh@josh-a31:~/Downloads/gfusion$ ./run_me
SDL Runtime Version: 1.2.14
SDL Compile Version: 1.2.12
SDL_image Runtime Version: 1.2.10
SDL_image Compile Version: 1.2.6
SDL_BYTEORDER == SDL_LIL_ENDIAN
irrKlang sound library version 1.3.0
Using ALSA driver
init_video: 0 0 0 0 1
_try_init_video(0,0,1)
Loadbmp: ../data/icon32.bmp
VideoInfo->vfmt->BitsPerPixel:32
res: 1
GL_RED_SIZE:8
GL_GREEN_SIZE:8
GL_BLUE_SIZE:8
GL_ALPHA_SIZE:0
GL_DEPTH_SIZE:24
GL_BUFFER_SIZE:24
GL_DOUBLEBUFFER:1
res: 1400 x 1050
vinfo: 1400 x 1050
loading: ../data/hit.wav
loading: ../data/explode.wav
loading: ../data/join.wav
loading: ../data/leave.wav
loading: ../data/start.wav
loading: ../data/stop.wav
loading: ../data/ping.wav
loading: ../data/new_hit.wav
loading: ../data/new_launch.wav
loading: ../data/new_explode.wav
loading: ../data/click.wav
loading: ../data/kazoo.ogg
stream_load in ticks: 50
stream_load in ticks: 33
stream_load in ticks: 70
stream_load in ticks: 84
stream_load in ticks: 84
loading texture 16: loader.png
loading ../data/loader.png as 1, fast: 0
sdlapp: ../../radeon/radeon_cs_gem.c:181: cs_gem_write_reloc: Assertion `boi->space_accounted' failed.
./run_me: line 1:  7880 Aborted                 ./sdlapp
```

---

### Post by ctyonahl on 2011-04-26
> **dniMretsaM said:**
> Install them via Synaptic.

Edit: Posted at the same time again. Lol

100th post BTW!!!
Congrats, man! Happy to be apart of it! :D

---

### Post by dniMretsaM on 2011-04-26
That's beyond me. I have no idea what that means. Sorry.

> **ctyonahl said:**
> Congrats, man! Happy to be apart of it! :grin:

Haha thanks!

---

### Post by ctyonahl on 2011-04-26
OK, I'll ask the developer what the problem might be. I'll let you know what he says.

---

### Post by dniMretsaM on 2011-04-27
Ok. I'd be interested in his answer. I'm always up for learning new stuff.

---

### Post by Lateralis on 2011-04-27
I'm not sure, but looks like the program is trying to secure some graphics memory but that is failing.  This may in fact be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/656100") and [this one too]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/602267").  What graphics card do you have, are you using proprietary drivers, and what version of the drivers are you using?

---

### Post by dniMretsaM on 2011-04-27
How can you tell that? I'm not trying to be smart, I'm just interested in learning.

---

### Post by ctyonahl on 2011-04-27
> **Lateralis said:**
> I'm not sure, but looks like the program is trying to secure some graphics memory but that is failing.  This may in fact be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/656100") and [this one too]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/602267").  What graphics card do you have, are you using proprietary drivers, and what version of the drivers are you using?

I'm really not sure what graphics card I have. :P I have a really old laptop, so it's not going to be a good one by any means. But the game I'm trying to install is 2D, so it should't take much graphics power.

---

### Post by ctyonahl on 2011-04-27
Here is the developer's message:
-----
Hmm, it looks like something about your video card doesn't agree with Galcon .. 

You can post on the forums and see if someone has any suggestions, I'm at a loss as to what that error means.

Otherwise, I can issue a refund if you like.

Cheers!
-Phil
-----
I'm not going to mess around with any graphics card drivers, since I don't even know which kind I have (unless it's very easy to do so). But if anyone has any other ideas, please let me know.

---

### Post by dniMretsaM on 2011-04-27
To find out what graphics/video card you have, run
```
lspci
```
It should tell you.

---

### Post by Lateralis on 2011-04-27
I could tell from the error that it was relating to the graphics card (radeon) with a memory alloc error. I googleised that particular error and found those bug threads. Iv'e also had similar physical memory errors eith some c code. As for how to fix it, I'm in the same shoes as the developer. Not a clue! But, you can check what drivers your using: in either preferences or administration in the System panel menu you'll find the 'Hardware drivers' menu. As you have a radeon card you should have proprietary drivers you can enable. 

Also, to determine your graphics card, you can also use 

```

sudo lshw -C display

```

---

### Post by ctyonahl on 2011-04-27
Here is the code from sudo lshw -C display

```
*-display               
       description: VGA compatible controller
       product: Radeon Mobility M7 LW [Radeon Mobility 7500]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:11 memory:e8000000-efffffff ioport:3000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff
```

EDIT: I don't know if any drivers are installed, none show up on the list.

---

### Post by Lateralis on 2011-04-28
Just done a bit more googleising.  It looks like the Mobility 7500 chip that you have is based on the R100 series.  The only Linux driver for that is currently in use on your system (in lshw, the line* configuration: driver=radeon* tells us this), and there are no proprietary drivers by ATI for this chipset series.  This is why none are listed in the System -> Administration -> Hardware Drivers menu, which normally lists any proprietary drivers that might be available for your system.  ATI will almost certainly not release any updates for this chipset series in the future.  (Why would they, when they haven't been arsed to release a driver for this series in the very first instance?)

So at this point I'm kinda stuck and am not sure how to proceed.  Having read those bug threads I posted previously, it seems like other ATI users (with the R200 chipset) have had near identical issues which have hopefully been fixed and should be released with Natty (11.04).  So, my only suggestion right now would be to boot into a Natty LiveCD and try running the game in the Live session (you'll obviously need to resolve the dependency issue you experienced previously before you can test the game).  If the game runs, then great!  Might be worthwhile installing Natty and using that.  If the game doesn't run, then I don't think you'll ever get it to run using your current hardware.  =(  You might have success in posting a bug report, but I don't think that will really go anywhere.

---

### Post by ctyonahl on 2011-04-28
> **Lateralis said:**
> Just done a bit more googleising.  It looks like the Mobility 7500 chip that you have is based on the R100 series.  The only Linux driver for that is currently in use on your system (in lshw, the line* configuration: driver=radeon* tells us this), and there are no proprietary drivers by ATI for this chipset series.  This is why none are listed in the System -> Administration -> Hardware Drivers menu, which normally lists any proprietary drivers that might be available for your system.  ATI will almost certainly not release any updates for this chipset series in the future.  (Why would they, when they haven't been arsed to release a driver for this series in the very first instance?)

So at this point I'm kinda stuck and am not sure how to proceed.  Having read those bug threads I posted previously, it seems like other ATI users (with the R200 chipset) have had near identical issues which have hopefully been fixed and should be released with Natty (11.04).  So, my only suggestion right now would be to boot into a Natty LiveCD and try running the game in the Live session (you'll obviously need to resolve the dependency issue you experienced previously before you can test the game).  If the game runs, then great!  Might be worthwhile installing Natty and using that.  If the game doesn't run, then I don't think you'll ever get it to run using your current hardware.  =(  You might have success in posting a bug report, but I don't think that will really go anywhere.

OK, cool! I'm upgrading to Natty right now...

---

### Post by Lateralis on 2011-04-28
Good luck!  I hope it works, but I wouldn't hold my breath. :P  As I said, the issues other people were experiencing were with more modern graphics cards which are actively supported.  But if it does work, then hurrah!  If it doesn't, then a newer laptop/computer might be in order! :P

---

### Post by ctyonahl on 2011-04-29
I just finished updating to 11.04, and everything works like a charm! The game plays really smoothly, too! Just one more question, how to I create a shortcut to the game in Applications-->Games and/or the desktop so I don't have to open the terminal every time I want to play?

---

### Post by Lateralis on 2011-04-29
Excellent!  Glad it works!  

To make a new launcher, go to System -> Preferences -> Main Menu.  Select whichever menu heading you want the launcher to be under, e.g. Games, hit "New Item" and add the command that you would type in the command line in the dialogue box.  You can change the launcher icon by clicking on the spring thingy and searching for an image file that you want/can use.  

You can do the same thing for the desktop if you wanted one there: right click -> create launcher.  

Have fun!

Oh!  Also, if you could mark the thread as being solved as well, that would be ace! (To do that, click the Thread Tools menu found towards the top of the thread.)

---

### Post by ctyonahl on 2011-04-29
> **Lateralis said:**
> Excellent!  Glad it works!  

To make a new launcher, go to System -> Preferences -> Main Menu.  Select whichever menu heading you want the launcher to be under, e.g. Games, hit "New Item" and add the command that you would type in the command line in the dialogue box.  You can change the launcher icon by clicking on the spring thingy and searching for an image file that you want/can use.  

You can do the same thing for the desktop if you wanted one there: right click -> create launcher.  

Have fun!

Oh!  Also, if you could mark the thread as being solved as well, that would be ace! (To do that, click the Thread Tools menu found towards the top of the thread.)

Done! Thanks so much!

---

### Post by dniMretsaM on 2011-04-29
Awesome dude! Glad you got it working. Glad I could help, too (even though I didn't really do that much)! Mark as solved and it'll be perfect. @Lateralis: I didn't know you could do that. LOL I just always made a shortcut (right click -> Create Shortcut) and changed the icon through the Properties menu.

---

### Post by Lateralis on 2011-04-29
Excellent!  Glad we could get you sorted ctyonahl.  I'm tempted to try the game out myself to see what its like. :P  

And glad I could help you too MasterMind!

---

