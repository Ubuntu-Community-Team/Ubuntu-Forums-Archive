---
title: "Noob cant install a program called Freesnell, please help!"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by tycho brahe on 2011-07-22
Hi,

Noob here. Trying to install program: [http://people.csail.mit.edu/jaffer/FreeSnell/FreeSnell.html#Installation](http://people.csail.mit.edu/jaffer/FreeSnell/FreeSnell.html#Installation)

Took me AGES to figure out that; 

 #! /bin/sh
     wget [http://groups.csail.mit.edu/mac/ftpdir/users/jaffer/slib.zip](http://groups.csail.mit.edu/mac/ftpdir/users/jaffer/slib.zip)
     wget [http://groups.csail.mit.edu/mac/ftpdir/users/jaffer/scm.zip](http://groups.csail.mit.edu/mac/ftpdir/users/jaffer/scm.zip)
     wget [http://groups.csail.mit.edu/mac/ftpdir/users/jaffer/wb.zip](http://groups.csail.mit.edu/mac/ftpdir/users/jaffer/wb.zip)
     wget [http://groups.csail.mit.edu/mac/ftpdir/scm/FreeSnell.zip](http://groups.csail.mit.edu/mac/ftpdir/scm/FreeSnell.zip)
     unzip slib.zip
     unzip scm.zip
     unzip wb.zip
     unzip FreeSnell.zip
     (cd slib; make install)
     (cd scm; make scmlit; make scm5; make mydlls; make wbscm.so; make install)
     (cd FreeSnell; make install)

Was Code. Put it into terminal, it downloaded some stuff. Wrote cd slib and it changed directory to slib,
But when I put in make install it just says error permission denied???

---

### Post by revinkey on 2011-07-22
did you try doing 
```

sudo make install

```

---

### Post by varunendra on 2011-07-23
> **tycho brahe said:**
> ....
....
 **#**! /bin/sh
Noticed that '**#**' sign in the beginning? It means that the guide assumed that you would be in a **root shell** to execute those commands. Root shell already has root permissions and as such the commands entered in it are allowed to make system-level changes.

Now notice your normal prompt in your terminal. it ends with '$' sign which indicates that the shell/terminal is in **user mode** which doesn't have root permission. But in order to install applications, you do need that 'root-permission'. 'sudo' does just that - for that single command that you type after 'sudo' - that is, runs that command as root.

[B]Hence the command that revinkey suggested. Try it.
[/B] 
Alternatively, you may try** sudo su** (not recommended to a new user) to become root for executing all the subsequent commands as root, until you close the terminal or exit to user mode using **exit** command.

---

### Post by Wim Sturkenboom on 2011-07-23
> **varunendra said:**
> Noticed that '**#**' sign in the beginning? It means that the guide assumed that you would be in a **root shell** to execute those commands. Root shell already has root permissions and as such the commands entered in it are allowed to make system-level changes.


**No, it does not.** *varunendra*, did you notice the exclamation mark (bang) after the hash? The hash bang indicates that it is actually part of a script; it tells the script to use bash as the shell.

I did not follow the link, but I'm sure that the given code was intended to be pasted in a file and saved. Next the file is made executable and can be run with the command
```
./whateverfilenameyouchose
```
Or in this case with sudo prepended

---

### Post by varunendra on 2011-07-23
> **Wim Sturkenboom said:**
> **No, it does not.** *varunendra*, did you notice the exclamation mark (bang) after the hash? The hash bang indicates that it is actually part of a script; it tells the script to use bash as the shell.
Oops! A stupid mistake on my part!!

I'm not yet much familiar with shell scripting, but I do know enough that I should have noticed that 8-[.. Thanks for correcting me Wim.

Actually the guide (at least the linked segment) tells nothing about what exactly to with that code, and for the installation step, we do need root permission.

Sometimes I also need to do it as **sudo ./make install**. But since the OP is getting "permission denied" error, I believe it means the command is already recognized, so he may not need to add ./ in his command and only needs to use sudo.

---

### Post by 3rdalbum on 2011-07-23
> **varunendra said:**
> Oops! A stupid mistake on my part!!

I'm not yet much familiar with shell scripting, but I do know enough that I should have noticed that 8-[.. Thanks for correcting me Wim.

Actually the guide (at least the linked segment) tells nothing about what exactly to with that code, and for the installation step, we do need root permission.

Sometimes I also need to do it as **sudo ./make install**. But since the OP is getting "permission denied" error, I believe it means the command is already recognized, so he may not need to add ./ in his command and only needs to use sudo.

You shouldn't need ./ when doing anything with Make. The ./ means run this in the current directory. The Make command is not in the same directory as the source code you're compiling.

---

### Post by tycho brahe on 2011-07-23
Ah, right... okay, wrote:

> Sudo make install

and it asked for password and looked like it was installing, but then I got a new error (yay, progress, :popcorn:)

> 
makeinfo slib.texi --no-warn --no-split -o slib-3b3.info
make: makeinfo: Command not found
make: *** [slib-3b3.info] Error 127


---

### Post by tycho brahe on 2011-07-23
Okay, the Slib, SCM and WB folders are downloaded and extracted (manually as SCM didnt extract and WB didnt download) as files in my home directory. Do I need to make a folder 'freesnell' and move them all into the same?

---

### Post by ziekfiguur on 2011-07-23
> **Wim Sturkenboom said:**
> **No, it does not.** *varunendra*, did you notice the exclamation mark (bang) after the hash? The hash bang indicates that it is actually part of a script; it tells the script to use bash as the shell.
Actually /bin/sh does not by default point to bash on ubuntu but to dash, which is a similar program but a bit lighter.


> Okay, the Slib, SCM and WB folders are downloaded and extracted (manually as SCM didnt extract and WB didnt download) as files in my home directory. Do I need to make a folder 'freesnell' and move them all into the same? 
No, you should also have downloaded a file FreeSnell.zip, extracted that and installed it.

Wim Sturkenboom was right about the code, if you just paste it in a file like this:
```
#! /bin/sh
wget http://groups.csail.mit.edu/mac/ftpdir/users/jaffer/slib.zip
wget http://groups.csail.mit.edu/mac/ftpdir/users/jaffer/scm.zip
wget http://groups.csail.mit.edu/mac/ftpdir/users/jaffer/wb.zip
wget http://groups.csail.mit.edu/mac/ftpdir/scm/FreeSnell.zip
unzip slib.zip
unzip scm.zip
unzip wb.zip
unzip FreeSnell.zip
(cd slib; make install)
(cd scm; make scmlit; make scm5; make mydlls; make wbscm.so; make install)
(cd FreeSnell; make install)
```
and run ```
sudo ./yourfilename
```
everything should be working

---

### Post by tycho brahe on 2011-07-23
OK, I pasted the code into a text file and saved it as 'free' to my home folder. I went to the terminal and typed;

> 
lord@DeepThought:~$ sudo ./free
[sudo] password for lord: 
sudo: ./free: command not found


I've a lot to learn...

---

### Post by tycho brahe on 2011-07-23
I have also manually downloaded and extracted FreeSnell.zip, so all 4 folders (slib, SCM, WB and FreeSnell are in my home folder....

---

### Post by fdrake on 2011-07-23
```
sudo chmod +x free
sudo ./free
```

---

### Post by tycho brahe on 2011-07-23
Okay, thats done something... I think its installed now... Thanks! Its still not finding some files but its at least partially running.:D

---

### Post by fdrake on 2011-07-23
can you post the output of the terminal maybe we can help

---

### Post by Wim Sturkenboom on 2011-07-25
> **ziekfiguur said:**
> Actually /bin/sh does not by default point to bash on ubuntu but to dash, which is a similar program but a bit lighter.

You're right; I thought the line was bin/bash, not bin/sh. Should have read better :redface::redface:

---

### Post by fdrake on 2011-07-25
> **Wim Sturkenboom said:**
> You're right; I thought the line was bin/bash, not bin/sh. Should have read better :redface::redface:

/bin/bash   bash
/bin/dash   dash
/bin/sh     pre-bash shell

---

