---
title: "Messed it up"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by DaveHannigan on 2009-07-20
Hi all
First time please be gentle:D

Installed Ubuntu 9.04 from iso image downloaded from Ubuntu

All went well, very impressed with installation.

Anyway on to how I messed it up.

I installed gnucash from the add/remove application and it went OK

I had been using GNUcash on windows prior to Ubuntu. I coppied the file accross from the windows puter but only got a list of accounts and no transactions.

I then noticed that the Windows version was 2.2.9 and the Ubuntu version was only 2.6.x (I think-cant access it now) so I downloaded 2.2.9 tarball from GNUcash and followed the install instructions.

After the $ ./configure I got the message that Glib was not up to date

So I downloaded Glib 2.9.6 and followed the instructions, this seemed ok and I went back to GNUcash and did $ ./configure, this now got futher than before but failed again. Whilst reading through i saw does your system require an $ lbconfigure ( at least I think thats what it was:()

Anyway when I did this the puter stopped responding, so I thought 'Ah needs a reboot'

Now I can only reboot to the command line. There is no GUI

I know I could reinstall but thought I would ask first to see if there was an easier way to sort the problem and if there was I would propably learn more this way.

Sorry for long post
thanks in advance
dave

---

### Post by regala on 2009-07-20
> **DaveHannigan said:**
> Hi all
First time please be gentle:D

Installed Ubuntu 9.04 from iso image downloaded from Ubuntu

All went well, very impressed with installation.

Anyway on to how I messed it up.

I installed gnucash from the add/remove application and it went OK

I had been using GNUcash on windows prior to Ubuntu. I coppied the file accross from the windows puter but only got a list of accounts and no transactions.

I then noticed that the Windows version was 2.2.9 and the Ubuntu version was only 2.6.x (I think-cant access it now) so I downloaded 2.2.9 tarball from GNUcash and followed the install instructions.

After the $ ./configure I got the message that Glib was not up to date

So I downloaded Glib 2.9.6 and followed the instructions, this seemed ok and I went back to GNUcash and did $ ./configure, this now got futher than before but failed again. Whilst reading through i saw does your system require an $ lbconfigure ( at least I think thats what it was:()

Anyway when I did this the puter stopped responding, so I thought 'Ah needs a reboot'

Now I can only reboot to the command line. There is no GUI

I know I could reinstall but thought I would ask first to see if there was an easier way to sort the problem and if there was I would propably learn more this way.

Sorry for long post
thanks in advance
dave

first, just for you information, 2.6.x is **after** 2.2 :)
second, on a Ubuntu Linux system, as on many other Linux systems, there are intelligent package management systems that take the pain of installing software from you. trying to install software on your own is the quickest way to doom.
you have gnucash, and it is likely to be more recent.

what you have done is simple: you have replaced libglib2.so.x that's shipped with your system, with an older version that no software installed can use. mostly everything that is graphics related on Ubuntu needs libglib2, so you screwed more than half of your system. That fastest way would be to reinstall I guess.

Now for you initial problem: the version you have on Ubuntu is likely the most recent you will get on any system, and maybe something changed in the format, on in the encoding of characters that makes your old files not being totally compatable. The next step would be to ask for some pointers before trying and downgrade your fresh new system :)

Oh, and glib > 2.9 was really installed on your system, next exercise is for you to try and understand why it said it is not installed (hint: on Ubuntu there's 2 kinds of packages, the libbla and the respective libbla-dev package).

---

### Post by DaveHannigan on 2009-07-20
> **regala said:**
> first, just for you information, 2.6.x is **after** 2.2 :)
second, on a Ubuntu Linux system, as on many other Linux systems, there are intelligent package management systems that take the pain of installing software from you. trying to install software on your own is the quickest way to doom.
you have gnucash, and it is likely to be more recent.

what you have done is simple: you have replaced libglib2.so.x that's shipped with your system, with an older version that no software installed can use. mostly everything that is graphics related on Ubuntu needs libglib2, so you screwed more than half of your system. That fastest way would be to reinstall I guess.

Now for you initial problem: the version you have on Ubuntu is likely the most recent you will get on any system, and maybe something changed in the format, on in the encoding of characters that makes your old files not being totally compatable. The next step would be to ask for some pointers before trying and downgrade your fresh new system :)

Oh, and glib > 2.9 was really installed on your system, next exercise is for you to try and understand why it said it is not installed (hint: on Ubuntu there's 2 kinds of packages, the libbla and the respective libbla-dev package).

Have now reinstalled
A typo on versions the windows version was 2.2.9 and the Ubuntu version is 2.2.6
So I wasn't trying to downgrade at all.

So are there any pointers as to why I cant transfer the data from windows version to linux??

---

