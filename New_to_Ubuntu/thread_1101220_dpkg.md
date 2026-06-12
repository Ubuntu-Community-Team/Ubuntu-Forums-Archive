---
title: "dpkg"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by teen eagle on 2009-03-20
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

what can i do for this problem

---

### Post by iaculallad on 2009-03-20
> **teen eagle said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

what can i do for this problem

Open your terminal and issue the command below:

```
sudo dpkg --configure -a
```

You are to input your password afterwards.

---

### Post by teen eagle on 2009-03-20
thank you very much

can you help me to solve the flash player problem it is already installed but youtube and others dont work

---

### Post by iaculallad on 2009-03-20
You could try installing the non-free version:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by taavikko on 2009-03-20
> **iaculallad said:**
> You could try installing the non-free version:

```
sudo apt-get install flashplugin-nonfree
```

That would help, but if user has installed alternate's to view flash, such as gnash or swdec, they should be removed that there is no contradiction.

---

### Post by teen eagle on 2009-03-20
i know that i am boring but he tills me that the plug in is already installed

```

```eagle@pc:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
eagle@pc:~$```

```

---

### Post by -LOC- on 2009-03-20
Are you trying to use flash with Firefox 3.0 which comes with Ubuntu 8.10?  If so, good luck.  I had this problem, too.  It's a bug for some users that currently has no fix.  Firefox would stop working completely if I tried to load up YouTube.  I fixed this problem by going into terminal and running```
sudo apt-get install opera
```  After I started using Opera, I had no problems with YouTube.  I really like FireFox and still use it mainly, but Opera's what I use for flash vids.

---

### Post by taavikko on 2009-03-20
First try to reconfigure flashplugin
```
sudo dpkg-reconfigure flashplugin-nonfree
```

Second does the plugin show when going to address ```
about:plugins
```
in browser URL_bar

---

### Post by teen eagle on 2009-03-20
hahahahahahahahhahaha  i am searching for two days for nothing

ok i will do as you did 

thank u very much

---

### Post by teen eagle on 2009-03-20
> Second does the plugin show when going to address "about:plugins"
in browser URL_baryes it does

---

### Post by benorner on 2009-03-25
I tried 
sudo dpkg --configure -a
but it said 
dpkg: status database area is locked by another process

any suggestions?

Thanks

---

### Post by Lunx on 2009-03-25
> **benorner said:**
> I tried 
sudo dpkg --configure -a
but it said 
dpkg: status database area is locked by another process

any suggestions?

Thanks

You haven't got Synaptic open at the same time by any chance? Not sure if that's your problem, but that's all my level of expertise can offer I'm afraid

---

### Post by Berserker v7 on 2009-03-25
I had problems with flashplugin-nonfree... so i tried adobe-flashplugin and it solved all my troubles... do try it out...

```
sudo apt-get install adobe-flashplugin
```

You need to have the multiverse repositories and third-party software sources selected in System->Administration->Software Sources.

---

### Post by decoherence on 2009-03-25
> dpkg: status database area is locked by another process

This means that dpkg is already doing something, or you have Synaptic running. Close it and try again.

If you don't have Synaptic running, and you haven't started any other commands like 'apt-get', 'aptitude' or 'dpkg,' then maybe your computer is configured to download and install security updates automatically? This can cause dpkg to run automatically at times. This is set in System > Administration > Software Sources (under the Updates tab)

If it is set, then chances are if you try again in a few minutes, it'll work. If it's not set, please post the output of

```
ps aux | grep dpkg
```

In any case, if you can't figure out what program is locking up dpkg's database, rebooting will almost certainly set things right.

If not, you'll have to manually unlock the database, however doing this when you don't have to can cause more harm than good. Try rebooting first.

---

