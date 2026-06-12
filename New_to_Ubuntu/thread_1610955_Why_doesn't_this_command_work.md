---
title: "Why doesn't this command work?"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-11-01
I am trying to 'force install' a 32-bit package on a 64-bit machine as per instructions at:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00081](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00081)



rob@rob-desktop:~/Downloads$ sudo apt-get install -force=yes mfc495cwcupswrapper-1.1.2-2.i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mfc495cwcupswrapper-1.1.2-2.i386.deb

Why can't it find the package when it is living in Downloads??

What am I doing wrong?

Thanks,

---

### Post by BugBuster on 2010-11-01
To install a package you already have downloaded use the dpkg command like so;

```
$ sudo dpkg -i --force <package-name>
```

---

### Post by TeoBigusGeekus on 2010-11-01
Try this
```
sudo dpkg -i --force-all mfc495cwcupswrapper-1.1.2-2.i386.deb
```

---

### Post by Robert.Thompson on 2010-11-01
> **BugBuster said:**
> To install a package you already have downloaded use the dpkg command like so;

```
$ sudo dpkg -i --force <package-name>
```

Thank you.

This happened:


rob@rob-desktop:~/Downloads$ sudo dpkg -i --force mfc495cwcupswrapper-1.1.2-2.i386.deb
[sudo] password for rob: 
dpkg: unknown force/refuse option `mfc495cwcupswrapper-1.1.2-2.i386.deb'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

Where did I go wrong this time?

Thanks,

---

### Post by migs73 on 2010-11-01
Shouldn't it be --force-all  not just --force?

BTW I get dizzy going round and round on the Brother linux website. I am glad they've got it but it's not very friendly.

---

### Post by BugBuster on 2010-11-01
Well.. I think I misplaced the options a bit.

Try this;
```
$sudo dpkg --force -i <package-name>
```

Or if that does not work;
```
sudo dpkg --force-all -i <package-name>
```

Either of these commands should work!

---

### Post by Robert.Thompson on 2010-11-01
> **migs73 said:**
> Shouldn't it be --force-all  not just --force?

Thank you, --force-all seemed to work.

---

### Post by migs73 on 2010-11-01
Robert, let me know if they work okay, I may yet be tempted to a 64bit install ;)

---

### Post by Elfy on 2010-11-01
and please do not post ridiculous thread titles in support forums.

---

### Post by Robert.Thompson on 2010-11-01
> **forestpiskie said:**
> and please do not post ridiculous thread titles in support forums.

Sorry.

---

### Post by Elfy on 2010-11-01
Thank you.

---

### Post by Robert.Thompson on 2010-11-01
> **migs73 said:**
> Robert, let me know if they work okay, I may yet be tempted to a 64bit install ;)

Well, the commands in this thread worked but I still cannot print.

Maybe there are other things that I must do but I, of course, have no idea what.

I think this 64-bit stuff just adds another level of confusion to an already severely confused noob - I will think about this for a few hours but I think that the 64-bit OS is toast.

---

### Post by migs73 on 2010-11-01
Have you added the new printer in Administration > Printing?
Does it see the new printer but not print?

---

### Post by oldos2er on 2010-11-01
> **Robert.Thompson said:**
> Well, the commands in this thread worked but I still cannot print.


Have you installed ia32-libs?

---

### Post by migs73 on 2010-11-01
Did you also follow all the pre-requisites I linked to in your other thread?
Are you trying to connect on a network (is it set up) or via USB?
Is CUPS set-up?
Did you download/install the LPR driver?

You may still have along way to go!!!

[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)  This helped me though it is quite old.

---

### Post by Robert.Thompson on 2010-11-02
> **migs73 said:**
> Have you added the new printer in Administration > Printing?
Does it see the new printer but not print?

I deleted all existing printers.

Then I added a printer.

When I did a test page print nothing printed.

---

### Post by Robert.Thompson on 2010-11-02
> **oldos2er said:**
> Have you installed ia32-libs?

Yes, it is installed.

---

### Post by Robert.Thompson on 2010-11-02
> **migs73 said:**
> Did you also follow all the pre-requisites I linked to in your other thread?
Are you trying to connect on a network (is it set up) or via USB?
Is CUPS set-up?
Did you download/install the LPR driver?

You may still have along way to go!!!

[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)  This helped me though it is quite old.

I followed your link and all the instructions therein and guess what...

***[COLOR="SeaGreen"][SIZE="5"]MY PRINTER PRINTS!!!!!!![/SIZE][/COLOR]***:):):)

Thank you to all who helped me.

---

### Post by migs73 on 2010-11-02
Glad to have been of help, I wish I had found that old thread earlier!!

:)

---

### Post by Robert.Thompson on 2010-11-04
After re-booting the 64-bit system, the printer ceased to work.

I blew out the 64-bit OS and installed the 32-bit version.

I download and installed the drivers and all is well.


Anyone want to buy 2 gig's of memory, cheap?

---

### Post by migs73 on 2010-11-04
Robert

see here;

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

should enable you to use all your RAM.

Also it should have installed already if you had all your RAM installed when you put the 32bit OS on. Check at  System > Administration > System Monitor and click on the System Tab. If you have it installed it'll look like this; see attachment with kernel PAE.

If you need any more help. post back. Don't sell your RAM yet!!!


Mike

---

### Post by Robert.Thompson on 2010-11-04
> **migs73 said:**
> Robert

see here;

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

should enable you to use all your RAM.

Also it should have installed already if you had all your RAM installed when you put the 32bit OS on. Check at  System > Administration > System Monitor and click on the System Tab. If you have it installed it'll look like this; see attachment with kernel PAE.

If you need any more help. post back. Don't sell your RAM yet!!!


Mike

Thanks Mike, you were correct, it was installed!

---

### Post by migs73 on 2010-11-05
Phew!!

I assume all your RAM (minus system overheads) was shown to.

You don't get that with windows!!! (not without buying the server edition anyway)

:)

---

