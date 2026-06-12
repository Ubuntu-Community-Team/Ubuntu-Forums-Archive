---
title: "how to use the Cube Effect (3D)"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by my_everything78 on 2008-12-24
Hello everyone .
Sorry guys cause I bring alot of questions here , sorry for that .

I have more than one question here .
1-  I want to use the Cube Effect(3d) i searched for compiz on my ubuntu so it said that compiz is installed ,the question how to find compiz and how to use it and configure it then run it ?


2- yesterday i tried to untar a packege called beryl , but it didnt work at all . so can any body tell me how to un tar a file and where is the directory i should untar in it .?

---

### Post by adult swim on 2008-12-24
you dont need beryl, it merged with compiz a while ago.
to get the cube going, youll need to install the compiz settingsmanager.
to do that go to a terminal and enter in ```
sudo apt-get install compizconfig-settings-manager
```  once it installs go to system>preferences>compiz settings manager.  there youll need to check the boxes desktop cube and rotate cube.  to get it to rotate you can hit ctrl+alt+left click and drag your mouse.  if youve got a mouse with a third button or a scroll wheel you can just click the scroll wheel/button and then drag to spin it.

---

### Post by SpenceMakesSense on 2008-12-24
go to synaptic package manager(system-administration) and look for compizconfig-settings-manager
install that
then look in system-preferences
you should find compiz config settings manager in there. 
Enable desktop cube and rotate cube
If it doesnt seem to work your graphics card might not be installed

---

### Post by my_everything78 on 2008-12-24
Greate , thank you guys so much .

But still need to learn how to untar a package if i have this package for example at /home/myuser/desktop/ , so how can i untar a package and where should i untar it ?

---

### Post by adult swim on 2008-12-24
generally to untar something you can run ```
tar xzvf file.tar.gz
``` replacing file with whatever it is you are trying to untar.  it will untar the file into the directory the tarball is in.  alternatively you could right click the tarball and choose extract here.

---

### Post by my_everything78 on 2008-12-24
thank you adult swim , it helps alot :)
Best Regards

---

