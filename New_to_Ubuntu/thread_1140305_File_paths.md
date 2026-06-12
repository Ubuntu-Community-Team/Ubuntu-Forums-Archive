---
title: "File paths"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by newport_j on 2009-04-27
If this is absolute beginner talk then i am in the right place. I want ask a questions about paths. I am using Ubuntu 8.04. I am going to do an install and I want to direct some install files into a new directory.
 
First, when someone types cd usr, the dir changes to usr if is in the next directory (seen when you ls). If it is not then some (not all ) directories can be reached by typing something like /usr/. Why is this different? You cannot do this all of the time on any directory-just some.
 
Does a directory have to exist before you move to it - can it be created when you move 
 
Also in Linux what does typing usr/ as opposed to /usr/ mean anything?
 
What are the rules for Linux file paths?
 
Not all Linux books go into this in detail.
 
I am askng because I am going to do a tricky install and which moves files to a different directory that what the installer would automatically put them in. I need to define the new paths and I need to know this before I mess up my file system by doing something that is irreversible.
 
Respectfully,
 
Newport_j

---

### Post by _Purple_ on 2009-04-27
In Linux, root directory where the filesystem begins is denoted by /. All the directories as subdirectories of /. You can go to any directory either by using the absolute path which starts from / or by using a relative path from the current directory. For example, if you are in the usr directory, you can go to /usr/bin by typing either the absolute path 
```
cd /urs/bin
```

or the relative path
```
cd bin
```

The following command will take you to the immediate parent directory 
```
cd ..
```

cd will change directory but will not create directory. The command to make directory is mkdir. 
The command below will create a directory named files in your current directory.
```
mkdir files
```

This command below will show you the directory you are in.
```
pwd
```

---

### Post by kanikilu on 2009-04-27
I think there are much more detailed guides out there (check out the [Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/")), but I'll try to briefly answer your questions...

When you use cd, the path you give it can be put one of two ways, relative and absolute.

When you type **cd example/**, you are saying, change to the directory called *example*, relative to the current working directory (use **pwd** to print the working directory).

So, say your working directory is **/home/username**, when you type **cd example/** what you are really saying is **cd /home/username/example** ("translated" to an absolute path), so if that directory doesn't exist, it will fail.

Another type of relative path you might see is **cd ../example**, basically this is shorthand for change directory by going to the directory *example* one level up from here. So using the same current working directory as before, this translates to **cd /home/example**. You can combine as many "../" together to go up as many directories as you want.

This also answers one of your other questions: no, you cannot cd to a directory that doesn't exist. You can combine the two commands, but that's about it, e.g. ```
mkdir directory; cd directory
```

You asked what the difference between usr/ and /usr/ is. The first is a relative path, so cd is expecting the directory to exist in your current directory. The second is an absolute path from the root (/).

Ok, maybe not so brief... ;)

Some other useful sites:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[http://www.basicconfig.com/linux/filesystem](http://www.basicconfig.com/linux/filesystem)

---

