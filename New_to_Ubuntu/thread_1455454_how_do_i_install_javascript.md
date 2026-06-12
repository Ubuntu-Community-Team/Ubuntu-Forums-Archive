---
title: "how do i install javascript?"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by purdurabo on 2010-04-16
ok now i am trying to install javascript. i got it downloaded and got the file unpacked.
i have been following the insrtuctions on the java site. i made it all the way to the end where it said that i have to create a symbolic link tho the file libjavaplugin.so.

i use the code examples that they gave and this is what i got:

```
ln -s /usr/allen/Downloads/jre1.6.0/plugin/i386/ns7/libjavaplugin_oji.so
ln: creating symbolic link `./libjavaplugin_oji.so': File exists
```

so seeing that i figured that it worked, right? the next step is to type "about:plugins" into the address bar to firefox to insure that everything worked. well java is not listed when i look at my plugins. can some one please tell me what went wrong????

---

### Post by ad_267 on 2010-04-16
You want the Java plugin, not javascript. They're two completely different things.

In Ubuntu you install stuff from the package manager, rather than downloading things from websites. Just go to Applications - Ubuntu Software Centre and search for "Java Plugin" and install the package called "Sun Java 6.0 Plugin".

Or in a terminal you could do:
```
sudo apt-get install sun-java6-plugin
```

---

### Post by Didius Falco on 2010-04-16
> **purdurabo said:**
> ok now i am trying to install javascript. i got it downloaded and got the file unpacked.
i have been following the insrtuctions on the java site. i made it all the way to the end where it said that i have to create a symbolic link tho the file libjavaplugin.so.

i use the code examples that they gave and this is what i got:

```
ln -s /usr/allen/Downloads/jre1.6.0/plugin/i386/ns7/libjavaplugin_oji.so
ln: creating symbolic link `./libjavaplugin_oji.so': File exists
```so seeing that i figured that it worked, right? the next step is to type "about:plugins" into the address bar to firefox to insure that everything worked. well java is not listed when i look at my plugins. can some one please tell me what went wrong????

Were you in the path/to/firefox/plugins directory when you ran that command?

If not, run the command in the /plugins directory where your Firefox is installed.

It's hard to make suggestions for a fix because you don't give much info about what steps you've taken, or even a link to the directions you are following at the Sun Java site.

Just out of curiosity, is there some reason you are doing it this way rather than using the repository to do so?

Regards,

Didius

---

### Post by purdurabo on 2010-04-16
here is the link to the site i was following. like i said i made it all the way to the end. and by the way, none of the files are in the mozilla directory they are still in my Downloads directory, if that makes any difference.

[http://www.java.com/en/download/help/linux_install.xml#selfextracting](http://www.java.com/en/download/help/linux_install.xml#selfextracting)

also, i am trying to get the java ide so that i can do this biginning programing tutorial that i found on the web

[http://www.alan-g.me.uk/tutor/index.htm](http://www.alan-g.me.uk/tutor/index.htm)

---

### Post by eginon on 2010-04-16
Hi,

You know after looking at that tutorial you are trying to work on, unless you heart is totally set on doing that particular one, I'm going to suggest that instead you work through the* How to Think Like A Computer Scientist* recommendation. Also, Dive Into Python (link below) is a great free introduction to the Python programming language. I suggest this only because it seems as if you're new to the world of programming,and if so, trying to get your head around a discussion about three different languages when you're not even comfortable in one language is just asking for headaches.

Link to Dive In:
[http://diveintopython.org/toc/index.html](http://diveintopython.org/toc/index.html)

---

### Post by Didius Falco on 2010-04-16
> **purdurabo said:**
> here is the link to the site i was following. like i said i made it all the way to the end. and by the way, none of the files are in the mozilla directory they are still in my Downloads directory, if that makes any difference.

[http://www.java.com/en/download/help/linux_install.xml#selfextracting](http://www.java.com/en/download/help/linux_install.xml#selfextracting)

also, i am trying to get the java ide so that i can do this biginning programing tutorial that i found on the web

[http://www.alan-g.me.uk/tutor/index.htm](http://www.alan-g.me.uk/tutor/index.htm)

Okay, in step 3 of the installation instructions, what directory did you change to?

> **Change to the  directory in which you want to install.** Type:
    cd <directory path name>
    For example, to install the software in the /usr/java/ directory,  Type:
    cd /usr/java/

---

### Post by trig on 2010-04-16
Open the package manager, it should be in there.

---

### Post by 3rdalbum on 2010-04-16
Welcome to Ubuntu.

One of the differences between Linux and other popular operating systems is that Linux distributions have vast "software repositories" that contain a lot of software that you can browse and install using your "Package manager". This is easier than trawling the internet and downloading and installing software from there. Also, when you install from the package manager, the software will keep up-to-date with security patches.

Ubuntu has a package manager, and its repositories contain Java. You might need to go to System > Administration > Software Sources and go to the Third Party tab, and explicitly tick the "partner" repository first. Close the window; you will be asked if you want to reload the package list. You do.

Now go to Applications > Ubuntu Software Center (this is a package manager) and you can search for and install Java from there. It will keep up-to-date with any security patches too.

If you want to develop with Java, you need the "JDK" package (Java Development Kit), but if you just want to look at Java applications then the "JRE" (Java Runtime Environment) package will suffice.

**Wherever possible, use your package manager. IT WILL MAKE THINGS EASIER FOR YOU.**

---

### Post by purdurabo on 2010-04-16
i was looking for the java ide in the package manager. so the jke and jdk is what i need.also i did get the java runtime and plugin.thanks guys. if i have any more questions i will post them here.

update i dont see jde or the jdk in the package manager.there is one called openjdk java 6 runtime. is that the same thing. the discription says that it is for executing java gui programs.

---

### Post by lovinglinux on 2010-04-16
[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by purdurabo on 2010-04-17
i feel dumb asking this question but i have to. when i list the file in the terminal (gnome terminal) like with

```
ls -a  
```

and some of them are in different colors. what do the colors mean?

---

### Post by nathan726 on 2010-04-17
> **purdurabo said:**
> what do the colors mean?

Usually directories are blue, compressed files and archives are red, executables are green, symlinks are light blue, sockets are pink and special devices are yellow.
 
 Although the colors can differ depending on how you set them (you can run 'man dircolors' in the terminal for more info).

---

### Post by 3rdalbum on 2010-04-17
> **purdurabo said:**
> i was looking for the java ide in the package manager. so the jke and jdk is what i need.also i did get the java runtime and plugin.thanks guys. if i have any more questions i will post them here.

update i dont see jde or the jdk in the package manager.there is one called openjdk java 6 runtime. is that the same thing. the discription says that it is for executing java gui programs.

The packages should be called "sun-java6-jre" and "sun-java6-jdk". They are in the Partner repository, which you need to activate from the System > Administration > Software Sources program. Go to the Third Party Software tab and you'll find that it's the first item in the list. Click the little checkbox to the left of it and close the program; you'll be asked if you want to reload the package list. Click Reload.

Now you'll be able to find the packages.

---

