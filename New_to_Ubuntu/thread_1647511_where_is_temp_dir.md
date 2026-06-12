---
title: "where is temp dir"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by degarb on 2010-12-17
I am trying to upgrade wubi, but it cannot unpack 'Unpacking replacement python-minimal'.


My bet is wubi has a temporary directory defined in a place that does not exist.   Thus unpacking will fail, as it will-without a hint- in MS Windows if a user moves the windows temp or temporary directory to a removable drive, then removes that drive.

How do I check the validity of the temp dir?

I tried repair packages, recovery mode install -f . On terminal now . I did all on [https://answers.launchpad.net/ubuntu/+s](https://answers.launchpad.net/ubuntu/+s) ... tion/87929 but no luck extracting python.

---

### Post by bcbc on 2010-12-17
> **degarb said:**
> I am trying to upgrade wubi, but it cannot unpack 'Unpacking replacement python-minimal'.


My bet is wubi has a temporary directory defined in a place that does not exist.   Thus unpacking will fail, as it will-without a hint- in MS Windows if a user moves the windows temp or temporary directory to a removable drive, then removes that drive.

How do I check the validity of the temp dir?

I tried repair packages, recovery mode install -f . On terminal now . I did all on [https://answers.launchpad.net/ubuntu/+s](https://answers.launchpad.net/ubuntu/+s) ... tion/87929 but no luck extracting python.

Wubi is not that mysterious. Once it is booted it is identical to a normal Ubuntu install (except for the virtual disk bit, except that running certain updates will break booting e.g. grub-pc and grub-common). There is no special temp directory.

What I am saying is any problem you have is likely unrelated to it being Wubi.

---

### Post by degarb on 2010-12-17
> **bcbc said:**
> Wubi is not that mysterious. Once it is booted it is identical to a normal Ubuntu install (except for the virtual disk bit, except that running certain updates will break booting e.g. grub-pc and grub-common). There is no special temp directory.

What I am saying is any problem you have is likely unrelated to it being Wubi.

So, ubuntu has no temporary directory that it uses to do task and not dirty up the directory that you run.  I don't buy this.  When apt-get unpacks a file, it must unpack it somewhere, where is what I ask.  Cause it either, a: python minimal replacement is broken for everyone, or the directory that it is unpack into does not exist.

---

### Post by Nath4n on 2010-12-17
The temp folder in Ubuntu is located in /tmp.  Got to places > Home Folder > select Filesystem in the left> open tmp folder.  

Hope that helps.

---

### Post by bcbc on 2010-12-17
All I am saying... is that it's not a "wubi" issue.

So, what exactly are you doing and what exactly is the error you are getting?

---

### Post by Sealbhach on 2010-12-17
Did you try:
```

sudo dpkg --configure -a

```Another thing worth trying is

```
sudo aptitude install -f
```As far as I know, the downloaded packaged are kept in /var/cache.

What you could do, as a last resort is to go to 

> /var/lib/dpkg/infofind the files relating to python-minimal and delete them. That wuld be a last resort though, and could have bad consequences. Very bad consequences.If you want to try it though, do:


> cd /var/lib/dpkg/info/
sudo rm python-minimal*
sudo apt-get clean
sudo apt-get update
sudo apt-get remove python-minimal
Then install python-minimal.

REF: [http://ubuntuforums.org/showpost.php?p=7269337&postcount=14](http://ubuntuforums.org/showpost.php?p=7269337&postcount=14)



.

---

### Post by degarb on 2010-12-17
> **Sealbhach said:**
> Did you try:
```

sudo dpkg --configure -a

```Another thing worth trying is

```
sudo aptitude install -f
```As far as I know, the downloaded packaged are kept in /var/cache.

What you could do, as a last resort is to go to 

find the files relating to python-minimal and delete them. That wuld be a last resort though, and could have bad consequences. Very bad consequences.If you want to try it though, do:


Then install python-minimal.

REF: [http://ubuntuforums.org/showpost.php?p=7269337&postcount=14](http://ubuntuforums.org/showpost.php?p=7269337&postcount=14)



.
  I will google doc save this post.  And try it, naturally, when at the machine in question.

I  believe I did sudo dpkg --configure -a   .  I had to.

I did apt-get install -f  ,not  sudo aptitude install -f.

Thanks

---

