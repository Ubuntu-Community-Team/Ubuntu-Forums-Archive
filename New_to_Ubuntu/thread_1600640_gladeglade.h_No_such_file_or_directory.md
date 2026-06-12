---
title: "glade/glade.h No such file or directory"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by a.sarkar on 2010-10-19
My system is ubuntu lucid.
I am trying to compile some c program with gtk+glade with the command

```
gcc -Wall -g -o program program.c `pkg-config --cflags --libs gtk+-2.0`
```However, its gives me the following error
```

error: glade/glade.h: No such file or directory

```I already have libglade2-dev installed. I also have the glade.h file in
```
/usr/include/libglade-2.0/glade/glade.h
```Am I missing something?

---

### Post by Hippytaff on 2010-10-19
Just a punt, I know nothing about C++ but is glade.h executable
 
```

sudo chmod a+x /usr/include/libglade-2.0/glade/glade.h

```
 
I might be way off the mark...so sorry in advance if I'm barking up the wrong tree

---

### Post by SuaSwe on 2010-10-19
Also possibly totally off the mark: what are the permissions of glade.h and the directory in which it resides?

---

### Post by a.sarkar on 2010-10-19
@Hippytaff: Thanks for your answer, but that didn't help. So I switched back to non executable mode.

@SuaSwe: The permission of my glade directory and glade.h are 

```

drwxr-xr-x 2 root root 4.0K .... glade
-rw-r--r-- 1 root root 1.2K .... glade.h

```Still cannot compile the program :(.

---

### Post by SuaSwe on 2010-10-20
Are you running it as root? Maybe try chowning the files to your own username? Can't think of any other reason for a file to read as non-existent when it's plainly there, unless bash is looking in the wrong place altogether. :/

---

### Post by a.sarkar on 2010-10-20
@SuaSwe: I am running the program as a normal user. I don't want to chown them to my username, since there are other user accounts to the same computer. Maybe as you said bash is looking for them in the wrong place after all.

I tried 
```
export CFLAGS="-I/usr/include/libglade-2.0/glade/"
```before I compiled. It didn't work.

Then I tried 
```
cd /usr/include
sudo ln -s libglade-2.0/glade .

```That produced new set of errors. 
```
/tmp/ccyYxGUu.o: In function `main':
progressbar.c:(.text+0xa4): undefined reference to `glade_xml_new'
progressbar.c:(.text+0xbc): undefined reference to `glade_xml_get_widget'
progressbar.c:(.text+0x11a): undefined reference to `glade_xml_get_widget'
collect2: ld returned 1 exit status
```So I guess that it actually couldn't find the header file after all. But my problem is still not solved. :(

---

### Post by SuaSwe on 2010-10-20
Can you run the command as sudo, then? I'm guessing if you're not running it as root and the file is not owned by you, there is a chance that the script is not able to use it? Not sure beyond that though as I'm not familiar with C! 

Anyone else got any suggestions? :D

---

### Post by a.sarkar on 2010-10-21
I think I solved it. Running the following command compiles the program.c

```
gcc -Wall -g program.c -o program  `pkg-config gtk+-2.0 --cflags --libs` -I/usr/include/libglade-2.0/ -lglade-2.0
```

---

