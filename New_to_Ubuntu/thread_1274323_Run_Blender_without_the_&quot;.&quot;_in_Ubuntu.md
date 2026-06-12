---
title: "Run Blender without the &quot;./&quot; in Ubuntu"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by mo0nykit on 2009-09-24
Hello!

When I install Blender from the Ubuntu repositories with ```
sudo apt-get install blender
``` I can run Blender with just ```
blender
```However, I asked around the IRC channels and they recommend **against** using Blender from the repositories. Besides, I couldn't get the latest Blender from there. I should download from the official site instead. I have several questions about what to do with the resulting **.tar.bz2** file

[LIST=1]
[*]Which (default, or best practices) directory should I untar the file?
[*]How can I run Blender from anywhere in the command line? I tried setting the PATH variable in **.bashrc**, editing the **/etc/environment** file, or even using the **export** command, but I still can't run Blender from anywhere.
[*]This question is closely related to #2. Somehow, despite setting the PATH variable, I still can't run Blender from anywhere since it requires ```
./blender
``` as opposed to the apt-get install where I can just do ```
blender
```
[/LIST]
Thanks in advance! :)

---

### Post by doas777 on 2009-09-24
is blender in /usr/bin/ ? if not try creating a link to it and place the link in /usr/bin/ then give it a try.

---

### Post by jmszr on 2009-09-24
moOnykit,

You can get a .deb for Blender 2.49b (the latest) from here: [http://www.getdeb.net/search.php?keywords=blender](http://www.getdeb.net/search.php?keywords=blender) .

---

### Post by sancho panza on 2009-09-24
If you wish to follow best practices, /usr/local is the folder to use for all programs you install manually without using any repositories. The steps are:
1. Within /usr/local you can unzip or whatever all the blender files into the      folder called blender.
2. Once you do that, create a symbolic link by name "blender" pointing to the executable file in /usr/local/blender and keep it in the folder /usr/local/bin. 
3. Make sure the symbolic link has executable permissions. Now you should be able to type "blender" into the command window to run it the way you wanted to.

Hope this helps,

---

### Post by mo0nykit on 2009-09-24
Thanks everyone for your suggestions!

**@sancho panza**
Your instructions worked like a charm!

Okay, for everybody's benefit, absolute beginner style, here's what I did:

[LIST=1]
[*]Create a directory in my **home** folder for any archives that I download manually ```
mkdir tars
```
[*]**cd** into the newly created tars directory ```
cd tars
```
[*]Download the **.tar.bz2** Blender archive from the official site with **wget** ```
wget http://download.blender.org/release/Blender2.49b/blender-2.49b-linux-glibc236-py26-i386.tar.bz2
```
[*]The following instructions will require root privileges, thus the **sudo** at the beginning of each command.
[*]Copy the **.tar.bz2** to the */usr/local* directory ```
sudo cp blender-2.49b-linux-glibc236-py26-i386.tar.bz2 /usr/local
```
[*]**cd** into */usr/local* ```
cd /usr/local
```
[*]Untar the Blender **.tar.bz2** ```
sudo tar xvjf blender-2.49b-linux-glibc236-py26-i386.tar.bz2
```
[*]Delete the **.tar.bz2** for clean-up purposes. Anyway, you have a copy of this archive in your *~/tars* directory.```
sudo rm blender-2.49b-linux-glibc236-py26-i386.tar.bz2
```
[*]**cd** into */usr/local/bin* ```
cd /usr/local/bin
```
[*]Create a symbolic link to your new Blender executable ```
sudo ln -s ../blender-2.49b-linux-glibc236-py26-i386/blender blender
```
[*]Now, just to prove that you can run Blender from anywhere, **cd** into any other directory and type ```
blender
```
[/LIST]
Problem solved! Thanks everyone! :)

---

### Post by sandyd on 2009-09-24
> **mo0nykit said:**
> Hello!

When I install Blender from the Ubuntu repositories with ```
sudo apt-get install blender
``` I can run Blender with just ```
blender
```However, I asked around the IRC channels and they recommend **against** using Blender from the repositories. Besides, I couldn't get the latest Blender from there. I should download from the official site instead. I have several questions about what to do with the resulting **.tar.bz2** file

[LIST=1]
[*]Which (default, or best practices) directory should I untar the file?
[*]How can I run Blender from anywhere in the command line? I tried setting the PATH variable in **.bashrc**, editing the **/etc/environment** file, or even using the **export** command, but I still can't run Blender from anywhere.
[*]This question is closely related to #2. Somehow, despite setting the PATH variable, I still can't run Blender from anywhere since it requires ```
./blender
``` as opposed to the apt-get install where I can just do ```
blender
```
[/LIST]
Thanks in advance! :)
assuming that the blender folder is on the desktop and its called "blender"
```

cd ~/Desktop
sudo mv blender /opt/
sudo chmod 777 /opt/blender/blender
sudo ln /opt/blender/blender /usr/local/bin/blender-custom

```run
```

blender-custom

```to start blender.

you can do that too ;)

---

### Post by Simian Man on 2009-09-24
> **mo0nykit said:**
> 
Delete the **.tar.gz** for clean-up purposes. Anyway, you have a copy of this archive in your *~/tars* directory. BE CAREFUL WITH THE **-rf** FLAGS! Make sure you know what those options mean. ```
sudo rm -rf blender-2.49b-linux-glibc236-py26-i386.tar.bz2
```


I just want to point out that you really do not need the -rf flags when deleting a single file.  They are only really needed when deleting entire directories.  Safer not to use it when it's not needed.

---

### Post by mo0nykit on 2009-09-25
**@Simian Man**

Thanks! Okay, I'll edit my [SOLUTION] post :)

---

### Post by kuttumiah on 2010-10-10
hey [mo0nykit]("http://ubuntuforums.org/member.php?u=904834"), thanks for the solution.
this is the best installation tutorial i've ever seen.
go on, have fun.
thanks.

---

