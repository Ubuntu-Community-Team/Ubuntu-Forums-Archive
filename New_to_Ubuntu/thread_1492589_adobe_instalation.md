---
title: "adobe instalation"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by johnnycatt on 2010-05-24
I have just gotten ubuntu 8.04

I am pissed as hell.

I have been trying to install Adobe (or any program) so I can read .pdf files.

I have tried everything i can find in a search of the subject.

anyone wanna help?

Please

-=-JAY

---

### Post by SRST Technologies on 2010-05-24
You don't have to install anything to read PDF files on Ubuntu or any other Linux that I know of.

Download a PDF and double click it to open it.  You'll be pleasantly surprised.

---

### Post by Jarthur121 on 2010-05-24
From the tutorial I found: [http://ubuntu-tutorials.com/2008/06/23/install-adobe-acrobat-reader-812-on-ubuntu-804/](http://ubuntu-tutorials.com/2008/06/23/install-adobe-acrobat-reader-812-on-ubuntu-804/)

Go to terminal and type:


Code:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O  /etc/apt/sources.list.d/medibuntu.list

```Once that is done you&#8217;ll likely want to add the Medibuntu GPG key as  well:

```

sudo apt-get update && sudo apt-get install  medibuntu-keyring && sudo apt-get update

```Then once that is also done, install Adobe Reader by typing:

```

sudo apt-get install acroread

```

Edit: If you want Adobe Reader.

---

### Post by adamk918 on 2010-05-24
> **johnnycatt said:**
> I have just gotten ubuntu 8.04

I am pissed as hell.

I have been trying to install Adobe (or any program) so I can read .pdf files.

I have tried everything i can find in a search of the subject.

anyone wanna help?

Please

-=-JAY
Why are you pissed if 10.04 has been out for almost a month and you chose 8.04 instead?

...and it *should* have native PDF support!

---

### Post by anarchywolf46 on 2010-05-24
I think like the next version of Ubuntu has it in the add/remove programs menu option, if I'm not mistaken, it has adobe reader and flash as well.

---

### Post by dtfinch on 2010-05-24
Have you tried Evince for viewing pdfs? I thought it was installed by default.

---

