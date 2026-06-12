---
title: "ProjectM"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2009-08-26
could anyone please point me in the direction to install ProjectM on Ubuntu 9.04 32bit. i have tried a few methods but i have recieved errors and have not successfully installed it.

Thanks in advanced - betterthanjordan79

---

### Post by JillSwift on 2009-08-26
[This page]("http://sourceforge.net/apps/trac/projectm/wiki/Get%20projectM%21") says it is in the repositories since Hardy (8.04).

You should be able to just hit the terminal with:
```
sudo apt-get install libvisual-projectm
```

If you want to go the compile and install route, see [here]("http://ubuntuforums.org/showthread.php?t=749793").

---

### Post by Penguin Guy on 2009-08-26
I am not 100% sure, but I believe 'libvisual-projectm' is what you are looking for. You can install it by clicking [[COLOR="Blue"]here[/COLOR]]("apt:libvisual-projectm") or running [COLOR="Green"]sudo apt-get install libvisual-projectm[/COLOR]. Have fun! :)

---

### Post by betterthanjordan79 on 2009-08-26
thanks for ur reply but i should have specified that i would like it to work through totem media player which it doesn't through this.

---

### Post by Darkwing-Duck on 2009-08-26
What method(s) have you tried for the install? Also, what is the output from the install? This will help us help you!

---

### Post by betterthanjordan79 on 2009-08-26
i used this method

