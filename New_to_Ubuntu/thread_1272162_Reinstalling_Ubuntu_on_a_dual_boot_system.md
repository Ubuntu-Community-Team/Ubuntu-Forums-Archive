---
title: "Reinstalling Ubuntu on a dual boot system"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by niallabrown on 2009-09-21
I searched but didn't find a clear answer as to how to re-install Ubuntu when it is dual booted with vista.  Can I get a full explanation of what to do assuming that I know nothing about what a mount point is or swap space.

It would be great if you could just click on an the graphic Ubuntu partition and indicate that you want to write over it or reinstall it. I will put this up on Ubuntu brainstorm.

Louieb, I know you are well meaning but it's not at all clear to a new user what to do once you get into the manual partitioning menu.

---

### Post by JC Cheloven on 2009-09-21
From memory (I hope not to forget anything important):

Boot from your ubuntu cd, and go install. 
When partitioning, choose manual, then use your current ubuntu partition with mountpoint "/", and the existing swap partition as swap.

That should be it.

Offtopic: you could consider using a filesystem backup utility, as fsarchiver, in order to avoid reinstalling the OS, updating it, reinstalling the apps ...

---

### Post by jpkotta on 2009-09-21
Have a look at [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace).  Also [http://www.linfo.org/mounting.html](http://www.linfo.org/mounting.html) and [http://www.linfo.org/swap_space.html](http://www.linfo.org/swap_space.html) for more general info.  I recommend not making swap much bigger than RAM; it's not really useful to make swap huge.

---

### Post by louieb on 2009-09-21
> **niallabrown said:**
> It would be great if you could just click on an the graphic Ubuntu partition and indicate that you want to write over it or reinstall it. I will put this up on Ubuntu brainstorm.

(re)Installing from the live CD, choose manual partitioning , and thats pretty much what you do.

---

### Post by niallabrown on 2009-09-22
JC Cheloven, that was the straight answer I was looking for.  It worked great... so if it's that simple why can't there just be a button for reinstall Ubuntu using the same partitioning configuration?  This was easy when given step by step instructions but for a for a new user who has no idea what / represents or ext3 or swap this is a point where I'm sure many new users say what?! you expect me to know how to do this?  Linux is to complicated for me.

Anyways posted an idea on brainstorm about it if anyone wants to contribute ideas to it.

Thanks for the help!

---

### Post by HarrisonNapper on 2009-09-22
I agree that there are always ways to make things easier, but one of the great things about Linux and Ubuntu is that these kinds of tasks are great opportunities to learn about how the OS works and participate in the Ubuntu community. I would also note that reinstalling Windows is usually nowhere near as easy and when it is, it is only because you have no alternatives to the option that Windows is giving you. One of the things that makes this OS so great is the fact that it does give you options, though it admittedly takes some getting used to.

/ is the beginning of a file tree and if you think of a folder in Windows that might be C:\Documents and Settings\ that means that the part of the file tree you are accessing begins on the branches preceding it. So on drive C (which in linux will usually not be a letter), you have the beginning of the file tree '\' followed by the branch you are accessing "Documents and Settings\". It works the same way in Linux except that when you reinstall, it is letting you choose where you want to start your file tree. This is useful for people who create a separate partition for their /Home directory so that whenever they reinstall, upgrade, or pretty much anything else with the native operating system, they keep all of their programs and the settings for those programs.

Backing up your files in linux is simply a matter of copying your /Home directory (though many will also want to keep their OS config settings by copying their /etc directory).

---

### Post by niallabrown on 2009-09-22
HarrisonNapper, that's a good explanation and I agree that it is important to have choices (which could still be a part of the menu) and for new users to have the opportunity to learn.  I think it is also important however to ensure that new users are successful and don't become intimidated.  This sort of thing scares me because I know that I could mess up my configuration and that has prompted me to leave the Ubuntu install abandoned for the last 3 months because I was scared that I would wreck my windows install.  However people with less computer skills can still become active contributors to the community.  I think to make Ubuntu very successful takes different people with different interests.  I contribute artwork to Ubuntu and Linux Mint and Templates for Scribus and Inkscape, contribute to Ubuntu and Kde brainstorms, report bugs and lots more.  That is how someone at my level of understanding of computers can contribute to the community.  I want to learn more about things like partitioning but I have many other focuses that I think are also valid.

---

### Post by HarrisonNapper on 2009-09-23
I agree those are excellent skills to bring to the community; I would venture to guess more people have switched after seeing a picture of someone's desktop using compiz than have switched because they learned about the differences between ext4 and ntfs. And I'm certainly not saying that everyone should learn everything, but if we each have different issues that affect us and we learn solutions to those issues and why they work, we can offer great support for essentially any issue that comes up. Not to mention we can do so through very insignificant contributions of our time. It's hard to find the balance between being user friendly/functional from an end-user perspective and involving people in the community and processes of the OS. If we concentrate too much on the former, we're just another Microsoft; security by obscurity, usability by confusability, etc. On the other hand, if we concentrate too much on the latter we become just another computer science club at your local college campus. I don't want you to think I was criticizing your skill set, only taking advantage of the opportunity to perhaps answer the question of an unsuspecting google searcher.

Anyway, question seems to have been answered, so we can probably mark the thread as solved and move on to other problems on the forum. Thanks!

---

### Post by niallabrown on 2009-09-23
I see what your saying and that makes sense.  I didn't mean to come off as defensive and I knew you weren't criticizing. I think these are important conversations to have in understanding the many different roles in the community and finding the balance you were talking about between user friendliness/functional.  I do agree that it's important that we all try to learn a variety of skills to support each other and I hope one day to be able to turn around and pass on what you replied to help others.

What I worry about is that new users may give up before they ever get a chance to be become a part of the community.  I may be a basic user but I have been around since Warty and there have been many times were I almost left because I am not great at understanding complex computer instructions.  Much has changed since then and I now know lots of tricks to make using Ubuntu comfortable for me and how to get help.

I don't know for sure what the solution is but I think choice plays a role.  Maybe users should get a choice if they want to do something with one click or if they want to explore and experiment and maintain the the ability to take it a step further.  I'm sure there is no right or wrong answer to this but it's interesting to think about.

This issues is solved and thanks for taking the time it's much appreciated!

---

