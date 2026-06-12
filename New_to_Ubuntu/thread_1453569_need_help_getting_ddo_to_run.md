---
title: "need help getting ddo to run"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by purdurabo on 2010-04-13
ok i am trying to run ddo on ubuntu 9.10, right? well i have been following the how-to on
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785)
i got to the part about downloading the pylotro launcher. the stand alone vers. can not patch the way i need it, so i got the source code at the bottom of the page just as the how-to recomended. the code he pu on the site does not work for me
```
tar xvjf PyLotRO-[version].tar.bz2
```
i put in
 ```
tar xvjf PyLotRO-0.1.11.tar.bz2
``` 
and this is what i got
```
tar xvjf PyLotRO-0.1.11.tar.bz2
tar: PyLotRO-0.1.11.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
```
i am new to this terminal thing so can somone please explain this to me?

---

### Post by jaco223 on 2010-04-13
Try this:
Open a teminal and type

```
sudo bunzip2 filename.tar.bz2 (where filename.txt.bz2 is the name of the  file you wish to uncompress
```)

After that you will be left with the .tar file, at the terminal type 

sudo tar -xzvf (name of the file)
[FONT=monospace]
After that you probably have to do

./configure

make

make install


[/FONT]Hope this helps.

Jaco

---

### Post by purdurabo on 2010-04-13
i tried the first code you gave me and this is what i got
```
sudo bunzip2 PyLotRO-0.1.11.tar.bz2
[sudo] password for allen: 
bunzip2: Can't open input file PyLotRO-0.1.11.tar.bz2: No such file or directory
```

---

### Post by f1r3flie on 2010-04-14
It looks like your problem is that you haven't navigated to the directory the file's in. Open up the folder that the file is in with a normal file browser. You then need to copy the directory (eg. /home/user/Desktop). Next you need to open up the terminal, type ```
cd
``` then a space, then right click on the terminal and choose "paste". This should navigate you to the directory you need to be in. Then you type 
```
tar xvjf PyLotRO-0.1.11.tar.bz2
``` and you're done, and can continue with the tutorial. Hope this helps! :)

---

### Post by purdurabo on 2010-04-14
this seemed to work. the bz2 file was in my downloads folder, so i used
```
cd Downloads
```
then i used
```
tar xvjf PyLotRO-[version].tar.bz2
```
it exestracted the package alright! files flow every where!!! lol  so then i used
```
sudo ./setup.py install
``` 
and this is what i got
```
running install
running build
running build_py
running build_scripts
running install_lib
running install_scripts
changing mode of /usr/local/bin/pylotro to 755
running install_data
running install_egg_info
Removing /usr/local/lib/python2.6/dist-packages/PyLotROLauncher-0.1.11.egg-info
Writing /usr/local/lib/python2.6/dist-packages/PyLotROLauncher-0.1.11.egg-info
writing list of installed files to 'pylotro-install.log'
```
now the icon is on my desk top just the way it should be, right? so i finished going through the how-to. i got to the end where is said i had to up-date the game
"
Run Tools->Update (IMPORTANT - the game will fail if you don't run the update first), then select your server and log in using your account username and password."
the problem is that there is no Tool->update option. so if any one knows what i did wrong and/or how to fix it please tell me!!!!

---

