---
title: "Upgraded app still uses old version"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-05-29
Hi Everyone,

I installed gpodder 2.14 a while back.  Today I noticed on the website that 2.15 for Natty has been released.  So I added the ppa and then 2.15 appeared in synaptic as well.

I clicked upgrade and now synaptic lists the new version as installed.

The problem is that when I run gpodder it runs the old version (2.14).

I've tried reinstalling gpodder.  Completely removing gopdder and then reinstalling it. That didn't seem to really be a complete removal though because when I reinstalled my podcast list was intact.  I thought a complete removal would delete the config file and thus my podcast list. I've logged out and even restarted the machine between installs.

Even though synaptic lists 2.15 installed I get this in the terminal:

```

john@john-11:~$ sudo apt-get install gpodder
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**gpodder is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@john-11:~$ gpodder --version
**gpodder 2.14**
john@john-11:~$

```

Does anyone have any ideas of how I can get the actual newest version to run?  I'm using Ubuntu version 11.04.

---

### Post by wolfen69 on 2011-05-29
Did you completely remove the old version before getting the new one?

---

### Post by GrouchyGaijin on 2011-05-29
> **wolfen69 said:**
> Did you completely remove the old version before getting the new one?

[QUOTE=grouchygaijin]I clicked upgrade and now synaptic lists the new version as installed.[/QUOTE]  I assumed that clicking the upgrade option in synaptic would be enough.

---

### Post by wildmanne39 on 2011-05-29
> **GrouchyGaijin said:**
> I assumed that clicking the upgrade option in synaptic would be enough.Hi, remove the old one first use the remove completely in synaptic, unless there is configuration files from the old one you want saved, but that could cause problems doing it that way.

---

### Post by GrouchyGaijin on 2011-05-29
> **wildmanne39 said:**
> Hi, remove the old one first use the remove completely in synaptic, unless there is configuration files from the old one you want saved, but that could cause problems doing it that way.

I've tried that twice.  Each time, I checked that the program was gone by trying to launch it from the terminal.  Each time I got the message that gpodder isn't installed.

But when I reinstall it via synaptic i'm back at version 2.14

---

### Post by webofunni on 2011-05-29
Did you update apt cache after adding the repo ? 

```

apt-cache show gpodder | grep "Version:"

```

?

---

