---
title: "ubuntu files on thumb-installed, how to get to ubuntu installed on HD?"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by RotorRick on 2011-03-28
Ok, so I tried ubuntu (desk) 10.10 on a thumb drive, ran it for several days, even downloaded a few torrents, this was a "thumbdrive install, persistant changes".  Ok, so I decided to take the plunge, and installed 10.04 onto my laptop, full install on the hard drive. That worked very well, pleased.

Last night I wanted to grab those torrents I downloaded onto the thumb drive...so with the laptop running 10.04, I just plugged in the USB drive. It seemed to recognize it, and I tried browsing through the files...but I did not see anything remotely looking like a video file at all. Or Documents, pics or anything else.

So I'm a little confused, and believe that I did something wrong, or didn't realize I had to do something. Am I making sense?

PS:  I come from the Windows world, should I be setting something up for security, regarding worms, spyware and stuff? I heard viruses don't touch Linux, but maybe I heard wrong...

---

### Post by An Sanct on 2011-03-28
The files on the "persistent" partition are stored inside the **casper-rw** and can be accessed from the live USB.

The solution: boot your laptop from the USB and copy or move the files over to the existing partition on the laptop.

PS. You can try [nod32 for linux]("http://beta.eset.com/linux") :) There is no OS, that has not got viruses, its just, that is is harder to target Linux users, opposite to windows users :), even Amiga and C64 had viruses...

---

### Post by fabricator4 on 2011-03-28
> **RotorRick said:**
> drive. It seemed to recognize it, and I tried browsing through the files...but I did not see anything remotely looking like a video file at all. Or Documents, pics or anything else.


The files are stored in a virtual drive on the USB stick.  Boot off the USB stick again, then copy the files to the home directory.  To get to the home directory (after booting the USB) open "computer" in places, double click on the hard drive - it will say something like xxx GB hard drive: xxx GB filesystem. Now double click on HOME, then double click on your username.  Open another window with the torrents and drag them into your username directory.  If you have problems with file permissions, start Nautilus file manager with "gksu nautilus".

> 
PS:  I come from the Windows world, should I be setting something up for security, regarding worms, spyware and stuff? I heard viruses don't touch Linux, but maybe I heard wrong...

No, you heard pretty well right.  Mostly, security is a matter of common sense the way Ubuntu and other Linux OS's are set up.  An Ubuntu using friend of mine used to like going to infected sites and seeing the popups come up: "Your C Drive is infected with viruses, send us money now".  Hilarious - Ubuntu doesn't have a C drive of course.

I remember I was working on a nasty bootloader program on a Windows machine at work - this was one that could also spread by putting an autorun on any disk that it came across.  Without thinking I brought my USB stick home and put it in my Ubuntu machine - Ubuntu politely informed me that some stupid windows autorun program was on the USB, what did I want to do with it?

No problems if you keep a little commonsense on hand.

Chris.

---

### Post by RotorRick on 2011-03-28
Thank you very much Gentlemen! :D

This is a great forum, constructive discussion in minutes and hours. Actually it was recommended to me by a Linux power-user...he had three laptops and two desktops all running simultaneously for various different needs...wrote and created music on one, another for general web browsing, still another dedicated to torrents, and I think one was for testing/debugging stuff...I don't really know. But Linux/Ubuntu was brand new to me and he recommended this site as being the 'go-to' site!

It's like the polar opposite of the typical Youtube comments...which nearly always leave me shaking my head wondering how some of them had enough brains to boot up a computer and learn to type...

---

### Post by Hedgehog1 on 2011-03-28
> **RotorRick said:**
> Thank you very much Gentlemen! :D

RotorRick,

Your plan to test Ubuntu using a persistent USB install was very good thinking.  This gave you time to see if Ubuntu was the right fit for you before loading it on a hard drive.

You are both smart AND well mannered.  You presence on the forum is very welcome.  **You will fit right in.** :D


***The Hedge***

:KS

---

### Post by An Sanct on 2011-03-29
> **Hedgehog1 said:**
> RotorRick,

Your plan to test Ubuntu using a persistent USB install was very good thinking.  This gave you time to see if Ubuntu was the right fit for you before loading it on a hard drive.

You are both smart AND well mannered.  You presence on the forum is very welcome.  **You will fit right in.** :D


***The Hedge***

:KS
I agree here too!

PS. Please, if this post helped, mark the thread as solved (under "Thread Tools"), to make it of relevance for future users.

---

