---
title: "[SOLVED] wireless connection"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by jboy012000 on 2008-12-12
Hi All,

I am looking to move back to Ubuntu, Vista is starting to cost me money now since vista premium does not come with desent back up software. Also I am fairly angry as I am a software develeper and I use Visual Studio and to buy a lisence for this software it costs £800.00. So I am going to learn pearl and my os will be Ubuntu.

So the one thing I need to know does the latest version of Ubuntu support my wireless chipset which is a Dell Wireless 1395 WLAN mini card - rev 2.10 (my laptop is a dell inspiron 1525).

Or do I need to use this NDISWRAPPER if that is the case how do I use this, I am going to download the latest release and try the live cd but any response would be much appreciated.

Thanks very much.

Johno.

---

### Post by Kareeser on 2008-12-12
My buddy has an Inspiron 1521 (could have a different network card, but in any case...)

Had some preliminary problems getting wireless working, but I didn't have to use ndiswrapper.

In any case, even if that wasn't the case, we can guide you through ndiswrapper :)

---

### Post by jboy012000 on 2008-12-12
oh dear,

it seems that windows has lost out big time, Ubuntu here I come, the answer to my own question is YES THE DELL INSPIRON 1525 WIRELESS WORKS, I didnt even need NDISWRAPPER, simply select your router e.g sky*** and enter your network key create a password and thats it done.

Thankyou Ubuntu.

---

### Post by anewguy on 2008-12-12
As a side note, I do some cross-platform development.  I personally use C and C++ with GTK in Linux, then install the GTK for Windows package in Windows itself.  There are some very minor things I have gotten around just by using compiler directives in the code - #if defined....  etc..

There are several languages you could do cross platform devleopment with.  Another is Java using the GUI development tool that comes with it - I think it's called Swing, but I'm not positive on that.

Just to keep you thinging if you want to develope programs for Windows in Linux, you can make them cross-platform fairly easily.

Dave ;)

---

### Post by omegamike3 on 2008-12-12
I have a Vostro 1400 with the same card. I've been running 8.10 for a while now using the non-free drivers. The open driver worked, but not all that greatly. The only limitation was that I had to plug my laptop into my router for a minute while I downloaded the driver for Ubuntu to install. It's been running great without any dropped connections or anything.

---

### Post by jboy012000 on 2008-12-12
Hi Dave,

This is something and probably the most important thing I need to sit down and think about, I started out learning to program with c++ but the book I was learning from kind of threw me in the deep end and I sort of got board and thats when I found Visual Basic, I know this is going to sound daft but is there software like vb.

If i can make a choice of were to continue with my programing then tommorow I can go out and get a couple of books and find some free tutorials online.

Is Perl or Python the way forward for creating User Interface applications or is there something better?

If I am better off with c++ then is there a compiler or code editer that is compatible with Ubuntu that I can use?

Cheers

John

---

### Post by anewguy on 2008-12-13
Perl and Python I don't have the experience to comment on, as I have never used Python and my perl programming has been non-GUI backends to web pages.  There are plenty of others who could answer that.

As far as a VB like language, I know there is something called Gambas or some such thing in the repositories, but I don't know how complete or usable it actually is.  I tried it once a couple of years ago but I think it was in Windows at that time and that particular port was incomplete.  I haven't tried the Linux one.

gcc and g++ (I'm trying to remember for sure, as it is second nature when I have to type it in) are both free and for Linux.  gcc might be installed by default - I'm not sure, but they are also in the repositories.

You may want to check synaptic package manager for them and Gambas as they are all there, and a better description will be there for you to look at.

C++ can be a challenge - I'm still lousy at it because I "grew up" on machine code, assembly, etc., and eventually to C.  The object orientation is probably the "hardest" part to "get", and in C++ that is sometimes more complicated.

Don't know much else to tell you!

Good luck!!

Dave ;)

---

### Post by kalaharix on 2008-12-14
Hi,

Gambas is GREAT (for my requirement: small business accounting in the broadest sense) but quite different from VB6. I urge you to give it a go. My favourite Linux Mag (Linux Format LXF114 Jan 09) says "...has blossomed into one of the finest development environments in the free software world" and "Gambas is, by a huge margin, the easiest way to dip your toe into open source coding, and we simply can't recommend it enough." 

Don't use Synaptic though: the version is woefully old. A small tutorial at [www.kalaharix.wordpress.com](www.kalaharix.wordpress.com) shows you how to get a later version.
A note to anewguy: Gambas doesn't do Windows and never has (and according to the creator, Benoit Minisini, never will). Some see lack of cross-platform as a disadvantage. I am trying to get away from the blue screen so this is not a problem for me.

---

### Post by jboy012000 on 2008-12-14
That would not be a problem for me either if I am honest but my wife and other people I write small applications for use windows but I will take a look anyway.

Thanks a lot for your advise.

Johno

---

