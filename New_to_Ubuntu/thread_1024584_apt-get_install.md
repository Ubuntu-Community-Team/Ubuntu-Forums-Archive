---
title: "apt-get install"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by loza on 2008-12-29
Hello

I would like to know where all you gurus find out about all the different apt-get packages?

I had a bit of a problem with C the other day and someone suggested I needed to 

sudo apt-get install build-essential

Is there a list on the Web somewhere?

I would just like to know where can I find out about what is available please.

thanx
loza

---

### Post by AllanPoe on 2008-12-29
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by RichardLinx on 2008-12-29
[http://www.getdeb.net/](http://www.getdeb.net/) 
Great site which lists most popular .deb downloads and has downloads for just about every .deb available for Ubuntu. Personally, I know about most the packages because I've seen them in synaptic. :)

---

### Post by moonoo on 2008-12-29
Here is another one:

[http://www.apt-get.org/](http://www.apt-get.org/)

:D

---

### Post by giannoug on 2008-12-29
If you want a list of all the packages available for your system (from all your repositories) go to System > Administration > Synaptic Package Manager. If you want a list of all the packages  provided for Ubuntu, go to [http://packages.ubuntu.com](http://packages.ubuntu.com) :)

---

### Post by mohitsoni on 2008-12-29
I think the best place to start with is [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"). Here the packages are neatly classified based upon the version releases. Also, the site allows to search for specific packages. Enjoy

---

### Post by cdwillis on 2008-12-29
If you'd like to search through the terminal you can type this:

apt-get cache search programname

or

apt-get cache seach 'web browser'

for example

---

### Post by Bankai56 on 2008-12-29
I think the best way is still synaptic since you can see there which packages you even have. Because for some you need to install new sources.

---

### Post by RichardLinx on 2008-12-29
> **Bankai56 said:**
> I think the best way is still synaptic since you can see there which packages you even have. Because for some you need to install new sources.

It's quicker through terminal though. Synaptic is great but a lot of packages aren't available through it.

---

### Post by Sealbhach on 2008-12-29
> **loza said:**
> Hello

I would like to know where all you gurus find out about all the different apt-get packages?

sudo apt-get install build-essential



This one is very well known because you need it to compile.


.

---

### Post by mkvnmtr on 2008-12-29
The search feature in Synaptic is great. If you are looking to do something put in the discription and it will come back with a list to check out. When you find an app that you think might be what you want you can check what it depends on and what it conflicts with. Also it will be listed with others that might do the same thing. Then you can install from the same place.

---

### Post by loza on 2008-12-30
Thank you so much everyone! My mind is blown! :D

---

### Post by kansasnoob on 2008-12-30
Start here to learn command line:

[https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands)

But you should know that there are now gui (graphical user interface) options for at least 90% of what you'll need to do in Ubuntu.

Let's say you want to check for updates. From command line:

```
sudo apt-get update
```

From gui go to System > Administration > Update manager, and click check!

Or you want to install ubuntu-restricted-extras. From command line:

```
sudo apt-get install ubuntu-restricted-extras
``` 

or from gui go to System > Administration > Synaptic Package Manager and click on Search. Type extras (or ubuntu), (or restricted). Ubuntu-restricted-extras will show up in the list!

---

### Post by minsf on 2008-12-30
I think this thread is pretty much solved. But just a couple of remarks for completeness:

1) Regarding command-line update:
> **kansasnoob said:**
> 
Let's say you want to check for updates. From command line:

```
sudo apt-get update
```

if you want to update from the command-line, then after "sudo apt-get update", you also need "sudo apt-get upgrade".

2) Regarding command-line package search:
> **cdwillis said:**
> If you'd like to search through the terminal you can type this:

apt-get cache search program_name

or

apt-get cache seach 'web browser'

for example
also possible is "aptitude search program_name", but the important point is that after this, when you see some package that interest you, you in the list, can see more details about it with
```
aptitude show some_package_name
```
but like people said, [http://packages.ubuntu.com](http://packages.ubuntu.com) and Synaptic are probably better options, than a command line search.

have fun

---

