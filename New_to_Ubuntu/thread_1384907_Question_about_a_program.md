---
title: "Question about a program"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by Extract_Here on 2010-01-18
Is there a program for ubuntu that is like windoze ccleaner?

thanks in advance

btw ccleaner is a program that removes unnecessary cache and temp files and so on.

---

### Post by adam814 on 2010-01-18
I'm guessing you're looking for some combination of features between BleachBit and the "Computer Janitor" under System > Administration.

---

### Post by Extract_Here on 2010-01-18
which one do i need or do i need both

---

### Post by warfacegod on 2010-01-19
I use Ubuntu Tweak. An extremely useful app, not just for cleaning. Another is Ailurus. Also highly useful to me.

---

### Post by lisati on 2010-01-19
Haven't really had the need for programs like that for Ubuntu, other than occasionally using something like: ```
sudo apt-get clean
sudo apt-get autoclean

```

(See link in sig. for one of my efforts for Windows)

---

### Post by PenguinInside on 2010-01-19
Temp files, AFAIK, are clean out every time Ubuntu reboots.

Computer Janitor will tell you if there are programs which were installed because they were required by another program, but that other program isn't installed anymore. It will also allow you to remove them.

---

### Post by warfacegod on 2010-01-19
> **PenguinInside said:**
> Temp files, AFAIK, are clean out every time Ubuntu reboots.

Computer Janitor will tell you if there are programs which were installed because they were required by another program, but that other program isn't installed anymore. It will also allow you to remove them.

Computer Janitor will also frag your setup. I just ran it and it found 6 unused packages.

compiz-switch (I use daily)
nVidia-173 (My *graphics driver!*)
2 theme packages (I'm currently using both)
ubuntu-tweak (I use at least twice per month)
swiftfox-1686 (I'm using it right now!)

---

### Post by 3rdalbum on 2010-01-19
> **warfacegod said:**
> Computer Janitor will also frag your setup. I just ran it and it found 6 unused packages.

compiz-switch (I use daily)
nVidia-173 (My *graphics driver!*)
2 theme packages (I'm currently using both)
ubuntu-tweak (I use at least twice per month)
swiftfox-1686 (I'm using it right now!)

It will only frag your setup if you confirm to it that its suggestions are correct. Computers are not as smart as you or me - that's why humans operate computers and not the other way around.

CCleaner mainly works around some of the less efficient parts of Windows XP that can get crufted up. Ubuntu doesn't have anywhere near as many hidey-holes that can gather gunk. Just keep track of orphaned packages yourself using Synaptic, and clear out your package archive with 'sudo apt-get clean'.

---

### Post by warfacegod on 2010-01-19
> **3rdalbum said:**
> It will only frag your setup if you confirm to it that its suggestions are correct. Computers are not as smart as you or me - that's why humans operate computers and not the other way around.

CCleaner mainly works around some of the less efficient parts of Windows XP that can get crufted up. Ubuntu doesn't have anywhere near as many hidey-holes that can gather gunk. Just keep track of orphaned packages yourself using Synaptic, and clear out your package archive with 'sudo apt-get clean'.

I agree, the user is ultimately responsible for checking on what their software is or wants to do. However, the fact remains that Computer Janitor wanted to remove my Display Driver and the Internet Browser I was using when I ran it. That is not reasonable behavior for any software.

---

### Post by Bilal Haddad on 2010-01-19
hi, am trying to share my external hard disk on my network by using the Ubuntu Operating system. can i someone help me please ?

---

### Post by audiomick on 2010-01-19
> **warfacegod said:**
> ... the fact remains that Computer Janitor wanted to remove my Display Driver and the Internet Browser I was using when I ran it. That is not reasonable behavior for any software.

Yes, it seems that the Janitor isn't really reliable yet. I've seen a number of posts warning that one should look very carefully at what it wants to do, and if in doubt, cancel.

---

### Post by audiomick on 2010-01-19
> **Bilal Haddad said:**
> hi, am trying to share my external hard disk on my network by using the Ubuntu Operating system. can i someone help me please ?

You should start your own thread. This one is about something completely different.

---

### Post by warfacegod on 2010-01-19
> **Bilal Haddad said:**
> hi, am trying to share my external hard disk on my network by using the Ubuntu Operating system. can i someone help me please ?

Do a search of the forums. Samba, from what I understand, is a good way to do what you want if you have Windows machines as well. If you can't find what you are looking for, then start a new thread.

FYI It's considered bad form to jump into a thread like this.

---

### Post by warfacegod on 2010-01-19
> **audiomick said:**
> Yes, it seems that the Janitor isn't really reliable yet. I've seen a number of posts warning that one should look very carefully at what it wants to do, and if in doubt, cancel.

I've never had it even show me things that should be removed. Only the packages that I need. I've used Ubuntu Tweak many times and never had it remove anything I as using or cause any harm to my system. I'm testing Ailurus at the moment but so far it hasn't done anything bad to my system either.

---

### Post by lavinog on 2010-01-19
+1 for bleachbit
The vacuum for firefox really speeds up firefox.

Computer janitor is still a work in progress.  If it does something that you think it shouldn't please file a bug.

A good thing to do every once in a while is to delete your .thumbnails folder.
I have had times when it would take up a couple of gigs of space for images that don't exist anymore.

---

### Post by warfacegod on 2010-01-19
> **lavinog said:**
> +1 for bleachbit
The vacuum for firefox really speeds up firefox.

Computer janitor is still a work in progress.  If it does something that you think it shouldn't please file a bug.

A good thing to do every once in a while is to delete your .thumbnails folder.
I have had times when it would take up a couple of gigs of space for images that don't exist anymore.

I removed it instead.

---

