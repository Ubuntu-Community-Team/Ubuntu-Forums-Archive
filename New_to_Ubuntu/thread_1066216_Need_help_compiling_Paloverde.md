---
title: "Need help compiling Paloverde"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Crusty Juggler on 2009-02-10
I've done a (very) little bit of compiling from source code in the past, mostly when I can just copy and paste the steps from a howto or something like that, so this one is beyond my depth.  

The source code is from this site: [http://loco.biosci.arizona.edu/paloverde/paloverde.html]("http://loco.biosci.arizona.edu/paloverde/paloverde.html")

The readme says to enter the following command after extracting the data:
```
make -f makefile.linux
```

However, I get the following:
```
cd my_structures; make
make[1]: Entering directory `/home/ryan/Desktop/paloverde.1.1/my_structures'
make[1]: `libmy_structures.a' is up to date.
make[1]: Leaving directory `/home/ryan/Desktop/paloverde.1.1/my_structures'
cd nexus_parser; make
make[1]: Entering directory `/home/ryan/Desktop/paloverde.1.1/nexus_parser'
yacc -d nexusParser.y
make[1]: yacc: Command not found
make[1]: *** [y.tab.c] Error 127
make[1]: Leaving directory `/home/ryan/Desktop/paloverde.1.1/nexus_parser'
make: *** [np] Error 2

```

Any help?

---

### Post by new4me on 2009-02-10
try installing flex bison then recompile.

sudo apt-get install flex bison

(I'm new at this also but I think that this is what I had to do for another similar thing that I had to do)

---

### Post by Crusty Juggler on 2009-02-10
Yeah, after I posted that, I looked a little closer and found that no program to run yacc and searching synaptic turned up bison.  Then nothing ran flex, so back to synaptic...

So you'd think all would be good, but now I get the following mess:
```
cd my_structures; make
make[1]: Entering directory `/home/ryan/Desktop/paloverde.1.1/my_structures'
make[1]: `libmy_structures.a' is up to date.
make[1]: Leaving directory `/home/ryan/Desktop/paloverde.1.1/my_structures'
cd nexus_parser; make
make[1]: Entering directory `/home/ryan/Desktop/paloverde.1.1/nexus_parser'
make[1]: `libnp.a' is up to date.
make[1]: Leaving directory `/home/ryan/Desktop/paloverde.1.1/nexus_parser'
gcc -g -DLINUX -I ./nexus_parser -I ./my_structures -L./nexus_parser -L./my_structures  layout_cone.c tree_openGL.c -o paloverde -lnp -lmy_structures \
-lglut -lGL -lGLU -L/usr/X11R6/lib -lX11 -lXi -lXmu -lm
In file included from layout_cone.c:11:
tree_openGL.h:5:22: error: GL/glut.h: No such file or directory
In file included from layout_cone.c:12:
layout_cone.h:48: error: expected declaration specifiers or ‘...’ before ‘GLfloat’
layout_cone.h:49: error: expected declaration specifiers or ‘...’ before ‘GLfloat’
layout_cone.h:50: error: expected declaration specifiers or ‘...’ before ‘GLfloat’
layout_cone.c:20: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘red’
layout_cone.c:21: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lt_red’
layout_cone.c:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lt_green’
layout_cone.c:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘white’
layout_cone.c:24: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘black’
layout_cone.c:625: error: expected declaration specifiers or ‘...’ before ‘GLfloat’
layout_cone.c: In function ‘labelColorClade’:
layout_cone.c:634: error: ‘color’ undeclared (first use in this function)
layout_cone.c:634: error: (Each undeclared identifier is reported only once
layout_cone.c:634: error: for each function it appears in.)
layout_cone.c:637: error: too many arguments to function ‘labelColorClade’
layout_cone.c: At top level:
layout_cone.c:640: error: expected declaration specifiers or ‘...’ before ‘GLfloat’
layout_cone.c: In function ‘subtreeColor’:
layout_cone.c:645: error: ‘color’ undeclared (first use in this function)
layout_cone.c:648: error: too many arguments to function ‘subtreeColor’
layout_cone.c: At top level:
layout_cone.c:650: error: expected declaration specifiers or ‘...’ before ‘GLfloat’
layout_cone.c: In function ‘treeColorClade’:
layout_cone.c:654: error: ‘color’ undeclared (first use in this function)
layout_cone.c:657: error: too many arguments to function ‘treeColorClade’
layout_cone.c: In function ‘setupTheTree’:
layout_cone.c:826: warning: format ‘%i’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
layout_cone.c:879: error: ‘black’ undeclared (first use in this function)
layout_cone.c:879: error: too many arguments to function ‘treeColorClade’
layout_cone.c:880: error: too many arguments to function ‘labelColorClade’
layout_cone.c:884: error: ‘white’ undeclared (first use in this function)
layout_cone.c:884: error: too many arguments to function ‘labelColorClade’
layout_cone.c:885: error: ‘lt_green’ undeclared (first use in this function)
layout_cone.c:885: error: too many arguments to function ‘treeColorClade’
layout_cone.c:887: error: ‘lt_red’ undeclared (first use in this function)
layout_cone.c:887: error: too many arguments to function ‘subtreeColor’
layout_cone.c: In function ‘setupSubclades’:
layout_cone.c:925: error: ‘lt_red’ undeclared (first use in this function)
layout_cone.c:925: error: too many arguments to function ‘treeColorClade’
In file included from tree_openGL.c:9:
layout_cone.h:6:22: error: GL/glut.h: No such file or directory
In file included from tree_openGL.c:9:
layout_cone.h:48: error: expected declaration specifiers or ‘...’ before ‘GLfloat’
layout_cone.h:49: error: expected declaration specifiers or ‘...’ before ‘GLfloat’
layout_cone.h:50: error: expected declaration specifiers or ‘...’ before ‘GLfloat’
tree_openGL.c:65: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘arc_color’
tree_openGL.c:117: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘spin’
tree_openGL.c:118: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
tree_openGL.c:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tree_material_amb_diffuse’
tree_openGL.c:129: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ground_material_amb_diffuse’
tree_openGL.c: In function ‘drawCylinder’:
tree_openGL.c:283: error: ‘qobj’ undeclared (first use in this function)
tree_openGL.c:283: error: (Each undeclared identifier is reported only once
tree_openGL.c:283: error: for each function it appears in.)
tree_openGL.c: In function ‘cylinders_quick’:
tree_openGL.c:298: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘arc_color’
tree_openGL.c:298: error: ‘arc_color’ undeclared (first use in this function)
tree_openGL.c:298: error: expected expression before ‘]’ token
tree_openGL.c:328: error: ‘GL_FRONT’ undeclared (first use in this function)
tree_openGL.c:328: error: ‘GL_AMBIENT_AND_DIFFUSE’ undeclared (first use in this function)
tree_openGL.c:332: error: ‘GL_FOG’ undeclared (first use in this function)
tree_openGL.c:333: error: ‘GL_FOG_DENSITY’ undeclared (first use in this function)
tree_openGL.c:408: error: ‘qobj’ undeclared (first use in this function)
tree_openGL.c: In function ‘drawCladeArcName’:
tree_openGL.c:443: error: ‘GL_LIGHTING’ undeclared (first use in this function)
tree_openGL.c:458: warning: format ‘%i’ expects type ‘int’, but argument 4 has type ‘long unsigned int’
tree_openGL.c:459: error: ‘GLUT_STROKE_ROMAN’ undeclared (first use in this function)
tree_openGL.c: In function ‘drawLabel’:
tree_openGL.c:490: error: ‘GL_LIGHTING’ undeclared (first use in this function)
tree_openGL.c:512: warning: format ‘%i’ expects type ‘int’, but argument 4 has type ‘long unsigned int’
tree_openGL.c:513: error: ‘GLUT_STROKE_ROMAN’ undeclared (first use in this function)
tree_openGL.c:538: error: ‘GL_BLEND’ undeclared (first use in this function)
tree_openGL.c:539: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
tree_openGL.c:539: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
tree_openGL.c:541: error: ‘GL_QUADS’ undeclared (first use in this function)
tree_openGL.c:560: error: ‘GL_FOG’ undeclared (first use in this function)
tree_openGL.c: In function ‘mouse’:
tree_openGL.c:653: error: ‘GLUT_ACTIVE_SHIFT’ undeclared (first use in this function)
tree_openGL.c:656: error: ‘GLUT_LEFT_BUTTON’ undeclared (first use in this function)
tree_openGL.c:657: error: ‘GLUT_DOWN’ undeclared (first use in this function)
tree_openGL.c:659: error: ‘GLUT_UP’ undeclared (first use in this function)
tree_openGL.c: In function ‘init’:
tree_openGL.c:719: error: ‘qobj’ undeclared (first use in this function)
tree_openGL.c:720: error: ‘GLU_FILL’ undeclared (first use in this function)
tree_openGL.c:721: error: ‘GLU_FLAT’ undeclared (first use in this function)
tree_openGL.c:725: error: ‘GLfloat’ undeclared (first use in this function)
tree_openGL.c:725: error: expected ‘;’ before ‘ambient’
tree_openGL.c:726: error: expected ‘;’ before ‘mat_specular’
tree_openGL.c:727: error: expected ‘;’ before ‘mat_shininess’
tree_openGL.c:728: error: expected ‘;’ before ‘light_position’
tree_openGL.c:731: error: ‘GL_SMOOTH’ undeclared (first use in this function)
tree_openGL.c:732: error: ‘GL_LIGHT_MODEL_AMBIENT’ undeclared (first use in this function)
tree_openGL.c:732: error: ‘ambient’ undeclared (first use in this function)
tree_openGL.c:733: error: ‘GL_FRONT’ undeclared (first use in this function)
tree_openGL.c:733: error: ‘GL_SPECULAR’ undeclared (first use in this function)
tree_openGL.c:733: error: ‘mat_specular’ undeclared (first use in this function)
tree_openGL.c:734: error: ‘GL_SHININESS’ undeclared (first use in this function)
tree_openGL.c:734: error: ‘mat_shininess’ undeclared (first use in this function)
tree_openGL.c:735: error: ‘GL_LIGHT0’ undeclared (first use in this function)
tree_openGL.c:735: error: ‘GL_POSITION’ undeclared (first use in this function)
tree_openGL.c:735: error: ‘light_position’ undeclared (first use in this function)
tree_openGL.c:737: error: ‘GL_LIGHTING’ undeclared (first use in this function)
tree_openGL.c:741: error: ‘GL_DEPTH_TEST’ undeclared (first use in this function)
tree_openGL.c:747: error: ‘GL_FOG’ undeclared (first use in this function)
tree_openGL.c:748: error: ‘GL_FOG_DENSITY’ undeclared (first use in this function)
tree_openGL.c: In function ‘display’:
tree_openGL.c:772: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘arc_color’
tree_openGL.c:772: error: ‘arc_color’ undeclared (first use in this function)
tree_openGL.c:772: error: expected expression before ‘]’ token
tree_openGL.c:780: error: ‘GL_COLOR_BUFFER_BIT’ undeclared (first use in this function)
tree_openGL.c:780: error: ‘GL_DEPTH_BUFFER_BIT’ undeclared (first use in this function)
tree_openGL.c:803: error: ‘GL_FRONT’ undeclared (first use in this function)
tree_openGL.c:803: error: ‘GL_AMBIENT_AND_DIFFUSE’ undeclared (first use in this function)
tree_openGL.c:803: error: ‘ground_material_amb_diffuse’ undeclared (first use in this function)
tree_openGL.c:804: error: ‘GL_FRONT_AND_BACK’ undeclared (first use in this function)
tree_openGL.c:804: error: ‘GL_FILL’ undeclared (first use in this function)
tree_openGL.c:806: error: ‘GL_QUADS’ undeclared (first use in this function)
tree_openGL.c:817: error: ‘tree_material_amb_diffuse’ undeclared (first use in this function)
tree_openGL.c: In function ‘reshape’:
tree_openGL.c:837: error: ‘GLsizei’ undeclared (first use in this function)
tree_openGL.c:837: error: expected ‘)’ before ‘w’
tree_openGL.c:838: error: ‘GL_PROJECTION’ undeclared (first use in this function)
tree_openGL.c:846: error: ‘GL_MODELVIEW’ undeclared (first use in this function)
tree_openGL.c: In function ‘specialKeyboard’:
tree_openGL.c:943: error: ‘GLUT_ACTIVE_SHIFT’ undeclared (first use in this function)
tree_openGL.c:947: error: ‘GLUT_KEY_UP’ undeclared (first use in this function)
tree_openGL.c:951: error: ‘GLUT_KEY_DOWN’ undeclared (first use in this function)
tree_openGL.c:955: error: ‘GLUT_KEY_LEFT’ undeclared (first use in this function)
tree_openGL.c:959: error: ‘GLUT_KEY_RIGHT’ undeclared (first use in this function)
tree_openGL.c: In function ‘setupCascadeMenu’:
tree_openGL.c:1105: error: ‘GLUT_RIGHT_BUTTON’ undeclared (first use in this function)
tree_openGL.c: In function ‘setupMenu’:
tree_openGL.c:1167: error: ‘GLUT_RIGHT_BUTTON’ undeclared (first use in this function)
tree_openGL.c: In function ‘tree_openGL’:
tree_openGL.c:1197: error: ‘GLUT_DOUBLE’ undeclared (first use in this function)
tree_openGL.c:1197: error: ‘GLUT_RGB’ undeclared (first use in this function)
tree_openGL.c:1197: error: ‘GLUT_DEPTH’ undeclared (first use in this function)
make: *** [paloverde] Error 1

```

I got the mac version to run on another computer, so it's not critical, but it is something I would like to figure out.

---

### Post by mc4man on 2009-02-10
You'd probably need these at the very least (plus what installs with them. (I'd start over with a fresh extracted source

libxmu-dev 
freeglut3-dev
flex 
bison

---

### Post by Crusty Juggler on 2009-02-10
Those additional 2 packages did it.  Thanks!

---

