---
title: "apt-get commands?"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by tahir.salfi on 2011-06-23
pleas give me all "suod apt-get install" commands:(

---

### Post by TeoBigusGeekus on 2011-06-23
> **tahir.salfi said:**
> pleas give me all "suod apt-get install" commands:(

Could you clarify it a bit more?
What commands are you talking about?

---

### Post by Beacon11 on 2011-06-23
You need to meet the man command.

```
man apt-get
```

---

### Post by 3rdalbum on 2011-06-23
You type:

```
sudo apt-get install
```

and then the name of the package you want to install.

If you don't know the name of the package you want to install, then you should be using Ubuntu Software Center or Synaptic Package Manager instead. Apt-get lets you install packages by name, but those other two let you search or browse for what packages are available to install.

---

### Post by gdonwallace on 2011-06-23
If you are asking for a list of all the possible switches and options for apt-get, there is an easy way to get that information from within Ubuntu.  

From the command line type "man apt-get".  This will bring up the "manual" page for apt-get and give you all the information that you need.

---

### Post by jerrrys on 2011-06-23
in terminal enter

sudo apt-get install apt-dpkg-ref

then in your address box of your browser enter

file:///usr/share/doc/apt-dpkg-ref/apt-dpkg-ref.html

---

### Post by Neoncamouflage on 2011-06-23
Agreed, the man command is your friend. Honestly, these couple are all I ever use:

```
apt-cache search "keyword"
```
Searches through the repositories for packages using your keyword.

```
apt-cache search "keyword" | grep "keyword"

apt-cache search "keyword" | less
```
First command uses *grep* to take the results of your search and only show those containing your exact word. Seriously helps cut down on the massive lists you can get at times.

Second command takes the list and uses the *less* text viewer to show it, useful if you have lists that go farther than you can scroll up, but it's fairly unused if you have any real idea what you're searching for and use the *grep* command as well.

```
apt-cache show "package"
```
Shows a short description of the package.

```
sudo apt-get install "package"
```
Downloads and installs the selected package.

```
sudo apt-get purge "package"
```
Completely removes the package, careful with this one.

I'm positive there's some that I've missed but this is what I use every time I need something, and it's yet to be an issue. I really can't stand using Synaptic or the Software Center so I've gotten everything through apt-get.

---

### Post by dFlyer on 2011-06-23
Another apt-get command to fix problems is:

sudo apt-get -f install

This will pull in missing libs if they are in the archives.

---

### Post by josephmills on 2011-06-23
I would also like to put the ```
info apt-get 
``` I think that is the same as man though ???  or ```
sudo apt-get --help
```

---

### Post by Neoncamouflage on 2011-06-23
> **josephmills said:**
> I would also like to put the ```
info apt-get 
``` I think that is the same as man though ???  or ```
sudo apt-get --help
```

Info and man are different, and often show different explanations. Honestly, I prefer the man command, but if it ever doesn't quite help I'll use info as well.

---

