---
title: "Ponyprog Install"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by kemo0o on 2009-04-10
Hello All 
i am going to install PonyProg to use it in my projects as i am using uC (AVR) . also i swapped from Windows ):P to UBUNTU 
 i had read this thread 
[http://ubuntuforums.org/showthread.php?t=223247](http://ubuntuforums.org/showthread.php?t=223247)

also applied the last reply and works perfect with me except the last Step while i try to "make"  

the terminal gives me ERROR  like this 
```
make[1]: Entering directory `/home/kareem/PonyProg2000-2.07c/v'
cd srcx ; make
make[2]: Entering directory `/home/kareem/PonyProg2000-2.07c/v/srcx'
make[2]: *** No rule to make target `v_defs.h', needed by `PonyProg2000-2.07c/v/objx/vapp.o'.  Stop.
make[2]: Leaving directory `/home/kareem/PonyProg2000-2.07c/v/srcx'
make[1]: *** [srcx] Error 2
make[1]: Leaving directory `/home/kareem/PonyProg2000-2.07c/v'
make: *** [vlib] Error 2
```

any Help ?? as  i need it too much

---

### Post by kemo0o on 2009-04-10
F1 .... is there anyone wanna Help me ?? :popcorn:

---

### Post by kemo0o on 2009-04-12
Where R U ?!! 

I onlu use that S H I T Windows For this only

---

### Post by Eisenwinter on 2009-04-12
Alright.

cd into the directory of PonyProg, in terminal, with the "cd" command.

Type ./configure
then type make

Report back if there are any errors.

If there are no errors, type sudo make install

---

### Post by kemo0o on 2009-04-12
Thanks for You 

but i fixed some missing data when i #make 
all files go correct but small error appear at the end 

> g++-3.4 -I/home/kareem/PonyProg2000-2.07c/v/includex -I/usr/X11R6/include  -O2 -DAthena -D_LINUX_ -Wall -fpermissive -Wno-deprecated -I/usr/src/linux-headers-2.6.22-14-generic/include -c ponyioint.cpp -o ponyioint.o
ponyioint.cpp:60:21: asm/io.h: No such file or directory
make: *** [ponyioint.o] Error 1
 

---

### Post by kemo0o on 2009-04-12
[COLOR="DarkRed"]OK OK BTW i installed it but when i want to import .hex file from media i can't ?? only from file system partition[/COLOR] 


[IMG]http://i42.tinypic.com/i211jt.jpg[/IMG]



[COLOR="DarkRed"]how can i import files from the media[/COLOR]

---

### Post by Icon2k on 2010-11-12
Hy, i have the same problem, but if i write ./configure i get:
bash: ./configure: No such file or directory
What do i wrong?

---

### Post by harish2704 on 2011-05-23
Try this 
this worked for me (Ubuntu 11.04)
[http://ponyprog.sourceforge.net/phorum/file.php?2,file=26,filename=ponyProg2000.tar.gz](http://ponyprog.sourceforge.net/phorum/file.php?2,file=26,filename=ponyProg2000.tar.gz)

---

### Post by py8elo on 2011-09-30
Hi harish2704 and all,
I am trying to install PonyProg on Ubuntu 11.04 and get a lot of errors.

-
py8elo@py8elo-OEM:~/PonyProg2000-2.07c$ make
cd v; make vlib
make[1]: Entrando no diretório `/home/py8elo/PonyProg2000-2.07c/v'
cd srcx ; make
make[2]: Entrando no diretório `/home/py8elo/PonyProg2000-2.07c/v/srcx'
g++-4.5 -c -fpermissive -Wno-deprecated -I/home/py8elo/PonyProg2000-2.07c/v/includex -I/usr/X11R6/include  -O2 -DAthena -o /home/py8elo/PonyProg2000-2.07c/v/objx/vapp.o vapp.cxx
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx: In member function ‘void vApp::initialize(int&, char**)’:
vapp.cxx:354:7: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:354:7: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:491:32: warning: deprecated conversion from string constant to ‘char*’
g++-4.5 -c -fpermissive -Wno-deprecated -I/home/py8elo/PonyProg2000-2.07c/v/includex -I/usr/X11R6/include  -O2 -DAthena -o /home/py8elo/PonyProg2000-2.07c/v/objx/vawinfo.o vawinfo.cxx
g++-4.5 -c -fpermissive -Wno-deprecated -I/home/py8elo/PonyProg2000-2.07c/v/includex -I/usr/X11R6/include  -O2 -DAthena -o /home/py8elo/PonyProg2000-2.07c/v/objx/vbaseitm.o vbaseitm.cxx
g++-4.5 -c -fpermissive -Wno-deprecated -I/home/py8elo/PonyProg2000-2.07c/v/includex -I/usr/X11R6/include  -O2 -DAthena -o /home/py8elo/PonyProg2000-2.07c/v/objx/vbasewin.o vbasewin.cxx
vbasewin.cxx: In copy constructor ‘vBaseWindow::vBaseWindow(const vBaseWindow&)’:
vbasewin.cxx:28:73: warning: deprecated conversion from string constant to ‘char*’
g++-4.5 -c -fpermissive -Wno-deprecated -I/home/py8elo/PonyProg2000-2.07c/v/includex -I/usr/X11R6/include  -O2 -DAthena -o /home/py8elo/PonyProg2000-2.07c/v/objx/vbtncmd.o vbtncmd.cxx
vbtncmd.cxx:34:26: fatal error: X11/Xaw/Form.h: Arquivo ou diretório não encontrado
compilation terminated.
make[2]: ** [/home/py8elo/PonyProg2000-2.07c/v/objx/vbtncmd.o] Erro 1
make[2]: Saindo do diretório `/home/py8elo/PonyProg2000-2.07c/v/srcx'
make[1]: ** [srcx] Erro 2
make[1]: Saindo do diretório `/home/py8elo/PonyProg2000-2.07c/v'
make: ** [vlib] Erro 2

-
Can somebody help me please?

Thanks in advance and Best regards,

Silva.

> **harish2704 said:**
> Try this 
this worked for me (Ubuntu 11.04)
[http://ponyprog.sourceforge.net/phorum/file.php?2,file=26,filename=ponyProg2000.tar.gz](http://ponyprog.sourceforge.net/phorum/file.php?2,file=26,filename=ponyProg2000.tar.gz)

---

### Post by lancos on 2011-11-06
Hi, 
you need some packets installed to build ponyprog,
try to install this:

sudo apt-get install libxaw7-dev

then download latest (2.08b) version from 
[http://sourceforge.net/projects/ponyprog/files/PonyProg%20sources/2.08b/](http://sourceforge.net/projects/ponyprog/files/PonyProg%20sources/2.08b/)

and read the INSTALL file 

> **py8elo said:**
> Hi harish2704 and all,
I am trying to install PonyProg on Ubuntu 11.04 and get a lot of errors.

-
py8elo@py8elo-OEM:~/PonyProg2000-2.07c$ make
cd v; make vlib
make[1]: Entrando no diretório `/home/py8elo/PonyProg2000-2.07c/v'
cd srcx ; make
make[2]: Entrando no diretório `/home/py8elo/PonyProg2000-2.07c/v/srcx'
g++-4.5 -c -fpermissive -Wno-deprecated -I/home/py8elo/PonyProg2000-2.07c/v/includex -I/usr/X11R6/include  -O2 -DAthena -o /home/py8elo/PonyProg2000-2.07c/v/objx/vapp.o vapp.cxx
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:200:5: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx: In member function ‘void vApp::initialize(int&, char**)’:
vapp.cxx:354:7: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:354:7: warning: deprecated conversion from string constant to ‘char*’
vapp.cxx:491:32: warning: deprecated conversion from string constant to ‘char*’
g++-4.5 -c -fpermissive -Wno-deprecated -I/home/py8elo/PonyProg2000-2.07c/v/includex -I/usr/X11R6/include  -O2 -DAthena -o /home/py8elo/PonyProg2000-2.07c/v/objx/vawinfo.o vawinfo.cxx
g++-4.5 -c -fpermissive -Wno-deprecated -I/home/py8elo/PonyProg2000-2.07c/v/includex -I/usr/X11R6/include  -O2 -DAthena -o /home/py8elo/PonyProg2000-2.07c/v/objx/vbaseitm.o vbaseitm.cxx
g++-4.5 -c -fpermissive -Wno-deprecated -I/home/py8elo/PonyProg2000-2.07c/v/includex -I/usr/X11R6/include  -O2 -DAthena -o /home/py8elo/PonyProg2000-2.07c/v/objx/vbasewin.o vbasewin.cxx
vbasewin.cxx: In copy constructor ‘vBaseWindow::vBaseWindow(const vBaseWindow&)’:
vbasewin.cxx:28:73: warning: deprecated conversion from string constant to ‘char*’
g++-4.5 -c -fpermissive -Wno-deprecated -I/home/py8elo/PonyProg2000-2.07c/v/includex -I/usr/X11R6/include  -O2 -DAthena -o /home/py8elo/PonyProg2000-2.07c/v/objx/vbtncmd.o vbtncmd.cxx
vbtncmd.cxx:34:26: fatal error: X11/Xaw/Form.h: Arquivo ou diretório não encontrado
compilation terminated.
make[2]: ** [/home/py8elo/PonyProg2000-2.07c/v/objx/vbtncmd.o] Erro 1
make[2]: Saindo do diretório `/home/py8elo/PonyProg2000-2.07c/v/srcx'
make[1]: ** [srcx] Erro 2
make[1]: Saindo do diretório `/home/py8elo/PonyProg2000-2.07c/v'
make: ** [vlib] Erro 2

-
Can somebody help me please?

Thanks in advance and Best regards,

Silva.

---

