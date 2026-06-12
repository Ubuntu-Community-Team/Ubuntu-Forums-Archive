---
title: "Running Games in Ubuntu"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by berger15 on 2010-02-24
Hi there. 
I am a complete Linux novice. I have managed to get so far, but now I am utterly stuck. I have downloaded and installed UFO: Alien Invasion, but I cannot seem to run it.:confused: I have tried running the executable file, both as a "run" and "run in terminal", but nothing appears to happen. I then searched the net for help, and came up against a myriad of things, but none of them have helped. these include opening a terminal and running the app from ./home/craig/ufoai/ufo.exe . 

The file is in /home/craig/ufoai - the default location. 

So please, tell me how I run the game!

Thanks in advance

---

### Post by dvlchd3 on 2010-02-24
It appears you downloaded the Windows version of the game.  Try downloading the tarball on Sourceforge:

[http://sourceforge.net/projects/ufoai/files/UFO_AI%202.x/2.2.1/ufoai-2.2.1-data.tar/download](http://sourceforge.net/projects/ufoai/files/UFO_AI%202.x/2.2.1/ufoai-2.2.1-data.tar/download)

then move to whereever you downloaded in the terminal.  If you downloaded it to your "Downloads" folder follow these directions:

```

cd ~/Downloads
tar -zxvf ufoai-2.2.1-data.tar
cd ufo*
./configure
sudo make
sudo make install

```

If you recieve any errors on the last three steps, post them here before proceeding.  This usually means you have some dependency you need to satisfy before installing.

---

### Post by kwacka on 2010-02-24
The route advised by dvlchd3 is for the installation of data files only.

If you go to [http://sourceforge.net/projects/ufoai/](http://sourceforge.net/projects/ufoai/) and download the linux files to (e.g.) Downloads, then:

```
cd Downloads
./ufoai-2.2-linux.run
```

The game should install. Download/installation of data & map files is not required.

---

### Post by kwacka on 2010-02-24
An additional step you need to take, make the downloaded file executable.

The easiest way is to right-click on the file in nautilus, choose 'properties' then 'permissions' and tick the box to make it executable. Then click on the file to install.

Alternatively, open a terminal and type:

```
cd Downloads

chown +x ./ufoai-2.2-linux.run <enter>

./ufoai-2.2-linux.run <enter>
```

A new folder (ufoai) will contain files for the game. Open a terminal, 'cd' to the new folder. Typing ./ufoai  there will run the game - or run from ALT+F2, or even clicking on the ufoai in nautilus will run.

---

### Post by ibuclaw on 2010-02-24
UFO is in the repositories, is it not? :)

(edit): I stand corrected, have a look at this site for games [http://www.playdeb.net](http://www.playdeb.net)

Regards
Iain

---

### Post by berger15 on 2010-02-25
Thanks - I made the file executable and have followed your installation steps, Kwacka. That overwrote the files already there, so I don't think I had the windows version of the game. Either way, I opened a terminal, cd'd to the ufoai file and entered ./ufoai - this should run the game as I understand it. Instead I get the following message:


./ufo: error while loading shared libraries: libSDL_ttf-2.0.so.0: cannot open shared object file: No such file or directory

Looks like I was missing something. So, I opened the package manager, searched for the package, installed it and tried starting the game again and . . . . Viola!! It works. Thanks again for all you help.

---

### Post by kwacka on 2010-02-25
Thanks for the link, IBUCLAW - makes life easier.

Good to hear you got sorted, berger15. If you right-click on one of the panels you can add a custom launcher to the panel, just point it to ufoai/ufoai or wherevever you have installed (theres' an icon in there too).

---

