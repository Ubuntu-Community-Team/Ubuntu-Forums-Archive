---
title: "HELP! How to install software in Ubuntu 9.10?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by archangelos14 on 2010-02-09
hello! i'm a newbie in using linux. I just tried it out of curiosity. I downloaded Ubuntu 9.10 and successfully installed it in my pc. now the problem is, don't know what to do with the softwares i downloaded from the net like amarok, wine, etch. files downloaded have extension name .tar. pls help. tnx!

---

### Post by barkej on 2010-02-09
First. Welcome to the crazy house. LOL. JK.

If you go to your Applications Menu You should have an option for Ubuntu software center. If you cant find what you want there check System > Administration > Synaptic.

If you plan on playing mp3's watching avi's and using flash I suggest you get the ubuntu-restricted-extras pakage. It should be in synaptic or you can open terminal and type this
```
sudo apt-get update
```
then
```
sudo apt-get install ubuntu-restricted-extras
```

I hope this helps some.

Again welcome to the forums.
:D

---

### Post by albert s on 2010-02-09
I would say first things first,
dont download stuff for the sake of it,
download programs cos you need/or want them.
I usually only download stuff when I go to do something and it dont work/says I need such and such dependencies

---

### Post by barkej on 2010-02-09
I almost forgot. You can also use the .tar stuff, you will normally have to compile it first though.

There are several threads here on compiling software just do a quick search. :)

---

### Post by albert s on 2010-02-09
yep.
go
system
admin
update

usually gets you most stuff
then it comes in bit by bit as you need it,
Im all new to this too,  :D

---

### Post by barkej on 2010-02-09
> **albert s said:**
> I would say first things first,
dont download stuff for the sake of it,
download programs cos you need/or want them.
I usually only download stuff when I go to do something and it dont work/says I need such and such dependencies

I couldn't agree more. ubuntu-restricted-extras is about the only thing I grab on a clean install. After that I just download programs as I see a need / dependency.

---

### Post by Revolutionary101 on 2010-02-09
These two tips may help you

1. You must likely don't need to download applications via your internet browser. It is a lot easier to install them via Synaptic Package Manager (System>Administration>Synaptic Package Manager) or the Ubuntu Software Center (Applications>Ubuntu Software Center). Just select a software package and it will automatically install it for you.

2. To install the .tar.whatever do this:
   I. Extract the .tar.whatever file to the folder of your choosing.
   II. Open Terminal from Applications>Accessories>Terminal
   III. Set Terminal to the location of the application by doing this
   ```
cd /path/of/extracted/files
```
   IV. After the path is set enter this into terminal
   ```
./compile
```
This will compile the program for installation
   V. Then type this
   ```
make
```
This will make the applications ready for installation
   VI. Finally type this
   ```
sudo make install
```

That should do it. I hope it helps.

---

### Post by albert s on 2010-02-09
> **barkej said:**
> I couldn't agree more. ubuntu-restricted-extras is about the only thing I grab on a clean install. After that I just download programs as I see a need / dependency.


yes, the restricted extras thing, gets your music and videos going a bit simplier,
you will still have to download some stuff though, 
but as I said, just let ubuntu do it as it needs to.
dont worry about getting everything all at once, its a totally different experience to some other OS, s.

---

### Post by barkej on 2010-02-09
> **archangelos14 said:**
> hello! i'm a newbie in using linux. I just tried it out of curiosity. I downloaded Ubuntu 9.10 and successfully installed it in my pc. now the problem is, don't know what to do with the softwares i downloaded from the net like amarok, wine, etch. files downloaded have extension name .tar. pls help. tnx!

You might also check this [guide]("http://www.ubuntupocketguide.com/download_main.html") out.

---

### Post by albert s on 2010-02-09
not having a go at revolutionary,
but do you really need to be running tar programs just yet.?
just try using synaptics etc for the time being and see if you get the progs you want.

---

### Post by albert s on 2010-02-09
> **barkej said:**
> You might also check this [guide]("http://www.ubuntupocketguide.com/download_main.html") out.


+1

best guide for me anyhow,
and Im lazy and only use the gui if I can,
and to be honest, in past 3months or so of 9.10 I think used a terminal about <dozen times, 
ubuntu is just getting so much easier for point and click people like me.  :D 
sorry to upset the hard core, I just want to do what I want to do, no fancy stuff.

---

### Post by archangelos14 on 2010-02-09
tried the synaptic package manager but can't find amarok, vlc player and wine. so i decided to download them. but the files i downloaded have .tar extensions. anyways, tnx so much for the replies. gonna try the suggested work around later. hope it works. :)

