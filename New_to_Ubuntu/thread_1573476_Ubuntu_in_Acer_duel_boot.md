---
title: "Ubuntu in Acer duel boot"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by Q2299 on 2010-09-12
I have installed Ubunu 10.04 in my Acer laptop...
It is such a pain!!!
It is a curtailed version of my desktop.
Unable to upgrade or update.
Cannot install new items.
I have installed as a dual boot with XP on one drive and Ubuntu in the other.
XP works well.
any help any one?

---

### Post by MaindotC on 2010-09-12
Describe what happens when you try to upgrade your system.

---

### Post by Iowan on 2010-09-12
Moved to Absolute Beginner Talk

---

### Post by drs305 on 2010-09-12
Q2299,

Welcome to the Ubuntu forums.  :-)

What exactly are you having problems installing? Unless it is related only to Networking, this thread is probably better placed in Absolute Beginners. I or one of the other forum staff members can move the thread if necessary.

As for your problems, as strAlan said, we really need to know what you are trying to do. Since you are new to Linux, you are probably more comfortable with GUI applications. We can learn more from a terminal though, so if you tell us what you are trying to do that fails we can provide the command to run in a terminal.

The advantage is that linux will provide us with error messages that might tell us why the command fails. For instance, if you are trying to update your repositories with Synaptic or Software Sources, you can run the same command in terminal.

To open a terminal, go to Applications, Accessories and click on Terminal.
Copy or type these commands into the terminal. One at a time, press ENTER after each one. The first one updates the program lists from servers, the second updates the programs you have on your computer:
(A note on copying/pasting: to paste into a terminal, CTRL-SHIFT-C to copy contents within a terminal, CTRL-SHIFT-V to paste contents *into* a terminal. Use CTRL-C and CTRL-V outside the terminal just like you are used to.

```
sudo apt-get update
sudo apt-get upgrad

``` 
It will ask for your password. Type it - as you type you won't see anything. Just continue typing and press ENTER after entering it.

You should see output in the terminal. At the end, it may say it failed and why.

If that happens, post the results here.

---

