---
title: "Error in Wine installation ,unable to connect to sourceforge.net."
date: 2010-11-25
forum: New to Ubuntu
---

### Post by alienxx on 2010-11-25
While installing wine I stuck at his step.

```
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-12-14 17:16:10--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-14 17:16:20--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `switch.dl.sourceforge.net'
--2009-12-14 17:16:30--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-12-14 17:16:40--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `dfn.dl.sourceforge.net'
--2009-12-14 17:16:50--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `heanet.dl.sourceforge.net'
--2009-12-14 17:17:00--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-12-14 17:17:10--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `nchc.dl.sourceforge.net'
--2009-12-14 17:17:20--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
```

At this point I terminated process by pressing Ctrl+c

Problem is I am behind my college network proxy which doesn't allow .exe files(andale32.exe).
But somehow wine was apperaing in the Appliations list but I was not using thinking it might give problems.

After some days,Next while installing unity interface on 10.10 Desktop Edition through this command
```
sudo apt-get install unity 
```
It downloaded all the required files and again stuck up at the above mentioned problematic area.It keeps on connecting to that website and fails, and also getting repeated while installing other softwares.

Now I want to "**completely remove WINE and it's traces**" from my computer.
Please help me in resolving this problem.I am 2weeks older as Ubuntu user.

---

### Post by sandyd on 2010-11-25
> **alienxx said:**
> While installing wine I stuck at his step.

```
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-12-14 17:16:10--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-14 17:16:20--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `switch.dl.sourceforge.net'
--2009-12-14 17:16:30--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-12-14 17:16:40--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `dfn.dl.sourceforge.net'
--2009-12-14 17:16:50--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `heanet.dl.sourceforge.net'
--2009-12-14 17:17:00--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-12-14 17:17:10--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `nchc.dl.sourceforge.net'
--2009-12-14 17:17:20--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
```

At this point I terminated process by pressing Ctrl+c

Problem is I am behind my college network proxy which doesn't allow .exe files(andale32.exe).
But somehow wine was apperaing in the Appliations list but I was not using thinking it might give problems.

After some days,Next while installing unity interface on 10.10 Desktop Edition through this command
```
sudo apt-get install unity 
```
It downloaded all the required files and again stuck up at the above mentioned problematic area.It keeps on connecting to that website and fails, and also getting repeated while installing other softwares.

Now I want to "**completely remove WINE and it's traces**" from my computer.
Please help me in resolving this problem.I am 2weeks older as Ubuntu user.

```

sudo dpkg --purge --force all wine wine-gecko
```

---

### Post by alienxx on 2010-11-25
Thanks very much for the reply!!
But not solved.


```
venky@ubuntu:~$ sudo dpkg --purge --force all wine wine-gecko
[sudo] password for venky: 
(Reading database ... 170053 files and directories currently installed.)
Removing wine ...
dpkg: warning: ignoring request to remove wine-gecko which isn't installed.
venky@ubuntu:~$ 

```

Now I have one more problem,since I interrupted(which i'll never do again) the process while installing unity, getting into Netbook Edition giving an error and I have to force shutdown. **I need to remove UNITY also now.** :( :(

---

### Post by sandyd on 2010-11-25
> **alienxx said:**
> Thanks very much for the reply!!
But not solved.


```
venky@ubuntu:~$ sudo dpkg --purge --force all wine wine-gecko
[sudo] password for venky: 
(Reading database ... 170053 files and directories currently installed.)
Removing wine ...
dpkg: warning: ignoring request to remove wine-gecko which isn't installed.
venky@ubuntu:~$ 

```

Now I have one more problem,since I interrupted(which i'll never do again) the process while installing unity, getting into Netbook Edition giving an error and I have to force shutdown. **I need to remove UNITY also now.** :( :(

```

sudo apt-get -f install
sudo apt-get install unity
```

---

