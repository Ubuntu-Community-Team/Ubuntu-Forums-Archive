---
title: "[SOLVED] ls problems"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by gatucar on 2008-12-26
Hello,
I am completely new to Ubuntu but I am  very interested in learning.
I have a problem with the ls command. 
gatucar@gino-laptop:/home$ ls gatucar 
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos 
gatucar@gino-laptop:/home$ ls Music 
ls: cannot access Music: No such file or directory 

As you see I cannot list some folders. Today I was able to list the Desktop folder (doing the same thing) with no problems but I still can not list subfolders. 
Help will be appreciated.

---

### Post by scorp123 on 2008-12-26
> **gatucar said:**
> Help will be appreciated. Linux ships with a manual that explains most commands. The manual for the "ls" command can be accessed by this command: ```
man ls
``` .. Use the cursor keys, PgUp and PgDown to navigate the pages. Use "q" to quit the manual again.

---

### Post by xjcannonx on 2008-12-26
Basically when you use ls it lists everything in the directory you are currently in, if you wanted the contents of the Music directory you either have to go there with the 'cd' command or you have to type the correct path te that directory...sowething like: ```
ls gatucar/Music
```

---

### Post by albinootje on 2008-12-26
> **gatucar said:**
> Hello,
I am completely new to Ubuntu but I am  very interested in learning.
I have a problem with the ls command. 
gatucar@gino-laptop:/home$ ls gatucar 
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos 
gatucar@gino-laptop:/home$ ls Music 
ls: cannot access Music: No such file or directory 

As you see I cannot list some folders. Today I was able to list the Desktop folder (doing the same thing) with no problems but I still can not list subfolders. 
Help will be appreciated.

Can you post the output of the following :
```

cd
pwd
ls Music

```

---

### Post by 73ckn797 on 2008-12-26
> **gatucar said:**
> Hello,
I am completely new to Ubuntu but I am  very interested in learning.
I have a problem with the ls command. 
gatucar@gino-laptop:/home$ ls gatucar 
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos 
gatucar@gino-laptop:/home$ ls Music 
ls: cannot access Music: No such file or directory 

As you see I cannot list some folders. Today I was able to list the Desktop folder (doing the same thing) with no problems but I still can not list subfolders. 
Help will be appreciated.

Typical terminal entry would be:

```
ls Documents
```

Displays all docs and sub-folders

```
ls Documents/sub-folder
```

*sub-folder being what ever the name is.

That will display any files contained within.

You cannot view the contents of the folders? Is there even anything in there?

---

### Post by dnairb on 2008-12-26
When you do **ls gatucar** it list the directories in the **gatucar ** directory. To list the files in the Music directory:

ls gatucar/Music

or:

cd gatucar 
ls Music

Edit: Ahh, xjcannonx already gave this answer above. Must get my eyes fixed.

---

### Post by namdung on 2008-12-26
> **gatucar said:**
> Hello,
I am completely new to Ubuntu but I am  very interested in learning.
I have a problem with the ls command. 
gatucar@gino-laptop:/home$ ls gatucar 
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos 
gatucar@gino-laptop:/home$ ls Music 
ls: cannot access Music: No such file or directory 

As you see I cannot list some folders. Today I was able to list the Desktop folder (doing the same thing) with no problems but I still can not list subfolders. 
Help will be appreciated.

If you want to see the Music folder
```
gatucar@gino-laptop:/home$ ls gatucar/Music 
```

U need to understand the Directory structures. Do let me know in case.

---

### Post by gatucar on 2008-12-26
> **albinootje said:**
> Can you post the output of the following :
```

cd
pwd
ls Music

```

Thank you for your help. It is very encouraging that there are so many people willing to help.

gatucar@gino-laptop:/home$ cd
gatucar@gino-laptop:~$ pwd
/home/gatucar
gatucar@gino-laptop:~$ Music
bash: Music: command not found

---

### Post by gatucar on 2008-12-26
> **namdung said:**
> If you want to see the Music folder
```
gatucar@gino-laptop:/home$ ls gatucar/Music 
```

U need to understand the Directory structures. Do let me know in case.

Am I doing something wrong?

gatucar@gino-laptop:~$ ls gatucar/Music
ls: cannot access gatucar/Music: No such file or directory

gatucar@gino-laptop:~$ ls home/gatucar/Music
ls: cannot access home/gatucar/Music: No such file or directory

---

### Post by albinootje on 2008-12-26
> **gatucar said:**
> 
gatucar@gino-laptop:~$ ls home/gatucar/Music
ls: cannot access home/gatucar/Music: No such file or directory

Try instead of ls home/gatucar/Music :
ls /home/gatucar/Music

---

### Post by gatucar on 2008-12-26
Albinootje,
OK I tryed it again and it worked. Still it is very strange that it works only sometimes. In addition I tryed to list the Madonna folder and nothing happened.
Any ideas?
Thank you