### Post by dcsoldschool53 on 2011-05-29
Remove the old version of gpodder from your system. Don't try to reinstall it from Synaptic Manager, because it will give you the same 2.14 version.
Basically, when you tried to upgrade before, you didn't upgrade your source.list file or add the signing key. This is why you kept getting the same old version. In the terminal, type```
sudo add-apt-repository ppa:thp/gpodder
```for 11.o4 natty and```
sudo apt-get update
```Open the program for your source.list and add```
deb [http://ppa.launchpad.net/thp/gpodder/ubuntu](http://ppa.launchpad.net/thp/gpodder/ubuntu) natty main
```

---

### Post by GrouchyGaijin on 2011-05-30
> **webofunni said:**
> Did you update apt cache after adding the repo ? 

```

apt-cache show gpodder | grep "Version:"

```

?

Thank you for the reply.
It seems I have both installed:

```

john@john-11:~$ apt-cache show gpodder | grep "Version:"
Version: 2.14-1
Python-Version: 2.6, 2.7
Version: 2.15-1~natty0
Python-Version: 2.6, 2.7

```

How can I remove the 2.14-1 version?

---

### Post by wildmanne39 on 2011-05-30
> **GrouchyGaijin said:**
> Thank you for the reply.
It seems I have both installed:

```

john@john-11:~$ apt-cache show gpodder | grep "Version:"
Version: 2.14-1
Python-Version: 2.6, 2.7
Version: 2.15-1~natty0
Python-Version: 2.6, 2.7

```

How can I remove the 2.14-1 version?
Hi, as long as you now the name you can use this command in terminal
```
sudo apt-get --purge remove packagename
```

---

### Post by dcsoldschool53 on 2011-05-30
> **GrouchyGaijin said:**
> Thank you for the reply.
It seems I have both installed:

```

john@john-11:~$ apt-cache show gpodder | grep "Version:"
Version: 2.14-1
Python-Version: 2.6, 2.7
Version: 2.15-1~natty0
Python-Version: 2.6, 2.7

```How can I remove the 2.14-1 version?

I just tried the same commad, and here is what I got```
 apt-cache show gpodder | grep "Version:"
Version: 2.15-1~lucid0
Python-Version: 2.6
Version: 2.2-1
Python-Version: 2.6

```I am guessing that you never removed the old version at all.

---

### Post by webofunni on 2011-05-30
I dont think it is a problem of repo or apt cache. I tried tit and got the same result. I can see that there is a bug/mistake in the new package that you are installing. I done 

```

wget http://ppa.launchpad.net/thp/gpodder/ubuntu/pool/main/g/gpodder/gpodder_2.15-1~natty0_all.deb
dpkg-deb --extract gpodder_2.15-1~natty0_all.deb tmp
grep -ir __version__ tmp/usr/share/pyshared/gpodder/__init__.py 

```

and this is what I got

```

grep __version__ tmp/usr/share/pyshared/gpodder/__init__.py 
__version__   = '2.14'

```

Please contact the package maintainer to fix it.

---

### Post by webofunni on 2011-05-30
> **dcsoldschool53 said:**
> I just tried the same commad, and here is what I got```
 apt-cache show gpodder | grep "Version:"
Version: 2.15-1~lucid0
Python-Version: 2.6
Version: 2.2-1
Python-Version: 2.6

```I am guessing that you never removed the old version at all.

I wonder how can it is possible to remove one package from cache unless we remove the entire repo.

---

### Post by dcsoldschool53 on 2011-05-30
Try this,```
sudo apt-get --purge remove gpodder
```Then type each of these commands separately in the terminal
```
sudo add-apt-repository ppa:thp/gpodder
sudo apt-get update
sudo apt-get install gpodder

``` to install the updated version.

---

### Post by dcsoldschool53 on 2011-05-30
> **webofunni said:**
> I wonder how can it is possible to remove one package from cache unless we remove the entire repo.

He only had one version, and it was 2.14.

---

### Post by webofunni on 2011-05-30
There will be 2 versions in cache

```

apt-cache show gpodder | grep -i version
Version: 2.14-1
Python-Version: 2.6, 2.7
Version: 2.15-1~natty0
Python-Version: 2.6, 2.7

```

the command apt-get putge, as far as I know deletes only the installed package. It will not remove from apt-cache. also I can see that apt installs the correct package. 

```

Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up python-feedparser (4.1-14) ...
Setting up python-mygpoclient (1.4-1) ...
Setting up libtidy-0.99-0 (20091223cvs-1) ...
Setting up python-mutagen (1.19-2build1) ...
Setting up python-gpod (0.8.0-2) ...
Setting up python-utidylib (0.2-6) ...
Setting up python-pymtp (0.0.4-2) ...
Processing triggers for python-central ...
Setting up gpodder (2.15-1~natty0) ...
Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

It is installing 

```

Setting up gpodder (2.15-1~natty0) ...

```

But the version hard coded in the application is wrong. That is what I can observe.

---

### Post by dcsoldschool53 on 2011-05-30
You didn't remove the first version before installing the second version.
```
sudo apt-get --purge remove gpodder
```OK I see what you are saying now

---

### Post by dcsoldschool53 on 2011-05-30
ok Run the program. What version does it show

---

### Post by webofunni on 2011-05-30
> **dcsoldschool53 said:**
> ok Run the program. What version does it show

What 

```
gpodder --version
```

shows in your system ?

---

### Post by dcsoldschool53 on 2011-05-30
> **webofunni said:**
> What 

```
gpodder --version
```shows in your system ?

I don't have the program any more...I removed it.

---

### Post by webofunni on 2011-05-30
It should be showing the hard coded version. Thats what I got. I am not able to see any other reason.

---

### Post by GrouchyGaijin on 2011-05-30
> **dcsoldschool53 said:**
> Remove the old version of gpodder from your system. Don't try to reinstall it from Synaptic Manager, because it will give you the same 2.14 version.
Basically, when you tried to upgrade before, you didn't upgrade your source.list file or add the signing key. This is why you kept getting the same old version. In the terminal, type```
sudo add-apt-repository ppa:thp/gpodder
```for 11.o4 natty and```
sudo apt-get update
```Open the program for your source.list and add```
deb [http://ppa.launchpad.net/thp/gpodder/ubuntu](http://ppa.launchpad.net/thp/gpodder/ubuntu) natty main
```

I removed gpodder via synaptic.  Then ran
```

sudo add-apt-repository ppa:thp/gpodder
```
I then ran
```
sudo apt-get update
```

 [IMG]http://dl.dropbox.com/u/23115609/Screenshot-Software%20Sources-1.png[/IMG]
I checked and the gpodder ppa url was still there from when I added it earlier.

At this point, typing gpodder in the terminal gets a program not installed error.  (good)

If I install gpodder again I see that 2.15 is installing, but 2.14 launches.

I just saw webofunni's post that there is a bug in the new package and he got the same result.  Boy do I feel better!  I'll file a bug report.

Thank you for all the help!

---

