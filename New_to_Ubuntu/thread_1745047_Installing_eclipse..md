---
title: "Installing eclipse."
date: 2011-04-30
forum: New to Ubuntu
---

### Post by abnordude on 2011-04-30
I downloaded eclipse java version from the official webite.
Tis in tar.gz format.
So, now I need to install it.
Please give me detailed information on how to do so?
I need step-by-step.
Please help me.

---

### Post by Lateralis on 2011-04-30
Installing from a tarball (a tarred file) can be tiresome and troublesome.  Instead, I've found eclipse listed in the main repositories.  You can either go use the Ubuntu Software centre, search for eclipse and install from there, or use the terminal:

```

sudo apt-get install eclipse

```

If this eclipse in the repositories is not what you're after - the description of this package is *Extensible Tool Platform and Java IDE* - then let us know and we can give you more help from [installing from a tar ball]("http://linux.byexamples.com/archives/156/installing-from-tarballs/").

---

### Post by abnordude on 2011-04-30
> **Lateralis said:**
> Installing from a tarball (a tarred file) can be tiresome and troublesome.  Instead, I've found eclipse listed in the main repositories.  You can either go use the Ubuntu Software centre, search for eclipse and install from there, or use the terminal:

```

sudo apt-get install eclipse

```If this eclipse in the repositories is not what you're after - the description of this package is *Extensible Tool Platform and Java IDE* - then let us know and we can give you more help from [installing from a tar ball]("http://linux.byexamples.com/archives/156/installing-from-tarballs/").

Eclipse in ubuntu repos is old version.
I need the latest version.
That is why I downloaded it from main website.
Could you please tell me how to install it?

---

### Post by Skaggz on 2011-04-30
Click his link.  The instructions for installing from a tar-ball are in there.

---

### Post by Lateralis on 2011-04-30
Unless there a very good reason or there is a feature in the latest version that you really can't be without, then you should just install from the repositories.  

If you really need the tar ball then I posted a link which helps to explain installing from a tarball.  Unfortunately, each program and each tarball is slightly different.  The instructions in that link will give you the basic steps but there should be a readme file or some other documentation in the tarball which you must definitely read before attempting to install the program.  If after reading that link and reading the readme you still don't know how to install the program, then feel free to ask a more specific question.  =)

---

### Post by GregBrannon on 2011-04-30
Installing Eclipse to your OS from a file downloaded from the Eclipse.org distribution site is not a big deal.  Download the version you want, and SIMPLY:

1. uncompress it to a directory over which you have complete control, usually /home/yourusername/eclipse,
2. create a shortcut to the resulting eclipse executable file in the directory in #1.

You don't have to compile anything.  Steps 1 and 2 are it, and you don't even have to do #2 if you're fine with finding the Eclipse executable file and running it each time you want to run Eclipse.

It's a piece of cake, works great, and there's no reason to worry about the comments you may hear that installing Eclipse outside the repositories is potentially trouble.

Let me know if you need more help.

---

