---
title: "how to create a starter for &quot;voodoo camera tracker v.1.0.1&quot;"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by tazztone on 2010-01-15
hi
in order to start the programm mentioned in the thread title I have to open a terminal window and type in the following seperately:
> 
  cd ./voodoo-x86Linux-1.0.1
export LD_LIBRARY_PATH=`pwd`/bin/
bin/voodoo  
how do i create a **starter** that would slow down the startup process for this app?
I tried tiping the following in the command field:
> gnome-terminal cd /home/tazz/Desktop/voodoo export LD_LIBRARY_PATH=`pwd`/bin/ bin/voodoo..but all what happens after doubleclicking the starter is, a terminal opens without commands being executed - just an empty terminal window. 
what has to be in the command field in order to get this working??

if you can't  help me with that, thank you for reading this and trying to do so.

cheers:popcorn:

---

### Post by alwayshere on 2010-01-15
right click on your desktop choose
"create launcher"

in the coommand box put your command 
if that dont work you might have to put sudo in front of it or maybe gksudo

you may need to change the "type" box to application in terminal ?

just have a go mix it up a bit

---

### Post by ajgreeny on 2010-01-15
```
gnome-terminal cd /home/tazz/Desktop/voodoo export LD_LIBRARY_PATH=`pwd`/bin/ bin/voodoo                      
```The best way to do this is to make that terminal input into a bash script and then point to that script in your launcher.
```
!#/bin/bash
cd ./voodoo-x86Linux-1.0.1
export LD_LIBRARY_PATH=`pwd`/bin/
bin/voodoo
```save this as voodoo.sh, make it executable, and it should work when your launcher points to it.

---

### Post by tazztone on 2010-01-15
thx alwayshere for u'r answer but i found no working combination of gksudo and the commands that would start the app.

thx very much ajgreeny, it worked. altough i didn't know what "make executable" meant, i found some infos suggesting i should "chmod +x voodoo.sh" and "chmod 755 voodoo.sh" it to do so (..no idea what this has done).
anyway,
i changed "!#" to "#!" like i've seen it in another script. was it a mistake of you?


btw: voodoo can be used to track points in a batch of images captured from video sequences and create a 3d python script out of them. this can then be imported to blender and serve as a model. 
the idea is from this video-tutorial: 
**3D mesh captured from video **[http://www.youtube.com/watch?v=vbvex7maHL8](http://www.youtube.com/watch?v=vbvex7maHL8)

---

### Post by ajgreeny on 2010-01-15
> **tazztone said:**
> thx alwayshere for u'r answer but i found no working combination of gksudo and the commands that would start the app.

thx very much ajgreeny, it worked. altough i didn't know what "make executable" meant, i found some infos suggesting i should "chmod +x voodoo.sh" and "chmod 755 voodoo.sh" it to do so (..no idea what this has done).
anyway,
i changed "!#" to "#!" like i've seen it in another script. was it a mistake of you?


btw: voodoo can be used to track points in a batch of images captured from video sequences and create a 3d python script out of them. this can then be imported to blender and serve as a model. 
the idea is from this video-tutorial: 
**3D mesh captured from video **[http://www.youtube.com/watch?v=vbvex7maHL8](http://www.youtube.com/watch?v=vbvex7maHL8)
Yes, sorry, but that was a typo.

Glad it worked for you.  The **chmod +x** command just makes the file you refer to executable, as does the **chmod 755**.  Have a look at man chmod in terminal for all the gen.  A bit difficult to read, but it's all there if you can understand it.

---

