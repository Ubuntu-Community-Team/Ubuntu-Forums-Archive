---
title: "I am so confuse for installing packages."
date: 2010-12-21
forum: New to Ubuntu
---

### Post by jijiisme on 2010-12-21
if i want to install some package in linux, I always face the problem. because of some package have many version and different kind of type. so I am really confuse to install right package that I want. 

I think so many beginner face the same problem like me.:D

---

### Post by stoopkitty on 2010-12-21
one of the ways to simplify this is to use ```
sudo apt-get install <package>
``` in terminal to install packages. it can sometimes get confusing with the sources, but the website for the application you are trying to install usually tells you those. to add sources, go to system menu-->administration->software sources. click the other software tab and then the add button and type in the source (repository) that you want to add.

to update all of your packages at once, you can use ```
sudo apt-get upgrade
``` and ```
sudo apt-get update
``` in terminal to upgrade them all at once.

if you find graphical utilities easier, you can use ubuntu software center, from the applications menu, and update manager, from the system->administration->software update menus.

---

### Post by Verbeck on 2010-12-22
which application(s) are you having problems installing?

---

### Post by jijiisme on 2010-12-22
I used deb distro.

---

### Post by Verbeck on 2010-12-22
you mean a .deb file?then from a terminal run
sudo dpkg -i /path/to/file.deb

---

### Post by 3rdalbum on 2010-12-22
If you are a new user, try using the Applications > Ubuntu Software Center program. It will only list the correct programs for your CPU and version of Ubuntu.

---

### Post by bodhi.zazen on 2010-12-22
> **jijiisme said:**
> if i want to install some package in linux, I always face the problem. because of some package have many version and different kind of type. so I am really confuse to install right package that I want. 

I think so many beginner face the same problem like me.:D

Installing applications (software) is very easy in Ubuntu.

You should use the repositories, doing so will automate this for you.

a deb is an archive, like a zip file, and so you can not simply install a random .deb

There is ample documentation on the Wiki:

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by prat22 on 2010-12-22
Go for software centre. This is the best way. Or use sudo apt-get install vlc, if you want vlc to be installed.

---

### Post by rburkartjo on 2010-12-25
yes when i switched to linux 4 years ago that was also one the biggest problems it had. good idea to sue the software center. it is easy to use and usually tells you where the new program was installed.. also easy to remove a program. if you really want to install a program that is not listed. do a goggle search for a deb install of x program. good luck. gets a lot easier with time,

---

### Post by IndyGunFreak on 2010-12-25
> **3rdalbum said:**
> If you are a new user, try using the Applications > Ubuntu Software Center program. It will only list the correct programs for your CPU and version of Ubuntu.

This is the true answer... All these terminal commands, etc.. Folks gotta remember newbs are coming from a "Point and click" world... Yeah, terminal works fine for those of us experienced, but when telling a newb how to do something, it's really best to stick w/ GUI tools (if at all possible)

IGF

---

### Post by lwalper on 2010-12-25
Same question, different package.

I would like to install DjVu reader, so I checked the synaptic repositories and don't see it listed. I have then downloaded the package

djvulibre-3.5.23.tar.gz

but cannot figure out how to install it?? The gz part I can do -- unzipping is no problem, but doesn't the package now need to be "installed" somewhere?

I have read the [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) and hve not found it to be much help. It talks about apt-get and such like which does not seem to apply to my situation since I have already "gotten" the package I want to install.

HELP!!

---

### Post by Verbeck on 2010-12-25
@ [lwalper]("http://ubuntuforums.org/member.php?u=252451")

[http://djvu.sourceforge.net/](http://djvu.sourceforge.net/)
> 
Available from [Ubuntu]("http://packages.ubuntu.com/src:djvulibre")  (apt-get!)
they do say that its in the repos

search for *djveiw* in the software center

---

### Post by lwalper on 2010-12-25
I just must not have known what to look for. Thanks for the input.

Anyhow, what I did was to unzip the package, then, in synaptic, clicked on File > Add downloaded packages. Then I was able to locate the package in synaptic and installed it from there. So far everything seems to work.

---

