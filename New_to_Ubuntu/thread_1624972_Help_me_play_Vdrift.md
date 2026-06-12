---
title: "Help me play Vdrift"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2010-11-18
Downloaded it, unzipped, started what the read me says 

```
sudo apt-get install g++ scons libsdl-gfx1.2-dev libsdl-image1.2-dev libsdl-net1.2-dev libvorbis-dev libglew-dev libasio-dev libboost-dev
```

Then it says 

```
There are two ways to use SCons. The first way is to install scons
 on your system through your package manager, then you can use it simply 
by the name of the program, "scons". If you followed the directions for 
installing prerequisites for Ubuntu above, then you're done and can continue
 on to the next section. The second way is to use the scons-local package 
(included with VDrift) which will do the same thing but doesn't require that
 you install scons on your system. To do this, you must move the 
scons-local-0.96.95.tar.gz archive from tools to the root vdrift folder,
 un-tar the archive, and then use the <code>./scons.py</code> command instead
 of <code>scons</code>.

===Get the Code===
You can get the code from a source package for a particular version, or you can
 [[Getting the development version|get the development version]].
====Source Package====
[http://sourceforge.net/project/showfiles.php?group_id=137283 Download] the 
latest VDrift Linux source package. All the files in the package are in a
 directory called vdrift-'''version'''-src where '''version''' is something
 like 2009-06-15.

Unpack the archive.

 tar jxvf vdrift-2009-06-15-src.tar.bz2

=====Enter directory=====
Now change directories into the location of your newly created VDrift source 
tree.
 cd vdrift-2009-06-15

```


I have no idea what any of that means.  I typed "scons" into the terminal, 
and I get an error, but the directions are unclear there, am I supposed to 
try that, even thought I "followed the directions for installing prerequisites 
for Ubuntu above"

---

### Post by Zzl1xndd on 2010-11-18
You might try installing it using PlayDeb.




[http://www.playdeb.net/updates/ubuntu/10.10/?q=vdrift](http://www.playdeb.net/updates/ubuntu/10.10/?q=vdrift)

---

### Post by DarrenMR415 on 2010-11-18
I tried that, but everytime I click the install button it brings me to a blank page.

---

### Post by Zzl1xndd on 2010-11-18
There should be a "Click here to learn how to install games from PlayDeb option" near the top of the page. You will have to install the Playdeb package first or manually configure your repositories.

---

### Post by DarrenMR415 on 2010-11-18
I did that, still get the blank page.

---

### Post by DarrenMR415 on 2010-11-18
```
Go to System-Administration-Software Sources, Third-Party Software tab, Add:
```

I dont have the Third-part software tab.

---

### Post by Zzl1xndd on 2010-11-18
Try going to Go to System-Administration-Synaptic Package Manager and click reload. Then attempt to install the game again.

---

### Post by DarrenMR415 on 2010-11-19
I still just get a blank page on Playdeb.

---

### Post by DarrenMR415 on 2010-11-20
Still getting the blank page.  Anything else I should try?

---

### Post by DarrenMR415 on 2010-11-20
Still getting the blank page.  Anything else I should try?

---

### Post by DarrenMR415 on 2010-11-21
Can anyone help?

---

### Post by Zzl1xndd on 2010-11-21
If thats still not working try this. Go to System > Administration > Synaptic Package Manager. 

Then Select Settings > Repositories. Select the Other Software tab and click add.

Enter deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb games > and click Add Source.

Now open a terminal and enter

```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```

Then Click reload in Synaptic. 

Now if you search for Vdrift in Synaptic it should be listed.

---

### Post by DarrenMR415 on 2010-11-22
That did it, thank you.

---

