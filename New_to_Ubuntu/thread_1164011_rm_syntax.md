---
title: "rm syntax"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by expatCM on 2009-05-19
I wish to delete all files with the extension of .THM from /home/data and all the subdirectories under that.

I am thinking that the following syntax would work

rm *.THM -R

Is that correct?

---

### Post by regala on 2009-05-19
> **expatCM said:**
> I wish to delete all files with the extension of .THM from /home/data and all the subdirectories under that.

I am thinking that the following syntax would work

rm *.THM -R

Is that correct?

nope.
rm never looks into subdirectories. -R,-r options tells rm to remove directories matching the cmdline. Your cmdline will remove any file *and* directory matching *.THM in the current directory.

To achieve the task you want, you need to use
```

find . -type f -name '*.THM' -exec rm -f '{}' \;

```

explanation: find . tells to search in current directory and subdirectories. -type f tells to only match files and not directories. -name '*.THM' tells to match '*.THM' and -exec rm -f '{}' \; to execute rm -f with the filename substituted to '{}'.


for more information, do
```

man find

```

br, mathieu :)

---

### Post by expatCM on 2009-05-19
ouch .....  thank you very much for saving my neck and for explaining what it should be and why .....

and there was me thinking that -R was going to be recursive ... 

So close to a disaster there....

---

### Post by scorp123 on 2009-05-19
> **expatCM said:**
> and there was me thinking that -R was going to be recursive ... Always make sure you read the manual before you do potentially dangerous stuff: ```
man rm
``` (use cursor keys to navigate, "Q" to quit)

---

### Post by expatCM on 2009-05-19
oh I read it .... that is why I opened the thread.  I was really not clear.

The relevant bit says

-r, -R
remove directories and their contents recursively

Which I interpreted to mean -r was to remove directories and -R was to remove files since I do not see any mention at all of the removal of individual items in the rm command.

It turns out that the approach is totally different (as explained earlier in the thread)  but if you started life with cp/m and then dos the logic behind rm is quite different to say del *.THM /s

---

### Post by andrew.46 on 2009-05-20
Hi ragala,

> **regala said:**
> 

To achieve the task you want, you need to use
```
find . -type f -name '*.THM' -exec rm -f '{}' \;

```

There is perhaps an extra layer of security by using:

```
find . -type f -name '*.THM' **[COLOR="Red"]-ok[/COLOR]** rm -f '{}' \;
```

instead, although this will be a pain if there is a large number of these files :-).

Andrew

---

### Post by scorp123 on 2009-05-21
> **expatCM said:**
> oh I read it .... that is why I opened the thread.  I was really not clear. 

The relevant bit says

-r, -R
remove directories and their contents recursively

Which I interpreted to mean -r was to remove directories and -R was to remove files since I do not see any mention at all of the removal of individual items in the rm command. First of all you have to read the whole thing. Just selectively reading a few bits might be dangerous. Just on the top of the manual page it clearly says:
```

**SYNOPSIS**
       rm [OPTION]... FILE...

``` ... So it clearly shows that options come first (like in most Unix commands) and then the argument (= what to delete in this case).

And as for the part you mention (taken from my Ubuntu 8.10 here):
```
**-r, -R, --recursive**
              remove directories and their contents recursively
```
It clearly says: **"remove *_directories_* and their contents"**

And "-r, -R, --recursive" obviously mean that the three do the same thing and have the same meaning. It's just a matter of personal preference which one you use.

To translate this stuff back into DOS lingo, these two commands **[COLOR="Red"](_WARNING:_ dangerous commands -- _think_ before you type!!)[/COLOR]**: 
```
rm -r /path/to/directory
rm -R /path/to/directory 
```
are the same as:
```
deltree C:\path\to\directory
```

The core of your confusion is that you seem to be used to commands doing multiple things -- which is typical for Microsoft's OS's. On Unix-like operating systems such as Linux most commands do only one thing (no big deal, beause there ways by which you can easily chain a few dozen commands into one single line of code ...). So "***rm file***" does what you think: it deletes a file. Same for "***rm tmp****": it will delete all files called "***tmp-something***". But as soon as you use "***rm -r anything***" it will do _precisely_ what the manual says: it will go after *directories and their contents* ... and not necessarily after individual files.

So if you want to scan sub-directories for the presence of certain files and then have them moved or deleted you have to rethink your approach to this. In DOS you'd simply use the command you already showed. Here you have to formulate what you want in plain English (at least while you're a beginner) and then translate this into Unix lingo.

Plain English:
> Find and print out all files with the name tmp00-something or TMP00-something in all the sub-directories that are present right here and have them moved away to the /tmp directory

Translates into this Unix command:
```
find . -iname tmp00* -print -exec mv {} /tmp/ \;
```
The dot "." means "right here", "-iname" specifies what you're looking for (and it is ignoring the difference between capital and small letters whereas the "-name" parameter would make a difference between the two), "-print" means you want the results printed to the screen, "-exec" means that whatever follows is a command that should be applied to each result, "{}" is a place-holder for each individual result, and "\;" means "hit the enter key" so the "-exec" parameter knows where the command ends.

