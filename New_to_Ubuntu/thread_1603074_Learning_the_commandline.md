---
title: "Learning the commandline"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by simolokid4 on 2010-10-22
Hey people,

Recently I've gone to the local library and got myself a system-management book for linux, and im going steady. Just the questions below I haven't been able to figure out.

Tough im sure it's something small, I just can't get them to work properly.

Could someone point me in the right direction? Thanks.

> Make a file where all errors will be put when u give the command to:
use grep to find all files in /etc which contain the word 'root'.(According to my linux book it has to contain atleast 30-40 lines, im only getting 7.)
Command so far:
```
ls /etc -R grep *root* 2> /home/myname/errorfile
```Clue of this is to edit the errorfile with vim. Since It says like 'edit line 25 ' I could just edit some other line, but I'd like to be sure im using the correct command :)

> Start a background proces where all files in /usr will be placed in a tar archive in the /home dir of your account. Then break this proces using ctrl + c for example.Command so far:
```
cat /usr/* tgz /home/myname
```Thanks for any response.

Note that this is NOT for school, just some self-studying i decided to do.

Kind regards,

Simolokid

---

### Post by ArgusVision on 2010-10-22
First things first. Each command has a syntax, an order that it must follow. Just like the english language has a particular order you expect to receive the words in. Usually the syntax is: 
   $ command -option argument1 argument2

Like the **ls** command you are using. ```
ls -R /etc
``` should display the contents of your /etc directory recursively.

It looks like you are trying to search (**grep**) the output for *root* (anything-root-anything). 
To do this you need a pipe | . Just hold shift+\ on most keyboards. The pipe allows you to "pipe" the output of the first command into the input of the second. In this case the second is **grep**. So the line:
```
$ ls -R /etc | grep *root*
``` should pipe the recursive list of /etc through grep and display the results.

Now, the **2>** at the end. I'm pretty sure that should be **&2>** in order to display the error out. -Someone correct me if I'm wrong.-

In the second line you posted, I'm not sure exactly what you're trying to do... **cat /usr/*** should display the contents of every file in the /usr directory. many of which are binary. So you'll get a very long list of garbage and probably have to shut down your terminal to get it back. If you're trying **cat /usr/*tgz** , that should display the contents of every file ending in tgz. Which are zipped tarfiles. Again, this will only output garbage.

Also, if you want more information on each command you can use the **man** command. ```

$ man ls
``` for example would explain the useage and options for the ls (list) command
Hope this helped a little.

---

### Post by ironic.demise on 2010-10-22
He wants to archive all /usr files into ~/*.tgz
Well, Cat "types out files"
you want to type a "man tar"
I don't have a shell available to check but it SHOULD go something like
"tar -cv /usr/* ~/usr.tgz"
that being tar(command) -cv(options, compress and verbose iirc) /usr/* (the files to compress, all in /usr) and ~/usr.tgz (where to compress them to, that being a .tgz file called usr in the ~/(home) directory).
 
OH and to start a process in the background, end it with &
 
so
```
 tar -cv /usr/* ~/usr.tgz &
```
Double check the options though... I'm not too sure

---

### Post by simolokid4 on 2010-10-22
```
$ ls -R /etc | grep *root*
```

I just tried it and I got a couple of premission denied errors (5 or so ).
Then i sudo'd it and it simply did nothing. Was done within a second, no errors and no output given.

Am I doing something wrong or is the assignment in my book seriously weird?

As for the archiving assignment. It seems to do more then nothing, but I can't seem to stop the proces with ctrl + c. It simply ignores it and just keeps archiving.

Any ideas?

Thanks alot for the help so far ;)

Kind regards

---

### Post by Hippytaff on 2010-10-22
If there is nothing after grep it means grep didn't find what it was told to look for.

---

### Post by haldean on 2010-10-22
When running grep, you don't need to put in wildcards. It will automatically search for the argument anywhere in a line. So when you run:
```
grep *root*
``` 
You're actually searching for the phrase "*root*" *not* "root". You want to run:
```
grep root
```

---

### Post by Stephen Morgan on 2010-10-22
Are you wanting to search for "root" in the files in /etc or in the TITLES of the files? Because the **ls** command will only list the names of files, so grep will only return the names of files with root in the name.

"use grep to find all files in /etc which contain the word 'root'. 			 		" - sounds like you'd be better off using **cat** rather than **ls** for this one.

As for this:

"Make a file where all errors will be put when u give the command to:"

Make a file: **echo > errors**
direct error messages into file:** [command] 2> errors**

That ought to put any errors returned by the commands into the file errors, which can be read with **cat errors**

---

### Post by ironic.demise on 2010-10-22
tar --create --add-file/usr/* ~/usr.tgz
--create can be used instead of -c

---

### Post by ArgusVision on 2010-10-22
Tar is one of those strange commands that don't follow the same syntax. 
It uses: **command** **options**(no dash) **file_name**(where you're putting it) **source**

for example ```
tar czf usr.tgz /usr/*
```

Will create a file called usr.tgz in your home directory containing the contents of your /usr directory.

---

### Post by Hippytaff on 2010-10-22
> **ArgusVision said:**
> Tar is one of those strange commands that don't follow the same syntax. 
It uses: **command** **options**(no dash) **file_name**(where you're putting it) **source**

for example ```
tar czf usr.tgz /usr/*
```Will create a file called usr.tgz in your home directory containing the contents of your /usr directory.

that has helped me no end...I was going around in loops thinking the syntax was the same a cp...

```

cp /place/folder/file/ /anotherplace/anotherfolder/file

```

sorry butt in :-)

---

### Post by ArgusVision on 2010-10-22
Glad I could help.

---

