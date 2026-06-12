---
title: "how to install xampp in ubuntu 9.10"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by chaotic_clone01 on 2009-11-23
Hi

I cannot install xampp 1.72  in  ubuntu 9.10.

I am  unable to install the mysql  in the  whole installation procedure  can any one help.

And when i try to start xampp its  saying that the  .sock  file is  not present.

---

### Post by Buuntu on 2009-11-23
Perhaps you did something wrong in the whole process or don't have the right permissions?
Get rid of the old file(s) and try running this in the Terminal:
```
wget http://sourceforge.net/projects/xampp/files/XAMPP%20Linux/1.7.2/xampp-linux-1.7.2.tar.gz/download
sudo tar -xvzf xampp-linux-1.7.2.tar.gz -C /opt
sudo /opt/lampp/lampp start
```After that you need to set it up (if you don't know how).  I stumbled across this video that looks pretty good: [http://www.youtube.com/watch?v=-CsDoEPJg4U](http://www.youtube.com/watch?v=-CsDoEPJg4U)

---

### Post by baltadt on 2009-11-23
You also might want to think about dropping it all together and checking out drupal.com. It is what I am using on my server for my website.

---

### Post by AdotB on 2009-11-29
I've installed xampp in the past without problems, but now after a new installation (extracting to /opt) I am able to get the splash page, but unable to get past it. Anyone else have this problem?

---

### Post by owenll on 2009-11-29
Hi, 
I had permission problems after installing on 9.10, so ran
> sudo chmod 777 -R /opt/lampp/htdocs/
and it worked fine. Ok to do on a testing server. Also created a link to htdocs and dropped files into a folder in home to reduce permission problems.
> sudo ln -s /home/user/folder /opt/lampp/htdocs/$USER
Aplogies if this is stuff you already know.

---

### Post by kapi on 2009-11-29
I have heard that xampp can cause a few problems so I use LAMP. It installed first time and I have had no problems. 

You might want to try that instead

---

### Post by AdotB on 2009-11-29
I looked up lamp, are you referring to the installation you get by running "sudo tasksel install lamp-server" ?

I'll have to do some reading on proper installation if that's the case. I really liked how xampp gives you the just-untar-and-go simplicity.

---

### Post by recentconvert on 2009-12-01
```

tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now

```I get that error when I try installing.
sudo tar -xvzf xampp-linux-1.7.2.tar.gz -C /opt
gives me that error. any hints to what I'm doing wrong?

---

### Post by AdotB on 2009-12-01
> **recentconvert said:**
> ```

tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now

```

It sounds like the  /opt  directory is missing.
Have you tried creating it with "sudo mkdir /opt"?

---

### Post by recentconvert on 2009-12-01
> **AdotB said:**
> It sounds like the  /opt  directory is missing.
Have you tried creating it with "sudo mkdir /opt"?
Considered it but I was worried I'd break something ^^;
So it'll be cool if I just make the dir since it is already missing?

---

### Post by AdotB on 2009-12-04
> **recentconvert said:**
> Considered it but I was worried I'd break something ^^;
So it'll be cool if I just make the dir since it is already missing?

Thats good. You always want to be careful using sudo and messing with directories outside your home, but yes creating /opt wont hurt anything, and if it does already exist, it mkdir wont touch it:
```
$ sudo mkdir /opt
[sudo] password for AdotB: 
mkdir: cannot create directory `/opt': File exists

```

---

### Post by ibrahim.k on 2009-12-19
I am getting this end please tell me why !!

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

---

### Post by AdotB on 2009-12-19
> **ibrahim.k said:**
> 
gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

It looks like the file is corrupt or incomplete. Try downloading it again.

---

### Post by airtonix on 2009-12-19
You should really forget about that non standard apache install and follow this guide instead (it works 100% every time )

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by airtonix on 2009-12-19
...

---

### Post by krtica on 2010-06-01
[http://www.devshed.com/c/a/Administration/How-to-Install-XAMPP-on-Ubuntu-Linux/](http://www.devshed.com/c/a/Administration/How-to-Install-XAMPP-on-Ubuntu-Linux/)

---

