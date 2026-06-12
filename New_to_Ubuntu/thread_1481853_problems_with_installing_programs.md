---
title: "problems with installing programs"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by thorbs on 2010-05-13
Hi I just started using ubuntu the last month and I am having problems with installing programs. I have not been able to install the e editor, xampp and xmind.

Maybe I should say that I am using a dual boot with wubi.

Also I read that the dual boot is reducing the performance. Does anybody know how much performance is reduced.


Thanks for reading.

---

### Post by apostate on 2010-05-13
Can you elaborate on what sort of problems you have?

What steps have you taken to install these packages?

---

### Post by mal1958 on 2010-05-13
> **thorbs said:**
> Hi I just started using ubuntu the last month and I am having problems with installing programs. I have not been able to install the e editor, xampp and xmind.

Maybe I should say that I am using a dual boot with wubi.

Also I read that the dual boot is reducing the performance. Does anybody know how much performance is reduced.


Thanks for reading.

First:  Using Wubi is a poor way to go for a Dual Boot system.  I would recommend that you boot from the Ubuntu Live cd and install from there.

Second:  When you are trying to get help, it would help us to help you, if you would give us the stats on your system  (IE  PC, Mac, Notebook: Type of chip and speed; Pent 3, 4 Core duo, quad, soforth and the speed it runs at.)  Memory installed, type of Video card (or Video chipset on the Mother/daughter board)  Ditto with sound card/chipset.    if you are Dual booting, what is the other OS?  What version of Ubuntu are you working with?  And if you know What Bios type and version?

Slight Example using my box:

PC:
System:  Pent 3  (1 gigahertz)
Mem:  512 meg
HD(S):  2 60 gig HDs
Video Card:  Invidia GeForce 6300 (AGP)
Sound:  Sound Blaster Audigy LE
BIos:  UNK.
Dual boot,  Windows XP (SP 2 ) on first Drive
                  Ubuntu 9.10 (Karmic Koala) on Second HD

   This would give us a point of reference to work from.  Also if you could provide a bit more detail on what you did to try to install and any messages you got if the install failed.  This would help us more so we could, in turn, help you.

Mike

---

### Post by MelDJ on 2010-05-13
how are you installing and what happens when you try to install?

---

### Post by warfacegod on 2010-05-13
I agree with mal1958, wubi is a poor man's way of dual booting. Wubi was never intended for much more than an alternative way of trying out Ubuntu.

From the Documentation pages:

"Installing Ubuntu from within Windows

The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning."

Note the key word here is "try".

That said, the performance loss (depending on your hardware, of course) is *fairly* small.

---

### Post by 3rdalbum on 2010-05-13
> **thorbs said:**
> Hi I just started using ubuntu the last month and I am having problems with installing programs. I have not been able to install the e editor, xampp and xmind.

Command-line programs don't appear in your Applications menu; I assume that the E Editor is command-line.

XAMPP is not a program that you run and interact with and then quit; it's a selection of programs. The web server Apache and the database management system MySQL run on startup, and PHP and Perl are invoked when needed (or you can run them on the command-line, but once again there's no GUI).

So XAMPP will not appear in the Applications menu, because it's not an application.

And Xmind doesn't appear to be in the repositories anymore, there's nothing you can do about this except try to find a third-party repository that contains it, or a prebuilt binary or source code from the web.

---

### Post by thorbs on 2010-05-28
Hi thanks for all the replies. I chose to make a real partition and to install 10.04.

---

### Post by warfacegod on 2010-05-28
Let us know how things go.

---