gatucar@gino-laptop:~$ cd
gatucar@gino-laptop:~$ pwd
/home/gatucar
gatucar@gino-laptop:~$ ls Music
Alberto Plaza                         Madonna
Alejandra Guzman                      musica bajada
Ana Carolina                          Pablo Milanes Y Silvio Rodriguez -
Ana Torroja                           Paulina Rubio
Barry White - You Sexy Thin.mp3       Pavarotti
Bee Gees                              Phil Collins
Cher - If I Could Turn Back Time.mp3  Pink - Get This Party Started.mp3
CREED                                 Ricardo Arjona
Diego Torres                          Ricardo Cocciante
El Concierto [Live] [Disc 1]          Ricardo Montaner
Estopa                                Ricardo Montaner y Franco de Vita
Frank Sinatra                         Richard Marx
Gabriel opensador                     Roxette
Gato                                  Sarah McLachlan
Guns and Roses                        Sergio Dalma
illya kuryaqui                        Shakira
Jewel                                 Skank
Jon Secada                            SUI GENERIS
José Luis Perales                     Tom Jones
Juanes                                Tracy MP3
Juan Luis Guerra                      Victor Manuel
Laura Pauzini
gatucar@gino-laptop:~$ ls home/gatucar/Music/Madonna
ls: cannot access home/gatucar/Music/Madonna: No such file or directory

---

### Post by gatucar on 2008-12-26
Albinootje,
This worked! Thank you.However I am following The Linux Phrasebook and according to the author I should be able to use relative pathways and absolute pathways. So far the absolute paths are working but the relative paths do not. Even more this book uses the relative path to teach the use of the wildcards but I am not able to replicate them in my computer. Any ideas?
gatucar

---

### Post by namdung on 2008-12-26
> **gatucar said:**
> Am I doing something wrong?

gatucar@gino-laptop:~$ ls gatucar/Music
ls: cannot access gatucar/Music: No such file or directory

gatucar@gino-laptop:~$ ls home/gatucar/Music
ls: cannot access home/gatucar/Music: No such file or directory

When u 1st open the terminal, u are in ur main home folder.
Type in terminal
```
pwd
```
This will show ur present working directory.

```
gatucar@gino-laptop:~$ pwd
```
Will show u
```
/home/gatucar
```
This means if u explore ur Computer, then ur in Filesystem-->home-->gatucar

Now use ls command to list the files and direcotries in ur present working directory
```
gatucar@gino-laptop:~$ ls
```

This will show u
**Desktop, Examples, Pictures, Music, Videos, Documents etc**

Now u can go inside any of this directory for ur present working directory by using the cd command
```
gatucar@gino-laptop:~$cd Music
```

**gatucar@gino-laptop:~/Music$ **

Now use the ls command to list the files and directories in ur Music folder
```
gatucar@gino-laptop:~/Music$ ls
```

Are u also familiar with the concept of relative and absolute path?

---

### Post by namdung on 2008-12-26
> **gatucar said:**
> 
gatucar@gino-laptop:~$ ls home/gatucar/Music/Madonna
ls: cannot access home/gatucar/Music/Madonna: No such file or directory

Absolute path always start with "/"
```
gatucar@gino-laptop:~$ ls /home/gatucar/Music/Madonna
```

---

### Post by albinootje on 2008-12-26
> **gatucar said:**
> However I am following The Linux Phrasebook and according to the author I should be able to use relative pathways and absolute pathways. So far the absolute paths are working but the relative paths do not. Even more this book uses the relative path to teach the use of the wildcards but I am not able to replicate them in my computer. Any ideas?

Okay. Try this :
```

cd /
ls home/gatucar/Music/Madonna

```
That should work because you are already in /
/ is the starting point of the Linux directory tree structure.

One little but important warning.
Your music directory shows sub-directories which have a space.
For example "Frank Sinatra".
If you want to use "cd" to go into that sub-directory, or "ls" to list it, the shell (/bin/bash default for Ubuntu users in a terminal) has problems handling this, just like ! & and some other characters, because these special characters (and space) are recognised as different things by /bin/bash
Therefore you can try this instead, using the "" characters to solve that problem :  ls "/home/gatucar/Music/Frank Sinatra"

---

### Post by gatucar on 2008-12-26
Namdung,
It is working. However the Linux book I got says that I should be able to use the relative paths too, and thesse are not working for me. Could you please explain the relative pathways to me?
Thank you

---

### Post by gatucar on 2008-12-26
Great advice,
I knew that Linux had troubles with spaces but I did not know hot to solve that. Thank you again.

---

### Post by namdung on 2008-12-26
> **gatucar said:**
> Namdung,
It is working. However the Linux book I got says that I should be able to use the relative paths too, and thesse are not working for me. Could you please explain the relative pathways to me?
Thank you

A relative path is a path relative to the working directory of the user or application, so the full absolute path may not need to be given.

[http://en.wikipedia.org/wiki/Path_(computing)#Unix_style](http://en.wikipedia.org/wiki/Path_(computing)#Unix_style)

Absolute path : (ur present working directory doesn't matter)
```
gatucar@gino-laptop:~$ ls /home/gatucar/Music/Madonna
```

Relative path : (depends on ur present working directory)
```
gatucar@gino-laptop:~$ ls Music/Madonna
```
Since ur already in */home/gatucar/*.

Hope this helps.

---

### Post by gatucar on 2008-12-26
Namdung,
I got it now! Very good explanation.
Thanks,
Gatucar

---

