---
title: "hjsplit"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-02-14
I have downloaded and extracted hpsplit from tar file..

now , i want to install it..
help me.

i read the r"readme" file in that tar.

but it didnot worked..
thanks.

the file type is 
```
executable (application/x-executable)
```

---

### Post by kronk on 2009-02-14
Hi kimikrishna,

did you mean hpsplit ?

Can you give us some more details on what your trying to do ?

Ta :)

---

### Post by kimikrishna on 2009-02-14
not hpsplit.

HJSPLIT.

> site :freebyte.com/hjsplit

---

### Post by kimikrishna on 2009-02-14
i try to install it 

but itt is not working

---

### Post by Malta paul on 2009-02-14
Hi, If I were you I would download the Java version of 'hjsplit'. I've used both but find the Java version worked best(easier) in Ubuntu. 
Don't open the folder, just click on the folder to run.
:)

---

### Post by cb951303 on 2009-02-14
I use the java version too, works without a problem

---

### Post by kimikrishna on 2009-02-15
help me .. 

i cannot understand,,
i downloaded the java version and when i double click it ,it opens with archive manager :O

it has the extensio of "JAR"

---

### Post by kimikrishna on 2009-02-15
i have downlded the windows version of it 
and running it with wine.. :(

i am confused.. if there is a linux version , why cant i use it for ubuntu ? :-O

---

### Post by kimikrishna on 2009-02-15
i want to use that linux version of it.
so help me with this

---

### Post by binbash on 2009-02-15
google > lxsplit

---

### Post by Malta paul on 2009-02-15
Sorry that you are a bit confused, Hisplit comes in all versions and can be run on Windows, linux and Ubuntu with Java installed.

As we said the Java version works great, perhaps you haven't install Java. So go to Applications>Add/remove select 'All available Applications' then type in 'Java' in the search box, click 'apply changes' and away you go:) 
The Java extension is .jar.
I'm sure you have this, 
The web link for hjsplit is:[http://www.freebyte.com/hjsplit/](http://www.freebyte.com/hjsplit/)

---

### Post by kimikrishna on 2009-02-15
there will be no real need for hjsplit to join files in linux.

simply we can use cat commad..

if we have files like, file.avi.001 , file.avi.002..

simply open terminal from app > acces > terminal

and then type

> cat file.avi.001 > file.avi

and it will automatically join the files..

this needs no softwre installatiion.

I read about this in a useful site.. !

---

### Post by kimikrishna on 2009-02-15
problem solved !! 

thanks to linux for having a easy method for joining hjsplit files !!

---

### Post by binbash on 2009-02-15
> **kimikrishna said:**
> there will be no real need for hjsplit to join files in linux.

simply we can use cat commad..

if we have files like, file.avi.001 , file.avi.002..

simply open terminal from app > acces > terminal

and then type



and it will automatically join the files..

this needs no softwre installatiion.

I read about this in a useful site.. !

This is not a good way, trust me.Sometimes it does not work.Use lxsplit when dealing with split files

---

### Post by kimikrishna on 2009-02-15
ok.. then tell me where is lxsplit ?

---

### Post by kimikrishna on 2009-02-15
found it myself.

> [http://sourceforge.net/project/downloading.php?groupname=lxsplit&filename=lxsplit_0.2.4-1_i386.deb&use_mirror=jaist](http://sourceforge.net/project/downloading.php?groupname=lxsplit&filename=lxsplit_0.2.4-1_i386.deb&use_mirror=jaist)

this is lxsplit..

thanks binbash

---

### Post by binbash on 2009-02-15
You can find the howto at the homepage of the official site.Easy to use

---

### Post by kimikrishna on 2009-02-15
now , i have got another problm..

i have nstalled the .deb file..

its not showing up in applications drop down menu ?????

---

### Post by binbash on 2009-02-15
It is a CLI only app no gui.You dont need a gui.From the official site : 

lxSplit splits and merges files with the -s and -j flags respectively. Starting with version 0.2.1, lxSplit can handle large files (>= 4 GB) both when splitting and joining.

Examples:

To split a big file into smaller pieces of 15 MB each, run the following command:

    lxsplit -s hugefile.bin 15M

Output size can be given in (M)egabytes, (k)ilobytes and (b)ytes.

To merge (join) the already split pieces into the original big file, run this command:

    lxsplit -j smallfiles.bin.001

All resulting files (from either splitting or joining) will be placed in the current directory.

---

### Post by kimikrishna on 2009-02-15
what are the supported formats ??????? 

any format ? or what ?

---

### Post by binbash on 2009-02-15
You can split everything.The files you gonna join will end like 001 002 003 etc.

---

### Post by kimikrishna on 2009-02-15
thankyou binbashh

---

### Post by ricardisimo on 2009-07-03
I have found and downloaded the hjsplit jar file. How would I go about creating a launcher for it in my menus? Thanks.

---

### Post by cb951303 on 2009-07-04
> **ricardisimo said:**
> I have found and downloaded the hjsplit jar file. How would I go about creating a launcher for it in my menus? Thanks.

java -jar hjsplit.jar

---

### Post by ricardisimo on 2009-07-07
Yay! Thanks.

---

### Post by yawnp0426 on 2012-08-09
> **kimikrishna said:**
> i try to install it 

but itt is not working

You can read it !

[http://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=243734](http://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=243734)

HJSplit &#21033;&#29992;&#40474;&#40289;&#34746;&#24037;&#20855;(nautilus actions)&#23433;&#35037;&#21855;&#21205;&#12304;HJ-split&#27284;&#26696;&#20999;&#21106;&#21512;&#20341;&#36575;&#39636;&#12305;&#25945;&#23416;&#65281;:)

---

### Post by wildmanne39 on 2012-08-10
Old thread closed.

---

