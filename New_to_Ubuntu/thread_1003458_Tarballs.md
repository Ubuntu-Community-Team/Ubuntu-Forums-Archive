---
title: "Tarballs"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by CalonD on 2008-12-06
...

---

### Post by gandaran on 2008-12-06
> **CalonD said:**
> Hey, I'm really confused.

I bought a wireless adapter that works with Linux, but I can't seem to run the installer, as the tarball won't extract, this is pretty nooby but I don't know where too save the tarball from the CD?

Any help pleaSE?
can't you copy the tar ball to desktop, right click, choose extract here from the drop down menu? and read the readme file for install instructions?

the wireless may already work with ubuntu without needing to install drivers, try it first,
what is the brand name?

---

### Post by CalonD on 2008-12-06
...

---

### Post by lovelyvik293 on 2008-12-06
Tell the vendor of your wifi card.

---

### Post by CalonD on 2008-12-06
...

---

### Post by lovelyvik293 on 2008-12-06
All right.
This is the same thread as yours:-
[http://ubuntuforums.org/showthread.php?t=994190](http://ubuntuforums.org/showthread.php?t=994190)


And i think u can get a how-to at:-
[http://ubuntuforums.org/archive/index.php/t-705733.html](http://ubuntuforums.org/archive/index.php/t-705733.html)

---

### Post by gandaran on 2008-12-06
> The driver disk has mac drivers, windows drivers and linux drivers folders, and inside the linux driver is a file called (i think) ZD1211LnxDrv_2_22_0_0.tar.gz, the instructions were useless

    tar zxvf ZD1211LnxDrv_2_22_0_0.tar.gz

    make

I saved the file to the desktop and entered,

    sudo tar zxvf ZD1211LnxDrv_2_22_0_0.tar.gz
    cd /home/oli/Desktop/ZD1211LnxDrv_2_22_0_0.tar.gz
    make

But i got nothing useful, the make said loads of parameters were undefined etc, i tried many different solutions on the website forum, including some nidiswrapper stuff (of course ndiswrapper goes untamed, so all the sources were unavailable).
I took this from the other thread, this is completely wrong
what you must do is copy ZD1211LnxDrv_2_22_0_0.tar.gz to desktop, right click the file and choose the extract here option
now open the terminal and cd to the **extracted file** not ZD1211LnxDrv_2_22_0_0.tar.gz, should be something like cd /home/'user'/Desktop 'ZD1211LnxDrv_2_22_0_0' the exact name of the extracted file then type the next command **make**
after installing you have to load the module

---

### Post by CalonD on 2008-12-07
...

---

### Post by CalonD on 2008-12-07
...

---

### Post by gandaran on 2008-12-07
you still doing something wrong, what is the exact file name of the extracted package contents?
it's not cd ZD1211LnxDrv_2_22_0_0, you have to enter the full path, cd /home/calon/Desktop 'file name' (Desktop with a capital D)
first you have to cd to that file and only then you enter the make command
you also need to install the build-essential package in synaptic first for compiling programs

---

### Post by CalonD on 2008-12-07
...

---

### Post by gandaran on 2008-12-07
> ZD1211LnxDrv_2_22_0_0
is this the correct file name after you extracted the tarball?
doesn't it have any file inside with install instructions?

---

### Post by CalonD on 2008-12-07
...

---

### Post by gandaran on 2008-12-07
> How do I get build-essential, can I sourceforge it or something because I have no internet on ubuntu, I'm running on XP until I have sorted ubuntu out with internet
well this is a big problem, build-essential needs internet to install, it as to many dependencies, can't you connect ubuntu to a Ethernet cable modem connection?

---

### Post by gandaran on 2008-12-07
also you must be running a root terminal to install this file
when you open the terminal the first thing to type is **sudo -i** hit enter and password then type the cd to file command and **make** next.
I'm not exactly sure if build-essential is needed, according to your instructions you only have to run the make command and make is already installed in ubuntu.

---

### Post by oldos2er on 2008-12-07
If you have an Ubuntu LiveCD, you can install build-essential from there.

---

### Post by Arkaniad on 2008-12-07
> **gandaran said:**
> also you must be running a root terminal to install this file
when you open the terminal the first thing to type is **sudo -i** hit enter and password then type the cd to file command and **make** next.
I'm not exactly sure if build-essential is needed, according to your instructions you only have to run the make command and make is already installed in ubuntu.
I second that, the only thing you should make sure to do before you make is ./configure

At least im pretty sure,
:)
It's source code, the sooner you get it, the more nerdy you feel.

---

### Post by CalonD on 2008-12-07
...

---

### Post by gandaran on 2008-12-08
well according to the errors messages there's no make file in the package can you post the install instructions (from the extracted contents package)?
> cd /home/calon/Desktop/ZD1211LnxDrv_2_22_0_0
try the cd command like this and don't forget the root terminal or use **sudo make**
**cd /home/calon/Desktop ZD1211LnxDrv_2_22_0_0**

---

### Post by mali2297 on 2008-12-08
To get build-essential from the CD, try the suggestion in this [post](http://ubuntuforums.org/showpost.php?p=1976369&postcount=4).

---

### Post by 3rdalbum on 2008-12-08
Guys, this isn't rocket science.

> calon@ubuntu:~/Desktop/ZD1211LnxDrv_2_22_0_0$

He's in the correct directory.

CalonD: Please post the included install instructions for us, unless they begin with "These are generic installation instructions" :-)  You'll need the build-essential package - insert the Ubuntu CD while the machine is running and click "Use in package manager" when prompted. Now you should be able to install build-essential from Synaptic Package Manager. I imagine you'll also need the kernel headers for the kernel version you are running, and either they will be on the disc too or you could install them from Synaptic if you plug your computer directly into your modem/router with an Ethernet cable.

---

### Post by CalonD on 2008-12-08
...

---

### Post by CalonD on 2008-12-10
And it works fine now. It turns out Plug 'N' play works in 10.04.

---

### Post by Michael.Godawski on 2008-12-10
Make sure the CD is checked in the software sources (system > administration)
then run ```
sudo apt-get install build-essential
```

---

### Post by oldos2er on 2008-12-10
Correct package name is build-essential

---

### Post by Michael.Godawski on 2008-12-10
> Correct package name is build-essential 	

Since the beginning of dawn I cannot remember this. :p

---

### Post by feisty john on 2008-12-10
CalonD,

I think people are making this harder than it needs to be. (Maybe it's already harder than it needs to be.) 

I don't know if you need it for this problem, but very soon you will need build-essential. Get it somehow. Either connect your computer directly to your modem with an ethernet cable or put in your Ubuntu CD. Then run:
```
sudo aptitude install build-essential
```

You could even download the build-essential .deb file on an internet-connected computer ([http://packages.ubuntu.com/dapper/build-essential]("http://packages.ubuntu.com/dapper/build-essential"), but replace "dapper" with your distro...gutsy, hardy, whatever) and transfer it to this one with a USB stick. Somehow, just get it. Installing .deb files is easy: just save it to the Desktop, right-click, choose install with GDebi package installer.

Maybe build-essential is necessary for this, maybe not. Being sort of a noob myself, I can't fathom any line of reasoning that would lead anyone to conclude that leaving build-essential out of the basic installation was a remotely good idea.

Anyway, you obviously got your tar.gz file to your Desktop and extracted it fine. It produced a new folder. You cd'd into that folder just fine. Great.

After you're in that folder in the Terminal, since there seems to be no README or other help file in that folder, try: 
```
./configure
```

Whether that works or not, try:
```
sudo make
```

After that, try:
```
sudo make install
```

Those three commands work for a lot of tarballs. Please post any other problems/issues/experiences after you've gotten further.

---

### Post by gandaran on 2008-12-11
CalonD
I have googled for your problem and from what I have seen nobody can install those drivers with the make command on new kernels, there are other drivers or other ways to get it to work for your wireless card, just search or go to plascom forum
also are you sure the card doesn't work when you plug it in? I still believe ubuntu 8.10 already supports you wireless card drivers

---

