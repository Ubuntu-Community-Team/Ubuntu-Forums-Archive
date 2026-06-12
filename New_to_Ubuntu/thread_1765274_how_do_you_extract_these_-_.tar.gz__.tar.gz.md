---
title: "how do you extract these - .tar.gz / .tar.gz??"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-22
Hello, I am confused.  I downloaded numerous .tar and .tar.gz files and the instructions are vauge at the most.  When downloading them, I have a few questions for you all;

1.Where do they go; what directory?

2.What do you do when you extract them?

3.Where do they end up?

4.How do you get rid of the files for the installation?

5.Is there a way to clean up those files after they install?

6.How do you make it show in the Ubuntu Software Center for easy installation afterwards?

---

### Post by Jesus_Valdez on 2011-05-22
Think of .tar.gz files just like another .zip or .rar type of files.

Normally just right click on them and choose Extract here... and for installation, well that depends on what are you downloading.

---

### Post by jtarin on 2011-05-23
> **TAspr said:**
> Hello, I am confused.  I downloaded numerous .tar and .tar.gz files and the instructions are vauge at the most.  When downloading them, I have a few questions for you all;

1.Where do they go; what directory?

2.What do you do when you extract them?

3.Where do they end up?

4.How do you get rid of the files for the installation?

5.Is there a way to clean up those files after they install?

6.How do you make it show in the Ubuntu Software Center for easy installation afterwards?

Since your a newbie I would recommend that you not install files with the endings of ".tar and .tar.gz". Ubuntu files end in the .deb file extension. These files are possibly installable and possibly not. Until you learn your way around Linux a little better I would stick to software in the "Software Center" or "Synaptic".If you feel a need for a certain application .....post and tell about your difficulty.

---

### Post by antmenj on 2011-05-23
> **TAspr said:**
> Hello, I am confused.  I downloaded numerous .tar and .tar.gz files and the instructions are vauge at the most.  When downloading them, I have a few questions for you all;

1.Where do they go; what directory?

2.What do you do when you extract them?

3.Where do they end up?

4.How do you get rid of the files for the installation?

5.Is there a way to clean up those files after they install?

6.How do you make it show in the Ubuntu Software Center for easy installation afterwards?

1. If you can't find your downloads go into firefox and select edit --> preferences -->General --> Save downolads to and see where its set for. 

If you mean where *should* they go that depends on what they are for.

2. *IF* you extract them you can just double click them, select the files to extract, select destination.  Some programs can use some tar.gz files in their unextracted state.

3. The place you selected

4. Highlight it then press delete.  Empty recycle bin latter. 

5. See point 4

6. You don't.  Install stuff from the software centre first.  If its not available there try synaptic.  If its not available there THEN go a manual install.

Hang in there.  Its a steep learning curve at first!

---

