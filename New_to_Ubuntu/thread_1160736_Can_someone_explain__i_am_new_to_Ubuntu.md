---
title: "Can someone explain ? i am new to Ubuntu"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by aravindc26 on 2009-05-15
can some one tell what what are the setup files in ubuntu.........
like .exe,.msi in windows......
this question might look dum .......
pls explain

---

### Post by radiocognition on 2009-05-15
welcome to Ubuntu,

Unlike windows, everything that comes with Ubuntu is extremely configurable.  I am not exactly sure what you mean by "setup file" but I can give you a brief overview of where important files are stored.

/bin ,   /usr/bin   , /usr/local/bin                     
each of these directories contain compiled programs (kinda like exe's )

/etc                               
contains most of the system wide configuration files

/home/username     
your home directory where all of your personal files and configurations are stored.

If you clarify your question I may be able to be more helpful.  If you just want to learn a little more about linux, let me recommend this excellent tutorial : [http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by kostkon on 2009-05-15
First of all, I would like to recommend you to check [this nice guide]("http://www.psychocats.net/ubuntu/installingsoftware") on how to install software in Ubuntu.

Nevertheless, to answer your question, the setup files in Ubuntu are files with a .deb extension

---

### Post by uupreti on 2009-05-15
> **aravindc26 said:**
> can some one tell what what are the setup files in ubuntu.........
like .exe,.msi in windows......
this question might look dum .......
pls explain

Other distros of linux like centos, redhat, Suse use .RPM file as a setup file but Debian and Ubuntu use .deb (Debian package) as a setup file. That's equivalent to .exe, .msi in MS windows environment. 

And there are lot's of package manager like dpkg, apt-get, aptitude , synaptic ( GUI package manager ) to install .deb files.

I hope you got basic idea...

---

### Post by zeroseven0183 on 2009-05-15
Check out the [Free Beginners Guide]("http://ubuntuforums.org/showthread.php?t=1052065") and download the [Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/") for the basics.

Quoting from Ubuntu Pocket Guide
> Generally speaking, the trend with Linux is not to use file extensions for system files. Executable programs under Ubuntu don&#8217;t have a file extension, such as .exe, as with Windows. Instead, the fact they are programs and not ordinary data files is indicated by the use of the executable file attribute.

---

### Post by aravindc26 on 2009-05-15
> **kostkon said:**
> First of all, I would like to recommend you to check [this nice guide]("http://www.psychocats.net/ubuntu/installingsoftware") on how to install software in Ubuntu.

Nevertheless, to answer your question, the setup files in Ubuntu are files with a .deb extension

thanx .........
i got some bit of knowledge now.....
...
one more question what do you mean by resporatories.....
and
lately i downloaded a realplayer installation file in .bin format, is there any graphical method to install .bin files without using terminal......
where can i get terminal tutorials.........

---

### Post by aravindc26 on 2009-05-15
> **radiocognition said:**
> welcome to Ubuntu,

Unlike windows, everything that comes with Ubuntu is extremely configurable.  I am not exactly sure what you mean by "setup file" but I can give you a brief overview of where important files are stored.

/bin ,   /usr/bin   , /usr/local/bin                     
each of these directories contain compiled programs (kinda like exe's )

/etc                               
contains most of the system wide configuration files

/home/username     
your home directory where all of your personal files and configurations are stored.

If you clarify your question I may be able to be more helpful.  If you just want to learn a little more about linux, let me recommend this excellent tutorial : [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

thanks buddy for the tutorial

---

### Post by radiocognition on 2009-05-15
With a windows machine, you have to troll around the internet to find a program that you want to install.  With linux machines, since all of the programs are free and open source, the compiled programs and the source code are hosted on big servers that are maintained by a team of volunteers.

The list of available packages (programs) available on a given server is a repository.  The advantage of this is that it makes installation and updates super easy.  All of the programs are installed from the same interface ( in the case of Ubuntu, the Add Remove program ) and are updated automatically when any bugs are patched.  There are lots of ways of installing new packages and adding new repositories - but for now you probably want to work in a GUI rather than a terminal.  If you want to see some of the more technical bits of your system you can try the synaptic package manager until you feel comfortable going into a terminal and editing the configurations manually (this is how I prefer to do it).

---

### Post by uupreti on 2009-05-16
> **aravindc26 said:**
> thanx .........
i got some bit of knowledge now.....
...
one more question what do you mean by resporatories.....
and
lately i downloaded a realplayer installation file in .bin format, is there any graphical method to install .bin files without using terminal......
where can i get terminal tutorials.........


By default ubuntu package managers will look at .deb file and dependcies for that file. If you downloaed .bin file for ubuntu and it's named **abc.bin** then try this. I am not sure if there is any GUI who can install .bin file..

1. **sudo chmod +x abc.bin** (this will make file executable)
2. .**/abc.bin** (Assume you are using command from same location where file is. Otherwise give full path of file)

---

