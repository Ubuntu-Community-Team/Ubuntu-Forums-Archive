---
title: "Typing Paths out to run a process"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by smiller85 on 2011-06-22
Hey

I am currently using a program in my directory of ~/blast/bin.  The program is called usearch4.  Usually I type cd ~/blast/bin to go to the directory where usearch4 and the other files I need are located.  However, when I go to run the program I still have to type ~/blast/bin/usearch4 to have the program run.  I am lazy and would like to just type usearch4 and the rest of the commands to run the file.  Is there a way to start the program without having to type the whole path every time?  Or is there like an alias I can make somehow?

Thanks

---

### Post by Mr Stoozer on 2011-06-22
```
cd ~/blast/bin
```

```
./usearch4
```

Should do the trick. For the super lazy, after "./u" hit tab to auto-complete.

---

### Post by GWBouge on 2011-06-22
> **smiller85 said:**
> Or is there like an alias I can make somehow?

There's this: [http://brockangelo.com/2009/05/30/my-top-10-ubuntu-aliases/]("http://brockangelo.com/2009/05/30/my-top-10-ubuntu-aliases/")
Or you can make a small script in /usr/local/bin (one of the places Ubuntu looks for executables).

```
cd /usr/local/bin
sudo gedit usearch4
```

Add in the following:

```
#!/bin/bash
/home/<your_user_name>/blast/bin/usearch4
```

Save it, and make it executable:

```
sudo chmod +x usearch4
```

Now you should be able to just call 'usearch4' from any directory.

---

### Post by Mr Stoozer on 2011-06-23
> **GWBouge said:**
> There's this: [http://brockangelo.com/2009/05/30/my-top-10-ubuntu-aliases/]("http://brockangelo.com/2009/05/30/my-top-10-ubuntu-aliases/")
Or you can make a small script in /usr/local/bin (one of the places Ubuntu looks for executables).

```
cd /usr/local/bin
**sudo gedit** usearch4
```

Add in the following:

```
#!/bin/bash
/home/<your_user_name>/blast/bin/usearch4
```

Save it, and make it executable:

```
sudo chmod +x usearch4
```

Now you should be able to just call 'usearch4' from any directory.

You should use gksu for gedit. Not sudo.

---

### Post by Neoncamouflage on 2011-06-23
I did this not ten minutes ago myself, adding two directories to the path so I just have to type the name of python and shell scripts to get them to run.

All you have to do is go into .profile, or .bashrc, or .bash_aliases, or anywhere else in the current path really, I use .bash_aliases for all my customizing to keep it organized.

Simply type in:
```
PATH=$PATH:~/blast/bin
```
Now every executable script that you place in ~/blast/bin will be able to be run simply by typing in the name, as it will now be included in the path your system searches for commands you type in. Note that this is run on startup, so to get it to take effect now simply type it into the terminal.

---

### Post by dcsoldschool53 on 2011-06-24
In a terminal, type```
PATH=$PATH:~/blast/bin
```Hit the ENTER key. Then, type```
export PATH
```Now type```
usearch4
```or any script name within the bin folder.

---

