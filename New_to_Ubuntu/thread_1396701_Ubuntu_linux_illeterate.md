---
title: "Ubuntu linux illeterate"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by Tindomul on 2010-02-02
Hi all

I am attempting to learn linux, and using it through Ubuntu.
It really is a foreign language to me.  Does anyone know what I can read to help out, I need to find out how to concatenate files, install a program that uses an approximate grep based on TRE regexp matching library.  

Thanks.

---

### Post by walt.smith1960 on 2010-02-02
Keir Thomas' guide (first sticky in this forum) is a nice introduction. This focuses on 8.10 and earlier so doesn't talk about the newest versions but the basics haven't changed that much. It seems like a good place to start.

---

### Post by LowSky on 2010-02-02
Are you taking an Advanced Linux Class?

You're using really nerdy words for someone who is Linux illiterate.

This should help with concatenate files, see the bottom of the page
[http://www.ahinc.com/linux101/files.htm#cat](http://www.ahinc.com/linux101/files.htm#cat)

---

### Post by lykwydchykyn on 2010-02-02
Concatenating files is done like so:
```

cat file1 file2 > file3

```
Where file1 and file2 are the files you want to concatenate, and file3 is the combined output.

For TRE regex grep, have a look at tre-agrep, which is in the repositories.  It can be installed with this command:
```

sudo aptitude install tre-agrep

```

To use it, the command would be
```

tre-agrep pattern filename

```

---

### Post by Wandering Ronin on 2010-02-02
You can download this for free:                                         &#65279; [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/).


There's also a lot of stuff to wade through at The Linux Documentation Project: 

                                         [http://tldp.org/](http://tldp.org/)  What you are looking for is called BASH, which you probably already know. 



It should be easy for you to find the Ubuntu wiki from the Ubuntu home page. 


[http://lottalinuxlinks.com/](http://lottalinuxlinks.com/) is a great place to begin a search.

---

### Post by dondiego2 on 2010-02-02
> **LowSky said:**
> Are you taking an Advanced Linux Class?

You're using really nerdy words for someone who is Linux illiterate.

This should help with concatenate files, see the bottom of the page
[http://www.ahinc.com/linux101/files.htm#cat](http://www.ahinc.com/linux101/files.htm#cat)


:p That's what I thought!  I'm a one month newbie and I am trying to learn something everyday in linux, on forums, podcasts etc. and he lost me!

---

### Post by kayvortex on 2010-02-02
What? Is nobody else going to point out that "illeterate" has been spelled illiterately. Oh come on!

Anyway, probably a good start would be the man pages.
```
man cat
```
etc.

I'm not sure you'll find a guide that'll explain all the things that you asked about in one go, but there'll be lots of stuff about the individual things themselves. Sure, it's a lot more work, but you'll find the answers. And anything you can't find we'll be happy to try to help with here.

---

### Post by Tindomul on 2010-02-02
OMG you guys are great, thanks.
 
Yes I am taking a linux class, in reality, its linux for botanists (Phytoinformatics), if that makes sense.  And I have no clue about what sound nerdy and what sounds like normal jargon to people who use ubuntu regularly  :oops:
 
 
Thanks for the help!!

---

### Post by Tindomul on 2010-02-02
Sorry bout the spelling,
 
Anyways, I actually tried man catenate, had no idea it was man cat. Thanks!!!!!

---

### Post by lykwydchykyn on 2010-02-02
> **Tindomul said:**
> 
Yes I am taking a linux class, 


Please tell me I didn't just do your homework for you?

---

### Post by kayvortex on 2010-02-02
>  Sorry bout the spelling

Meh, I can hardly spell "sure" without firefox telling me there's no "h" in it...

> Anyways, I actually tried man catenate, had no idea it was man cat. Thanks!!!!!

It's probably useful to remember that lots of linux commands are abbreviated ("remove" is "rm", "update (locate) database" is "updatedb" etc.) You can use tab completion to help you out in these cases; so entering ca<tab><tab> would have given you a list of possible commands, including "cat".

---

### Post by oldos2er on 2010-02-02
> **Tindomul said:**
> Sorry bout the spelling,
 
Anyways, I actually tried man catenate, had no idea it was man cat. Thanks!!!!!

**apropos** is a great command for beginners (and intermediaters too) when you know what you want to do, but don't know the command to do it:

ann@ann-desktop:~$ apropos concatenate
cat (1)              - concatenate files and print on the standard output
FcStrPlus (3)        - concatenate two strings
pnmcat (1)           - concatenate portable anymaps
tac (1)              - concatenate and print files in reverse
tccat (1)            - concatenate multimedia streams from medium and print o...

---

### Post by Tindomul on 2010-02-02
LOL, yes and no, you helped me do my homework, but what does it matter, as long I learn how to do it.  So the reason I say I am illiterate is because even thought I wrote all them fancy words, I just spent the last two hours reading up on what they mean, because I had no idea what those words are.

Question, does TRE mean directory tree file??

---

