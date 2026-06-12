---
title: "PLEASE HELP!! Unable to follow installation instructions for PTAM on ubuntu"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by kemiga on 2011-03-03
Hi all,

I started using ubuntu in October when I started a conversion masters in computer science. So basically all I can do is write and compile C and Java programs.

For the final part of my course I have to use a program called PTAM (Parallel Tracking and Mapping). I'm the only one doing a project that involves this on my course so I can't turn to coursemates for help! However, I'm so bad with linux that I can't even follow these instructions. I don't know how to do makefiles or use ./configure or install libraries so I'd be super grateful if anyone could read these instructions and explain them to me in children's language!

Here's the link: [http://www.robots.ox.ac.uk/~gk/PTAM/README.txt]("http://www.robots.ox.ac.uk/%7Egk/PTAM/README.txt")

Thank you for reading :)

---

### Post by treesurf on 2011-03-03
I actually know very little about compiling, but those libraries should be easily install with the command 

```
sudo apt-get update
sudo apt-get install LIBRARYNAME
```


You only need to do the apt-get update once, as it just makes sure that all of the package lists are up to date.  :)

EDIT:  Here's an great how to on compiling:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by mick8985 on 2011-03-03
The dependencies needed for PTAM aren't in the ubuntu repositories,
You need to fetch them from a source control system known as [CVS]("http://en.wikipedia.org/wiki/Concurrent_Versions_System")
Which you'll need to install, along with other tools you'll need to compile source code
```
sudo apt-get install cvs build-essential
```
Create a working directory and change to the directory you created
```

mkdir $HOME/Projects
cd $HOME/Projects

```

Get the dependencies from CVS
```
export CVS_RSH=ssh
cvs -z3 -d:pserver:anonymous@cvs.savannah.nongnu.org:/sources/toon co -D "Mon May 11 16:29:26 BST 2009" TooN
cvs -z3 -d:pserver:anonymous@cvs.savannah.nongnu.org:/sources/libcvd co -D "Mon May 11 16:29:26 BST 2009" libcvd
cvs -z3 -d:pserver:anonymous@cvs.savannah.nongnu.org:/sources/libcvd co -D "Mon May 11 16:29:26 BST 2009" gvars3
```

In your working directory you will now see (ls) three folders TooN, libcvd and gvars3, each containing the source code for dependencies you will need to compile and install.

However to compile those libraries you'll need to install their dependencies, which are available in the apt repositories

```
sudo apt-get install libblas-dev liblapack-dev libgfortran3 libncurses5-dev libreadline-dev libdc1394-22-dev libraw1394-dev libtiff4-dev libjpeg8-dev libpng12-dev
```

Now you need to compile TooN interestingly there is no need to make (compile) anything here. Just configure it and install it
```
cd TooN
./configure --prefix=/usr
sudo make install
cd ..
```

Next up it's libcvd
```
cd libcvd
export CXXFLAGS=-D_REENTRANT
./configure --prefix=/usr --without-ffmpeg
make
sudo make install
cd ..
```

and then onto the next one

```
cd gvars3/
./configure --disable-widgets
make
sudo make install
```

The rest is just installing PTAM whatever that is.

---

### Post by kemiga on 2011-03-04
Thank you so so much!! That's been a really big help, I was all over the place before!

Thanks again :)

---