---

### Post by archangelos14 on 2010-02-09
@barkej: sudo apt-get update doesn't work. proxy authentication required. i guess because i connect to the internet via proxy. pls help. tnx so much...

---

### Post by nhasian on 2010-02-10
okay first of all, forget about compiling software for the time being.  that is more advanced and not necessary for what you are asking to do.

First go to System->Administration->Software Sources.  Make sure the boxes are ticked for:

Canonical-supported Open Source software (main)
Community-maintained Open Source software (universe)
Proprietary drivers for devices (restricted)
Software restricted by copyright or legal issues (multiverse)

after all those are checked, then close the software sources, and go to System->Administration->Update manager.  Check for, then install any updates.  you may need to reboot.


Now Go to Applications->Ubuntu Software Center

VLC is in there!
Amarok is in there!
Wine is in there!

it is easy to install and uninstall programs with the ubuntu software center.  other ways to install software is with .deb files, PPAs, and tar.gz source files being the most difficult to install and most likely you will never need to compile anything.

> **archangelos14 said:**
> tried the synaptic package manager but can't find amarok, vlc player and wine. so i decided to download them. but the files i downloaded have .tar extensions. anyways, tnx so much for the replies. gonna try the suggested work around later. hope it works. :)

---

### Post by Cheesemill on 2010-02-10
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by 3rdalbum on 2010-02-10
> **archangelos14 said:**
> @barkej: sudo apt-get update doesn't work. proxy authentication required. i guess because i connect to the internet via proxy. pls help. tnx so much...

Go into System > Administration > Synaptic Package Manager. Under one of the menus you can set your proxy.

Once you've set that up, hit the Reload button in the main window. You can now do a 'find' for those programs and then mark them for installation.

Don't download programs inside a .tar.gz if you can avoid it. They are usually source code, which must be compiled first; this process is not hard, but it's not especially user-friendly either (it's done for programmers to look at the source code, or for distribution developers to make packages of). Stick to the repositories.

---

### Post by archangelos14 on 2010-02-10
I am now able to use the synaptic package manager. tnx for all your help. but still wasn't able to figure out what's wrong with sudo apt-get update command. error 407 proxy authentication required. i've read articles on how to solve it by editing the apt.conf. but still can't have it run properly. just trying different ways on how to update/install softwares. well i guess i'll have to stick with the synaptic manager for now. :D still hope i can make sudo apt-get update work...

---

### Post by andybu on 2010-03-23
> **Revolutionary101 said:**
> These two tips may help you

1. You must likely don't need to download applications via your internet browser. It is a lot easier to install them via Synaptic Package Manager (System>Administration>Synaptic Package Manager) or the Ubuntu Software Center (Applications>Ubuntu Software Center). Just select a software package and it will automatically install it for you.

2. To install the .tar.whatever do this:
   I. Extract the .tar.whatever file to the folder of your choosing.
   II. Open Terminal from Applications>Accessories>Terminal
   III. Set Terminal to the location of the application by doing this
   ```
cd /path/of/extracted/files
```   IV. After the path is set enter this into terminal
   ```
./compile
```This will compile the program for installation
   V. Then type this
   ```
make
```This will make the applications ready for installation
   VI. Finally type this
   ```
sudo make install
```That should do it. I hope it helps.


Hi, I'm new to Ubuntu but have a similar problem.

I couldnt find postfix using the apt-get method or the synaptic package manager method, so i downloaded the postfix-2.6.5.tar.gz file and unzipped it to a directory on my Ubuntu box.

I have cd'd into the directory where all the unzipped files are and typed 
"./compile" 

but I get the error "compile: command not found" I guess it's not in the current directory

what am i missing ?

thanks
Andy
but I guess that-s not in my path as

---

### Post by Paqman on 2010-03-23
> **andybu said:**
> 
I couldnt find postfix using the apt-get method or the synaptic package manager method, so i downloaded the postfix-2.6.5.tar.gz file and unzipped it to a directory on my Ubuntu box.


Here's a [PPA with postfix]("https://launchpad.net/~damoxc/+archive/postfix") in it that I found through Google. Add that PPA and you'll be able to get it through Synaptic.

Just say no to messy compiling!

---

### Post by oldos2er on 2010-03-23
> **andybu said:**
> I have cd'd into the directory where all the unzipped files are and typed 
"./compile" 

but I get the error "compile: command not found" I guess it's not in the current directory


 Try "./configure" instead.

---

### Post by andybu on 2010-03-23
Excellent, Thanks for this, I'll try when I get in tomorrow !

Andy

---