> [http://ubuntuforums.org/showthread.php?t=749793](http://ubuntuforums.org/showthread.php?t=749793)

got as far as 

> make && sudo make install

then this happens

> daniel@dv6000-laptop:~/projectm/projectM-Trunk/src$ make && sudo make install
[  1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/FBO.o
[  1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/MilkdropWaveform.o
[  1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/PerPixelMesh.o
[  1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Pipeline.o
[  1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Renderer.o
In file included from /usr/include/FTGL/ftgl.h:32,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/ft2build.h:56:38: error: freetype/config/ftheader.h: No such file or directory
In file included from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/ftgl.h:33:10: error: #include expects "FILENAME" or <FILENAME>
/usr/include/FTGL/ftgl.h:34:10: error: #include expects "FILENAME" or <FILENAME>
/usr/include/FTGL/ftgl.h:35:10: error: #include expects "FILENAME" or <FILENAME>
In file included from /usr/include/FTGL/ftgl.h:110,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTPoint.h:75: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/FTGL/FTPoint.h: In constructor ‘FTPoint::FTPoint(int)’:
/usr/include/FTGL/FTPoint.h:77: error: ‘ft_vector’ was not declared in this scope
In file included from /usr/include/FTGL/ftgl.h:111,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTBBox.h: At global scope:
/usr/include/FTGL/FTBBox.h:75: error: expected `)' before ‘glyph’
In file included from /usr/include/FTGL/ftgl.h:114,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGlyph.h:58: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTGlyph.h:112: error: ‘FT_Error’ does not name a type
/usr/include/FTGL/FTGlyph.h:196: error: ‘FT_Error’ does not name a type
In file included from /usr/include/FTGL/ftgl.h:115,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTBitmapGlyph.h:50: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTBitmapGlyph.h:77: error: ‘FT_GlyphSlot’ was not declared in this scope
In file included from /usr/include/FTGL/ftgl.h:116,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTBufferGlyph.h:49: error: expected `)' before ‘glyph’
In file included from /usr/include/FTGL/ftgl.h:117,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTExtrdGlyph.h:59: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTExtrdGlyph.h:97: error: ‘FT_GlyphSlot’ was not declared in this scope
/usr/include/FTGL/FTExtrdGlyph.h:97: error: expected primary-expression before ‘float’
/usr/include/FTGL/FTExtrdGlyph.h:98: error: expected primary-expression before ‘float’
/usr/include/FTGL/FTExtrdGlyph.h:98: error: expected primary-expression before ‘float’
/usr/include/FTGL/FTExtrdGlyph.h:99: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTExtrdGlyph.h:99: error: initializer expression list treated as compound expression
In file included from /usr/include/FTGL/ftgl.h:118,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTOutlineGlyph.h:56: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTOutlineGlyph.h:88: error: ‘FT_GlyphSlot’ was not declared in this scope
/usr/include/FTGL/FTOutlineGlyph.h:88: error: expected primary-expression before ‘float’
/usr/include/FTGL/FTOutlineGlyph.h:89: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTOutlineGlyph.h:89: error: initializer expression list treated as compound expression
In file included from /usr/include/FTGL/ftgl.h:119,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTPixmapGlyph.h:50: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTPixmapGlyph.h:77: error: ‘FT_GlyphSlot’ was not declared in this scope
In file included from /usr/include/FTGL/ftgl.h:120,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTPolyGlyph.h:57: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTPolyGlyph.h:92: error: ‘FT_GlyphSlot’ was not declared in this scope
/usr/include/FTGL/FTPolyGlyph.h:92: error: expected primary-expression before ‘float’
/usr/include/FTGL/FTPolyGlyph.h:93: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTPolyGlyph.h:93: error: initializer expression list treated as compound expression
In file included from /usr/include/FTGL/ftgl.h:121,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTTextureGlyph.h:59: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTTextureGlyph.h:92: error: ‘FT_GlyphSlot’ was not declared in this scope
/usr/include/FTGL/FTTextureGlyph.h:92: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTTextureGlyph.h:93: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTTextureGlyph.h:93: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTTextureGlyph.h:94: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTTextureGlyph.h:94: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTTextureGlyph.h:94: error: initializer expression list treated as compound expression
In file included from /usr/include/FTGL/ftgl.h:123,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTFont.h:128: error: ‘FT_Int’ has not been declared
/usr/include/FTGL/FTFont.h:137: error: ‘FT_Encoding’ has not been declared
/usr/include/FTGL/FTFont.h:151: error: ‘FT_Encoding’ declared as a ‘virtual’ field
/usr/include/FTGL/FTFont.h:151: error: expected ‘;’ before ‘*’ token
/usr/include/FTGL/FTFont.h:363: error: ‘FT_Error’ does not name a type
/usr/include/FTGL/FTFont.h:378: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTFont.h:378: error: expected ‘;’ before ‘(’ token
/usr/include/FTGL/FTFont.h:411: error: expected ‘,’ or ‘...’ before ‘(’ token
/usr/include/FTGL/FTFont.h:451: error: ‘FT_Encoding’ has not been declared
/usr/include/FTGL/FTFont.h:467: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/include/FTGL/FTFont.h:579: error: ‘FT_Error’ does not name a type
In file included from /usr/include/FTGL/ftgl.h:124,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLBitmapFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTGLBitmapFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:125,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTBufferFont.h:79: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTBufferFont.h:79: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:126,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLExtrdFont.h:82: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTGLExtrdFont.h:82: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:127,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLOutlineFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTGLOutlineFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:128,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLPixmapFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTGLPixmapFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:129,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLPolygonFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTGLPolygonFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:130,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLTextureFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTGLTextureFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:132,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTLayout.h:134: error: ‘FT_Error’ does not name a type
/usr/include/FTGL/FTLayout.h:187: error: ‘FT_Error’ does not name a type
make[2]: *** [libprojectM/Renderer/CMakeFiles/Renderer.dir/Renderer.o] Error 1
make[1]: *** [libprojectM/Renderer/CMakeFiles/Renderer.dir/all] Error 2
make: *** [all] Error 2
daniel@dv6000-laptop:~/projectm/projectM-Trunk/src$ 


---

### Post by decoherence on 2009-08-26
Looks like you need to install libfreetype6-dev
```

sudo apt-get install libfreetype6-dev
```

try it again... it will error out on the next dependency if there is one. post the output, if needed.

here's a tip... when compiling software it is often only the first error that matters. In the case of your output,

> daniel@dv6000-laptop:~/projectm/projectM-Trunk/src$ make && sudo make install
[ 1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/FBO.o
[ 1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/MilkdropWaveform.o
[ 1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/PerPixelMesh.o
[ 1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Pipeline.o
[ 1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Renderer.o
In file included from /usr/include/FTGL/ftgl.h:32,
from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
from /home/daniel/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/ft2build.h:56:38: error: freetype/config/ftheader.h: No such file or directory

is sufficient. Just look for the first line that indicates an error (but still be sure to include everything before it!)

---

### Post by wirelessmonkey on 2009-08-26
Did you install ftgl-dev and libfreetype6-dev?  Looks like the error is from Freetype...

---

### Post by betterthanjordan79 on 2009-08-26
i got this

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
libfreetype6-dev is already the newest version.
libfreetype6-dev set to manually installed.
The following packages were automatically installed and are no longer required:
  autoconf intltool libtool autotools-dev libltdl7-dev automake
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
daniel@dv6000-laptop:~$ 


---

### Post by betterthanjordan79 on 2009-08-26
yes i have ftgl-dev and libfreetype6-dev

---

