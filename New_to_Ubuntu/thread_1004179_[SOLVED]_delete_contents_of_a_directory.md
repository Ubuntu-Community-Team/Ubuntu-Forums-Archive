---
title: "[SOLVED] delete contents of a directory"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by 007casper on 2008-12-06
I am trying to delete the contents of a directory but leaving the directory. (removing just the contents)

I followed the instructions here... 
[http://www.unix.com/shell-programming-scripting/23528-remove-contents-directory-but-not-directory.html](http://www.unix.com/shell-programming-scripting/23528-remove-contents-directory-but-not-directory.html)

and cant get it to work in the terminal 

tried
```
rm -rf /ROOT/*
```

it didnt give me an error, but the contents still remain in the directory :o

(this is not the root in system, it is the ROOT in the application)

thank you

---

### Post by ibutho on 2008-12-07
Have you tried changing into /ROOT first and then deleting the contents.

---

### Post by linuxguymarshall on 2008-12-07
try 

```
cd /dir/of/file
```



```
dir
```


```
sudo rm names of files
```

---

### Post by xjcannonx on 2008-12-07
I think you should be able to just do a ```
rm *
``` to remove all files in a directory

---

### Post by Kareeser on 2008-12-07
```

sudo rm -r [COLOR="Red"]/path/to/dir[/COLOR]/*

```

Note the asterisk. The "-r" deletes all subdirectories in it as well, and sudo'ing the command lets the command do the dirty work without stopping to ask questions every time a write-protected file appears.

---

### Post by 007casper on 2008-12-07
I also check this out 
[http://ubuntuforums.org/showthread.php?t=976690&highlight=remove+contents+directory](http://ubuntuforums.org/showthread.php?t=976690&highlight=remove+contents+directory)

I am at the root level in the terminal

I have tried Kareeser's command
```
sudo rm -r /ROOT/*
```
I am in the path that has ROOT directory

didnt work... it still has all the contents in the directory :shock:

it gave me an error

rm: cannot remove '/ROOT/*':No such file or directory

I did ls -al 

directory is there

---

### Post by bodhi.zazen on 2008-12-07
All those solutions work, the real question, IMO, is what error message ?

---

### Post by xjcannonx on 2008-12-07
Make sure you cd into the directory you want to delete the files from (or type the full path to the directory in the command that kareeser mentioned) I prefer to cd in thoough because with rm you could easily delete unwanted stuff.

---

### Post by 11hjpphty76lkjj on 2008-12-07
I'm guessing permissions problem.
```

sudo chmod -R 777 <dir to be deleted>
```

Then delete using the above.

---

### Post by zvacet on 2008-12-07
Is directory named ROOT or root?That make difference.

---

### Post by jamesrl on 2008-12-07
Move to the directory that ROOT is in.
I will assume its something like: /usr/local/ROOT/
```

cd /usr/local/ROOT
pwd  
rm -r *

```

---

### Post by 007casper on 2008-12-07
bodhi.zazen >>what error message ?
rm: cannot remove '/ROOT/*':No such file or directory

xjcannonx ~ I cd into the directory that has the ROOT directory, I just need to delete ROOT's contents... 

zvacet - directory is "ROOT" with capital letters - not root

just like kalosaurusrex... I wonder if I should change its permission, it is not 777, but I am at the root level as a user
=============
I am going to cd into ROOT directory and...
 
sudo rm* 

is that the right command?

I just dont want to f*c up anything

---

### Post by tuxcanfly on 2008-12-07
WHOA! Did i hear sudo rm * ?? This may COMPLETELY wipe you hard disk if executed!! Remember that rm * will select . and .. directories too!

---

### Post by xjcannonx on 2008-12-07
```
rm *
```
will delete all files in that direectory that dont have permissions and it wont delete any subdirectories, if the files you want to delete have permissions then you need to use the chmod command mentioned earlier in this post

If you want to see what files it will delete then you can replace rm with ls

---

### Post by jamesrl on 2008-12-07
Your problem seemed to be you kept doing rm -r /ROOT/ and unless your path to root is /ROOT/  it will not work.

Also are you aware that the intrepid 8.10 repository has ROOT (look for root-system, and the appropriate root-plugin).  Not that I would recommend using ROOT, in my opinion there are better tools for HEP analysis than the ones written by physicists at CERN.  [See: [http://www.insectnation.org/howto/problems-with-root](http://www.insectnation.org/howto/problems-with-root) or discussion on wikipedia page, or on mailing list.]

---

### Post by jamesrl on 2008-12-07
rm * will not wipe all your directories clean that you have permission to edit.  The wild card * will not select files that begin with a period '.' such as '.' and '..'.  For example:
try
```

mkdir new
cd new
touch a b .c
rm *

```
(and if you want to be paranoid you can do rm -i to prompt before deleting.)
You will find on ls -a after rm *
that in your directory you still have 
```
.  ..  .c
```

---

### Post by bodhi.zazen on 2008-12-07
> **007casper said:**
> bodhi.zazen >>what error message ?
rm: cannot remove '/ROOT/*':No such file or directory

Well you are not specifying the proper path then.

There is a difference between 

rm -rf ROOT/*

and 

rm -rf /ROOT/*

Use the full path (assuming home)

rm -rf /home/user/application/ROOT

---

### Post by 007casper on 2008-12-07
I would like to thank everyone

especially to  jamesrl
Gee! These Aren't Roasted!

it was scary... and I just went for it

cd /usr/local/ROOT
rm -r *

and it seems to work after all... 

and I have '.' '..'

I am going to be optimistic about this... hoping I havent wrecked anything under the sun

cheers
:-)

thank you, thank you!

---

### Post by 007casper on 2008-12-07
bodhi.zazen even though I solved the issue at hand

sorry for my ignorance but can you explain the difference between the two... even though I used rm -rf /ROOT/* it didnt work before.

I do understand that the proper way would have been rm -rf /home/user/application/ROOT but I prefer to cd into the directory or one up from the directory

rm -rf ROOT/*

and

rm -rf /ROOT/*

???

---

### Post by adult swim on 2008-12-07
rm -rf ROOT/* is going to look for a directory ROOT in the current directory you are in.  rm -rf /ROOT/* is going to look for ROOT in the directory / (which is ubuntu's root directory.)  it cannot delete what it cannot find.

---

### Post by linuxguymarshall on 2008-12-07
you could just 

```
gksudo nautilus
```

and do it through the new, shiny GUI

---

### Post by 007casper on 2008-12-07
adult swim when I was in /usr/local/ I tried to get rid of ROOT's content by using rm -rf /ROOT/* it just seemed like it worked and when I checked the ROOT folder's contents, nothing was deleted in the ROOT folder... and I didnt get any error messages in the terminal.

What do you think I deleted at that point?  I was cd into usr/local... and ubuntu's root directory still there... thank god it didnt get deleted... whew! 

at this point, I wonder why I didnt get an error message, and trying to figure if it deleted anything it wasnt suppose to...

---

### Post by adult swim on 2008-12-07
if you try to delete something that isnt there, nothing is deleted and no error messages are returned.  you probably didnt delete anything because there is nothing at /ROOT.  if you had ran rm -rf /root/* that probably would have been a different story because folders are case sensitive and there is a folder at /root.  it gets kind of confusing talking about a folder name ROOT that isnt rooted in the root directory ;)

---

### Post by 007casper on 2008-12-07
cheers ;-)

---

