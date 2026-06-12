---
title: "installing programs from source code"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by augie2051 on 2010-01-31
Trying to figure out how to install programs using the source code when the programs specifically with a tar.gz or a tar.bz2 extension.  I found a link that gives instructions but it doesn't seem to work for me. I get an error that says no such file or directory.  I assume that when I download the file goes to my home directory?  Here is the link: [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html).  If anyone could give me a comprehensive walk through it would be greatly appreciated.

---

### Post by MelDJ on 2010-01-31
have you cd'd to the extracted folder after extracting the tar?
try [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by Perfect Storm on 2010-01-31
a tar file is like the zip file you know from windows. They can contain anything. Also there are many ways to compile source codes, depending which tools they used etc.

Try look at the source codes you downloaded and check for a readme or INSTALL file which might explain their installation proceeding.

---

### Post by gigaferz on 2010-01-31
DISCLAIMER

: I BREAK MY UBUNTU VERY OFTEN , i might be doing it again but note this warning

i dont think im qualified to answwer but still..here i go:

download a package tar  or something.

right click it and extract it.

launch terminal and go to that directory;

   example   user@whatever>cd /home/downloads/"name of sftware"/specific_folder/
i pute "name of software as an example when to change to a directory with long names and spaces like for example  to go to Program Files you type cd "Program Files"
  still with me ?

anyways before you do the maggic you need to have your linux headers or something .

Im about to do it like this:

 sudo apt-get install linux-headers*

but im not really sure!!!  ill let you know.

is because i can not find a guide yet, ive done it before but  sinces dapper i havent installed from source.
anyways. once you do that

you type in that folder

./configure   i think you could do it with sudo

then after it checks everything ok

sudo make

then after the magic happens sudo make install.

hopefully itll help you or confuse you and scare you so you go back to the deb pacakges...lol

---

### Post by halitech on 2010-01-31
what are you trying to install? there may be an easier way then compiliing from source.

---

### Post by Mornedhel on 2010-01-31
> **augie2051 said:**
> I assume that when I download the file goes to my home directory?

You're assuming wrong. The files downloaded go where Firefox is told to store them. Open Firefox, go to Edit > Preferences, select the General section, and check where downloaded files are stored. It's usually your Desktop or Downloads folder in your home folder.

If you have a terminal open, "ls" will print the files in the current directory.

---

### Post by augie2051 on 2010-01-31
> **halitech said:**
> what are you trying to insttall? there may be an easier way then compiliing from source.

Snort

---

### Post by Perfect Storm on 2010-01-31
> **augie2051 said:**
> Snort

It's in the repositories:
```
sudo apt-get install snort
```

---

### Post by augie2051 on 2010-01-31
> **Artificial Intelligence said:**
> It's in the repositories:
```
sudo apt-get install snort
```
Wow thanks! I guess I should have checked there first, now i feel like an idiot.

---

