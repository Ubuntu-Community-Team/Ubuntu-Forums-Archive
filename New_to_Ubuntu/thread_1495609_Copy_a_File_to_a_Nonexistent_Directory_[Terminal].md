---
title: "Copy a File to a Nonexistent Directory [Terminal]"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by SKhan on 2010-05-28
I wrote a bash script to copy a file to a directory, that is supposed not to be present when i execute the script.

for this purpose i wrote the following two-line script
```
mkdir ~/Desktop/easystroke_backup
cp ~/.easystroke/actions-0.4.1 ~/Desktop/easystroke_backup
```

here "easystroke_backup" is the nonexistent directory.

Is it possible to write a SINGLE-LINE script which does the same thing?

A command which creates a directory, ONLY IF the directory IS NOT already there.

---

### Post by daverj on 2010-05-28
if [ ! -d ~/Desktop/easystroke_backup ]; then mkdir ~/Desktop/easystroke_backup; fi
cp ~/.easystroke/actions-0.4.1 ~/Desktop/easystroke_backup

---

### Post by kaibob on 2010-05-28
> **SKhan said:**
> I wrote a bash script to copy a file to a directory, that is supposed not to be present when i execute the script.

for this purpose i wrote the following two-line script
```
mkdir ~/Desktop/easystroke_backup
cp ~/.easystroke/actions-0.4.1 ~/Desktop/easystroke_backup
```

here "easystroke_backup" is the nonexistent directory.

Is it possible to write a SINGLE-LINE script which does the same thing?

A command which creates a directory, ONLY IF the directory IS NOT already there.

Your specific command may be written as a one-liner as follows. The mkdir -p option suppresses an error message if the directory already exists:

```
mkdir -p ~/Desktop/easystroke_backup ; cp ~/.easystroke/actions-0.4.1 ~/Desktop/easystroke_backup
```

A general-purpose version of this:

```
#!/bin/bash
mkdir -p "$2"
mv "$1" "$2"
```

SOURCE:
[http://ubuntuforums.org/showthread.php?t=1403831](http://ubuntuforums.org/showthread.php?t=1403831)

---

### Post by lavinog on 2010-05-28
I believe rsync can make the directory for you.

---

### Post by SKhan on 2010-05-28
> **daverj said:**
> if [ ! -d ~/Desktop/easystroke_backup ]; then mkdir ~/Desktop/easystroke_backup; fi
cp ~/.easystroke/actions-0.4.1 ~/Desktop/easystroke_backup
ok but the code given by you has 2 lines and it's even more complex than the one given by me.
i had the doubt that i am using 2 commands for what can easily be done in one simple command, that's why i asked the question in my first post.

---

### Post by SKhan on 2010-05-28
> **kaibob said:**
> Your specific command may be written as a one-liner as follows. The mkdir -p option suppresses an error message if the directory already exists:

```
mkdir -p ~/Desktop/easystroke_backup ; cp ~/.easystroke/actions-0.4.1 ~/Desktop/easystroke_backup
```


i already knew that semicolon technique. :) I meant one single command in one single line. Not two commands in one line. I should have been more clear he he.:)
anyways -p solved my problem. ;) although i will still have to use 2 commands.

there should be a special copy command that copies a file to a given location and if the command fails to find the given location then it will create it on its own.

---

### Post by SKhan on 2010-05-28
> **lavinog said:**
> I believe rsync can make the directory for you.
rsync is tool but i want to use bash file for that purpose.

---

### Post by SKhan on 2010-05-28
> **kaibob said:**
> A general-purpose version of this:

```
#!/bin/bash
mkdir -p "$2"
mv "$1" "$2"
```

