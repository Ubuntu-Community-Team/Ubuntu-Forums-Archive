---
title: "Terminal commands understanding how to use them(Help, not an advice or proper use)"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by Like67ninjas on 2009-10-03
Alright, well first off, Hello, happy to be apart of the forums(im new, obviously).

I just made the change to Ubuntu, ive used Windows since my first pc and now that I started using this OS I cant believe that everyone doesnt.

I need some help with terminal commands, what they mean and how to use them properly, I want to start using that as much as possible so I can better understand the OS and I want to get into scripting ect.  

I know Sudo gives you root permissions and thats about as far as it goes, my buddy tried showing me some simple ones, on how to move files and changed directorys but ive already forgotten how to do it all.

I pretty much know sudo apt-get install " " or sudo apt-get remove " " lol

if this is already a thread or there is a part of a thread where this has been answered please point me in that direction or post a link here, thanks in advance for any help.

---

### Post by klytu on 2009-10-03
> **Like67ninjas said:**
> Alright, well first off, Hello, happy to be apart of the forums(im new, obviously).

I just made the change to Ubuntu, ive used Windows since my first pc and now that I started using this OS I cant believe that everyone doesnt.

I need some help with terminal commands, what they mean and how to use them properly, I want to start using that as much as possible so I can better understand the OS and I want to get into scripting ect.  

I know Sudo gives you root permissions and thats about as far as it goes, my buddy tried showing me some simple ones, on how to move files and changed directorys but ive already forgotten how to do it all.

I pretty much know sudo apt-get install " " or sudo apt-get remove " " lol

if this is already a thread or there is a part of a thread where this has been answered please point me in that direction or post a link here, thanks in advance for any help.

Welcome to Ubuntu! Here's a couple of links to get you started with terminal commands and shell scripting:

