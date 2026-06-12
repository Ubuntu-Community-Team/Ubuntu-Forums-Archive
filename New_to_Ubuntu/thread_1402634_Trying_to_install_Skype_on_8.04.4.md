---
title: "Trying to install Skype on 8.04.4"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by L Campbell on 2010-02-09
I'm running 8.04.4 on a PC and trying to install Skype.

  I went to this website:-

    [http://tinyurl.com/yftprhn](http://tinyurl.com/yftprhn)


and got these instructions:-

 Here are a* quick set of steps to install skype on Ubuntu 8.04.
Download skype static from here 
Execute the following commands at the terminal: 
$ tar -xvf skype_static-2.0.0.68.tar.bz2
$ mv /yourpath/skype_static-2.0.0.68 /usr/share/
$ mv skype_static-2.0.0.68/ skype
$ cd skype/
$ cp skype /usr/bin/
$ rm /etc/dbus-1/system.d/skype.conf
$ cp /usr/share/skype/skype.conf /etc/dbus-1/system.d/
$ skype

So I now have the Skype package (skype_static-2.1.0.81.tar.bz2) on my Desktop and I tried the first instruction.

The result was:-

qwer@qwer-desktop:~$ tar -xvf skype_static-2.0.0.68.tar.bz2

tar: skype_static-2.0.0.68.tar.bz2: Cannot open: No such file or directory

tar: Error is not recoverable: exiting now

qwer@qwer-desktop:~$ 


I would appreciate it if you have a suggestion here?

TIA.

---

### Post by ptn107 on 2010-02-09
I have a better idea.

1) Download here: _[Skype 32-bit]("http://www.skype.com/go/getskype-linux-beta-ubuntu-32")_, or _[Skype 64-bit]("http://www.skype.com/go/getskype-linux-beta-ubuntu-64")_ if your PC is 64-bit (if you don't know use the 32-bit one).  Save it to your desktop.

2) Double-click the file you downloaded to open the package installer.  Click "Install Package."

The link to run Skype is under Applications -> Internet when you're done.

---

### Post by patchwork on 2010-02-09
..otherwise cd to Desktop and run the tar command from there

```
cd Desktop
```

---

### Post by L Campbell on 2010-02-09
> **ptn107 said:**
> I have a better idea.

1) Download here: _[Skype 32-bit]("http://www.skype.com/go/getskype-linux-beta-ubuntu-32")_, or _[Skype 64-bit]("http://www.skype.com/go/getskype-linux-beta-ubuntu-64")_ if your PC is 64-bit (if you don't know use the 32-bit one).  Save it to your desktop.

2) Double-click the file you downloaded to open the package installer.  Click "Install Package."

The link to run Skype is under Applications -> Internet when you're done.

Thanks for your suggestion but, unfortunately, it doesn't work.

When I try to 'Install Package' I get this error:-

'Error: Dependancy is not satisfiable: libasound2

I have checked Synaptic and  libasound2 IS installed.

Kind regards.

---

### Post by ptn107 on 2010-02-10
Are you running 64-bit Ubuntu?

If you're running 32-bit Ubuntu you need to have the package 'libasound2' installed.  If your using 64-bit Ubuntu you need to have the package 'lib32asound2' installed.

---

### Post by L Campbell on 2010-02-11
> **ptn107 said:**
> Are you running 64-bit Ubuntu?

If you're running 32-bit Ubuntu you need to have the package 'libasound2' installed.  If your using 64-bit Ubuntu you need to have the package 'lib32asound2' installed.

Thanks for your interest.

I got to feeling like I was kind of 'spinning my wheels', so I replaced my 8.04.4 with 8.10.

8.10 was the only version of Skype that I saw on the Skype website, so I downloaded it and it installed perfectly.

Now I have Skype working I don't need to use XP.    :-)

---

