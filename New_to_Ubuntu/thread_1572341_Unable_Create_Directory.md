---
title: "Unable Create Directory"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by happydisaster on 2010-09-10
Hi! I am really new to Linux in any form.
 I really like everything so far, but I am running into a problem with a program I need to download for my job.  The program requires java so I downloaded that, had a few problems that I think I have worked out, and now this is what I have java-wise:
```
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Client VM (build 16.3-b01, mixed mode, sharing)
```Now I can download the program to desktop, but if I try to open it I get the following error message: " Unable Create Directory: /NaturalBodycare/BusinessSuite/ "  

I emailed the Tech Support for the company I work for and was told that "[SIZE=2]Although we don't  support the Business Suite on Linux (because we don't have Linux  desktops to test it on), it should work fine on Linux" and to make sure that I have the right version of java downloaded.
[/SIZE]
How do I tell if the version I have is the right version? Is there any thing I might be overlooking/not doing right?  I really appreciate any tips & tricks that would be helpful.

---

### Post by 3rdalbum on 2010-09-11
The program is quite badly behaved - it is trying to create a directory in your root filesystem. You will need to run it as root in order for it to create its directory, unfortunately.

---

### Post by uRock on 2010-09-11
Welcome to Ubuntu Forums!

For java, don't bother with downloading from the net. Ubuntu Software Center will install it for you. Go in the menu to Ubuntu Software Center and search for ubuntu-restricted-extras. It is a large package that contains Java, Flash and many other things needed for everyday use, such as MP3 codecs.

uRock

---

### Post by happydisaster on 2010-09-12
> **uRock said:**
> 
For java, don't bother with downloading from the net. Ubuntu Software Center will install it for you. Go in the menu to Ubuntu Software Center and search for ubuntu-restricted-extras. It is a large package that contains Java, Flash and many other things needed for everyday use, such as MP3 codecs.


Is there anything I need to remove then?

---

### Post by col48 on 2010-09-12
Can't help with the main issues, I'm afraid but I suggest
1. backup now so that if java gets entangled at least you can get back to where you are now
2. there must be a way round the issue of having to run as root.  Perhaps it arises from the version of java not being as Linux-compliant as it should be, although I would suspect it really is the program being naughty.  If so, I wonder if it would be happy if you created the folder as root before running the program?  Or maybe there is an environment variable or something in a config file whose absence is making it behave like this?

I wonder what evidence your Tech Support have for saying the Suite "should be OK on Linux"?  Is this other companies' experience, or the Suite's manual?  In either case, they might be persuaded to point you in the right direction for support if you buy them a beer (or whatever fits your company ethos!).

---

### Post by sadaruwan12 on 2010-09-12
Bro, I think it's trying to create a directory in a unwanted place of you computer any way if you know what you're doing run the program with root privileges. To do that use the command bellow,

```
$gksudo <your program name>
```

Try this and tell us what happened.

Oh, and welcome over to the enlightened side.

---

### Post by happydisaster on 2010-09-12
Just to be sure, my program name is  /NaturalBodycare/BusinessSuite/ ?

the folder on my desktop is named BusinessSuite.jnlp so might this be the program name, instead?

---

### Post by uRock on 2010-09-12
Have you tried installing ubuntu-restricted-extras yet? Also, if you search the Ubuntu Software Center you will find the Java plugins that you are trying to install.

---

### Post by happydisaster on 2010-09-12
uRock, 

yes, I have all the java installed now, and the restricted extras. 


PS to sadaruwan12:  Last time I checked, I am definitely a gal. :D

---

### Post by happydisaster on 2010-09-13
I was talking to a friend and he suggested to try ```
mkdir
``` because he didn't see what ```
gksudo
``` would do.  I tried his way and this is what happened:

```
melissa@missywins:~$ mkdir /NaturalBodycare/BusinessSuite/
mkdir: cannot create directory `/NaturalBodycare/BusinessSuite/': No such file or directory
melissa@missywins:~$ cd /
melissa@missywins:/$ pwd
/
melissa@missywins:/$ mkdir NaturalBodycare
mkdir: cannot create directory `NaturalBodycare': Permission denied
```

He had me check if I was root and this happened:
```
melissa@missywins:/$ su - root
Password: 
su: Authentication failure
melissa@missywins:/$ su - root
Password: 
su: Authentication failure
```

So I tried what was suggested above
```
melissa@missywins:/$ gksudo /NaturalBodycare/BusinessSuite/
```
and a window popped up, asked me for the password, and disappeared.  I tried this again:
```
melissa@missywins:/$ mkdir /NaturalBodycare/BusinessSuite/
mkdir: cannot create directory `/NaturalBodycare/BusinessSuite/': No such file or directory
melissa@missywins:/$ 
```

I don't know what to do next. I really only partially understand what I did...

---