### Post by I2k4 on 2011-05-23
I'm pretty new and have pretty much the same reaction to these files - I avoid them.  I've noticed that FireFox 4.0 has an open/install option for .DEB files in its download dialog box (Chrome doesn't seem to have it.) and it's possible to just do the installation from within the FireFox download dialog (don't close it until the full install is finished.) 

Note also that the Synaptic Package Manager (which I use a lot) sometimes requires adding extra "Repositories" to get what you want, via Settings > Repositories > Other Software.  Sometimes you have to paste in a "ppa" commend to get something that Ubuntu doesn't include.  Others will be better experts than me about it.

As to getting rid of things, I've been pleased to discover "BleachBit" which is a configurable mass clean-up utility that works.  (Something called "Janitor" that comes with Ubuntu fouled up my system and forced a fresh install.)  Also by default the SPM saves all its installations in a cache, but this can be changed via Settings > Preferences > Files.  I've set it to delete downloaded packages after installation and not noticed any ill-effects.

---

### Post by TAspr on 2011-06-04
> **antmenj said:**
> 1. If you can't find your downloads go into firefox and select edit --> preferences -->General --> Save downolads to and see where its set for. 

If you mean where *should* they go that depends on what they are for.

2. *IF* you extract them you can just double click them, select the files to extract, select destination.  Some programs can use some tar.gz files in their unextracted state.

3. The place you selected

4. Highlight it then press delete.  Empty recycle bin latter. 

5. See point 4

6. You don't.  Install stuff from the software centre first.  If its not available there try synaptic.  If its not available there THEN go a manual install.

Hang in there.  Its a steep learning curve at first!


I tried to download "Transcoder", and it is  a .tar.gz file.  ***When you said You don't.  Install stuff from the software centre first***, what do you mean not to use the software center?

---

### Post by 3xp10r3r|X13 on 2011-06-04
for tar.gz files : "tar -xvf whatever-file" (that command extracts the whole thing-now there should be a new folder according to the zip file, in the directory, you are currently located in)
after you've extracted it go into that folder and type: "./configure" or "./setup"   (you can also type: "sh configure" or "sh setup" or whatever it is you need to run)

NOTE: You don't have to perform "make" and "make install" when you ran setup (it should guide you through the installation process by itself)

wait for it to finish...then type: "make"
and after that: "make install"

then it is going to install the wanted software (after it finished, you're able to launch the program)

edit:
the launcher will end up in: /usr/bin 
the libraries in: /usr/share 

well, usually

If that's not detailed enough, just ask!

---

### Post by TAspr on 2011-06-04
> **jtarin said:**
> Since your a newbie I would recommend that you not install files with the endings of ".tar and .tar.gz". Ubuntu files end in the .deb file extension. These files are possibly installable and possibly not. Until you learn your way around Linux a little better I would stick to software in the "Software Center" or "Synaptic".If you feel a need for a certain application .....post and tell about your difficulty.

Man, I am still finding it hard to use the synaptic package manager coming over from an ex windows user, well, almost ex.  I wish there was a pictorial for how to use this software.

---

### Post by TAspr on 2011-06-04
> **3xp10r3r|X13 said:**
> for tar.gz files : tar -xvf whatever-file 
after you extracted it go into the folder and run: ./configure or ./setup

wait for it to finish...then type: make
and after that: make install

then it will install the wanted software

Do you mean going into the folder itself and using the terminal as well as the two "**Make** Commands???

---

### Post by gandaran on 2011-06-04
> **TAspr said:**
> Man, I am still finding it hard to use the synaptic package manager coming over from an ex windows user, well, almost ex.  I wish there was a pictorial for how to use this software.
synaptic package manager is easy to use, just type the application name in search box then select the package, mark for install and click the apply button.
almost every linux program is in the repositories but if you want the newer versions you can add a PPA repository if it is available for the new program.   
click the reload button before doing the search.

---

### Post by jocko on 2011-06-04
> **TAspr said:**
> Man, I am still finding it hard to use the synaptic package manager coming over from an ex windows user, well, almost ex.  I wish there was a pictorial for how to use this software.
This is how to use synaptic:

1. Open synaptic.
2. Search for the program you need. If you know the the name (or part of the name) of the program, just search for that name. Otherwise you may need to extend your search to "description and name" or any of the other options...
3. Right-click the name of the program in the list of results, click "Mark for installation" in the menu that appears.
4. Click apply.
5. Done.

---

### Post by matt_symes on 2011-06-04
Hi

If you are talking about **transcode** and not **transcoder**, you can get it from synaptic package manager. Open synaptic package manager and search for it.

```
matthew@matthew-laptop:~$ apt-cache search ^transcode
transcode - Utility to encode raw video/audio streams
transcode-doc - Documentation for transcode
transcode-utils - Transcode utility programs
matthew@matthew-laptop:~$ 
```The point made by [antmenj]("http://ubuntuforums.org/member.php?u=180858") was

1. Try the software center (centre) first.
2. Try synaptic package manager second.
3. Install from a tar.gz file third.
4. Build and install from source last.

They are gradated for difficulty, the software centre being the easiest and installing after building from source the hardest.

You don't need to look around the web for almost all the applications you need so try to get out of that windows mentality and you will find installing software a breeze.

Kind regards

---

### Post by 3xp10r3r|X13 on 2011-06-04
All right,
to install tar.gz files you should use the terminal. Just launch your console and type in the following:
(first of all, your always located at your home directory, so navigate, using the "cd" command, to the directory, where  the tar.gz file is located in. Once there type: )

tar -xvf name.tar.gz 

(just type in the first few letters of the file and press tab, so you don't have to write the whole thing out)

(the whole thing got extracted now, so there should be a folder in the directory, with the name of your program or the name of the tar.gz file., you've just extracted. Type "ls" to view the content of the directory - the folder should be there. Then type : )

cd nameofthefolder 

(now you should be right in the extracted folder. Type: )

ls 

(now there are two ways you can go. Either, there is a little executable called "configure" or "setup". In the first case continue with: )

sudo ./configure

(type in your password and hit enter. It will run the "configure" file. After that type: )

make

(wait a few seconds, till it finished and type: )

HINT: You might need root privileges, so put a sudo in front of it 

make install

(done! now, if it's a "setup" file you can spot, type: )

./setup

(now it should guide you through a setup)

Hope this helped :)

---

### Post by Chronon on 2011-06-04
> **3xp10r3r|X13 said:**
> for tar.gz files : "tar -xvf whatever-file" (that command extracts the whole thing-now there should be a new folde,r according to the zip file, in the directory, you are currently located in)
after you've extracted it go into the folder and type: "./configure" or "./setup"   (you can also type: "sh configure" or "sh setup" or whatever it is you need to run)

NOTE: You don't have to perform "make" and "make install" when you ran setup (it should guide you through the installation process by itself)

wait for it to finish...then type: "make"
and after that: "make install"

then it is going to install the wanted software (after it finished, you're able to launch the program)

edit:
the launcher will end up in: /usr/bin 
the libraries in: /usr/share 

well, usually

If that's not detailed enough, just ask!

A couple of points:
1) These instructions assume that the .tar.gz archive contains a buildable source tree.  This seems like an unwarranted assumption as it could contain a theme or binaries with an install script or . . ..
2) For a newbie it's much easier to just have them locate the archive in the file manager and open it (e.g. double-click).  The associated archive manager (file-roller, ark, etc.) should open the archive automatically.  At this point the user can inspect the contents of the archive to determine if it's source code that needs building or not.  Usually the archive will contain a README that provides usage instructions.

---

### Post by 3xp10r3r|X13 on 2011-06-04
in the most cases they do have executable files, such as "setup" or "configure". Have a look at my more detailed description. I think it made the process pretty clear. 

But I agree with all of you, that it is much easier to use the traditional software center :)

---

### Post by TAspr on 2011-06-04
> **matt_symes said:**
> Hi

If you are talking about **transcode** and not **transcoder**, you can get it from synaptic package manager. Open synaptic package manager and search for it.

```
matthew@matthew-laptop:~$ apt-cache search ^transcode
transcode - Utility to encode raw video/audio streams
transcode-doc - Documentation for transcode
transcode-utils - Transcode utility programs
matthew@matthew-laptop:~$ 
```The point made by [antmenj]("http://ubuntuforums.org/member.php?u=180858") was

1. Try the software center (centre) first.
2. Try synaptic package manager second.
3. Install from a tar.gz file third.
4. Build and install from source last.

They are gradated for difficulty, the software centre being the easiest and installing after building from source the hardest.

You don't need to look around the web for almost all the applications you need so try to get out of that windows mentality and you will find installing software a breeze.

Kind regards


Thanks for the confidence.. I need it.

---

### Post by TAspr on 2011-06-04
> **3xp10r3r|X13 said:**
> All right,
to install tar.gz files you should use the terminal. Just launch your console and type in the following:
(first of all, your always located at your home directory, so navigate, using the "cd" command, to the directory, where  the tar.gz file is located in. Once there type: )

tar -xvf name.tar.gz 

(just type in the first few letters of the file and press tab, so you don't have to write the whole thing out)

(the whole thing got extracted now, so there should be a folder in the directory, with the name of your program or the name of the tar.gz file., you've just extracted. Type "ls" to view the content of the directory - the folder should be there. Then type : )

cd nameofthefolder 

(now you should be right in the extracted folder. Type: )

ls 

(now there are two ways you can go. Either, there is a little executable called "configure" or "setup". In the first case continue with: )

sudo ./configure

(type in your password and hit enter. It will run the "configure" file. After that type: )

make

(wait a few seconds, till it finished and type: )

HINT: You might need root privileges, so put a sudo in front of it 

make install

(done! now, if it's a "setup" file you can spot, type: )

./setup

(now it should guide you through a setup)

Hope this helped :)

Yes, I will try it for sure after I get brave enough to conquer going into the terminal..lol.

---

