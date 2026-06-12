---
title: "how to delete a dir"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by bj218 on 2011-04-03
How can I delete a dir that has data in it?

---

### Post by idoitprone on 2011-04-03
this deletes everything inside and the dir

full dir
```
rm -r dir/

```

empty dir
```
rmdir dir
```

---

### Post by garvinrick4 on 2011-04-03
If you want to do it in GUI:
alt/f2 key command:
type in gksudo nautilus
you are now in root in GUI.
go to directory you want to delete and will now do it.
Be careful while in root.

---

### Post by bj218 on 2011-04-03
what did I do wrong?

---

### Post by jeremy101 on 2011-04-03
LOL! Right click on a directory and click "Move to Trash". :)

---

### Post by idoitprone on 2011-04-03
> **bj218 said:**
> what did I do wrong?

I want you to replace the dir i wrote with the actual directory. If you write dir first, then rm will search for dir and also /media/homeubu_/etc. /media/homeubu_/etc just so happens to be write-protected. If you type "y", then you are able to delete the file. You did nothing wrong, execept you type in a file that does not exist dir.

In your case you type 

```
rm -r /media/homeubu_/etc
```

Since you do not understand the basics of the command line, i suggest you to use jeremy101 advice, which is simplier for you.

---

### Post by bj218 on 2011-04-03
> **idoitprone said:**
> I want you to replace the dir i wrote with the actual directory. If you write dir first, then rm will search for dir and also /media/homeubu_/etc. /media/homeubu_/etc just so happens to be write-protected. If you type "y", then you are able to delete the file. You did nothing wrong, execept you type in a file that does not exist dir.

In your case you type 

```
rm -r /media/homeubu_/etc
```

Since you do not understand the basics of the command line, i suggest you to use jeremy101 advice, which is simplier for you.

Where do I put the y?  Where do I find jeremy101?

---

### Post by bj218 on 2011-04-03
Move to trash is not highlited so this does not work!!

---

### Post by idoitprone on 2011-04-03
> **bj218 said:**
> Where do I put the y?  Where do I find jeremy101?

in the terminal 


```
rm: remove write-protected regular empty file `1231415'? "the y goes here"

```

if that does not work, then you may have to add permissions to the directory

```
chmod 777 -R /media/homeubu_/etc
```

then you can delete with any method

---

### Post by grahammechanical on 2011-04-03
From looking at the screen shot I would guess that homeubu is a partion with a Linux OS on it and the etc folder/directory that you want to delete cannot be deleted because it is part of the operating system's folders/directories. Delete the etc folder and you break the OS. Perhaps this is why you are failing to do what you want.

Regards.

---

### Post by garvinrick4 on 2011-04-04
You have a directory in media named homeubu
so when you mount homeubu in nautilus it shows up as homeubu_
delete the /media/homeubu directory and when you mount
that partition it will then be /media/homeubu and not /media/homeubu_

So unmount /media/homeubu_ and then remove that sub-directory /media/homeubu
sudo chown rick: /media/homeubu (rick = your user name) just showing how to put directory in your name in permissions. Can remove from root or sudo below either way.
sudo rm -r -v /media/homeubu

rm command can get you in a lot of trouble if not focused!
Pay attention to Post #10 and do not attempt to remove part of / file system such as /etc

---

### Post by bj218 on 2011-04-04
> **idoitprone said:**
> in the terminal 


```
rm: remove write-protected regular empty file `1231415'? "the y goes here"

```

if that does not work, then you may have to add permissions to the directory

```
chmod 777 -R /media/homeubu_/etc
```

then you can delete with any method

I tried chmod 777 -R /media/homeubu_/etc & what I got is in the attachment!!

---

### Post by Daniel0108 on 2011-04-04
> **bj218 said:**
> I tried chmod 777 -R /media/homeubu_/etc & what I got is in the attachment!!

Try:
> sudo chmod 777 -R /media/homeubu_/etc
or
> sudo rm -R /media/homeubu_/etc

Yours,
Daniel

---

### Post by bj218 on 2011-04-04
> **Daniel0108 said:**
> Try:

or


Yours,
Daniel
see attachment

---

### Post by Daniel0108 on 2011-04-04
> **bj218 said:**
> see attachment

Does the directory really exist?

Type:
> cd /media/homeubu_/ && ls | grep etc
And post me the output :)

-- Daniel

---

### Post by bj218 on 2011-04-04
See screen shot 5.

---

### Post by AlphaLexman on 2011-04-04
Is this a 'Wubi' install?

---

### Post by bj218 on 2011-04-04
no

---

### Post by CharlesA on 2011-04-04
Is there a reason you want to delete the etc folder?

---

### Post by bj218 on 2011-04-04
> **CharlesA said:**
> Is there a reason you want to delete the etc folder?

Yes I want to learn how to delete a file or a dir that is full of data!!

---

### Post by CharlesA on 2011-04-04
> **bj218 said:**
> Yes I want to learn how to delete a file or a dir that is full of data!!
You can learn how to remove a directory that has data in it without crippling the OS on the other drive. /etc is a system directory and shouldn't be removed.

Try this:

```
cd
mkdir test
cd test
touch one two three four five six seven eight nine ten
ls -l
cd ..
rm -rvi test
```

ls -l will show you a list of the ten files located in ~/test.

---

### Post by bj218 on 2011-04-04
> **CharlesA said:**
> You can learn how to remove a directory that has data in it without crippling the OS on the other drive. /etc is a system directory and shouldn't be removed.