Once you get the syntax (which surprisingly isn't *that* far away from normal English language, IMHO) it's very easy to have files automagically moved around, deleted, renamed ... whatever.

Just make sure you really really understand the manual pages. It won't hurt to go to e.g. the **/tmp** directory (where only temporary garbage gets stored) and experiment around with files there, e.g. you could easily create garbage files yourself by copying stuff there or by quickly opening an editor and writing a few lines of gibberish into a file ... just for the sake of having a file to "play with" ... before you do what you had in mind for real on the real files.

.
.
.
EDIT: stupid typo removed :D  (it's "-print" and not "-list" .... nvm. :D )

---

### Post by expatCM on 2009-05-22
MAGNIFICENT .... thank you for the time and effort you have put into this post ....  it really is helpful.

I guess the core problem I have is knowing what command to look for in the first place.  It is fine if you know but if you do not you need to work off what you know or what you can discover... it is tough.

Whist it is wrong, Linux rm and Dos del almost go in the same thinking / association ...  I would not really have figured out to use find instead .....

---

### Post by andrew.46 on 2009-05-22
Hi expatCM,

> **expatCM said:**
> I would not really have figured out to use find instead .....

Hmmm.... perhaps this is as good a time as any to pimp a guide I have written on find:

Linux Basics: A gentle introduction to 'find'
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

All the best,

Andrew

---

### Post by expatCM on 2009-05-22
Thank you for expanding this thread :)

---

### Post by scorp123 on 2009-05-22
> **expatCM said:**
>  I guess the core problem I have is knowing what command to look for in the first place. The shell is your friend. Know then that there is this little helpful command:  **apropos**

"**apropos**" knows all commands and what they do. You just have to ask. Let's suppose you wanted to delete files and let's suppose you would not know that there is a "**rm**" command ... So how would you find out? You ask "**apropos**" about what it knows about file deletion:

```
> apropos delete

at (1)               - queue, examine or delete jobs for later execution
atq (1)              - queue, examine or delete jobs for later execution
atrm (1)             - queue, examine or delete jobs for later execution
batch (1)            - queue, examine or delete jobs for later execution
groupdel (8)         - delete a group
lppasswd (1)         - add, change, or delete digest passwords.
shred (1)            - overwrite a file to hide its contents, and optionally delete it
tr (1)               - translate or delete characters
userdel (8)          - delete a user account and related files 
```

So in the above example "apropos" spits out each and every command that has something to do with deletion. Deleting users, deleting batch jobs, deleting .... **and the command about deleting files is missing??? LOL. :D **

This is funny. OK, bad example. Then let's search for the word "remove" and let's see what "apropos" knows about removing stuff:

```
> apropos remove

colrm (1)            - remove columns from a file
computer-janitor-gtk (8) - remove cruft from system (GUI version)
cut (1)              - remove sections from each line of files
delgroup (8)         - remove a user or group from the system
deluser (8)          - remove a user or group from the system
lvremove (8)         - remove a logical volume
modprobe (8)         - program to add and remove modules from the Linux Kernel
pvremove (8)         - remove a physical volume
remove-shell (8)     - remove shells from the list of valid login shells
[COLOR="Red"][B]rm (1)               - remove files or directories
rmdir (1)            - remove empty directories[/B][/COLOR]
rmmod (8)            - simple program to remove a module from the Linux Kernel
unlink (1)           - call the unlink function to remove the specified file
update-inetd (8)     - create, remove, enable or disable entry in /etc/inetd.conf
update-rc.d (8)      - install and remove System-V style init script links
vgremove (8)         - remove a volume group
```

There we go (highlighted in red). Much better.

The numbers in those brackets (as in "rmdir (1)") are chapter numbers of the manual. There might be two commands or function calls that have the same name, but do different things (e.g. one might be a system command whereas the other might be a C function call that could be interesting to programmers ...). Hence they are distinguishable by their chapter number: "Chapter 1" are usually user commands, where as higher chapters such as 8 are more interesting to advanced system administration and programmers. 

One such example of having the same name twice in different chapters is e.g. "time":

```
> apropos time

time (1)             - run programs and summarize system resource usage
time (7)             - overview of time and timers
```

So "**time (7)**" is about how time is measured here (an interesting topic BTW) where as "**time (1)**" is a system command. So with the numbers in those brackets that "apropos" spits out you can make sure you get to the right manual.

So for reading the manual of the system command you'd type:
```
man 1 time
```

But for reading about the various concepts of time on your Linux you'd type:
```
man 7 time
```

Sorry for this long post :)  ... But all you need to remember from this is one single command: ```
[COLOR="Red"]apropos[/COLOR]
```

BTW, the command "**man -k**" has the same function as "**apropos**" ... Just in case you ever run into a system that claims that "**apropos**" is not a valid command (might happen ...) then you could try "**man -k**" instead. :)


```
> apropos apropos

apropos (1)          - search the manual page names and descriptions
```

---

