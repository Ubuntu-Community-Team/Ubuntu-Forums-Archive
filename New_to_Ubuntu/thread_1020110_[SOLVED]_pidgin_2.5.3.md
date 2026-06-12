---
title: "[SOLVED] pidgin 2.5.3"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by RavensCry on 2008-12-23
I am new to linux (as of yesterday) and the new pidgin is out and only available in source, how can I install it?

---

### Post by mrbiggbrain on 2008-12-23
> **RavensCry said:**
> I am new to linux (as of yesterday) and the new pidgin is out and only available in source, how can I install it?

you need to download the source, untar the file (its likely also bzipped/gunzipped)

enter the directory (you may need to use the command:

```
sudo chown username /directory/
```

to make sure you OWN and can actualy do things.

then us

```
ls -a
```

this will show all scripts, files, normaly there is one called config, ect, if you can find one open a file with instructions.

usualy youll need to use make, this requires root privliges so youll need to use 

```

sudo make

or

sudo makesomethingelse

```

if you can find documentation it would help you alot


also note that your useing ubuntu, its not well known for having everything needed to compile something, so running

```

apt-get install <package>-dev

or

apt-get install <package>-devel

or

apt-get build-dep <package>


```

and also you may need to do some hunting, updates ect ect

---

### Post by northern lights on 2008-12-23
The newest version as of today is 2.5.3.a (bugfixed) and is available as a .deb from [here]("http://www.getdeb.net/app/Pidgin") - no installation from source necessary.

If you have the GDebi package installer installed, you can set up pidgin by double-clicking the .deb
Run```
sudo apt-get install gdebi
```to get the package installer working or use dpkg to install the .deb:```
sudo dpkg -i /path/to/folder/pidgin.deb
```

[EDIT]
> **mrbiggbrain said:**
> usualy youll need to use make, this requires root privliges so youll need to use 

```

sudo make

or

sudo makesomethingelse

```
unless the source files are stored outside the home folder, make does not need to be run as root. Only the installation requires superuser rights, that'd be```
sudo make install
```[/EDIT]

[EDIT2]
If you currently have pidgin installed from the repositories, it'd be advisable to remove it before installing the new version```
sudo aptitude purge pidgin
```[/EDIT2]

---

### Post by mrbiggbrain on 2008-12-23
> **northern lights said:**
> The newest version as of today is 2.5.3.a (bugfixed) and is available as a .deb from [here]("http://www.getdeb.net/app/Pidgin") - no installation from source necessary.

If you have the GDebi package installer installed, you can set up pidgin by double-clicking the .deb
Run```
sudo apt-get install gdebi
```to get the package installer working or use dpkg to install the .deb:```
sudo dpkg -i /path/to/folder/pidgin.deb
```

[EDIT]

unless the source files are stored outside the home folder, make does not need to be run as root. Only the installation requires superuser rights, that'd be```
sudo make install
```[/EDIT]

thanks, good to know, i usualy keep my source in a seperate /sources/<packagename>/ directory, so i am usualy haveing to sudo my way around.

---

### Post by northern lights on 2008-12-23
> **mrbiggbrain said:**
> i usualy keep my source in a seperate /sources/<packagename>/ directory, so i am usualy haveing to sudo my way around.Fair enough. But why do you prefer to have a /sources/ folder in the rootfilesystem? You could just as easily keep sources in /home/USER/sources/. Just my 2 cents.

> **mrbiggbrain said:**
> also note that your useing ubuntu, its not well known for having everything needed to compile something, so running

```

apt-get install <package>-dev

or

apt-get install <package>-devel

or

apt-get build-dep <package>

``` 
The meta-package *build-essential* contains the most common tools for compiling, foremost gcc (GNU C Compiler).

---

### Post by mrbiggbrain on 2008-12-23
> **northern lights said:**
> Fair enough. But why do you prefer to have a /sources/ folder in the rootfilesystem? You could just as easily keep sources in /home/USER/sources/. Just my 2 cents.

 
The meta-package *build-essential* contains the most common tools for compiling, foremost gcc (GNU C Compiler).

im learning how to do all that from Linux-from-scratch so i just followed theregeneral idea outside the book.

and i had to stop LFS for now becuse i cant get the headers and files needed to compile the clean kernel headers, iv done everything i listed on every package, plus build-essentials, and alot of other stuff, and it still dosnt ahve the things needed for the clean linux headers

```
make ARCH=x86_64 headers_check 

```
always fails.

so i guess im not the best to talk about compileing dependencys

---

### Post by northern lights on 2008-12-23
> **mrbiggbrain said:**
> ```
make ARCH=x86_64 headers_check 

```
always fails.What kernel version are your attempting this with? There was a bug in some of the 2.6.24.X kernels that caused this to happen.
I think some of the 2.6.24.X kernels contained headers meant for 2.6.25-rcX...

P.S. This is far more complicated than compiling pidgin, though.

---

### Post by mrbiggbrain on 2008-12-23
linux-2.6.24.7
linux-2.6.27.10
linux-2.6.27.4

so far all the same

---

### Post by adobrakic on 2008-12-23
Why not just [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

---

### Post by northern lights on 2008-12-24
> **adobrakic said:**
> Why not just [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)
> **northern lights said:**
> The newest version as of today is 2.5.3.a (bugfixed) and is available as a .deb from [here]("http://www.getdeb.net/app/Pidgin")

"here" = getdeb.net/app/Pidgin

---

