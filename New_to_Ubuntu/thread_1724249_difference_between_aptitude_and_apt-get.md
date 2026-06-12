---
title: "difference between aptitude and apt-get?"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by RememberWhenItRained on 2011-04-08
what is the difference between aptitude and apt-get?

for instance
```
 sudo aptitude dict install
```and
```
 sudo aptitude remove dict
```or
```
 sudo apt-get cowsay
```and
```
 sudo apt-get remove cowsay
```not sure if i did those right, but what's the difference between using apt-get and aptitude?

---

### Post by GregBrannon on 2011-04-08
According to [this]("http://www.cyberciti.biz/tips/linux-debian-package-management-cheat-sheet.html") article, the command 'aptitude' opens a text based interface to the package manager, while apt-get is a package manager command.  You can learn more by reading the article and the many other resources that detail the use of the package manager.

---

### Post by Paqman on 2011-04-08
Bottom line: not much difference.

They're both programs for using the package manager. As GregBrannon mentions, aptitude does have a text-based interface available, which makes it popular on servers, as it does a bit more than apt-get. But they're basically the same thing.

Apt-get is installed by default on all versions of Ubuntu, aptitude is available in the repos.

---

### Post by philinux on 2011-04-08
> **RememberWhenItRained said:**
> what is the difference between aptitude and apt-get?



Please see here.

[http://ubuntuforums.org/search.php?searchid=80345036](http://ubuntuforums.org/search.php?searchid=80345036)

And this.

[http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

---

### Post by realzippy on 2011-04-08
..note that aptitude isn't installed anymore in vanilla Ubuntu.
Anyone knows why?

---

### Post by klytu on 2011-04-08
> **RememberWhenItRained said:**
> what is the difference between aptitude and apt-get?

for instance
```
 sudo aptitude dict install
```and
```
 sudo aptitude remove dict
```or
```
 sudo apt-get cowsay
```and
```
 sudo apt-get remove cowsay
```not sure if i did those right, but what's the difference between using apt-get and aptitude?

When you use aptitude to remove a package that you installed with aptitude, any dependencies installed with that package are also removed. Using apt-get as you do above leaves behind the dependencies.

In the examples you give above, let's assume that the package "dict" depends on the package "lex" and that "lex" was not originally installed on your system.

```
sudo aptitude install lex
```
Installs the package "dict" and its dependency "lex".
```
sudo aptitude remove "dict"
```
Removes the packages "dict" and "lex".
```
sudo apt-get install dict
```
Installs the package "dict" and its dependency "lex".
```
sudo apt-get remove dict
```
Removes the package "dict", but leaves "lex" installed. But:
```
sudo apt-get autoremove dict
```
Removes the packages "dict" and "lex".

If I recall correctly, older versions of apt-get from a couple of years ago did not have the autoremove option. For that reason
I got in the habit of using aptitude to install and remove packages. Note that aptitude will not remove dependencies of a package installed by apt-get and vice-versa. FYI, it's also a good idea to 
```
sudo aptitude update
``` or
```
sudo apt-get update
``` before installing packages. 

There are some other differences between aptitude and apt-get, but generally they can both be used to achieve the same results if you understand the correct options to use. For more information check out the man pages:

```
man aptitude
``` and 
```
man apt-get
``` or post back with specific questions and we'll try to help.

---

### Post by philinux on 2011-04-08
> **realzippy said:**
> ..note that aptitude isn't installed anymore in vanilla Ubuntu.
Anyone knows why?

To save space on the livecd I guess. Since both software centre and synaptic use apt.

---

