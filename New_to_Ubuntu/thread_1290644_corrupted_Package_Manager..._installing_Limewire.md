---
title: "corrupted Package Manager... installing Limewire"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by tcbermy on 2009-10-13
Thanks all in advance!

I am new to Ubuntu, just a few weeks.  While i am a confident user of PC's and the MS world i do not go into the guts too much so please try to keep instructions really simple.

i have tried to search the forums but returned no matches.

i was Installing Limewire and for some reason the process hung up, (i have very slow and unrealizable internet and i believe it hung during a download of one of the packages)

i was downloading from the website and not through the package manager.
i could not re-start the install because i get an error that says an action is in process.
and i cannot open the package manager: i get the following error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I do not know how to do this.  any help would be appreciated.
tc

---

### Post by wojox on 2009-10-13
In the terminal run:

```
sudo dpkg --configure -a'
```

---

### Post by tcbermy on 2009-10-13
> **wojox said:**
> In the terminal run:

```
sudo dpkg --configure -a'
```


I assume the 'Terminal' is like the windows "RUN" utility?  but where is it?  
sorry but could you give me a path:

System>Administration>???

Thanks again.

---

### Post by jeremyswalker on 2009-10-13
Applications > Accessories > Terminal

---

### Post by marshmallow1304 on 2009-10-13
Applications -> Accessories -> Terminal

Edit: Bah! Beaten to the punch.

You can also get there by Alt+F2 then typing gnome-terminal and pressing Enter.

---

### Post by tcbermy on 2009-10-13
i get the following

sudo dpkg --configure -a'
[sudo] password for taran: 
dpkg: unknown option -


Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [

i am afraid i do not know what any of this means! i tried to keep away from the RUN utility when i used Win.

Thanks all!

---

### Post by tcbermy on 2009-10-13
OK,OK,OK

so i took out the ' at the end and now i get:

taran@taran-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
taran@taran-laptop:~$ 

I and the only user, and i believe i have all privileges?

---

### Post by wojox on 2009-10-13
Sorry tcbermy, that was my fault. :P

You still have to run sudo.

---

### Post by marshmallow1304 on 2009-10-13
> **tcbermy said:**
> OK,OK,OK

so i took out the ' at the end and now i get:

taran@taran-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
taran@taran-laptop:~$ 

I and the only user, and i believe i have all privileges?

You left out the sudo.

---

### Post by jeremyswalker on 2009-10-13
> **wojox said:**
> 
```
**sudo** dpkg --configure -a
```

.

---

### Post by ace007 on 2009-10-13
Sudo is something you affix to the beginning of a command to tell the system to run the command as the "root". Use google to find out exactly who root is.

If your account is an administers account that doesn't you can just delete or install things all willy nilly. You'll have to use sudo to let Ubuntu know you mean to run the command as root. Being an administer means you're allowed to temporarily become root. Think of it as a safety, you can't delete any system files or do anything catastrophic without invoking sudo.

Oh, and something you'll need to learn since your coming from windows. The error message reported generally tells you exactly what is wrong and possibly how to fix it. Dont just cry when you see an error, try to read it and go from there.

---

### Post by tcbermy on 2009-10-13
Getting there:

I ran:
taran@taran-laptop:~$ sudo dpkg --configure -a
Setting up java-common (0.28ubuntu3) ...

and now the package manager is working again!!!! sorry for the painful progress! :}

It now tells me:

[I]You have 1 broken package on your system!

Use the "Broken" filter to locate it.[/I]

I go to CUSTOM FILTERS
and select BROKEN

i then found the broken package.  it did not allow me to remove it immediately because it was too inconsistent.  so i completed the install and everything seems to be working properly now!!  :)

It is so great to be able to get help and fix minor errors in a system yourself! :)
Thanks to all the forum for the help and the patience.

---

