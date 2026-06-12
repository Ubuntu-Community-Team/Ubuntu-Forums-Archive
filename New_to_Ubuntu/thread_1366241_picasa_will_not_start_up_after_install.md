---
title: "picasa will not start up after install"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by irishy on 2009-12-28
Help 
can anyone point me in the right direction I have installed picasa 2.7I in ubuntu 9.10 but cannot get it to start up  
thanks 
Irishy

---

### Post by arochester on 2009-12-28
Try:
1)Alt+F2 and type picasa
2) Open a Terminal and type picasa
3) In the Menu find and click on "Run" and type picasa

You may need to manually edit your Menu to add Picasa

---

### Post by irishy on 2009-12-28
Thanks for your help I tried alt f2 no luck
I opened  a terminal and typed picasa and entered but no luck  I am unsure were menu is I really am basic
thanks again

---

### Post by MelDJ on 2009-12-28
what is the output when you type picasa in terminal?
it should be in apps-graphics

---

### Post by irishy on 2009-12-28
$ picasa
/usr/bin/picasa: line 139:  4031 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175:  4134 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

---

### Post by Midnighter on 2009-12-28
2.7 would not run for me either, so i installed 3.0 instead and it runs fine.

---

### Post by mlentink on 2009-12-28
You did not inadvertently try to install the Windows version of Picasa through Wine?

Did you download it from here: [http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html) ?

---

### Post by irishy on 2009-12-28
Thanks for all your help I did download it from the link you have supplied but it was not the windows version
thanks

---

### Post by irishy on 2009-12-29
Thanks for all your help I have done what midnighter suggested and that works
thanks

---

### Post by cmuxed on 2010-08-09
> **Midnighter said:**
> 2.7 would not run for me either, so i installed 3.0 instead and it runs fine.

Cheers from a fellow Aussie.. this worked for me too.  I contemplated installing the beta but decided to comment out my test repo and just installed the stable... pfft.  Didnt work... heard the hdd ticking over but nothing.  Picasa 3 beta started up right away!

Cheers :)

---

### Post by AmanJivan on 2010-08-27
> **Midnighter said:**
> 2.7 would not run for me either, so i installed 3.0 instead and it runs fine.

this was the only solution that worked for me as well. Thanks for the advice :D

---

### Post by thedaylights on 2010-10-08
I'm having the same problem. I think the issue is that it's not being opened under wine. I don't know how wine works. It looks like Picasa 3 will save me some headaches so I'll try that.

---

### Post by pipia on 2011-08-17
Hi!

Same problem here, I just installed Picasa 3 (downloaded from the Linux section) and I installed it. So it appears in my list of programs. But when I click to open on it, nothing happens.
So I tried to open it trough the terminal, and I got this:

> **irishy said:**
> $ picasa
/usr/bin/picasa: line 139:  4031 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175:  4134 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

Any suggestions? Unfortunately I installed 3.0, so the lucky guys' trick with installing the newer version is not applicable here.
Sorry if I'm asking a stupid question, I am really novice on Ubuntu ;-)

---

### Post by merlin666 on 2011-08-29
> **pipia said:**
> Hi!

Same problem here, I just installed Picasa 3 (downloaded from the Linux section) and I installed it. So it appears in my list of programs. But when I click to open on it, nothing happens.
So I tried to open it trough the terminal, and I got this:



Any suggestions? Unfortunately I installed 3.0, so the lucky guys' trick with installing the newer version is not applicable here.
Sorry if I'm asking a stupid question, I am really novice on Ubuntu ;-)
Getting the same message here. Can this be solved?

---

### Post by bigtel on 2011-11-20
I am getting the same message to..! Help..!

---

### Post by rewyllys on 2011-11-20
> **bigtel said:**
> I am getting the same message to..! Help..!
Without any difficulty, I just installed Picasa 3 via the Software Manager in Linux Mint 11 (which is based on Ubuntu 11.04).  It starts up perfectly.

---

### Post by fleamour on 2011-11-20
Hijack!  (The Terrorist Group! The, The-The-The, The Terrorist Group.)

How can I manually edit menu along with icon?  Picasa is not showing up under Graphics.  I am running Xubuntu 10.04.

---

