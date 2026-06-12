---
title: "read only how to change"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by bj218 on 2010-09-29
How do I change an open office odt read only file so that I can add/remove data.

---

### Post by bbqsandwich on 2010-09-29
> **bj218 said:**
> How do I change an open office odt read only file so that add/remove data.

In a terminal: 

```
chmod 755 filename.odt
```

---

### Post by bj218 on 2010-09-29
> **bbqsandwich said:**
> In a terminal: 

```
chmod 755 filename.odt
```

Ubuntu9.10 is on my B drive. On another partition of this drive is miscu where I keep Misc. items.
As you can see below the command you suggested did not work or I did something wrong!!

 root@bill-desktop:/media/miscu# chmod 755 /md5 how to ck.odt' 

chmod: cannot access `/md5': No such file or directory

chmod: cannot access `how': No such file or directory

chmod: cannot access `to': No such file or directory

chmod: cannot access `ck.odt \nroot@bill-desktop:/media/miscu# chmod 755 /md5 how to ck.odt': No such file or directory

---

### Post by ddonohu2 on 2010-09-29
For various reasons the terminal doesn't like spaces in file names. If you rename the file without spaces then this should work.

---

### Post by ArrSea on 2010-09-29
You could also use quotes "   " around the file name like this...

"/media/whatever/filename with spaces.odt"

---

### Post by Tibuda on 2010-09-29
If you are using standard Ubuntu with Gnome, then you can right-click the file, choose "Properties", and change the options in the "Permissions" tab.

I think there's something similiar in Kubuntu or Xubunut.

---

### Post by Tibuda on 2010-09-29
> **bj218 said:**
>  root@bill-desktop:/media/miscu# chmod 755 /md5 how to ck.odt' 

and why are you running as root?

---

### Post by bbqsandwich on 2010-09-30
> **bj218 said:**
> Ubuntu9.10 is on my B drive. On another partition of this drive is miscu where I keep Misc. items.
As you can see below the command you suggested did not work or I did something wrong!!

 root@bill-desktop:/media/miscu# chmod 755 /md5 how to ck.odt' 

chmod: cannot access `/md5': No such file or directory

chmod: cannot access `how': No such file or directory

chmod: cannot access `to': No such file or directory

chmod: cannot access `ck.odt \nroot@bill-desktop:/media/miscu# chmod 755 /md5 how to ck.odt': No such file or directory

As ddonohu2 said, this happened because of the spaces in the filenames. You can tell because it interprets "how," "to" and "ck.odt" as separate files.

In general it is best to use underscores or dashes instead of spaces in filenames (I prefer underscores, myself!). :)

---

### Post by bj218 on 2010-09-30
> **ArrSea said:**
> You could also use quotes "   " around the file name like this...

"/media/whatever/filename with spaces.odt"

bill@bill-desktop:/media/miscu$ chmod 755 "/md5 how to ck.odt"
chmod: cannot access `/md5 how to ck.odt': No such file or directory
bill@bill-desktop:/media/miscu$ 

What is the next thing I should try?

---

### Post by bj218 on 2010-09-30
> **Tibuda said:**
> If you are using standard Ubuntu with Gnome, then you can right-click the file, choose "Properties", and change the options in the "Permissions" tab.

I think there's something similiar in Kubuntu or Xubunut.

I am using standard Ubuntu with Gnome & I changed all 3 of the entries in the "Permissions" tab. to read/write but it did not work.

---

### Post by davidmohammed on 2010-09-30
the reason why that fails is because you are trying to change a file located in the root partition.

Are you in the correct folder?

e.g.

cd <some folder>
chmod 755 <your space.odt file>


to give you another example

cd Downloads
chmod 755 "my space.odt"


Better still - just right click the file - choose properties and and change the permissions in the Permissions tab.

---

### Post by ddonohu2 on 2010-09-30
As davidmohammed mentioned, the problem now is that you've included a / before the file name (which I should have noticed earlier, sorry). This means you are trying to execute the command on a file in the / (root) directory, rather than the local directory. Instead of the command you entered you should probably do this:

bill@bill-desktop:/media/miscu$ chmod 755 "md5 how to ck.odt"

---

### Post by emoguitarist06 on 2010-09-30
**OR**

[B][COLOR="Red"]ALT+F2
gksudo nautilus[/COLOR][/B]

type password

now nautilus the file manager will open as root and you can navigate to your "B" drive and right click that file and change the permissions and change the group to allow yourself access :)

---

### Post by adwhitenc on 2010-09-30
> **bj218 said:**
> bill@bill-desktop:/media/miscu$ chmod 755 "/md5 how to ck.odt"
chmod: cannot access `/md5 how to ck.odt': No such file or directory
bill@bill-desktop:/media/miscu$ 

What is the next thing I should try?

Is /md5 a folder?

---

### Post by bj218 on 2010-10-02
> **adwhitenc said:**
> Is /md5 a folder?

no
/media/miscu/md5 how to ck.odt

---

### Post by davidmohammed on 2010-10-03
try

chmod 755 "/media/miscu/md5 how to ck.odt"



or


cd /media/miscu/
chmod 755 "md5 how to ck.odt"

---

### Post by bj218 on 2010-10-03
> **davidmohammed said:**
> try

chmod 755 "/media/miscu/md5 how to ck.odt"



or


cd /media/miscu/
chmod 755 "md5 how to ck.odt"

bill@bill-desktop:~$ chmod 755 "/media/miscu/md5 how to ck.odt"
bill@bill-desktop:~$ 
this did not work 
Whats next?

---

### Post by Bradtek on 2010-10-03
Open the file
then
File Menu | Save a Copy

---

### Post by cariboo on 2010-10-03
You need to use sudo to change the file permission.

```
sudo chmod 755 "/media/miscu/md5 how to ck.odt"
```

You need to be root, as your regular user doesn't own the directory the file is located in. You may want to change the ownership too, as with a permission of 755 you only have read access as a regular user:

```
sudo chown bill:bill "/media/miscu/md5 how to ck.odt"
```

---

### Post by bj218 on 2010-10-07
Thanks to all I will probably get back to this problem in the near future
I hope!! I had a problem trying to install Ubuntu10.04 & I tried a suggestion I got from the internet & now my 250GB drive is blank. I thought about committing suicide but changed my mind I think I will see if there is a way to salvage this drive??

---

### Post by Quackers on 2010-10-07
Don't do it :-) There is usually help available.
Can I assume that nothing is bootable now?

---

