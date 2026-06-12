---
title: "Installing tar.gz files/Nokia N95"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by ukbuckstop on 2010-01-24
Hi. I wonder if anyone can help.

I am a happy user of Ubuntu 9.04 and getting more used to installing programs every day. I am getting a bit more confident with terminal, and command lines etc, after many years of using windows....(never going back!)

However, I am still having a problem installing tarball files, (tar.gz) and the ONLY problem I have with Ubuntu, in that the only drawback i have had so far, is that I can't connect my Nokia N95 and use with Ubuntu. However, someone has (apparently) devised a program that works, and supposedly it is compatible and effective. See here [http://bit.ly/8sjptA](http://bit.ly/8sjptA) 

But, I can't for the life of me work out how to run the program. I have extracted the tar.gz file, and tried to follow the instructions in the read me file....but nothing. 

Can anyone help a newbie???:)

---

### Post by Shhnap on 2010-01-24
Inside the install file was this:

> Linux:
Please install all requirements first, for example use this command in Fedora:
# yum install python PyQt4 pybluez python-obexftp python-matplotlib

You can test the installation before you install it:
# cd pc
# ./series60_remote.py

If you want to install the application just run
# ./setup.py install
in your root directory.

This will create the folders /usr/lib/pythonX.Y/site-packages/series60_remote
and /usr/share/series60-remote and a wrapper script in /usr/bin/series60-remote
on Linux.

If you want to change these folders you have to use the --prefix argument (for
example: ./setup.py install --prefix=/usr/local )

To me that means you just have to cd the terminal to that directory and run './setup.py install' and you are done. :) Let tme know if that works.

---

### Post by ukbuckstop on 2010-01-25
Hi thanks for your reply. LOL Not sure what happened whwn I did that...

This was the message in terminal:

Traceback (most recent call last):
  File "./setup.py", line 62, in <module>
    version = __import__('pc.series60_remote').series60_remote.get_version()
  File "/home/peter/Desktop/series60-remote-0.3.90/pc/series60_remote.py", line 14, in <module>
    import lib.device
  File "/home/peter/Desktop/series60-remote-0.3.90/pc/lib/device.py", line 7, in <module>
    import devices.series60
  File "/home/peter/Desktop/series60-remote-0.3.90/pc/devices/series60.py", line 5, in <module>
    import bluetooth
ImportError: No module named bluetooth
peter@peter-laptop:~/Desktop/series60-remote-0.3.90$ 


what next??? :))

oh and thanks dude....:P

---

### Post by Shhnap on 2010-01-28
Whoops, "No module named bluetooth" is the error you want to solve. It looks like you are missing sole sort of bluetooth library for python...what I did is open up a terminal and:

```
$ aptitude search bluetooth
```

That revealed a package called 'python-bluetooth' so if I were you I would install it and try to run the setup again like follows:

```
sudo apt-get install python-bluetooth
./setup.py install
```

If that does not work then let me know.

---

### Post by Jivinathejamboree on 2010-02-16
well, I'm more new... Linux knowledge doesn't exactly speak for itself... how do I CD to a driectory? The tar.gz series60_remote file is on my desktop, in a tangled mess of files...

---

### Post by Shhnap on 2010-02-16
Okay, here is not really the right place to introduce you to the awesome power that is the terminal. You should just know that you have stumbled upon the most powerful program on your machine and, if you learn to use it properly, which should not take too long (like a few weeks). Then you will be able to do everything so much faster.

Here is an introduction: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

In the guide it explains what typing 'cd' in the terminal means; 'cd' is the terminal program for changing directory and you should read the guide to learn how to cd and more.

Once you are done look at the cool things you can do. Ask questions and walk the road to being awesome. :D Just so you know, every developer worth their salt (or superuser) knows how to use a terminal.

---

### Post by aeiah on 2010-02-16
the readme tells you to install dependencies first. the one suggested may be all you need in ubuntu. the readme recommends you run:
```

yum install python PyQt4 pybluez python-obexftp python-matplotlib

```

if you're in fedora (fedora uses yum instead of apt-get or aptitude)

using synaptic (gui package manager), apt-get or aptitude to make sure you have those installed would be your first step. you may find that running 

```
sudo apt-get install python-bluetooth

```

is all you need to install for the dependencies to be met, however.

---

