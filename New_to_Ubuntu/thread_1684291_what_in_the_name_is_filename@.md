---
title: "what in the name is filename@ ?"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by rajn on 2011-02-08
I know this must be easy one. I Googled and Binged but could not get an answer. I typed in filename@ in help forum but nothing. Apparently, I did not know what to ask for..... but imagine a noob trying to figure out what does a filename such as cpp@ mean after he/she types in ~.bin> ls

I can guess what it must be but any precise answers?
And also kindly some pointers on how to figure this answer on the Net or how to figure out other strange symbols at the end of the filename such as *, ~, &, ^, % etc....
Thanks,

---

### Post by wojox on 2011-02-08
> **rajn said:**
> I know this must be easy one. I Googled and Binged but could not get an answer. I typed in filename@ in help forum but nothing. Apparently, I did not know what to ask for..... but imagine a noob trying to figure out what does a filename such as cpp@ mean after he/she types in ~.bin> ls

Could you try and reword this. It makes no sense to me. :p

---

### Post by matt_symes on 2011-02-08
Hi

Can you post the output of

```
ls ~/.bin
```

I think that is what you mean by* ~.bin> ls*. Your post is unclear.

To know what type a file is type

```
file <filename>
```

On my machine, for an ascii file, it returns

```
matthew@matthew-laptop:~$ ls -l test
-rwxr--r-- 1 matthew matthew 12 2011-01-31 21:32 test
matthew@matthew-laptop:~$ file test
test: ASCII text
matthew@matthew-laptop:~$ 
```

Different files types will return different answers.

Is this what you mean ?

Kind regards.

---

### Post by vidtek on 2011-02-08
> **rajn said:**
> I know this must be easy one. I Googled and Binged but could not get an answer. I typed in filename@ in help forum but nothing. Apparently, I did not know what to ask for..... but imagine a noob trying to figure out what does a filename such as cpp@ mean after he/she types in ~.bin> ls

I can guess what it must be but any precise answers?
And also kindly some pointers on how to figure this answer on the Net or how to figure out other strange symbols at the end of the filename such as *, ~, &, ^, % etc....
Thanks,

Rajn-

I think you have phrased the question rather badly.  The other replies don't seem to know what question you are asking.


I think what you mean this:  what meaning do the various suffixes you see on filenames have?  i.e. anyfilename@  anyfilename~ etc.

Am I correct insofar as this is your question?

Tony

---

### Post by rajn on 2011-02-09
My apologies. I was not in my senses.
I think vidtek got it correct. I am sorry for causing aggravation.

What I meant is this. When I go to /usr/bin and then type ls
I get files such as env@ or cpp@ and others such as xyz* and I wanted to know what do these extra characters mean. I tried to pose this question on google and the fact that you did not understand my question obviously meant google would never understand my abstruse wording.

Hope I am clear enough and again my apologies.
And I have the answer too as suggested by matt_symes. 

what does filename odvips@ or zipnote* imply

$file odvips
odvips: symbolic link to `dvips'

$ file zipnote
zipnote: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, stripped
so I guess @ stands for link and * stands for executables. That was easy but long shot for me.
Thank you,

---

### Post by Arndt on 2011-02-09
> **rajn said:**
> My apologies. I was not in my senses.
I think vidtek got it correct. I am sorry for causing aggravation.

What I meant is this. When I go to /usr/bin and then type ls
I get files such as env@ or cpp@ and others such as xyz* and I wanted to know what do these extra characters mean. I tried to pose this question on google and the fact that you did not understand my question obviously meant google would never understand my abstruse wording.

Hope I am clear enough and again my apologies.
And I have the answer too as suggested by matt_symes. 

what does filename odvips@ or zipnote* imply

$file odvips
odvips: symbolic link to `dvips'

$ file zipnote
zipnote: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, stripped
so I guess @ stands for link and * stands for executables. That was easy but long shot for me.
Thank you,

I think your 'ls' command is aliased to 'ls -F'.

The manual page for 'ls' doesn't say much about it, but these are the ones I know:

@ is a symbolic link
* is an executable
/ is a directory

---

### Post by Arndt on 2011-02-09
> **Arndt said:**
> I think your 'ls' command is aliased to 'ls -F'.

The manual page for 'ls' doesn't say much about it, but these are the ones I know:

@ is a symbolic link
* is an executable
/ is a directory

The Solaris man page says more:

 ```
    -F    Marks directories with a  trailing  slash  (/),  doors
           with  a  trailing  greater-than  sign  (>), executable
           files with a  trailing  asterisk  (*),  FIFOs  with  a
           trailing  vertical  bar  (|),  symbolic  links  with a
           trailing 'at' sign (@),  and  AF_UNIX  address  family
           sockets with a trailing equals sign (=).

```

---

### Post by matt_symes on 2011-02-09
Hi

> I am sorry for causing aggravation.

You caused no aggravation :) I was just unsure what you were asking and that is my bad not yours. Feel free to post any questions you may have in the future. There are always people here willing to answer.

Good work vidtek and Arndt.

Kind regards

---

