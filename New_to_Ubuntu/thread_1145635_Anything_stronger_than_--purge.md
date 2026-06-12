---
title: "Anything stronger than --purge?"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by Mariane on 2009-05-01
I put "Other" in the Prefix because I had to 
put something, but what I really mean is "any". 

Sometimes in trying to solve problems I make things 
worse. So I wondered if there is a command which 
allows me to uninstall - reinstall a program I 
have messed up in it's original state. Really in 
its original state. 

For example, I changed settings in a file for the 
alsa drivers called /etc/modprobe.c/alsa-base
A while later I got sound problems again. I did 
sudo apt-get remove --purge alsa-base
sudo apt-get install alsa-base

I knew I had to re-write my change in the 
alsa-base file but... surprise! My change had 
remained. Well, this is a mixed blessing, as now 
I don't have a copy of the original version. 

So, is there a command stronger than --purge which 
really removes EVERYTHING related to what you are 
removing? 

Mariane

---

### Post by spiderbatdad on 2009-05-01
when using --purge you don't want to precede the command with remove. I believe apt-get will only see the remove command. I know the man page says differently. See man apt-get for more details.

When you alter system files, by editing, generally ubuntu automatically makes a back up for you, but it may be hidden. To see for sure, navigate to the directory in a terminal and run ```
ls -al
```
or simply run ```
ls -al /etc/modprobe.d/
```Look for alsa-base~

---

### Post by _Purple_ on 2009-05-01
You can use autoremove to remove packages that were automatically installed to satisfy dependencies. For details on apt-get,
```
man apt-get
```

When you make any changes to the configuration files, it is better to keep backup of the file before making changes so that you can always use it.

---

### Post by spiderbatdad on 2009-05-01
sorry double posted.

---

### Post by zvacet on 2009-05-01
If you want to remove all 

```
sudo dpkg --remove --force-remove-reinstreq package_name
```

---

### Post by brian_p on 2009-05-02
> **Mariane said:**
> 

So, is there a command stronger than --purge which 
really removes EVERYTHING related to what you are 
removing? 

In short, no. If

```
sudo apt-get remove --purge <package>
```

or

```
sudo apt-get purge <package>
```

does not remove everything there is a bug lurking somewhere.

---

### Post by Mariane on 2009-05-04
> **brian_p said:**
> 
If

```
sudo apt-get remove --purge <package>
```

or

```
sudo apt-get purge <package>
```

does not remove everything there is a bug lurking somewhere.


Well, it doesn't. I'll try the dpkg next, looks 
promising. Thank you to all of you. 

Mariane

---

### Post by Vonnick on 2009-05-04
Yes, you can use a command to wipe the entire filesystem. Much better than --purge. :P

---

### Post by decoherence on 2009-05-04
If you aren't sure whether purge is purging the files you want, I suggest you confirm that you're removing the right package. The following command will tell you all the files that were installed by the alsa-base package.

```
dpkg-query -L alsa-base
```

If you want to do it the other way around, searching for a file and getting a package, install apt-file. 

```

apt-file update
apt-file search /etc/modprobe.d/alsa-base

```

which, predictably, gives us alsa-base as the parent package.

So, if this is the package you're talking about, and /etc/modprobe.d/alsa-base.conf isn't being removed by purge... well, let's just see what the output says.

---

