---
title: "sudo rm not finding files"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-04-25
When using *rm* with *sudo*, I'm finding odd situations where *rm* doesn't find the files. Look at the following specific example.
```
$ sudo ls -l /home/michelle/.openoffice.org/3/user/backup/
total 0
-rw-r--r-- 1 michelle michelle 0 2009-04-25 09:07 testfile
$ sudo rm /home/michelle/.openoffice.org/3/user/backup/*
rm: cannot remove `/home/michelle/.openoffice.org/3/user/backup/*': No such file or directory
```Notice how *sudo ls* finds the file, but *sudo rm* doesn't. :confused:

Interestingly, when I run this command on my own directory, then it works. It only fails when using it on other users' directories -- but only some of the directories!

If I explicitly name the file, then *sudo* finds it.
```
$ sudo rm /home/michelle/.openoffice.org/3/user/backup/testfile
```I've worked around this issue with the following cumbersome command, but please could someone explain why *sudo rm* doesn't find the files?
```
$ sudo find /home/michelle/.openoffice.org/3/user/backup/ -type f -print -delete
/home/michelle/.openoffice.org/3/user/backup/testfile
```The computer uses Intrepid 8.10

---

### Post by gandaran on 2009-04-25
is it a file or folder?
for files **rm** is enough
for folders use **rm -r**
there's no need to use sudo for deleting files in home user directory.

---

### Post by Paddy Landau on 2009-04-25
> **gandaran said:**
> is it a file or folder?
A file.
> **gandaran said:**
> there's no need to use sudo for deleting files in home user directory.
That's the point; it's not my own user, but someone else's. I need to use *sudo*.

---

### Post by MrWES on 2009-04-25
None the less -- if it's a folder you need the -r flag for recursive.

Bill

---

### Post by Paddy Landau on 2009-04-25
> **MrWES said:**
> None the less -- if it's a folder you need the -r flag for recursive.
Um, I don't understand your point. I don't want to delete the folder. I want to delete all the files within the folder.

I added the -r to the command, but I get exactly the same result:
```
$ sudo rm -r /home/michelle/.openoffice.org/3/user/backup/*
rm: cannot remove `/home/michelle/.openoffice.org/3/user/backup/*': No such file or directory
```If I remove the asterisk, then it deletes all the files and the folder itself, which is not what I want. I want to delete the files within the folder, but not the folder itself.
```
$ sudo rm -r /home/michelle/.openoffice.org/3/user/backup/
```

---

### Post by lukjad on 2009-04-25
Well, here is something that you can try. It's not a fix, rather it's an alternate method.

Open up a terminal and type:
```
gksudo nautilus
```

Then browse to the file(s) or folder(s) you wish to delete and press Shift+Del. Agree that you wish to permanently delete them, and they should be gone.

---

### Post by spiderbatdad on 2009-04-25
If the file is not writable...which looks like the case in your example. It is writable by the owner but no others. Then, unless you specify the file, the way you did, you must use the -f force option.

```
$ sudo rm -f /home/michelle/.openoffice.org/3/user/backup/*

```

---

### Post by Paddy Landau on 2009-04-25
> **lukjad007 said:**
> gksudo nautilus
Thanks for the idea; I need to code this in a script, though.

---

### Post by Paddy Landau on 2009-04-25
> **spiderbatdad said:**
> ... use the -f force option... sudo rm -f ...
This showed no error (unsurprisingly, as -f suppresses error messages). But it still didn't work; sudo rm seems to think that the file doesn't exist. That's the bizarre thing.

Edit: I've never needed to use -f to delete other people's files when using sudo, so I think that may be a red herring.

---

### Post by spiderbatdad on 2009-04-25
to edit files owned by other users try a root session rather than sudo command. First:```
sudo -i
then
rm -f /home/michelle/....
```

---

### Post by llamabr on 2009-04-25
What happens if you navigate to that folder?  Can sudo rm it there?

---

### Post by Paddy Landau on 2009-04-25
> **spiderbatdad said:**
> to edit files owned by other users try a root session ... sudo -i
This works on the terminal, thanks for the idea, but I don't know how to put this into a script.

---

### Post by Paddy Landau on 2009-04-25
> **llamabr said:**
> What happens if you navigate to that folder?  Can sudo rm it there?
I don't have permission to navigate to that folder.

---

### Post by Paddy Landau on 2009-04-25
Is anyone able to duplicate this problem, or is it just me?

---

### Post by Paddy Landau on 2011-07-23
This is really old, but I've finally figured out the answer to why it happens!

In the code:
```
sudo rm -rf /some/path/*
```... bash expands the asterisk into the actual file names *before* passing the command to sudo. As I do not have access to the path, [FONT=Courier New]sudo rm -rf[/FONT] receives nothing!

You could get around it as follows:
```
sudo ls -1A /some/path/ | sudo xargs --delimiter="\n" -I '{}' rm -rf "/some/path/{}"
```A bit messy, but it does the job.

---

### Post by SoFl W on 2011-07-23
Thank you, I had a question about wildcard usage, that might be the answer to why it didn't work the way I expect.

---

### Post by bodhi.zazen on 2011-07-23
> **Paddy Landau said:**
> This is really old, but I've finally figured out the answer to why it happens!

In the code:
```
sudo rm -rf /some/path/*
```... bash expands the asterisk into the actual file names *before* passing the command to sudo. As I do not have access to the path, [FONT=Courier New]sudo rm -rf[/FONT] receives nothing!

You could get around it as follows:
```
sudo ls -1A /some/path/ | sudo xargs --delimiter="\n" -I '{}' rm -rf "/some/path/{}"
```A bit messy, but it does the job.

or use find ;)

Or use sudo, with quotes 

```
sudo bash -c "rm -rf /some/path/*"
```

---

### Post by bodhi.zazen on 2011-07-23
Actually, sudo rm -rf /somepath/* works here.

> Lets make some test files
bodhi@Fedora:~$mkdir -p test/{one,two,three}
bodhi@Fedora:~$touch test/{one,two,three}/{one,two,three}
bodhi@Fedora:~$ls test/one/
one  three  two

[color=darkred][b]# No errors with that command, removes the above directories and files
bodhi@Fedora:~$sudo rm -rf test/*
bodhi@Fedora:~$ls test/[/b][/color]

[color=green]bodhi@Fedora:~$[/color]

---

### Post by Paddy Landau on 2011-07-23
> **bodhi.zazen said:**
> or use find
I had problems with find in this particular case; I forget what.

> **bodhi.zazen said:**
>  Or use sudo, with quotes
```
sudo bash -c "rm -rf /some/path/*"
```Cool, thanks.

> **bodhi.zazen said:**
> Actually, sudo rm -rf /somepath/* works here.
Try making the directories unavailable to you:
```
sudo chown -R root:root test/{one,two,three}
sudo chmod -R go-rwx test/{one,two,three}
```Then try again with the wildcard.
EDIT: Rather do test itself:
```
sudo chown -R root:root test
sudo chmod -R go-rwx test
```

---

### Post by CaptainMark on 2011-07-23
i have been unable to replicate this error ```
mark@desktop:~/Desktop$ sudo su
root@desktop:/home/mark/Desktop# mkdir testdir
root@desktop:/home/mark/Desktop# touch testdir/testfile
root@desktop:/home/mark/Desktop# chown root testdir/testfile 
root@desktop:/home/mark/Desktop# chmod 700 testdir/testfile 
root@desktop:/home/mark/Desktop# exit
mark@desktop:~/Desktop$ sudo rm testdir/*
mark@desktop:~/Desktop$ ls -l testdir/
total 0

```ive made a test directory and file as root, changed owner to root (just for good measure) and made it so the owner has full rights and no one else has read write or execute permissions and still sudo rm's the files no problems

---

### Post by bodhi.zazen on 2011-07-23
> **CaptainMark said:**
> i have been unable to replicate this error ```
mark@desktop:~/Desktop$ sudo su
root@desktop:/home/mark/Desktop# mkdir testdir
root@desktop:/home/mark/Desktop# touch testdir/testfile
root@desktop:/home/mark/Desktop# chown root testdir/testfile 
root@desktop:/home/mark/Desktop# chmod 700 testdir/testfile 
root@desktop:/home/mark/Desktop# exit
mark@desktop:~/Desktop$ sudo rm testdir/*
mark@desktop:~/Desktop$ ls -l testdir/
total 0

```ive made a test directory and file as root, changed owner to root (just for good measure) and made it so the owner has full rights and no one else has read write or execute permissions and still sudo rm's the files no problems

Odd, I can not replicate it either.

```
bodhi@Fedora:~$ls -lA test
total 12
drwx------. 2 root root 4096 Jul 23 20:35 one
drwx------. 2 root root 4096 Jul 23 20:35 three
drwx------. 2 root root 4096 Jul 23 20:35 two

bodhi@Fedora:~$ls -lA test/one
[color=red]ls: cannot open directory test/one: Permission denied[/color]

bodhi@Fedora:~$sudo !!
sudo ls -lA test/one
total 0
-rw-------. 1 root root 0 Jul 23 20:33 one
-rw-------. 1 root root 0 Jul 23 20:33 three
-rw-------. 1 root root 0 Jul 23 20:33 two

[color=green][b]bodhi@Fedora:~$sudo rm -rf test/*
bodhi@Fedora:~$ls -lA test
total 0[/color][/b]
```

---

### Post by The Cog on 2011-07-24
It is access to the directory (to read the list of contents) that is the issue. If the directory is not readable then filename expansion cannot occur. I was surprised to see that instead of an empty file list, the * gets passed through to the program. I expected it to be expanded to nothing.
```
steve@StevesPC:~/test$ mkdir noaccessdir
steve@StevesPC:~/test$ touch noaccessdir/foo
steve@StevesPC:~/test$ touch noaccessdir/bar
steve@StevesPC:~/test$ echo ls noaccessdir/*
ls noaccessdir/bar noaccessdir/foo
steve@StevesPC:~/test$ chmod 700 noaccessdir
steve@StevesPC:~/test$ sudo chown root noaccessdir
steve@StevesPC:~/test$ echo ls noaccessdir/*
ls noaccessdir/*
steve@StevesPC:~/test$ 

```

---

### Post by sisco311 on 2011-07-24
> **The Cog said:**
> It is access to the directory (to read the list of contents) that is the issue. If the directory is not readable then filename expansion cannot occur.
Yep, you need read and execute permissions for the pathname expansion and write permission to delete files.  

> **The Cog said:**
> 
I was surprised to see that instead of an empty file list, the * gets passed through to the program. I expected it to be expanded to nothing.


In bash you can use nullglob or failglob.

```
shopt -s nullglob
for file in *
do
    :
done

```

```
shopt -s failglob
grep 'PATTERN' *

```

but you have to be careful with nullglob, for example, the following code will list the content of the current working directory:
```

shopt -s nullglob
mkdir new
ls new/*

```

---

### Post by Paddy Landau on 2011-07-24
Everyone, thanks for looking at this.

I have resorted to a script:
```
for FNAME in $( sudo ls -1 "${PATHTODIR}" )
do
        sudo rm -Rf "${PATHTODIR}/${FNAME}"
done
```I'm hoping there's a simpler way, but so far it doesn't look like it.

---

### Post by The Cog on 2011-07-24
How about:
> sudo sh -c "rm -Rf pathname/*"
The quotes stop the filename expansion from happening until sh runs, and does the expansion with elevated rights.

---

### Post by Paddy Landau on 2011-07-25
> **bodhi.zazen said:**
> Or use sudo, with quotes 
```
sudo bash -c "rm -rf /some/path/*"
```
> **The Cog said:**
> ```
sudo sh -c "rm -Rf pathname/*"                      
```
Thank you, I have tried this and it's perfect!

There always is a solution with Linux, isn't there?

Marking as solved...

---

