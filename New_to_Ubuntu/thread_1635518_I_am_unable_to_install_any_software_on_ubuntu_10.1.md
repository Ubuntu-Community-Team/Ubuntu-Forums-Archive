---
title: "I am unable to install any software on ubuntu 10.10"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by prmdk on 2010-12-01
This is my first post.
Not matter which software i try to installed i get this error. I think  the software package is downloaded just fine but system has trouble  installing it.

Any help is appreciated..
[IMG]http://i.imgur.com/e9NrZ.png[/IMG]](*,)](*,)](*,)

---

### Post by Utkarsh Ray on 2010-12-01
I too am novice,
so couldn't help with the technical things but there's a workaround. If you have unlimited internet data plan. The easiest way to install packages is to download their .deb files from [http://countryname.archive.ubuntu.com/ubuntu/pool/](http://countryname.archive.ubuntu.com/ubuntu/pool/)
or you may manually download the package files from /ubuntu/dist/yourubuntuversionname of ubuntu site and copy them to ./var/cache/apt/archive using the command
sudo nautilus

this method was told to me by fellow members when I had asked for help.

---

### Post by karthick87 on 2010-12-02
[[IMG]http://imgur.com/fYoun.png[/IMG]** See this Thread**]("http://ubuntuforums.org/showthread.php?t=56281")

---

### Post by prmdk on 2010-12-02
thanks for the reply Karthick!

But the code given on that thread didn't work for me..
Actually, after entering the code.. there was not any line as the output.

---

### Post by karthick87 on 2010-12-02
Can you post the output of 

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by prmdk on 2010-12-02
> **karthick87 said:**
> Can you post the output of 

```
sudo apt-get install -f
``````
sudo dpkg --configure -a
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 188 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: parse error, in file '/var/lib/dpkg/available' near line 29102 package 'make':
 EOF during value of field `Description' (missing final newline)
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by prmdk on 2010-12-02
```
sudo dpkg --configure -a
```

dpkg: parse error, in file '/var/lib/dpkg/available' near line 29102 package 'make':
 EOF during value of field `Description' (missing final newline)


this is all i got from the second code...

Thanks...

---

### Post by srikanth.gundaz on 2010-12-02
> **prmdk said:**
> ```
sudo dpkg --configure -a
```

dpkg: parse error, in file '/var/lib/dpkg/available' near line 29102 package 'make':
 EOF during value of field `Description' (missing final newline)


this is all i got from the second code...

Thanks...
try this.
sudo apt-get update

---

### Post by srikanth.gundaz on 2010-12-02
> **prmdk said:**
> ```
sudo dpkg --configure -a
```

dpkg: parse error, in file '/var/lib/dpkg/available' near line 29102 package 'make':
 EOF during value of field `Description' (missing final newline)


this is all i got from the second code...

Thanks...
try this.
**> sudo apt-get update**

---

### Post by prmdk on 2010-12-02
> **srikanth.gundaz said:**
> try this.


well 

This was the code after which i first found the problem..
My PC can download the updates but its having problem in installing them..

---

### Post by srikanth.gundaz on 2010-12-02
> **prmdk said:**
> This is my first post.
Not matter which software i try to installed i get this error. I think  the software package is downloaded just fine but system has trouble  installing it.

Any help is appreciated..
[IMG]http://i.imgur.com/e9NrZ.png[/IMG]](*,)](*,)](*,)

Try this. 
> sudo gedit /var/lib/dpkg/available
Now go to 29102 line and check whether newline character(\n) is missing.
If missing, then add \n and check installing some package :p :)

---

### Post by rajeev1204 on 2010-12-02
Try this [https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)

---

### Post by prmdk on 2010-12-03
> **rajeev1204 said:**
> Try this [https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)


Thanks Rajeev1204, that solved the problem...:D:D:D:D:D

---