Try this:

```
cd
mkdir test
cd test
touch one two three four five six seven eight nine ten
ls -l
cd ..
rm -rvi test
```

ls -l will show you a list of the ten files located in ~/test.

see attachment!!

---

### Post by bj218 on 2011-04-04
> **CharlesA said:**
> You can learn how to remove a directory that has data in it without crippling the OS on the other drive. /etc is a system directory and shouldn't be removed.

Try this:

```
cd
mkdir test
cd test
touch one two three four five six seven eight nine ten
ls -l
cd ..
rm -rvi test
```

ls -l will show you a list of the ten files located in ~/test.

see my second picture??

---

### Post by CharlesA on 2011-04-04
Sounds like there was already a file or directory in your home directory called "test"

Try this:

```
ls -l
```

See if it lists test.

---

### Post by rosencrantz on 2011-04-04
Regarding 'Screenshot-6.png': 
I'm not quite sure what you are trying to do with 
'cd test 123456789' - create directory content? Use CharlesA's method, 'touch one two' instead, it creates empty files named one and two, as can be verified with ls.
rmdir test below that fails because you are already in 'test', and there is no subdirectory in 'test' named 'test'. 
cd ..
rm -r test
would have worked.
Instead of using screenshots, can you copy and paste directly from the terminal? Screenshots are not displayed inline and we can't quote from them.

Cheers,
rosencrantz

---

### Post by MButterman on 2011-04-04
> **bj218 said:**
> Yes I want to learn how to delete a file or a dir that is full of data!!
 
you might want to reconsider removing /etc folder unless you back it up first. There are system sensitive files contained in it that could cause your system harm.
 
A directory can't be deleted in there are files with in, once those files are removed the the directory can be removed. There is a single command for that was provided earlier. Google is also a great reference for command line operations

---

### Post by bj218 on 2011-04-05
What constitutes a file or dir? Also how can I delete something that is
not a file or dir.

bill@bill-desktop:~$ rm -r /media/homeubu/etc
rm: cannot remove `/media/homeubu/etc': No such file or directory
bill@bill-desktop:~$  rm -r /media/homeubu/etcy
rm: cannot remove `/media/homeubu/etcy': No such file or directory
bill@bill-desktop:~$ chmod 777 -R /media/homeubu/etc
chmod: cannot access `/media/homeubu/etc': No such file or directory
bill@bill-desktop:~$ sudo chmod 777 -R /media/homeubu/etc
[sudo] password for bill: 
chmod: cannot access `/media/homeubu/etc': No such file or directory
bill@bill-desktop:~$ sudo rm -R /media/homeubu/etc
rm: cannot remove `/media/homeubu/etc': No such file or directory
bill@bill-desktop:~$

---

### Post by rosencrantz on 2011-04-05
> **bj218 said:**
> What constitutes a file or dir? Also how can I delete something that is
not a file or dir.

bill@bill-desktop:~$ sudo rm -R /media/homeubu/etc
rm: cannot remove `/media/homeubu/etc': No such file or directory
bill@bill-desktop:~$
I think objects are always either files or dirs. 'no such file or dir' means it doesn't exist.

---

### Post by 5149.5 on 2011-04-05
> **rosencrantz said:**
> I think objects are always either files or dirs. 'no such file or dir' means it doesn't exist.
If it's not a file or directory, it must be 'just a bunch of bits'. :popcorn:

---

### Post by bj218 on 2011-04-05
> **rosencrantz said:**
> I think objects are always either files or dirs. 'no such file or dir' means it doesn't exist.

See attachment!!

---

### Post by rosencrantz on 2011-04-05
Looking at your attachment, you are deleting files in /media/homeubu, but are displaying /media/homeubu_ in the file browser. Please check /media/homeubu either via ls or file browser. I am pretty sure you will not find an etc folder.

---

### Post by idoitprone on 2011-04-07
> **bj218 said:**
> What constitutes a file or dir? Also how can I delete something that is
not a file or dir.

bill@bill-desktop:~$ rm -r /media/homeubu/etc
rm: cannot remove `/media/homeubu/etc': No such file or directory
bill@bill-desktop:~$  rm -r /media/homeubu/etcy
rm: cannot remove `/media/homeubu/etcy': No such file or directory
bill@bill-desktop:~$ chmod 777 -R /media/homeubu/etc
chmod: cannot access `/media/homeubu/etc': No such file or directory
bill@bill-desktop:~$ sudo chmod 777 -R /media/homeubu/etc
[sudo] password for bill: 
chmod: cannot access `/media/homeubu/etc': No such file or directory
bill@bill-desktop:~$ sudo rm -R /media/homeubu/etc
rm: cannot remove `/media/homeubu/etc': No such file or directory
bill@bill-desktop:~$

Looking at your screenshots, I agree with rosencrantz, you are typing the directory path incorrectly. That is why you been receiving consistent errors.

try 
```
sudo chmod 777 -R /media/homeubu_/etc                      
sudo rm -R /media/homeubu_/etc                      
```These command that daniel018 kindly modified for me, since you never typed it in correctly.

 Remember Linux is case-sensitive and homeubu is different from homeubu_

---

### Post by bj218 on 2011-04-07
I think my problem all along has been that I did not include the underline at the end of homeubu!! 
The command below worked for 1 file is there a way to remove several files at once from  /media/homeubu_?
sudo rm -R /media/homeubu_/etc

---