SOURCE:
[http://ubuntuforums.org/showthread.php?t=1403831](http://ubuntuforums.org/showthread.php?t=1403831)

I read that thread and it seems to be a solution. altough still there's no default command for this purpose. I will have to create the command.
will you please tell me what $1 and $2 stand for?
can i replace mv with cp because i want to copy the flie and don't want to move the source file.
I am still very new to linux.

---

### Post by kaibob on 2010-05-28
> **SKhan said:**
> will you please tell me what $1 and $2 stand for? can i replace mv with cp because i want to copy the flie and don't want to move the source file.

$1 and $2 are command-line arguments. If you name the shell script mv2 and invoke it as follows:

```
mv2 testfile.txt /home/kaibob/
```

Then $1 would contain testfile.txt and $2 would contain /home/kaibob. You can use cp rather than mv.

---

### Post by lavinog on 2010-05-29
> **SKhan said:**
> rsync is tool but i want to use bash file for that purpose.

You can use rsync in a bash file.
cp and mkdir are not bash commands, but programs.

---

### Post by BoneKracker on 2010-05-29
Yes, they are programs -- but they're an order of magnitude smaller than rsync.

Here's another alternative that's sometimes useful:
```
cp --parents ~/.easystroke/actions-0.4.1 ~/Desktop
```

That will create /Desktop/.easystroke and then copy into it only the file actions-0.4.1.  That gets it done in a single command, but it has the drawback of not renaming the directory (you are creating a "hidden" dot-directory on the desktop).

---

### Post by SKhan on 2010-05-29
> **kaibob said:**
> $1 and $2 are command-line arguments. If you name the shell script mv2 and invoke it as follows:

```
mv2 testfile.txt /home/kaibob/
```

Then $1 would contain testfile.txt and $2 would contain /home/kaibob. You can use cp rather than mv.
thanks. i have understood it.

---

### Post by SKhan on 2010-05-29
> **lavinog said:**
> You can use rsync in a bash file.
cp and mkdir are not bash commands, but programs.
you may be correct, I will try rsync as well.
tell me how come cp and mkdir are programs not commands?

---

### Post by lavinog on 2010-05-29
> **SKhan said:**
> 
tell me how come cp and mkdir are programs not commands?

bash commands like if, for, and while are internal to bash
if you use whereis you will get no location:
```

whereis -b if for while
if:
for:
while:

```

but cp, mv, rsync exist on the filesystem as executable programs:
```

whereis -b cp mv rsync
cp: /bin/cp
mv: /bin/mv
rsync: /usr/bin/rsync

```

---

### Post by SKhan on 2010-05-29
> **lavinog said:**
> bash commands like if, for, and while are internal to bash
if you use whereis you will get no location:
```

whereis -b if for while
if:
for:
while:

```

but cp, mv, rsync exist on the filesystem as executable programs:
```

whereis -b cp mv rsync
cp: /bin/cp
mv: /bin/mv
rsync: /usr/bin/rsync

```

thanks i got it. :)

---

### Post by SKhan on 2010-05-29
> **BoneKracker said:**
> Here's another alternative that's sometimes useful:
```
cp --parents ~/.easystroke/actions-0.4.1 ~/Desktop
```

That will create /Desktop/.easystroke and then copy into it only the file actions-0.4.1.  That gets it done in a single command, but it has the drawback of not renaming the directory (you are creating a "hidden" dot-directory on the desktop).
No!
this is creating a directory ~/Desktop/home and a subdirectory ~/Desktop/home/MyUserAccount
and it's not copying actions-0.4.1 in either directory.
please review the code.

---

### Post by BoneKracker on 2010-05-29
> **SKhan said:**
> No!
this is creating a directory ~/Desktop/home and a subdirectory ~/Desktop/home/MyUserAccount
and it's not copying actions-0.4.1 in either directory.
please review the code.

Oops.  To get rid of the extraneous path elements (/home/MyUserAccount/), just use a relative path:
```
cd ~
cp --parents .easystroke/actions-0.4.1 Desktop
```

And yes, it actually _did_ create the ".easystroke/" directory and copy the file "actions-0.4.1".
Maybe you overlooked that the copy of .easystroke/ is a hidden directory.  It was there.

