---
title: "Plasma Workspace crashes on bootup - can't use Kubuntu!"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by EssexEagle on 2009-09-24
A couple of days ago I installed Kubuntu 9.04 on my laptop and it's been working fine, until last night when I turned it off. All the GUI seemed to close down OK, then it went to a black screen - normally a load of white writing appears at this point before the computer switches itself off, but this time nothing happened at all, and I just had to hold down the laptop's power button until it went off.

Today, when I tried to turn the laptop on, I got as far as the Kubuntu log-on screen, entered my password, the splash screen appeared as normal, but then I got a message saying "A fatal error occurred - The application Plasma Workspace (plasma) crashed and caused the signal 11 (SIGSEGV)".
A couple of windows opened (Konsole and Pidgin, since they were open last time I switched off) but they had no titlebar. I had nothing on my desktop, and no panel at the bottom of the screen. All I could do was press the power button and then log out, shut down or restart. I've tried booting up several times, but always with the same result.

A bit of Googling discovered lots of people with similar problems, and the consesnus seems to be that removing the ~/.kde/share/config/plasma-appletsrc file is the best fix, but that doesn't work for me :(

Can anyone help me work out what's wrong, and help me to fix it? :confused:

---

### Post by EssexEagle on 2009-09-24
Perhaps I should add:
I added the kubuntu backport repositories yesterday following [these instructions]("http://webupd8.blogspot.com/2009/08/install-kde-43-in-ubuntu-jaunty-904.html") with a view to upgrading from KDE 4.2 to 4.3
I then ran
```
$ sudo apt-get update
$ sudo apt-get upgrade
```
and then
```
$ sudo apt-get dist-upgrade
```
but saw that there were over 200MB of files to download and, given that that's 10% of our monthly download limit in one go, decided against it.

Could doing this have broken my KDE installation somehow?

---

