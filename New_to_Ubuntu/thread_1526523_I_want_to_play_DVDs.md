---
title: "I want to play DVDs"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by Gaiasfriend on 2010-07-08
Hi, 

I used to be able to watch DVDs on my laptop... my home entertainment system :-) but not since I switched to Ubuntu...:-(

In my latest attempt at following instructions via the forum this is what I did and got..

 sudo wget --output-document=/ect/apt/soucres.list.d/medibuntu.list htt:/www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get--quiet update && sudo apt-get --yes --quiet __allow-unauthenricated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for jn: 
/ect/apt/soucres.list.d/medibuntu.list: No such file or directory
jn@jn-laptop:~$ ^C
jn@jn-laptop:~$ sudo wget --output-document=/ect/apt/soucres.list.d/medibuntu.list htt:/www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get--quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibunti-keyring && sudo apt-get --quiet update
/ect/apt/soucres.list.d/medibuntu.list: No such file or directory

Maybe someone can spot where I've gone wrong....Thank you

---

### Post by redbook4574 on 2010-07-08
> **Gaiasfriend said:**
> Hi, 

I used to be able to watch DVDs on my laptop... my home entertainment system :-) but not since I switched to Ubuntu...:-(

In my latest attempt at following instructions via the forum this is what I did and got..

 sudo wget --output-document=/ect/apt/soucres.list.d/medibuntu.list htt:/www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get--quiet update && sudo apt-get --yes --quiet __allow-unauthenricated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for jn: 
/ect/apt/soucres.list.d/medibuntu.list: No such file or directory
jn@jn-laptop:~$ ^C
jn@jn-laptop:~$ sudo wget --output-document=/ect/apt/soucres.list.d/medibuntu.list htt:/www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get--quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibunti-keyring && sudo apt-get --quiet update
/ect/apt/soucres.list.d/medibuntu.list: No such file or directory

Maybe someone can spot where I've gone wrong....Thank you

Try replacing "/ect/apt/soucres" with /etc/apt/sources wherever this error occurs, I think a large part of your problem is spelling.

---

### Post by philinux on 2010-07-08
> **Gaiasfriend said:**
> Hi, 

I used to be able to watch DVDs on my laptop... my home entertainment system :-) but not since I switched to Ubuntu...:-(
Maybe someone can spot where I've gone wrong....Thank you



Yes. It's better to use copy and then paste into the terminal.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by 3rdalbum on 2010-07-08
> **philinux said:**
> Yes. It's better to use copy and then paste into the terminal.

+1 - copy and paste the big long command from the Medibuntu website into your terminal. It saves you heaps of typing and also means that you don't misspell anything.

---

### Post by ankit singh on 2010-07-08
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list  http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list  && sudo apt-get --quiet update && sudo apt-get --yes  --quiet --allow-unauthenticated install medibuntu-keyring &&  sudo apt-get --quiet update

```

directly copy and paste this

---

### Post by oldos2er on 2010-07-08
> **Gaiasfriend said:**
>  sudo wget --output-document=/ect/apt/soucres.list.d/medibuntu.list htt:/www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get--quiet update && sudo apt-get --yes --quiet __allow-unauthenricated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for jn: 
/ect/apt/soucres.list.d/medibuntu.list: No such file or directory
jn@jn-laptop:~$ ^C
jn@jn-laptop:~$ sudo wget --output-document=/ect/apt/soucres.list.d/medibuntu.list htt:/www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get--quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibunti-keyring && sudo apt-get --quiet update
/ect/apt/soucres.list.d/medibuntu.list: No such file or directory

Maybe someone can spot where I've gone wrong....Thank you

I agree with the advice to copy & paste, but just to point out your error, you misspelled "etc" as "ect". Just FYI.

---

### Post by Gaiasfriend on 2010-07-10
Thanks to all of those who came to the rescue...spelling was the first reason I began to use computers for so no surprise it was a coding error.  I can now watch DVDs again :-) and I've learned that the quick keys for paste in terminal are different.

I've a few more glitches to work through so you'll hear from me again.  Thanks again.

---

### Post by SKhan on 2010-07-10
> **Gaiasfriend said:**
> Thanks to all of those who came to the rescue...spelling was the first reason I began to use computers for so no surprise it was a coding error.  I can now watch DVDs again :-) and I've learned that the quick keys for paste in terminal are different.

I've a few more glitches to work through so you'll hear from me again.  Thanks again.

:) you are welcome. ;)

---