[http://linuxcommand.org/](http://linuxcommand.org/)
[http://en.tldp.org/LDP/abs/html/](http://en.tldp.org/LDP/abs/html/)
[http://bash.cyberciti.biz/guide/Main_Page](http://bash.cyberciti.biz/guide/Main_Page)

---

### Post by doas777 on 2009-10-03
cd and ls are two key ones. 

cd is "change directory" (same as cd in dos).
ls is "list contents" (same as dir in dos).

so lets say I want to see all the files in /etc/samba, but when I open the terminal, the default location is /home/user/

i could either run:
```
ls /etc/samba
```
or instead of specifying the path, I could change directories to it.
```
cd /etc/samba
ls
```

---

### Post by takiama on 2009-10-03
> **doas777 said:**
> cd and ls are two key ones. 

cd is "change directory" (same as cd in dos).
ls is "list contents" (same as dir in dos).

so lets say I want to see all the files in /etc/samba, but when I open the terminal, the default location is /home/user/

i could either run:
```
ls /etc/samba
```or instead of specifying the path, I could change directories to it.
```
cd /etc/samba
ls
```

dir actually works as well, I did not know about ls so I assumed it was dir and it has been working fine:).  The only difference is that ls changes the color of the item based on file type and dir keeps it the default color.   I am using 9.04 Jaunty so I don't know if it works on earlier versions.  And I totally agree, why ever use any other OS, I was always a windows user myself until I switched just recently like you.

---

### Post by MelDJ on 2009-10-04
see this: [http://www.linuxguide.it/linux_commands_line_en.htm](http://www.linuxguide.it/linux_commands_line_en.htm)

---

### Post by nhasian on 2009-10-04
a few terminal commands good to know:

shutdown -r now
top
pkill
killall
man
sudo for terminal stuff
gksu for gui stuff
ls, cd, mkdir, rm, pwd
cat
press UP to show previous commands
press Control-R to search for a previously entered command
Shift-Insert to paste
pico or vi to edit a document, though vi is complicated for beginners.

---

### Post by klytu on 2009-10-04
> **takiama said:**
> dir actually works as well, I did not know about ls so I assumed it was dir and it has been working fine:).  The only difference is that ls changes the color of the item based on file type and dir keeps it the default color.   I am using 9.04 Jaunty so I don't know if it works on earlier versions.  And I totally agree, why ever use any other OS, I was always a windows user myself until I switched just recently like you.

Funny, I have been using Linux for several years and didn't know about **dir** !

I checked the man pages on both commands (Ubuntu Hardy 8.04) and they are supposed to behave identically. But in fact, as you indicate, **ls** does change the color of the output based on file type. This can be replicated with **dir** by typing ```
dir --colors
``` The colors used for each file type can be changed with the command **dircolors**.

---

### Post by ikisham on 2009-10-04
Also pressing tab in the Terminal completes the name of a file or directory and pressing tab twice does something that I don't remember now... :b

---

### Post by MrWES on 2009-10-04
> **Like67ninjas said:**
> Alright, well first off, Hello, happy to be apart of the forums(im new, obviously).

I just made the change to Ubuntu, ive used Windows since my first pc and now that I started using this OS I cant believe that everyone doesnt.

I need some help with terminal commands, what they mean and how to use them properly, I want to start using that as much as possible so I can better understand the OS and I want to get into scripting ect.  

I know Sudo gives you root permissions and thats about as far as it goes, my buddy tried showing me some simple ones, on how to move files and changed directorys but ive already forgotten how to do it all.

I pretty much know sudo apt-get install " " or sudo apt-get remove " " lol

if this is already a thread or there is a part of a thread where this has been answered please point me in that direction or post a link here, thanks in advance for any help.

The Advanced-Bash Scripting Guide is also a good resource. Section 4 as a list of commands:
[http://www.tldp.org/LDP/abs/html/]("http://www.tldp.org/LDP/abs/html/")

~Bill

---

### Post by scorp123 on 2009-10-04
> **Like67ninjas said:**
>  I need some help with terminal commands, what they mean and how to use them properly ... but ive already forgotten how to do it all. Why not ask the system?

No, I am not making fun of you. Know then that there is this nifty program:
```
apropos
```

"apropos" will suggest commands specific to the topic you ask about. [COLOR="Red"]It's the _only_ command you really need to remember.[/COLOR] And maybe **"man"** to get to the **man**uals, but that's it :D

So let's suppose you want to know how to work with directories but for the life of you, you can't remember the command your buddy showed you. So let's ask the system:

```
> apropos directories

bluetooth-browse (1) - GTK application for browsing directories over Bluetooth
cp (1)               - copy files and directories
dh_clean (1)         - clean up package build directories
dh_compress (1)      - compress files and fix symlinks in package build directories
dh_fixperms (1)      - fix permissions of files in package build directories
dh_install (1)       - install files into package build directories
dh_installchangelogs (1) - install changelogs into package build directories
dh_installdebconf (1) - install files used by debconf in package build directories
dh_installdirs (1)   - create subdirectories in package build directories
dh_installdocs (1)   - install documentation into package build directories
dh_installexamples (1) - install example files into package build directories
dh_installinit (1)   - install init scripts into package build directories
dh_installman (1)    - install man pages into package build directories
dh_installmenu (1)   - install debian menu files into package build directories
dh_installmime (1)   - install mime files into package build directories
dh_link (1)          - create symlinks in package build directories
dh_lintian (1)       - install lintian override files into package build directories
dh_usrlocal (1)      - migrate usr/local directories to maintainer scripts
FcCacheNumSubdir (3) - Return the number of subdirectories in cache.
FcConfigGetCacheDirs (3) - return the list of directories searched for cache files
FcConfigGetConfigDirs (3) - Get config directories
FcConfigGetFontDirs (3) - Get font directories
**[COLOR="Red"]mkdir (1)            - make directories[/COLOR]**
[COLOR="Red"]**rm (1)               - remove files or directories**[/COLOR]
**[COLOR="Red"]rmdir (1)            - remove empty directories[/COLOR]**
[COLOR="Red"]**tree (1)             - list contents of directories in a tree-like format.**[/COLOR]

```

See the number in those brackets? That's the chapter of the manual. Sometimes a user command and e.g. a C programming library might have the same name .... so to differentiate between the two a chapter number can be added to any manual queries.

For example ... if you ask about passwords via **"apropos passwd"** you will get two results that might look the same at first glance:

```
> apropos passwd

passwd (1)           - change user password
passwd (5)           - the password file
```

So, simply invoking **"man passwd"** will give you the manual for the "passwd" binary (because it's the first on the list). So to make sure you'd get e.g. the manual for the **/etc/passwd** config file you'd add the chapter number in the brackets to your query:
```
man 5 passwd
```

So, armed with **"apropos"** and **"man**" you can pretty much look up any shell command you might ever need without having to learn anything by heart. Just knowing how and where to look is more than enough most of the time. Knowing the stuff by heart will then come automagically with time ;)

---

### Post by MrWES on 2009-10-04
Very nice!

---

### Post by ankspo71 on 2009-10-04
> **scorp123 said:**
> Why not ask the system?

No, I am not making fun of you. Know then that there is this nifty program:
```
apropos
```

"apropos" will suggest commands specific to the topic you ask about. [COLOR="Red"]It's the _only_ command you really need to remember.[/COLOR] And maybe **"man"** to get to the **man**uals, but that's it :D


Thanks for mentioning that command. It sure makes things easier. :P
James

---

### Post by praveesh on 2009-10-04
Please see my signature. That points to the linux documentation project . [Http://tldp.org](Http://tldp.org)

---

### Post by starcannon on 2009-10-04
> **nhasian said:**
> a few terminal commands good to know:

shutdown -r now
top
pkill
killall
man
sudo for terminal stuff
gksu for gui stuff
ls, cd, mkdir, rm, pwd
cat
press UP to show previous commands
press Control-R to search for a previously entered command
Shift-Insert to paste
pico or vi to edit a document, though vi is complicated for beginners.

+1 too which I would add:

find
|
grep
nano to edit documents, it is easy, and suitable for most needs.

GL and HF

---

### Post by Like67ninjas on 2009-10-09
Wow, thank you guys so much for all the help, I just got around to checking everything out today, im definitely gonna read up on all this today, thanks again :)

---

### Post by jerome1232 on 2009-10-09
> **klytu said:**
> Funny, I have been using Linux for several years and didn't know about **dir** !

I checked the man pages on both commands (Ubuntu Hardy 8.04) and they are supposed to behave identically. But in fact, as you indicate, **ls** does change the color of the output based on file type. This can be replicated with **dir** by typing ```
dir --colors
``` The colors used for each file type can be changed with the command **dircolors**.


They actually do behave the same, ubuntu just has ls aliased to ls --color=auto, the alias exists in .bashrc for dir as well but is commented out, so if you want dir to give colors, edit .bashrc and uncomment the line in the aliases section.

---

### Post by guriinii on 2009-10-09
Here is a link which helped me loads when I first started:

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by cholericfun on 2009-10-09
just had to try out apropos,
and found ```
fortune
```

what!??
lol

---

### Post by jerome1232 on 2009-10-09
It gives you random quotes and gibbets of wisdom, one of my sigs came from fortune :p.

I have it set to run every time I open a terminal lol.

---

### Post by niteshifter on 2009-10-09
> **klytu said:**
> Funny, I have been using Linux for several years and didn't know about **dir** !

I checked the man pages on both commands (Ubuntu Hardy 8.04) and they are supposed to behave identically. But in fact, as you indicate, **ls** does change the color of the output based on file type. This can be replicated with **dir** by typing ```
dir --colors
``` The colors used for each file type can be changed with the command **dircolors**.

Actually, ls and dir do behave the same. So where does the different behavior of ls come from?

Look in your ~/.bashrc file:
(clipped from mine which is still basically the 'stock' .bashrc)
```
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    [COLOR="Red"]alias ls='ls --color=auto'[/COLOR]
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

```

I mention this to add "alias" to nahasian's list of handy commands to know. If one gets into making new aliases put them in ~/.bash_aliases - makes it easier to maintain / keep track of them. The stock .bashrc file will incorporate your .bash_aliases file automagically.

---

