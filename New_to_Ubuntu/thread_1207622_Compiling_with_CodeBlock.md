---
title: "Compiling with Code::Block"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by sevic33 on 2009-07-08
I have install Code Block on Ubuntu 9.04,when i try to build and run the code ,console pop up and it said Permission Denied.
What could be the problem?

---

### Post by DGortze380 on 2009-07-08
> **sevic33 said:**
> I have install Code Block on Ubuntu 9.04,when i try to build and run the code ,console pop up and it said Permission Denied.
What could be the problem?

What else does it say?
Where are you saving your source files? You're just having permissions issues.

---

### Post by carml on 2009-07-08
Are you sure you installed the package build-essential?
Go to Applications->Accessories->Terminal and type "sudo apt-get install build essential" (without quotes)
and post here the result

---

### Post by sevic33 on 2009-07-08
I save it on Desktop and its said: 

```
sh: /home/m/Desktop/Untitled1: Permission denied

Press ENTER to continue
```

---

### Post by carml on 2009-07-08
> **sevic33 said:**
> I save it on Desktop and its said: 

```
sh: /home/m/Desktop/Untitled1: Permission denied

Press ENTER to continue
```

Please,can you explain better what you did?

---

### Post by sevic33 on 2009-07-08
> **carml said:**
> Are you sure you installed the package build-essential?
Go to Applications->Accessories->Terminal and type "sudo apt-get install build essential" (without quotes)
and post here the result
```

m@m-laptop:~$ sudo apt-get install build essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build

```

---

### Post by DGortze380 on 2009-07-08
> **sevic33 said:**
> ```

m@m-laptop:~$ sudo apt-get install build essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build

```

build-essential

not build essential

You do need it, so lets check, but I don't think that's your current problem.

---

### Post by sevic33 on 2009-07-08
> **carml said:**
> Please,can you explain better what you did?

1.First i run Code Block GUI
2.File>New>Empty File
3.i write my C code
4.I click on "Build and run" icon
5.chose to save file on Desktop
6.I got massage what i write you above

---

### Post by carml on 2009-07-08
> **DGortze380 said:**
> build-essential

not build essential

You do need it, so lets check, but I don't think that's your current problem.

My mistake,I forgot the - .
You need that package if you want to compile something :)

---

### Post by sevic33 on 2009-07-08
ok,i instal build-essenital package but still have the same problem

---

### Post by carml on 2009-07-08
Are you sure you have to use necessarly Code Block? There are other compilers avaible.
The message you've seen it's werid,it's like you don't have permission to use the software. :( :confused:

---

### Post by DGortze380 on 2009-07-08
> **carml said:**
> Are you sure you have to use necessarly Code Block? There are other compilers avaible.
The message you've seen it's werid,it's like you don't have permission to use the software. :( :confused:

No, not at all... Codes::Blocks is an IDE, not a compiler. The compiler is gcc.
The message has nothing to do with the software, it's a file system permissions error.
Please, if you don't have accurate advice, don't give any. And, 'don't use the software' is not a solution.

He doesn't have permission to access the source file/directory.



Please post the output of 

```

ls -al /home/m/Desktop

```

and

```

ls -al /home/m/Desktop/Untitled1

```

---

### Post by carml on 2009-07-08
@ DGortze380 I'm still relately new to Linux,so I lack a lot of knowledge,
it's the first time I see someone someway unable to access his home tree of directories.

---

### Post by DGortze380 on 2009-07-08
Problem Duplicated...


I don't know why, but Code::Blocks is saving your source file with incorrect permissions. I'll have to look at how to fix it permanently, but for now try the following.

```

chmod 777 /home/m/Desktop/Untitled1

```

then in Code::Blocks click Build -> Run

You'll have to do this each time you save the file until we find a permanent solution.

---

### Post by sevic33 on 2009-07-08
```
m@m-laptop:~$ ls -al /home/m/Desktop
total 48
drwxr-xr-x  3 m m 4096 2009-07-08 18:31 .
drwxr-xr-x 56 m m 4096 2009-07-08 18:31 ..
drwxr-xr-x  3 m m 4096 2009-07-02 16:06 apps
-rw-r--r--  1 m m 6626 2009-07-07 01:53 chronic
-rw-r--r--  1 m m   25 2009-07-08 00:50 ez acc
-rw-r--r--  1 m m   47 2009-07-07 03:29 ez acc~
-rwxr-xr-x  1 m m  406 2009-07-02 02:52 gnome-nettool.desktop
-rwxr-xr-x  1 m m  474 2009-07-02 02:52 gnome-terminal.desktop
-rwxr-xr-x  1 m m  483 2009-07-02 02:56 nautilus-computer.desktop
-rw-r--r--  1 m m    0 2009-07-02 20:22 pass~
-rw-r--r--  1 m m 1740 2009-07-08 00:46 Ububtu tips
-rw-r--r--  1 m m    0 2009-07-07 22:51 Ububtu tips~
-rw-r--r--  1 m m  679 2009-07-08 18:31 Untitled1
m@m-laptop:~$ ls -al /home/m/Desktop/Untitled1
-rw-r--r-- 1 m m 679 2009-07-08 18:31 /home/m/Desktop/Untitled1
m@m-laptop:~$ 

```

---

### Post by sevic33 on 2009-07-08
tnx for help DGortze380,i hope you will fix it soon :)

---

### Post by DGortze380 on 2009-07-08
You should just need to change the extension on the source file.

Change "Untitled1" to "Hello.cpp" or "Hello.c" depending on which language you're using. Should compile fine after that. Seems that Code::Blocks depends on the extension for setting permissions??

---

