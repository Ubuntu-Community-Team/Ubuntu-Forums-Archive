---
title: "Creating a laucher from the Terminal"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by aas452 on 2009-02-22
As of now I load all my programs through the terminal, but one of my recently downloaded program came with no documentation about a keyword where I can launch the application. And I am stuck with navigating to the path of the program and launching it from there.

I figure there is a way to add and change these keywords??? Is there a specific file I need to manipulate.

---

### Post by mcduck on 2009-02-22
Programs are not started using keywords, but simply by giving the name of the program's executable file. When you type anything into the terminal and press enter all locations specified in your path are searched through to find if executable file with that name exists. If such file is found, it's started, if not, you get error message.

Every single command you use is actually just executable file in one of the directories defined in your path.

By default, path includes /bin, /sbin, /usr/bin, /usr/games, /usr/local/bin, /usr/local/sbin (and ~/bin, if it exists).

Most of the time executables for user-level programs are located in /usr/bin. You can also find where program's executable is located by running "which *nameoftheprogram*. For example "which firefox" would respond "usr/bin/firefox". This only works for programs installed with the package manager.

If this program you are having with is something you installed manually (so it wasn't installed with Ubuntu's package management tools, or into any of default locations) the best way is to either create a symbolic link to it's executable file in one of the directories included in the path.

Of course you could also create a script to start the program, and put that in some place that's in your path, or add the program's location to the path.

---

### Post by aas452 on 2009-02-22
Ok I see, downloader was a .tgz and I followed the instructions and downloaded it to /usr/local/Nuke5.1v3

The executable is called Nuke5.1, I tried to make a symbolic link to the /usr/bin directory but it looks like that doesn't work.

Any suggestions on how to get this running??

```

root@VOXEL:/usr/local/Nuke5.1v3# cp -s Nuke5.1 /usr/bin/
cp: `/usr/bin/Nuke5.1': can make relative symbolic links only in current directory

```

---

### Post by mcduck on 2009-02-22
Try this:
```

sudo ln -s /usr/local/Nuke5.1v3/Nuke5.1 /usr/local/bin/Nuke5.1
```

(linking into /usr/bin should work just as well, but since it's locally installed program I'd personally rather link it into /usr/local/bin)

---

### Post by aas452 on 2009-02-22
Looks like that did it. Thanks a million, I need to read up on sudo and ln, still very new to linux command line, do you suggest any books??

---

### Post by mcduck on 2009-02-22
No problem, great that you got it working.

I can't really recommend any books as I haven't read any, I've just learned everything by reading the man pages and these forums and searching with Google when ever I had some problem I had to solve.. ;)

(of course that was a bit easier for me since I started using computers in the days before graphical user interfaces so CLI, text based configuration files and reading manual pages felt more like returning to home after the years I wasted with Windows :D )

If you ask me these forums are a great place for learning about Linux. You can get a pretty good answer for almost any question either by asking here or by searching from the forums Also trying to help others here whenever you can provides endless opportunities for learn new things as well. Quite often other people come up  with solutions and ideas you didn't even know about. :)

Somebody else will probably be able to recommend good Linux books. But If I have to suggest something, try to get as generic Linux/Unix book as possible, The ones talking about specific distributions/versions tend to get outdated pretty fast (often Linux distributions have already moved to next version even before the book gets out of the print) while any book talking about Unix/Linux in general should be useful no matter if it's 10 years old or was released yesterday.

---

