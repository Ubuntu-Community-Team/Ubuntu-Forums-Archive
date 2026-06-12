---
title: "256 mb ram .. cant istall"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-02-21
I gave my ubu cd to my frnd..
she tried to run it as livecd and she failed..
/
/
I went to her home and tried Wubi.. It said > "you have ***_only 253 mb_*** ram.. installatin will fail"

but She has ***256 Mb ***ram in her computer

How do i install ubu in her computer ???

---

### Post by daniel014 on 2009-02-21
Maybe you could try the alternate installer.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by kimikrishna on 2009-02-21
ok..

is it possible to get cd to home ? just like my ubu cd ?

---

### Post by kimikrishna on 2009-02-21
i started downloading a alternate cd..

i have 64 kB per sec internet speed..
and dwlding 700 megab is such a great thing for me......

so, plz make it sure that > ubuntu will run in a system with 256 mb ram .... and it shouldnot show that it has only 253 ram

---

### Post by yeats on 2009-02-21
> ubuntu will run in a system with 256 mb ram .... and it shouldnot show that it has only 253 ram 

If I were you, I would investigate xubuntu ([http://www.xubuntu.org/get]("http://www.xubuntu.org/get")).  It runs better on computers with lower resources.  You'll definitely get opinions here that 256 MB RAM should be fine, but IMHO, what's *possible* does not always mean what is *enjoyable* :-).

As for the 253 vs. 256 number - I wouldn't worry about that too much - You'll find sometimes that "256 MB RAM" or an "80 GB" hard drive may be a few numbers off here and there.  You should only worry if the computer is seeing something like "128 MB RAM" when you know you have 256.

Anyway - hope that helps and good luck.

---

### Post by kimikrishna on 2009-02-21
> **chrissharp123 said:**
>  You should only worry if the computer is seeing something like "128 MB RAM" when you know you have 256.

:lolflag: ... ok . i'll try xubuntu..../

---

### Post by kimikrishna on 2009-02-21
but tell sure that Xubu will work on 253 [256] ram

---

### Post by kimikrishna on 2009-02-21
> [http://mirror.internode.on.net/pub/ubuntu/xubuntu/8.10/release/](http://mirror.internode.on.net/pub/ubuntu/xubuntu/8.10/release/)

this page has many files....

which one is to download ??

---

### Post by kimikrishna on 2009-02-21
```
xubuntu-8.10-alternate-i386.iso
```

i started the link with this name..
but do i need to download all ???? :O

---

### Post by philinux on 2009-02-21
Crunchbang linux which is based on ubuntu would fly on that machine.

[http://distrowatch.com/table.php?distribution=crunchbang](http://distrowatch.com/table.php?distribution=crunchbang)

---

### Post by yeats on 2009-02-21
> **kimikrishna said:**
> ```
xubuntu-8.10-alternate-i386.iso
```

i started the link with this name..
but do i need to download all ???? :O

Yes - it looks like you chosen the right file.  No you do not need to download any other links.  Sounds like it will be a while. :-)

There is another link on that page that you'll want to click on once the download is finished called "MD5SUMS."  This is the line you want:

> db016f2f55ea2109b787a191b8115c67 *xubuntu-8.10-alternate-i386.iso


When your download finishes, open a terminal and type (or paste in)

```
md5sum xubuntu-8.10-alternate-i386.iso
```

which should return the long string "db016f2f55ea2109b787a191b8115c67", character for character.  If anything's different, you're file was corrupted somehow during the download and you'll have to start over. No way to know that until the end though, unfortunately. :-)

---

### Post by kimikrishna on 2009-02-21
> **chrissharp123 said:**
> Yes - it looks like you chosen the right file.  No you do not need to download any other links.  Sounds like it will be a while. :-)

There is another link on that page that you'll want to click on once the download is finished called "MD5SUMS."  This is the line you want:



When your download finishes, open a terminal and type (or paste in)

```
md5sum xubuntu-8.10-alternate-i386.iso
```

which should return the long string "db016f2f55ea2109b787a191b8115c67", character for character.  If anything's different, you're file was corrupted somehow during the download and you'll have to start over. No way to know that until the end though, unfortunately. :-)


i didnot even understand a word from this...

tell me step by step..

i dont know more about these....../

---

### Post by yeats on 2009-02-21
> i didnot even understand a word from this...

Okay - first things first, then.  Read this:

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

which should clear up your questions about what I've posted.

> tell me step by step..

i dont know more about these....../ 

We're all happy to help here, but most of the burden is on you to learn how to do this.  I think Google searches for unfamiliar terms are a good place to start.  I would venture to say that nearly everyone here on the forums had to learn all this themselves.  If you need pointers toward resources (books, from the web, etc.) - just ask.

---

### Post by kimikrishna on 2009-02-21
ok.. 
i did gooogle.. 
but coudnt find out..
thats why asked you to tell step bby sstep..
i always google everything :P

---

### Post by yeats on 2009-02-21
> ok..
i did gooogle..
but coudnt find out..
thats why asked you to tell step bby sstep..
i always google everything 

I think this will work best if you ask specific questions and someone here can answer them.  What is it about my instructions above that does not make sense to you?

---

### Post by kimikrishna on 2009-02-21
> **chrissharp123 said:**
> I think this will work best if you ask specific questions and someone here can answer them.  What is it about my instructions above that does not make sense to you?

no .. i understd..

thanks

and i have download time of 13 hours left....

i will reply after i finsh downld

---

