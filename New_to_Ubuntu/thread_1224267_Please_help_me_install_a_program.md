---
title: "Please help me install a program"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by gareththomasnz on 2009-07-27
Have been using Ubuntu Hardy for 3-4 weeks now and its great, 

I know how to use the repositories and .deb files but have not yet installed an application like this.

I am prepping for a difficult calculus paper so want to try this simple trigonometry program.

If somebody can show me how to install this I will be able to figure it out next time.

Heres the application [http://www.coyotegulch.com/products/unit_circle/](http://www.coyotegulch.com/products/unit_circle/)

Download direct: [http://www.coyotegulch.com/distfiles/unit_circle-1.0.1.tar.gz](http://www.coyotegulch.com/distfiles/unit_circle-1.0.1.tar.gz)

I have no idea how to get this made and set up at all.

---

### Post by bailbath on 2009-07-27
Hi right click the downloaded file and choose 'open with archive manager' Once it has opened click 'extract' from the menu bar then a box opens so you can choose to extract in a place. I use my home folder which is the default. Click extract at the bottom and it will extract, then look in the folder that has been extracted it will have a 'install' file which will tell you how! If you are still scratching year head post back on this thread and you will be helped.
Ian

---

### Post by t0p on 2009-07-27
First of all, search the repos to see if the app is there.

If it isn't in the repos, search [www.getdeb.net]("http://www.getdeb.net")  to see id there's a .deb package of this app available.

If there's no .deb: That .tar.gz archive contains an apparently simple-to-compile source code.  So, use Archive Manager to extract the archive (right-click on the .tar.gz archive and select Extract To Here).  Next, go visit [this link]("https://help.ubuntu.com/community/CompilingEasyHowTo").   There you will find easy-to-follow instructions on compiling source.  This is a skill which will stand you in good stead if you insist on wanting to install software that is only available as source.  And reading the instructions will help you a whole lot more than being told what commands to type in but not learning *why* you use those commands.

---

### Post by The Cog on 2009-07-27
The downloaded archve containts source code that needs compiling. 
You need to install a compiler first, with this command:
**sudo aptitude install build-essential**

The normal way to compile is to unzip the file:
**tar xfz unit_circle-1.0.1.tar.gz**
then change into the just-unpacked directory:
**cd unit_circle-1.0.1**
then run these two commands:
[b]./configure
make[/b]
followed by:
**sudo make install**
but we have a problem here. configure has the job of checking that everything is ready to actually do the compilation, and it is complaining that it can't find the package libgnomeui-2.0. Now I've looked in synaptic, and there is no such package, so I can't install it and try again. And I'm not good enough to know how to fix the problem in the code. So to me at least, the program is not installable.

---

### Post by bailbath on 2009-07-27
> **The Cog said:**
> The downloaded archve containts source code that needs compiling. 
You need to install a compiler first, with this command:
**sudo aptitude install build-essential**

The normal way to compile is to unzip the file:
**tar xfz unit_circle-1.0.1.tar.gz**
then change into the just-unpacked directory:
**cd unit_circle-1.0.1**
then run these two commands:
[b]./configure
make[/b]
followed by:
**sudo make install**
but we have a problem here. configure has the job of checking that everything is ready to actually do the compilation, and it is complaining that it can't find the package libgnomeui-2.0. Now I've looked in synaptic, and there is no such package, so I can't install it and try again. And I'm not good enough to know how to fix the problem in the code. So to me at least, the program is not installable.

In synaptic package manager you will find/search 'libgnomeui' that fufills that requirement with 'libgnomeui-common and 'libgnomeui-dev'.

---

### Post by bailbath on 2009-07-27
It is up and running on ubuntu here.
So to recap extract the downloaded file.
Then open Synaptic package manager search for 'libgnomeui' I installed 'libgnomeui-common' and 'libgnomeui-dev' it will download a lot of other bits and pieces.

Make sure that you have the right tools to build the program open a terminal copy and paste the following then put in your password when it asks 

```
sudo aptitude install build-essential
```

You only have to do that once as this will help every time you want to compile a program.

Now still in the terminal change to the folder that you have extracted which if you extracted to the home folder
```
cd /home/yourusername/unit_circle-1.0.1
```
obviously change yourusername to whatever is your user name!
Next 
```
./configure
```
then 
```
make
```
Then you have to be super user for next bit
```
sudo make install
```

It should all work now by putting 
```
unit_circle
``` 
in the terminal you can add it to the menu if you go to system-preference-main menu and use new item on the menu bar I put mine in graphics sub menu.

---

### Post by gareththomasnz on 2009-07-31
OK I will have a play around with this tonight because its a skill you really need with LINUX

Cool.

Hey I also found this [http://www.geogebra.org/cms/index.php?option=com_content&task=blogcategory&id=72&Itemid=58](http://www.geogebra.org/cms/index.php?option=com_content&task=blogcategory&id=72&Itemid=58)

Its awesome software for studying graphs and functions. Shows the unit circle and corresponding graph

---

