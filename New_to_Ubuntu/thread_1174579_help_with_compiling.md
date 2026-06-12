---
title: "help with compiling"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by BoobsLover on 2009-05-31
i'm trying to install firefox 3.5beta4 from the tar.bz2 package,but when i try to use the ./configure i get this:

```
kladionica@0klad1:~/Desktop/firefox$ ./configure
bash: ./configure: No such file or directory
```

???

---

### Post by nolliecrooked on 2009-05-31
[EMAIL="lmfao@your"]lmfao@your[/EMAIL] username
 
anyway just double click the file called **FIREFOX** in the tar file to test the firefox beta out.

---

### Post by BoobsLover on 2009-05-31
> **nolliecrooked said:**
> [EMAIL="lmfao@your"]lmfao@your[/EMAIL] username
 
anyway just double click the file called **FIREFOX** in the tar file to test the firefox beta out.
You mean the shell?Yes i did and nothing happens :(

---

### Post by 3rdalbum on 2009-05-31
Right-click the FIREFOX file, go to Properties and the Permissions tab, and make the program executable.

Now double-clicking should probably work; if it doesn't, try dragging the FIREFOX icon into a terminal window to run Firefox in a terminal.

---

### Post by BoobsLover on 2009-05-31
> **3rdalbum said:**
> Right-click the FIREFOX file, go to Properties and the Permissions tab, and make the program executable.

Now double-clicking should probably work; if it doesn't, try dragging the FIREFOX icon into a terminal window to run Firefox in a terminal.

yep,doesn't work :
```
kladionica@0klad1:~$ '/home/ubuntu/Desktop/firefox/firefox' 
/home/ubuntu/Desktop/firefox/run-mozilla.sh: 399: /home/ubuntu/Desktop/firefox/firefox-bin: not found

```

---

### Post by zortec on 2009-05-31
kladionica@0klad1:~/Desktop/firefox$ ./configure
bash: ./configure: No such file or directory

Check the path of the file that you are trying to run the configure script for.  Based on the message above, you are not in the directory where the file is located.  

You can use the **locate** command to find out where the file is.

---

### Post by wizard10000 on 2009-05-31
> **zortec said:**
> You can use the **locate** command to find out where the file is.

Doesn't work unless the file is in the database.  updatedb runs as a daily cron job and you can't use locate to find something you just put on the hard drive unless you update locate's database first.  Do this -

```
sudo updatedb
```

then

```
sudo locate *search-string*
```

note:  As of Ubuntu 9.04 you've gotta run locate as superuser.  I filed a bug on this and was told notabug but a deliberate security decision.  I agree with the logic on the security decision but once again...

ARE YOU LISTENING, UBUNTU DEVELOPERS?

sorry for shouting.

Once again, security updates that reduce functionality from earlier versions need to be addressed in the release notes.

;)

---

### Post by BoobsLover on 2009-05-31
[QUOTE=wizard10000;7375947]Doesn't work unless the file is in the database.  updatedb runs as a daily cron job and you can't use locate to find something you just put on the hard drive unless you update locate's database first.  Do this -

```
sudo updatedb
```

then

```
sudo locate *search-string*
```

the result is :

```
kladionica@0klad1:~$ sudo locate /home/ubuntu/Desktop/firefox/firefox
/home/ubuntu/Desktop/firefox/firefox
/home/ubuntu/Desktop/firefox/firefox-bin
kladionica@0klad1:~$ '/home/ubuntu/Desktop/firefox/firefox' 
/home/ubuntu/Desktop/firefox/run-mozilla.sh: 399: /home/ubuntu/Desktop/firefox/firefox-bin: not found

```

still nothing & can't ./configure :???:
It doens't make any sense ,because i can cd to the folder and i know the firefox shell is there .

---

### Post by cooprocks123e on 2009-06-05
Hello! I do not have much experience with compiling as I am 11 and have only compiled a few programs, but it almost sounds like you need to make ./configure executable (just an idea). I think you can check by right-clicking the file, clicking Properties, and going to Permissions and looking for it near the bottom of selecting the permissions. You can then double-click it, run it, and then look at ./config.log

---

### Post by mc4man on 2009-06-05
Some reading may be advised,
[https://developer.mozilla.org/en/Build_Documentation](https://developer.mozilla.org/en/Build_Documentation)

---

### Post by Hund on 2009-06-05
I can recomend Fabian Tassin's PPA archive: [https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)

There you will find the version your looking for and some other versions to. :)

---

### Post by cooprocks123e on 2009-06-07
OHHH! I think I get it! Do ```
sudo ./configure
``` and it should work. IF you were sudoing before, then stop because su might not be able to access it?

---

### Post by snova on 2009-06-07
> **BoobsLover said:**
> i'm trying to install firefox 3.5beta4 from the tar.bz2 package,but when i try to use the ./configure i get this:

```
kladionica@0klad1:~/Desktop/firefox$ ./configure
bash: ./configure: No such file or directory
```

???

If the file doesn't exist, the file doesn't exist. What *does* exist in here?

If it's just the standard .tar.bz2 package from [www.mozilla.org](www.mozilla.org), you don't have to compile it. There should be a program named "firefox" that you can run.

Try typing this:

```
./firefox
```

And if this doesn't work, paste the output of that command, and also of this:

```
ls -l
```

---

### Post by cooprocks123e on 2009-06-12
> **snova said:**
> If the file doesn't exist, the file doesn't exist. What *does* exist in here?

If it's just the standard .tar.bz2 package from [www.mozilla.org](www.mozilla.org), you don't have to compile it. There should be a program named "firefox" that you can run.

Try typing this:

```
./firefox
```

And if this doesn't work, paste the output of that command, and also of this:

```
ls -l
```


Ohhh... never mind. I tried it out and it launched the installed 3.0.10. I don't know how to get it to work. I think it's in mozilla-sh. I would check but I'm on a Windows (XP) pc.

P.S.  you don't compile:D

---

### Post by cooprocks123e on 2009-06-17
Go to 
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

for instructions.

---

### Post by LewRockwell on 2009-06-17
[http://www.justlinux.com/nhf/Software/Compiling_Software.html](http://www.justlinux.com/nhf/Software/Compiling_Software.html)

---

### Post by cooprocks123e on 2009-07-03
:KS:KSPeople, this has nothing to do with compiling. The executable is already there. The link I put up worked for me. If it doesn't work for you, then you are on your own.

---

