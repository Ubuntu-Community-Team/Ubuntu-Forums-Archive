---
title: "Need to change the boot order on Wubi install"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by ErrolRay on 2010-06-27
On startup, I get an option to boot to XP and Ubuntu.  XP is the top of the list, and is the default.  This is the one I would like Ubuntu to be the default, and I assume it is controlled by XP

The second choice, when I choose Ubuntu, has the latest Ubuntu at the top, as the default, and XP at the bottom. 2 or 3 other choices are between the two, and I assume they are previous versions of Ubuntu that have been updated.

I have read on the forum something about how to change the first boot screen to have Ubuntu as the default, but for the life of me, I cannot find it.  I have searched.[-o<

Thanks,
Errol

---

### Post by bcbc on 2010-06-27
it's in the c:\boot.ini file. you can tweak the timeout and the default. It's read only so you have change this first (right-click, properties)

---

### Post by ErrolRay on 2010-06-27
Thanks for the response BCBC, but there is no boot.ini file that I can find. This is a Win 7 computer.  I have "Hide all hidden files" unchecked, and "show System Files" checked, and I still don't see it.

Any other suggestions?

Thanks,
Errol

---

### Post by varunendra on 2010-06-27
> **ErrolRay said:**
> Thanks for the response BCBC, but there is no boot.ini file that I can find. This is a Win 7 computer.  I have "Hide all hidden files" unchecked, and "show System Files" checked, and I still don't see it.

Any other suggestions?

Thanks,
Errol

First you said it shows options for XP & Ubuntu, then you are saying it is Win7 machine. What's going on? ;)

Anyway, here's your solution. Follow post #32, 33, & [COLOR=Red]**especially #39**[/COLOR] on this page.
[http://ubuntuforums.org/showthread.php?t=1498681&page=4](http://ubuntuforums.org/showthread.php?t=1498681&page=4)

You may wish to browse the whole thread to have a better understanding of the context.
:cool:




[SIZE=2]**PS: [COLOR=DarkRed]If you only want to change boot order in the first (Windows7) boot menu and it is indeed Windows 7, then [here's]("http://www.sevenforums.com/tutorials/2282-default-operating-system-change-default-boot-os.html") the way to go.[/COLOR]**[/SIZE]

---

### Post by ErrolRay on 2010-06-27
Sorry varunendra, I am confusing myself and everyone else trying to help.
I have 3 machines that I work off, and I was confusing my 7 machine with my XP/Ubuntu machine.

I will try to modify the boot.ini file on the C drive of the combination machine.

Thanks for bringing that up, I would not have noticed it for a while.

Errol

---

### Post by varunendra on 2010-06-27
:lol::lol:   8-[8-[  :lol::lol:

---

### Post by ErrolRay on 2010-06-27
Here are the contents of the XP boot.ini file.  I need to know just how to change it without screwing it up.  I did save a copy of the original.

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

C:\wubildr.mbr = "Ubuntu"

Thanks,
Errol

---

### Post by varunendra on 2010-06-27
Here's how your new file should look like:> [boot loader]

timeout=30

default=C:\wubildr.mbr

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

C:\wubildr.mbr = "Ubuntu"



---

### Post by ErrolRay on 2010-06-27
So the only thing I need to do, is change the default statement?

Thanks

---

### Post by varunendra on 2010-06-27
There are 6 lines in all. What else do you expect?

To change the order they appear in menu, just change their order in boot.ini file.
> C:\wubildr.mbr = "Ubuntu"

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /fastdetect /NoExecute=OptIn

To change the timeout (say 10sec. instead of 30) just overwrite 30 with 10.

Just don't change the title (first line, that says [boot loader]), filename, addresses of listed items (multi(0)disk(0)......... etc.) or their parameters (/fastdetect /Noexec.......) (well... this one you can change, but only when you know what you are doing).

That's all!
:popcorn:

---

### Post by ErrolRay on 2010-06-27
Thanks again.

Errol

---

