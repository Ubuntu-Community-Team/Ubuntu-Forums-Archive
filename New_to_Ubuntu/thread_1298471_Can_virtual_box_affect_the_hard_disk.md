---
title: "Can virtual box affect the hard disk?"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by Mariane on 2009-10-22
Hi, 

I installed virtualbox and got it running vista but next time I booted Kubuntu I got as far as the login screen and could do nothing there. The mouse did not move the cursor, the keyboard was inactive. I tried 3 times then booted in checking mode. Dell Vostro 1520, a 2-weeks old laptop. I got the error code 2000-0146. I phoned Dell support and they said I would have to change my hard disk. 

I booted from Ubuntu CD and it booted and displayed my files, as if nothing was wrong. Then I rebooted from the CD and did the check-disk option of the Ubuntu CD. It tells me nothing is wrong. 

But I still can't boot from the hard disk. 

What is going on??? 

Mariane

---

### Post by Dullstar on 2009-10-22
Hmm, try [SuperGrubDisk]("http://http//www.google.com/search?q=supergrubdisk&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

I don't guarantee it will work, but why not give it a try?

---

### Post by earthpigg on 2009-10-22
> **Mariane said:**
> Hi, 

I installed virtualbox and got it running vista but next time I booted Kubuntu I got as far as the login screen and could do nothing there. 

hi,

i don't suggest playing with super grub disk as Dullstar suggested. grub itself appears to be working fine. in fact, grub working fine is what may save the day for you:

virtual box installs a kernel module, which could be the problem... especially since the problem happened the very first time you booted after installing the kernel module.

at the GRUB screen when you first turn the computer on ("Press esc to somethingorother...3...2...1..."), do you see multiple kernel versions? if so, give one of those a shot and let us know what happens.

make sure you are looking at your GRUB screen for different kernels, and not your BIOS screen. both say "press -something- to enter setup"... grub is the one that says "GRUB" and has "Ubuntu something or other" on the screen :D

---

### Post by Mariane on 2009-10-23
I have "press F2 to enter BIOS setup, press F12 for boot options" when I boot with Ubuntu CD in the machine and pressing "Escape" just starts the system bell. 

When I press "Escape" while booting without the Ubuntu CD a menu appears with twice Ubuntu and twice Ubuntu in recovery mode. I selected recovery mode and got lots and lots of errors. 

Finally it said: 
/dev/sda1: UNEXPECTED INCONSISTENCY; run fsck manually. Without -a or -p options. fsck died with exit status 4. 

I got a prompt so I typed fsck. I am again getting errors. It is asking me several times "Ignore error?" and "Force rewrite?" with the only offered answer "Yes". So I kept hitting the y key for a while. 

What should I do next? 

Mariane

---

### Post by Mariane on 2009-10-23
It is not my files which are being displayed... :( 

I tried /home and in fact it seems to be reading from the cd... 

```

df -h

```

Gives me a list of all the devices and stuff, along with the amount of available disk space. The -h parameters says to display this in human readable format. The hard disk is not in this list. And /dev itself (the directory) displays its usual list of tty34 and loop43 and whatever not which I have never been able to make heads or tails of. 

Back to the shop with this machine. 

Mariane

---

### Post by Mariane on 2009-10-23
Maybe I should have tried super grub after all. Before I did this grub thing I was asked for my Ubuntu user name and password when booting from the CD, after the grub I was not asked for it anymore. Maybe I should have tried to backup what I could before the grub. 

Anyway. I most certainly have no hard feelings as I am sure the advice I received was well intentioned. These things happen. The repair shop told me 7 to 10 days and meanwhile I still have the old laptop. 

Mariane

---

### Post by Dullstar on 2009-10-23
This is an interesting little issue here.  I wonder how it happened.  too bad I'm not good at finding the causes of these little issues here and there.

---

### Post by Mariane on 2009-10-23
> **Dullstar said:**
> 
I wonder how it happened.


Me too. I wonder whether I should give virtualbox another try when I get this laptop back. I wonder what they would say at the shop if I brought it back again saying the hard disk doesn't work... again. 

They didn't sound happy when I told them the file system was ext3... If I ever have to bring it in again they would probably say it's my fault if it gets messed up. Maybe it is my fault. 

Mariane

---

### Post by Dullstar on 2009-10-23
Where did you take it?  Most tech places will only do Windows and, if you're lucky, Mac.

---