The code above will create ~/Desktop/.easystroke, if it doesn't exist, and place a copy of "actions-0.4.1" in it.  The only drawback is that it's a hidden directory like the original.  I'm not saying this is a better way than the others in this particular case -- I'm just trying to make people aware of the "--parents" option to cp, which I think is seldom used.

---

### Post by SKhan on 2010-05-31
> **BoneKracker said:**
> Oops.  To get rid of the extraneous path elements (/home/MyUserAccount/), just use a relative path:
```
cd ~
cp --parents .easystroke/actions-0.4.1 Desktop
```

And yes, it actually _did_ create the ".easystroke/" directory and copy the file "actions-0.4.1".
Maybe you overlooked that the copy of .easystroke/ is a hidden directory.  It was there.

The code above will create ~/Desktop/.easystroke, if it doesn't exist, and place a copy of "actions-0.4.1" in it.  The only drawback is that it's a hidden directory like the original.  I'm not saying this is a better way than the others in this particular case -- I'm just trying to make people aware of the "--parents" option to cp, which I think is seldom used.
This one simply does nothing that i can notice. May be it creates folder somewhere that i don't know.
again review the code.

---

### Post by Azrael3000 on 2010-05-31
it creates a hidden directory you need to use **ls -a** to see all directories and files

---

### Post by BoneKracker on 2010-05-31
> **SKhan said:**
> This one simply does nothing that i can notice. May be it creates folder somewhere that i don't know.
again review the code.

See that little dot?  That means it's a hidden directory.  This copies your hidden directory and makes a copy (a hidden directory) on Desktop.  That means you need to 'ls -a' (or in Nautilus, open the folder and press ctrl+h) to see it.  If you original folder weren't hidden, the copy wouldn't be.

Like I said, this may not suit your specific need here (e.g., if you are morally opposed to having it take two commands to achieve this, with the second command renaming the directory to strip the dot), but it's good to know about the 'copy --parents' option.  Most people are aware of 'mkdir -p', but I dont' see 'copy --parents' used very often.

---

### Post by lavinog on 2010-05-31
> **BoneKracker said:**
>  but it's good to know about the 'copy --parents' option.  Most people are aware of 'mkdir -p', but I dont' see 'copy --parents' used very often.

I never knew how to use it.  The man page isn't really obvious:
```

 --parents
              use full source file name under DIRECTORY

```

Thanks for the info.

---

### Post by BoneKracker on 2010-05-31
> **lavinog said:**
> The man page isn't really obvious:```
--parents
              use full source file name under DIRECTORY
```
Yeah. What the heck does that mean? :???:

Some man pages authors seem to prefer "concise" to "complete" or "comprehensible".

---

### Post by mrbiggbrain on 2010-05-31
> **SKhan said:**
> i already knew that semicolon technique. :) I meant one single command in one single line. Not two commands in one line. I should have been more clear he he.:)
anyways -p solved my problem. ;) although i will still have to use 2 commands.

there should be a special copy command that copies a file to a given location and if the command fails to find the given location then it will create it on its own.

You could achieve this pretty easily through creating a custom shell script or writing a clean little c/c++ program. you would just need to try and copy, check for the return value of the cp command, and then execute a mkdir and cp if it does not exist (or just cp if it does) or you could just roll the example previously given into a shell script and execute it that way.

---

### Post by BoneKracker on 2010-05-31
> **mrbiggbrain said:**
> You could achieve this pretty easily through creating a custom shell script or writing a clean little c/c++ program. you would just need to try and copy, check for the return value of the cp command, and then execute a mkdir and cp if it does not exist (or just cp if it does) or you could just roll the example previously given into a shell script and execute it that way.

I think you missed where he said he's trying to see if he can do it with a single command.

---

### Post by SKhan on 2010-05-31
> **Azrael3000 said:**
> it creates a hidden directory you need to use **ls -a** to see all directories and files

thanks i found it on desktop, by accessing desktop folder from nautilus. Before this i didn't hit upon the idea of accessing desktop from nautilus. :)
I already knew how to view hidden files accept for the hidden files on desktop, Otherwise i couldn't have accessed .easystroke in the first place.

---

### Post by SKhan on 2010-05-31
> **BoneKracker said:**
> See that little dot?  That means it's a hidden directory.  This copies your hidden directory and makes a copy (a hidden directory) on Desktop.
Understood. I will take care next time.

> **BoneKracker said:**
> That means you need to 'ls -a' (or in Nautilus, open the folder and press ctrl+h) to see it.
already knew that.

> **BoneKracker said:**
> If you original folder weren't hidden, the copy wouldn't be.
Understood. I will take care next time.

> **BoneKracker said:**
> Like I said, this may not suit your specific need here (e.g., if you are morally opposed to having it take two commands to achieve this, with the second command renaming the directory to strip the dot)
Not morally opposed. Just wanted to know if a single line command to achieve the same goal already exists. 

> **BoneKracker said:**
> but it's good to know about the 'copy --parents' option.  Most people are aware of 'mkdir -p', but I dont' see 'copy --parents' used very often.
--parents still is a bit confusing for me. But i think i will understand it after using it a few times.

---

### Post by SKhan on 2010-05-31
> **lavinog said:**
> I never knew how to use it.  The man page isn't really obvious:
```

 --parents
              use full source file name under DIRECTORY

