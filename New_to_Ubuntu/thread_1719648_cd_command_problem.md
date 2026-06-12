---
title: "cd command problem"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by zaafar on 2011-04-02
hi , i was trying to learn how to use the terminal and the common commands like cd,
and every time i try to go in the default folders like pictures , music , downloads it says " no such file or directory" .???  if "music" is a valid folder then cd command should work ? i created a test folder named abc and cd works there ..
 ( forgive me if its a stupid question, i know nothing about commands :()

zaafar@mirza:~$ ls
abc            Desktop    Downloads         Music     Public     Videos
crypt-manager  Documents  examples.desktop  Pictures  Templates  xyz
zaafar@mirza:~$ cd music
bash: cd: music: No such file or directory
zaafar@mirza:~$ cd abc
zaafar@mirza:~/abc$

---

### Post by Hoopz on 2011-04-02
Linux is case sensitive.  Need to do cd Music and not cd music

---

### Post by Hoopz on 2011-04-02
This drove me nuts too when I first started using Linux

---

### Post by TheCompBoy on 2011-04-02
I also had this problem but just as Hoopz says its Case sensetive

---

### Post by zaafar on 2011-04-02
oh RRIGHT !!  thanx ..

---

### Post by andrew.46 on 2011-04-02
> **zaafar said:**
> oh RRIGHT !!  thanx ..

For bonus points just type in:

```
cd M
```

and press the tab key :).

Andrew

---

### Post by rudihawk on 2011-04-02
> **andrew.46 said:**
> For bonus points just type in:

```
cd M
```

and press the tab key :).

Andrew

Tab completion will soon become your best friend!:guitar:

---

### Post by nahallac on 2011-04-02
Also useful is the ability to go back up one directory by cd-ing to ..
 
So, if you're in Music, typing cd .. and hitting enter will take you back to your home directory, which is represented by the ~ symbol. To take it even further, you can change to your Downloads directory from within Music by entering: 
 
cd ../Downloads
 
Hope that makes sense...
 
And yes, tab completion is the best thing ever!

---

### Post by AlphaLexman on 2011-04-02
Or make an alias like this...
```
alias docs='cd ~/[D,d]ocuments'
```

---

