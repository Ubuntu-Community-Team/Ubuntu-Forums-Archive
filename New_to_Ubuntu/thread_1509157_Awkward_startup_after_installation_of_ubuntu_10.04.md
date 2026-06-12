---
title: "Awkward startup after installation of ubuntu 10.04"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by RPfeynman on 2010-06-13
I recently bought a Dell with a windows 7 OP pre-installed, but decided I would benefit from having ubuntu as well. Hence, I went through the installation process and set-up a dual boot on my pc. After logging out from a windows 7 session, shutting down the computer, and turning it back on, it seemed the GRUB bootloader had been overridden by some DELL software, which made it so I could no longer access the windows OP nor ubuntu. So, I wiped out both operating systems and re-installed ubuntu as my current (and only) operating system. 

Now to my question..
When I shut down the computer and attempt to get back on, the DELL logo is displayed with the usual options in the lower right hand corner (F2 Setup, etc.) After this loading step is completed, a blank screen is shown with only a blinking cursor on the display screen. The computer screen just stays this way.  However, when I restart the computer by holding the power button ubuntu eventually starts up and runs properly. 

Any suggestions on what might be going on?

---

### Post by shardvexspangler on 2010-06-13
Need more information...
 
Try doing it a few times?
What do you mean by blinking cursor?

---

### Post by RPfeynman on 2010-06-13
A cursor; like the one we use to type with (except this one is horizontal and not vertical). There's just a black screen with a white, blinking, horizontal cursor. When Ubuntu does start up, a bunch of words or commands show up on the screen after a few seconds.

---

### Post by shardvexspangler on 2010-06-13
Sorry, someone else help him!!!!!!!!

---

### Post by michaelaye on 2010-06-13
what u are seeing is normal. it is grub2 doing what ever it does during this time.

---

### Post by rukiaEnix on 2010-06-13
the "a lot of letters you see" is just ubuntu starting up it shows you the services that are starting.
and I know what you talking about, it also has happened to me the blinking cursor thing, sometimes when I start ubuntu it stays like that and I have to turn off my computer and after that it starts.
I was wondering if it has something to do with Apache2 startup, because when I shutdown the computer I can see that the service that was starting when ubuntu hang up was Apache2.

---