```


Not being native English speaker, it's even more confusing for me. They should use easy to understand explanations in man pages. Because we refer to man pages only when we want to get some real help. If i am already expert enough to understand that technical language, why would I bother going to man page?

---

### Post by SKhan on 2010-05-31
> **mrbiggbrain said:**
> You could achieve this pretty easily through creating a custom shell script or writing a clean little c/c++ program. you would just need to try and copy, check for the return value of the cp command, and then execute a mkdir and cp if it does not exist (or just cp if it does) or you could just roll the example previously given into a shell script and execute it that way.
thanks but that trick has already been explained in a previous post.

---

### Post by BoneKracker on 2010-05-31
> **SKhan said:**
> --parents still is a bit confusing for me. But i think i will understand it after using it a few times.

You are not alone. :)

Basically, it copies a file and its whole path of directories as well.

Just remember to first 'cd' to the directory above what you want to copy, and use a path relative to that directory.

Let's say there's a file you want to copy into your ~/project/include folder, along with two levels of directories above it (and you do not want any other files in those directories):
```
/usr/include/matroska/c/libmatroska.h
```
then you would do:```
cd /usr/include
cp --parents matroska/c/libmatroska.h ~/project/include
```or```
cd /usr
cp --parents include/matroska/c/libmatroska.h ~/project
```

---

### Post by SKhan on 2010-06-10
> **BoneKracker said:**
> You are not alone. :)

Basically, it copies a file and its whole path of directories as well.

Just remember to first 'cd' to the directory above what you want to copy, and use a path relative to that directory.

Let's say there's a file you want to copy into your ~/project/include folder, along with two levels of directories above it (and you do not want any other files in those directories):
```
/usr/include/matroska/c/libmatroska.h
```
then you would do:```
cd /usr/include
cp --parents matroska/c/libmatroska.h ~/project/include
```or```
cd /usr
cp --parents include/matroska/c/libmatroska.h ~/project
```
understood :p

---

### Post by sinisterstuf on 2011-02-16
> **BoneKracker said:**
> Yes, they are programs -- but they're an order of magnitude smaller than rsync.

Here's another alternative that's sometimes useful:
```
cp --parents ~/.easystroke/actions-0.4.1 ~/Desktop
```

That will create /Desktop/.easystroke and then copy into it only the file actions-0.4.1.  That gets it done in a single command, but it has the drawback of not renaming the directory (you are creating a "hidden" dot-directory on the desktop).
I came here with the same question as OP and this answer is exactly what I needed, somehow I missed --parents in the manpage! Thanks!

---

