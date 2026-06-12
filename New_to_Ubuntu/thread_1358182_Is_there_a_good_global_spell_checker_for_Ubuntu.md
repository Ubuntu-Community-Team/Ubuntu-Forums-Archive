---
title: "Is there a good global spell checker for Ubuntu?"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by BioVirtual on 2009-12-18
Hi, I downloaded Aspell. Is there any better application than that? And How to install Aspell?
 

 Thanks.

---

### Post by Temposs on 2009-12-18
aspell is a library used by some applications for spell checking. It is not a global spell checker. You will not be able to use it directly. 

In general, each application needs to set up its own spell checking mechanism, and most do have them.

If you want to check your spelling for a certain word, you could open the Applications->Office->Dictionary program and type the word you need to check. If a definition appears and it's the meaning you intended, then you've spelled the word correctly :-)

---

### Post by jamieleshaw on 2009-12-18
Google is a spell checker.

---

### Post by BioVirtual on 2009-12-18
I realized that a version of aspell is already installed with Ubuntu and in Synaptic Package Manager the square beside it is green. So why it doesn't work? How can I use it and if it's installed why I cannot see it in my applications? It is applicable for many other other applications I guess!

---

### Post by Temposs on 2009-12-18
> **BioVirtual said:**
> I realized that a version of aspell is already installed with Ubuntu and in Synaptic Package Manager the square beside it is green. So why it doesn't work? How can I use it and if it's installed why I cannot see it in my applications? It is applicable for many other other applications I guess!

As I said, you cannot use aspell by itself. It is not an application, so you will not see it in your Applications menu. Other applications use aspell as their spell checker.

---

### Post by BioVirtual on 2009-12-18
OK. Now I want to install the latest version I just downloaded. In the read me file it's mentioned that: > 
 To install the program simply type

     make install


But it simply doesn't work! :lolflag:

---

### Post by Temposs on 2009-12-18
it is unnecessary to install that, and it may mess up your other applications that use aspell. I recommend just leave it alone.

---

### Post by lidex on 2009-12-18
This is somewhat of a hack, but may provide some usefulness:
[Random Ubuntu tip of the day—Spell check everywhere]("http://simulacra.in/2007/11/random-ubuntu-tip-of-the-day-spell-check-everywhere/")

---

### Post by sisyphus1978 on 2009-12-18
With aspell installed you can type from the terminal (CLI)

```
aspell -c <filename>
```Replace <filename> with your text file and you'll get a good spell checker. 

I like aspell and find it works perfectly with nano. GL.

---

### Post by Sir Jasper on 2009-12-18
Hi,

Ubuntu 9.04 advertised that it introduced Dictionary 2.26.0 (under Office in my Xubuntu). I had previously noticed that this dictionary did not work, but upon reading this post I checked it out and discovered my outgoing firewall connection had not allowed port 2628.

My regards

---

