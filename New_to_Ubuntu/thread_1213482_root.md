---
title: "root"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by misswham on 2009-07-14
I am trying to install zenity and this is the error message I am getting when I put the command in the terminal

:~$ apt-get install zenity mplayer
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

What does the root mean and how can I get it to download?

---

### Post by oldos2er on 2009-07-14
Give yourself admin or root privleges by using "sudo", e.g.
```
sudo apt-get install zenity mplayer
```

---

### Post by TheNosh on 2009-07-14
root refers to the root user (equivalent to admin account in windows)

in ubuntu the command "sudo" gives you root priveleges needed for some tasks, for most other distros it's su

---

### Post by misswham on 2009-07-14
Thanks now I am trying to update clam and i keep getting the root message again

You must be root to install updates.

How do I let clam know I am the root?  I am going to clam then update signatures and hit update and thats where I get the message.  Do I have to update it everyday?

---

### Post by oldos2er on 2009-07-14
Are you using "sudo" to update clam?

---

### Post by ~sHyLoCk~ on 2009-07-14
> **misswham said:**
> Thanks now I am trying to update clam and i keep getting the root message again

You must be root to install updates.

How do I let clam know I am the root?  I am going to clam then update signatures and hit update and thats where I get the message.  Do I have to update it everyday?

What command are you using to update?

---

### Post by misswham on 2009-07-14
i havent used any command.  Dont really know how.  Can you tell me the command and do I need to do this everyday?

---

### Post by misswham on 2009-07-14
gksudo clamtk

got it thanks

---

### Post by TheNosh on 2009-07-14
right, i forgot to mention gksudo for graphical stuff (i assume what you're now talking about is graphical, no?)

---

### Post by misswham on 2009-07-15
I am not sure.  I just want to update my virus protection so i can scan files for the latest viruses

---

### Post by TheNosh on 2009-07-15
well i don't think updating the software would require a graphical interface so you would use sudo, not gksudo

whatever the commaned to update is, just type "sudo" in front of it. you'll then be prompted to enter your password, do that and you should be done

---

### Post by 3rdalbum on 2009-07-15
From your previous posts it doesn't look like you are running an e-mail server or any sort of server for Windows machines. I assume you're aware that Ubuntu doesn't get viruses?

---

### Post by ericab on 2009-07-15
> **3rdalbum said:**
> From your previous posts it doesn't look like you are running an e-mail server or any sort of server for Windows machines. I assume you're aware that Ubuntu doesn't get viruses?

dont bother using any anti-virus scanner for ubuntu please... clam-av is just a toy to make you *feel* secure.

save sudo for something important.

its getting cliche these days

[IMG]http://ubuntuforums.org/images/smilies/smiley-faces-80.gif[/IMG]

---

### Post by TheNosh on 2009-07-15
it isn't entirely unheard of for people to share files with friends who have windows, so it would make sense to make sure none of those files are infected

---

### Post by scorp123 on 2009-07-15
> **TheNosh said:**
> it isn't entirely unheard of for people to share files with friends who have windows, so it would make sense to make sure none of those files are infected If they are so *intelligent* and use Windows then let them take care of their own security.

@OP: Don't bother with that anti-virus stuff. You use Linux now, those days are over. Enjoy your new freedoms and new spare time (no more disk defragmenting, no more scanning for viruses ...)

---

### Post by Barrucadu on 2009-07-15
Does everybody really have to jump in and tell the OP not to use AV simply because he uses Linux? There may be no viruses in the wild for Linux, but scanning files which are to be shared with Windows computers is only polite.

---

### Post by TheNosh on 2009-07-15
> **Barrucadu said:**
> Does everybody really have to jump in and tell the OP not to use AV simply because he uses Linux? There may be no viruses in the wild for Linux, but scanning files which are to be shared with Windows computers is only polite.

glad to see i'm not the only one who feels that way.

---

### Post by 3rdalbum on 2009-07-15
> **Barrucadu said:**
> Does everybody really have to jump in and tell the OP not to use AV simply because he uses Linux? There may be no viruses in the wild for Linux, but scanning files which are to be shared with Windows computers is only polite.

Sorry, I guess I started the trend, but I did ask if they were sharing files with Windows computers.

---

### Post by scorp123 on 2009-07-15
> **Barrucadu said:**
>  but scanning files which are to be shared with Windows computers is only polite. Maybe it is *polite* but it is also a total waste of time because those AV definitions will always be one or two steps behind the "threat du jour" that Windows users have to put up with. 

Let everybody take responsibility for their own OS's problems. And for Windows users this means: let them scan for viruses. They are the ones who are supposed to be running anti*-this*, anti*-that* and anti*-something* software anyway, they are the ones who will be affected.

And your "politeness" might also backfire:

What if you tell a Windows user "Don't worry bro, I scanned those files for viruses, they are clean ... " and then something happens? YOU scanned for those viruses, YOU claimed the files are clean ... YOU are the one who gets the blame if something happens.

Just my last 0.2&#8364; on this topic. Have a nice day everyone ):P

---

### Post by TheNosh on 2009-07-15
> **scorp123 said:**
> And your "politeness" might also backfire:

What if you tell a Windows user "Don't worry bro, I scanned those files for viruses, they are clean ... " and then something happens? YOU scanned for those viruses, YOU claimed the files are clean ... YOU are the one who gets the blame if something happens.

you don't need to **guarantee** anything, just make an effort to be as sure as you can that files are clean. your friends should still know that virus scans aren't 100% effective and practice caution

---

