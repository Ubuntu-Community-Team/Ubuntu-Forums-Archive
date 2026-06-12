---
title: "completely new with .tgz"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by brucebruce on 2011-08-02
I just kinda started with linux about a week ago as i dual booted my pc with it just to mess around and blah blah blah, i came across a .tgz file as it is the only option i have for a game i want to play n ive done searches on how to extract them n then wat to do afterwards n such n i have gotten as far as extracting the file but then now not knowing wat to do....if anyone is really curious im trying to install "Tibia" on ubuntu 11.04 n i have tried the whole tar xvf(which ever it was) tibia910.tgz thing which never worked but i did just right lick n say extract here n it worked....after that im lost and nowhere can i figure this out so if someone could help me id appreciate it

---

### Post by nmaster on 2011-08-02
not much of a gamer, myself... are you refering to this?[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/RPG/Tibia-22257.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/RPG/Tibia-22257.shtml)

go into the folder where you extracted Tibia.  then just double click the file named 'Tibia'. the application started for me.

btw,  i guess you're used to either Mac OS X or MS Windows? try reading here to learn more about using Ubuntu:[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by brucebruce on 2011-08-02
yes thats the game i was talking about but i was trying to get it from tibia.com where the latest one is

---

### Post by nmaster on 2011-08-02
> **brucebruce said:**
> yes thats the game i was talking about but i was trying to get it from tibia.com where the latest one is

then give us a link to the tgz in question.  tgz is just a tar file that's been gzipped.  think of it like a zip file on windows.  as a result, it could have anything in it and there is not a one-size-fits-all solution to your problem.

---

### Post by brucebruce on 2011-08-02
[https://secure.tibia.com/account/?subtopic=downloadclient](https://secure.tibia.com/account/?subtopic=downloadclient)

thats where i got the download file from

---

### Post by brucebruce on 2011-08-02
> **nmaster said:**
> not much of a gamer, myself... are you refering to this?[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/RPG/Tibia-22257.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/RPG/Tibia-22257.shtml)

go into the folder where you extracted Tibia.  then just double click the file named 'Tibia'. the application started for me.

btw,  i guess you're used to either Mac OS X or MS Windows? try reading here to learn more about using Ubuntu:[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

i did this with the file u showed me n the one i had before n literally nothing happens after i double click it. n i am used to windows but i have done a lot of cmd work but this is still something entirely different n new to me

---

### Post by kaldor on 2011-08-02
> **brucebruce said:**
> [https://secure.tibia.com/account/?subtopic=downloadclient](https://secure.tibia.com/account/?subtopic=downloadclient)

thats where i got the download file from

I saved "tibia910.tgz" to my desktop. I then right-clicked on it and pressed "Extract Here". It created a "Tibia" folder, so I opened that up. There was a file inside called "Tibia" and double-clicking it opened it for me. Check my attachment.

---

### Post by brucebruce on 2011-08-02
> **kaldor said:**
> I saved "tibia910.tgz" to my desktop. I then right-clicked on it and pressed "Extract Here". It created a "Tibia" folder, so I opened that up. There was a file inside called "Tibia" and double-clicking it opened it for me. Check my attachment.

could there be something certain that i need inorder to run it cuz everytime i double click i just get nothing

---

### Post by garvinrick4 on 2011-08-02
# 1: Uncompress tarball

To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/

# 2: Build and install software

Generally you need to type 3 commands as follows for building and compiling software:
# ./configure
# make
# make install

Where,

    ./configure will configure the software to ensure your system has the necessary functionality and libraries to successfully compile the package
    make will compile all the source files into executable binaries.
    Finally, make install will install the binaries and any supporting files into the appropriate locations.

# 3: Read INSTALL / README file

Each tarball comes with installation and build instructions. Open INSTALL or README file for more information:
$ nano INSTALL
or open INSTALL or README file with gedit in GUI

---

### Post by cbennett926 on 2011-08-02
Ok, this isn't a solution but I really wanna know this and it's related. What is a .tgz file?

---

### Post by brucebruce on 2011-08-02
i can get it extract its just that the executable file is not playing at all...this just sucks

---

### Post by brucebruce on 2011-08-02
i just installed wine n it worked...but still shouldnt it have worked without it considering i did download the linux version?

---

### Post by garvinrick4 on 2011-08-02
> **cbennett926 said:**
> Ok, this isn't a solution but I really wanna know this and it's related. What is a .tgz file?
Just a different tarball that needs extracting. There are also .zip  that you just use:
unzip (name .zip file) :do not need to use tar in otherwords just unzip to extract.

#A *.tgz file is a gnu-zipped .tar file.

---

### Post by garvinrick4 on 2011-08-02
rick@rick-HP:~$ sudo -i
[sudo] password for rick: 
root@rick-HP:~# 

Always check in instructions if you are giving code from $ or from #
Or using "sudo" command from $

---

### Post by nmaster on 2011-08-03
> **cbennett926 said:**
> Ok, this isn't a solution but I really wanna know this and it's related. What is a .tgz file?

if you "really" want to know, then read the thread more carefully.  i already tried to explain to the OP:
[QUOTE=nmaster] tgz is just a tar file that's been gzipped.  think of it like a zip file on windows.[/QUOTE]

after reading what i posted, it would then make sense to skim the wikipedia page:
[http://en.wikipedia.org/wiki/Tar_%28file_format%29](http://en.wikipedia.org/wiki/Tar_%28file_format%29)

happy learning :)

---

### Post by nmaster on 2011-08-03
> **brucebruce said:**
> i did this with the file u showed me n the one i had before n literally nothing happens after i double click it. n i am used to windows but i have done a lot of cmd work but this is still something entirely different n new to me

if you try running the program from the command line, you may see an error message that explains what is going on.  it could simply be that the binary is not executable. try this and post any output:
```

cd /to/the/directory/where/you/extracted/Tibia
chmod +x Tibia
./Tibia

```

---

