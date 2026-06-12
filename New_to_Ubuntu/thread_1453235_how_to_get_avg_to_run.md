---
title: "how to get avg to run"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by purdurabo on 2010-04-13
I just down loaded the free AVG anti-virus .deb package. i hit install and nothing happened. then when i finally found the file ./opt/avg   i read the readme file. it said that i needed a dependence( cant remember what it is now) so i went into the synaptic manager and got the dependence i needed,right. then i restarted and still nothing happened. while playing around i tried to change the permittions on the folder and it said that i could not because i was not the owner.
           i was reading about logging in as root. so i tried that and never could figure it out either. so my question is what do i have to do to get this avg to run?

---

### Post by lisati on 2010-04-13
Have a look here: [http://ubuntuforums.org/showpost.php?p=7273980&postcount=6](http://ubuntuforums.org/showpost.php?p=7273980&postcount=6)

---

### Post by purdurabo on 2010-04-13
i copied and pasted [COLOR=RoyalBlue]sudo avgct1[COLOR=Black] and it ask for my pass work, then said that command does not exist

[/COLOR][/COLOR]

---

### Post by lisati on 2010-04-13
> **purdurabo said:**
> i copied and pasted [COLOR=RoyalBlue]sudo avgct1[COLOR=Black] and it ask for my pass work, then said that command does not exist

[/COLOR][/COLOR]

That's **avgctl** with a small "ell", not a number one. :)

---

### Post by SnickerSnack on 2010-04-13
I've never used AVG, but a quick googling turned up this: [http://www.tuxradar.com/content/reviewed-avg-anti-virus-85-linux](http://www.tuxradar.com/content/reviewed-avg-anti-virus-85-linux).

For one thing, you don't log in as root (in ubuntu, there is no root account by default), you simply precede a command that needs root privileges with the command "sudo".  You must be very careful with this, as you can damage your system if you don't know what you are doing.

For example, if I want to update the "locate" database, I run

```
sudo updatedb
```

simply running

```
updatedb
```

will not work.  When using sudo, you will be prompted for your password.  After using sudo once, you will not be prompted for a password in the next few minutes.

Second, you may need to reinstall the .deb file in a way that handles dependencies.  I'm not certain on how to do that since I generally use apt.  I know that you will need to use dpkg, but I am not fluent in its use.  Hopefully, someone who is will come along.

Third, are you sure that you need it?  Afaik, its sole purpose is to scan ntfs filesystems (windows), but you can do that from inside windows using avg or another antivirus.  The only use I can see is trying to repair a damaged windows system from inside linux.  If that's what you're doing, well, then good luck you.

---

### Post by Crunchy the Headcrab on 2010-04-13
Just so you know, those virus programs generally look for windows viruses.  You likely don't need that for Ubuntu.  For one thing windows viruses do not harm linux computers, for another there aren't many viruses that are out in the wild that target linux desktop users.

The best policy, as with windows, is just to avoid shady/risky sites/downloads.

---

### Post by trig on 2010-04-13
Why do you need avg? [http://www.linux.com/news/software/applications/8261-note-to-new-linux-users-no-antivirus-needed](http://www.linux.com/news/software/applications/8261-note-to-new-linux-users-no-antivirus-needed) well ubuntu has one built in i think. look under clamshell.

---

### Post by purdurabo on 2010-04-13
ok now that done somthing. its said opporation sucessful. but still i cant tell that any thing happened. what does that command do anyways? i am new to this command line stuff.

---

### Post by SnickerSnack on 2010-04-13
When you try commands that posters here give you, it's best to copy and paste the text in the terminal so we can see exactly what you've done and the outcome.


edit: I mean highlight the relevant lines in the terminal (which copies to a clipboard), middle click in the forum post field box (which pastes), then highlight that, and click on the button with the # sign to give it a code tag.

Example:

[NOPARSE]```
sudo updatedb
```[/NOPARSE]

makes

```
sudo updatedb
```

---

### Post by lisati on 2010-04-13
> **purdurabo said:**
> ok now that done somthing. its said opporation sucessful. but still i cant tell that any thing happened. what does that command do anyways? i am new to this command line stuff.

As others have said, there's not the same need for antivirus software in Ubuntu as there is with Windows.

It has been a while since I've had AVG on my Ubuntu installation, but if memory serves correctly, avgctl sets things up so that you can use other parts of the AVG system. Once you have run avgctl you can use avgupdate to update its definitions, and avgscan to check for malware.

---

### Post by purdurabo on 2010-04-13
```
sudo avgctl
```
like that?

---

### Post by oldsoundguy on 2010-04-13
and there is nothing in the AVG definitions files that will be in ANY LINUX.  So a SCAN will find nothing every time it is run!

You need to get yourself out of the Windows mindset as far as MALWARE and virus is concerned.

As stated here by many
Linux is NOT Windows!

---

### Post by purdurabo on 2010-04-13
ok i think i got that last bit of instruction, and i appreciate it. now like i said i am new to this "terminal" thing. so if any one can explain it or give me a link to some place helpful i would also appreciate that!

---

### Post by purdurabo on 2010-04-13
this is a linux version of avg. but in the end i guess you are right.

---

### Post by arnab_das on 2010-04-13
to scan a file u should type "avgscan <location>" without the quotes, and to update definitions, the command is "avgupdate".

---

### Post by purdurabo on 2010-04-13
ok you guys are right. i dont need the avg. but how do i get it off my computer now?

---

### Post by arnab_das on 2010-04-13
> **purdurabo said:**
> ok you guys are right. i dont need the avg. but how do i get it off my computer now?

sudo apt-get remove <the name of the .deb file you downloaded>

(dont include .deb in the command, just the filename)

---

### Post by Elfy on 2010-04-13
[https://help.ubuntu.com/community/Antivirus/Avg](https://help.ubuntu.com/community/Antivirus/Avg)

I would have a read of this - there is something about viruses near the beginning -  [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by purdurabo on 2010-04-13
i put
```
sudo apt-get remove avg
```
avg being the name of the file in ./opt/avg   and it said
```
sudo apt-get remove avg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avg
```

---

### Post by arnab_das on 2010-04-13
> **purdurabo said:**
> i put
```
sudo apt-get remove avg
```
avg being the name of the file in ./opt/avg   and it said
```
sudo apt-get remove avg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avg
```

its the "name of the file" you downloaded. not the one in the opt folder. it should be something like "avg85flx-r732-a3168.i386"

---

### Post by purdurabo on 2010-04-13
```
sudo apt-get remove avg85flx-r732-a3168.i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avg85flx-r732-a3168.i386.deb

```this is what i got. the file name is avg85flx-r732-a3168.i386.deb it is in my download folder

---

### Post by arnab_das on 2010-04-13
> **purdurabo said:**
> ```
sudo apt-get remove avg85flx-r732-a3168.i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avg85flx-r732-a3168.i386.deb

```
this is what i got

i just gave u an example. the version of the file you have downloaded might be different. thats what my point was. you should take a look at "your" .deb file (which you have downloaded from the avast website) and then type in the command.

---

### Post by purdurabo on 2010-04-13
that is the name of the file package i downloaded

---

### Post by lisati on 2010-04-13
> **purdurabo said:**
> ```
sudo apt-get remove avg85flx-r732-a3168.i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avg85flx-r732-a3168.i386.deb

```this is what i got. the file name is avg85flx-r732-a3168.i386.deb it is in my download folder

Try:
```
sudo apt-get remove avg85flx
```

---

### Post by purdurabo on 2010-04-13
> **lisati said:**
> Try:
```
sudo apt-get remove avg85flx
```
now that worked!! 
what made it work where as the others did not. pleeeaaaasssseeee explain!!!!!!

---

### Post by purdurabo on 2010-04-13
take that back, this is what i got
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  avg85flx
0 upgraded, 0 newly installed, 1 to remove and 251 not upgraded.
After this operation, 110MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128858 files and directories currently installed.)
Removing avg85flx ...
 * Stopping avgdcat: /opt/avg/avg8/var/run/avgd.pid: No such file or directory
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
 (not running)
 *                                                                       [fail]
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing avg85flx (--remove):
 subprocess installed pre-removal script returned error exit status 150
Errors were encountered while processing:
 avg85flx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by arnab_das on 2010-04-13
no offence to @lisati but try this:

sudo apt-get remove avg85flx-r732-a3168

---

### Post by purdurabo on 2010-04-13
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avg85flx-r732-a3168
```

---

### Post by purdurabo on 2010-04-13
ok i deleted the .deb package by putting it in the trash then emptying it. but how do i get read of the one in m ./opt file?

---

### Post by purdurabo on 2010-04-13
i got it guys!!!
the file was not a file, it was a directory. the code to remove it was
```
sudo rm -r /opt/avg
```

like i said i am new to this terminal thing, but i have learned alot form this web site
[http://lowfatlinux.com/linux-delete-files-rm.html](http://lowfatlinux.com/linux-delete-files-rm.html)

very good place for noobies.

---

### Post by Chronon on 2010-04-13
Another method to uninstall a package installed from a .deb is ```
sudo dpkg -r *package*.deb
```

---

### Post by Matiancai74 on 2010-04-25
sudo dpkg -r avg85lms-r812-a3371.i386
dpkg - warning: ignoring request to remove avg85lms-r812-a3371.i386 which isn't installed.

I have been having exactly the same issue as described in this thread and it seems to me that 'installing' the package doesn't actually install it. It creates a load of folders and unpacks files but AVG does not show up in Synaptic at all, even after following a registration process.

---

