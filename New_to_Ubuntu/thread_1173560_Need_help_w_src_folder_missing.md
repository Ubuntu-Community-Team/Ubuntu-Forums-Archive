---
title: "Need help w/ src folder missing"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by darksky13 on 2009-05-29
do I just create an src folder or is there supposed to be one put there?
thanks.

trying to use the 

cd src/ 

command but it says src doesn't exist...

---

### Post by Rocket2DMn on 2009-05-29
What are you trying to do exactly?  Are you trying to extract an archive?  By default there is no "src" directory in your home folder or in the root of the filesystem.

---

### Post by darksky13 on 2009-05-29
yeah im extracting a tarball and it says

Please follow the following steps to build a native client:
1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed.
2) Change directory to src/ and type "make install".
3) If the build succeeds, return to this directory and run this script again.

when I execute the what i am assuming is the equivalent of ./configure with

luke@luke-desktop-ubuntu:~/cube2$ ./sauerbraten/sauerbraten_unix

---

### Post by Rocket2DMn on 2009-05-29
I would assume that after you extracted the tarball, you would need to change directories to the new one that was created, and there should be a src/ subdirectory that it is asking you to change to.  In essence, you need to change directories twice.  Does that help?
```
<do extraction>
cd <new directory>
cd src/
```

---

### Post by darksky13 on 2009-05-29
Thanks, that worked, but now i have another question... I was stupid and asuumed Step 1 was ok but then it screwed up because they werent there how do i fix

/bin/sh: sdl-config: not found
shared/cube.h:34:17: error: SDL.h: No such file or directory
shared/cube.h:35:23: error: SDL_image.h: No such file or directory
shared/cube.h:40:24: error: SDL_opengl.h: No such file or directory
shared/cube.h:42:22: error: GL/glext.h: No such file or directory
shared/cube.h:55:18: error: zlib.h: No such file or directory

Thanks a ton for your help

---

### Post by Rocket2DMn on 2009-05-29
Ok, let's back up for a minute.  What is it that you are trying to install, and where did you get the file and directions for it?  I will have a look myself and see if I can reproduce your problem.

---

### Post by ad_267 on 2009-05-29
You need to install these packages:
libsdl1.2-dev
libsdl-image1.2-dev
libsdl-mixer1.2-dev
zlib1g-dev
libgl1-mesa-dev

I'm not 100% sure if that last one is correct.

---

### Post by darksky13 on 2009-05-29
Im installing Sauerbraten but it is now installing correctly
thanks for the package names those are working now.
sorry for being a noob, lol.

---

### Post by ad_267 on 2009-05-29
Is there a particular reason why you're installing from the source? You can install sauerbraten from the Ubuntu package repositories using Synaptic or apt-get.

---

### Post by darksky13 on 2009-05-29
I did that but it was an older version, otherwise it would have been easier, lol.
well at least i know even more now, thanks.

---

### Post by ad_267 on 2009-05-29
Ok yeah, just remember when you're compiling something you need the development packages that end in "-dev".

You should be able to do: "sudo apt-get build-dep sauerbraten" to install all the packages required for building sauerbraten too.

---

