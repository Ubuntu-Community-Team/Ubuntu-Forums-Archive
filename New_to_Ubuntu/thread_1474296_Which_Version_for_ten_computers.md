---
title: "Which Version for ten computers?"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by McRat on 2010-05-05
We have 10 WinTel computers at work running peer-to-peer Gbit ethernet using a 16-port switch, and a hardware firewall to the internet, with one computer being used as the file server.  We process about 100 spreadsheet reports a month, and have 24,000 reports in our archive.

After playing with Ubuntu a couple days, I decided we are going to move to Ubuntu Linux.  

I want one computer to do the following:

[LIST]
[*]Act as a firewall to the internet.
[*]Be a file server.  No permissions, open access.
[*]Run a midnight backup every night.
[/LIST]

Can I do this with the 32bit Desktop version, or do I need to run the 64bit Server Version?

I'll admit the Ubuntu Server command line confuses me.  I was a wiz at DOS, but I have zero experience with Linux.  If the GUI version will get the job done just as well, I'd run that until I get up to speed with Linux command line control.

---

### Post by steveneddy on 2010-05-05
I think the question you are trying to ask is:

Can I run a GUI on the server version?

The answer is YES

```
sudo apt-get install ubuntu-desktop
```

More server info:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Servers](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Servers)

Let it do it's thing then restart.

You can also turn off/on the GUI to save system resources by:

to start from the command line type

```
sudo /etc/init.d/gdm start
```

to stop in terminal type

```
sudo /etc/init.d/gdm stop
```

In this manner you can have the GUI installed but it doesn't have to run all the time to save the precious resources for the processes that the server runs.

Hope this helps - and look - you learned some more command line stuff.

:popcorn:

---

### Post by McRat on 2010-05-05
Thanks!):P

I will use the AMD64 version for the fileserver, then for the rest, the 32bit version.

---

### Post by 3rdalbum on 2010-05-05
steveneddy's post is not quite correct.

Ubuntu Desktop is essentially Ubuntu Server plus a GUI. So you might as well start with Ubuntu Desktop and add packages, rather than start with Ubuntu Server and fumble around on the command-line to install a GUI.

Also, if you did desire to turn off the GUI temporarily (it saves some system resources, you probably won't need to do it) and you are running **Ubuntu 9.10 or later**:

```
sudo service gdm stop
```

Turning it on again:

```
sudo service gdm start
```

Steveneddys advice is only applicable for older versions of Ubuntu which you probably shouldn't use anyway.

---

### Post by oldfred on 2010-05-06
I do not have a server but have saved a few threads & comments:

Server with extras
[http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3)

Thread on servers More hardware related:
[http://ubuntuforums.org/showthread.php?t=1460267](http://ubuntuforums.org/showthread.php?t=1460267)
I use/sold a lot of linux home servers....
[http://ubuntuforums.org/archive/index.php/t-1286445.html](http://ubuntuforums.org/archive/index.php/t-1286445.html)

Someone posted a link to ipcop which looked very interesting:
[http://www.ipcop.org/1.4.0/en/install/html/decide-configuration.html](http://www.ipcop.org/1.4.0/en/install/html/decide-configuration.html)

---

### Post by steveneddy on 2010-05-06
IMHO - it IS better to start with the server edition and simply add the ubuntu-desktop package as there are way too many things in the desktop packages that you will not need for the server edition.

I run several Ubuntu servers at home and in a mobile application and honestly the server edition in the better way to go.

---

