---
title: "What are Graphical Applications ?"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by mikodo on 2009-07-13
Hello everyone,

In our forums it is recommended to run graphical applications using the command gksudo and not by sudo. Fair enough, but for newbies like myself who don't know what graphical applications are, where can we find a description of them.

I know this must be a real dumber, but I don't know, and am willing to bet I'm not the only newbie who doesn't. 

Thank you.

---

### Post by Elfy on 2009-07-13
Applications that don't run in a terminal is the simplest explanation. 

For example you can use nano or gedit to edit text files - run nano with sudo and gedit with gksudo.

---

### Post by nothingspecial on 2009-07-13
Applications with buttons to click and boxes to check.

As opposed to commands run in the terminal

---

### Post by sisco311 on 2009-07-13
non [text-based]("http://en.wikipedia.org/wiki/Text-based_(computing)") applications. :evil:

---

### Post by mikodo on 2009-07-13
Thank you,

So would this be the same as GUI's?

---

### Post by lisati on 2009-07-13
> **mikodo said:**
> Thank you,

So would this be the same as GUI's?

Pretty much so: GUI = "Graphical User Environment"

---

### Post by fballem on 2009-07-13
> **mikodo said:**
> Hello everyone,

In our forums it is recommended to run graphical applications using the command gksudo and not by sudo. Fair enough, but for newbies like myself who don't know what graphical applications are, where can we find a description of them.

I know this must be a real dumber, but I don't know, and am willing to bet I'm not the only newbie who doesn't. 

Thank you.

Mikodo:

I felt really old when my kids asked me, "Dad, what's a payphone?". The question was perfectly reasonable - they are young and there are very few payphones around anymore.

I am now feeling positively ancient! My suspicion is that you grew up knowing nothing but Windows on a computer. Some of us have been using PCs since the early 1980s, when they ran DOS. I remember taking a computer course in the late 1960s using punch cards and praying that the operator who loaded the punch cards didn't drop them.

As my darling daughter frequently reminds me, "Dad, you're old!" I don't think I'll share this post with her, so that I can remain merely old and not ancient in her eyes.

Regards,

---

### Post by zipperback on 2009-07-13
> **lisati said:**
> Pretty much so: GUI = "Graphical User Environment"



GUI = Graphical User Interface


- zipperback
:popcorn:

---

### Post by t0p on 2009-07-13
> **fballem said:**
> 
I felt really old when my kids asked me, "Dad, what's a payphone?". The question was perfectly reasonable - they are young and there are very few payphones around anymore.


I guess this must be a Canadian thing.  Here in the UK there are loads of payphones about.  Okay, many of them do SMS and email in addition to voice calls.  Okay, they don't come in the old-style red booths any more. And okay, lots of them take credit cards as well as cash.  But they are still payphones. 

Which is pretty weird, when you consider the ubiquity of cellphones nowadays.

---

### Post by fballem on 2009-07-13
> **t0p said:**
> I guess this must be a Canadian thing.  Here in the UK there are loads of payphones about.  Okay, many of them do SMS and email in addition to voice calls.  Okay, they don't come in the old-style red booths any more. And okay, lots of them take credit cards as well as cash.  But they are still payphones. 

Which is pretty weird, when you consider the ubiquity of cellphones nowadays.

The cell phone has pretty much killed payphones over here. If you do find a payphone, then the chances are very good that it won't work. I do remember that when I worked in New York a few years ago, payphones were pretty common in Manhattan, but the cords were cut more often than not.

We've probably gone off topic. I do hope that the OP doesn't mind too much.

---

### Post by ByteJuggler on 2009-07-13
> **lisati said:**
> Pretty much so: GUI = "Graphical User Environment"

Edit: Never mind, repeated what someone else already said (having not read the entire thread.) Sorry!

---

### Post by Phlex_de on 2009-07-13
I sometimes go back to my console and see it busy because of the gksudo. I found out appending ' &' to the command makes it run in the background and the console stays usable. (gksudo gedit ... for example)

Would you recommend running all gksudo commands with ' &'? 
Are there reasons for or against running some commands in the background?

---

### Post by halitech on 2009-07-13
the only time you should be running an app (text or graphical) with sudo is when you are actively using it. If you are running a graphical app with gksudo, press ALT + F2, type the command in and hit okay. It will prompt you for the password and then run so you don't tie up the terminal.

there are very few apps I have to run with sudo and usually only for a few minutes. You should *NEVER* have to run everyday apps like firefox as sudo.

---

### Post by mikodo on 2009-07-13
> **fballem said:**
> Mikodo:

I felt really old when my kids asked me, "Dad, what's a payphone?". The question was perfectly reasonable - they are young and there are very few payphones around anymore.

I am now feeling positively ancient! My suspicion is that you grew up knowing nothing but Windows on a computer. Some of us have been using PCs since the early 1980s, when they ran DOS. I remember taking a computer course in the late 1960s using punch cards and praying that the operator who loaded the punch cards didn't drop them.

As my darling daughter frequently reminds me, "Dad, you're old!" I don't think I'll share this post with her, so that I can remain merely old and not ancient in her eyes.

Regards,

Hi folks,

Thanks for the posts. I've enjoyed them. 

Yes,fballem my first OS was MS Vista; but on the other hand, I remember when our community(Saskatchewan) first had installed Television in the fifties, and my father had run out and bought our first Black and White set. As a kid then, I sat and watched the "snow" for who knows how many days until the cable was connected to our house!! My point being, I am very new to computers and am old, both making this journey into GNU/Linux Ubuntu challenging. I'm having a lot of fun, I just ask a lot of dumb questions.

Bye for now,

mikodo

---

### Post by fballem on 2009-07-13
> **mikodo said:**
> Hi folks,

Thanks for the posts. I've enjoyed them. 

Yes,fballem my first OS was MS Vista; but on the other hand, I remember when our community(Saskatchewan) first had installed Television in the fifties, and my father had run out and bought our first Black and White set. As a kid then, I sat and watched the "snow" for who knows how many days until the cable was connected to our house!! My point being, I am very new to computers and am old, both making this journey into GNU/Linux Ubuntu challenging. I'm having a lot of fun, I just ask a lot of dumb questions.

Bye for now,

mikodo

Thanks for sharing that - I remember my dad buying our first black and white tv in the 50s. We were living in Calgary. We didn't have cable - we had two television stations (CBC and CTV) that broadcast. We had a rabbit-ear antenna that had to be positioned "just so". Of course the "just so" position was different for each of the two stations. I suspect that we're contemporaries, but you're newer to computers than I am.

I suspect that you will have an easier time adapting to ubuntu than I did. Like many long-time users of computers, specifically Windows, we have gotten used to doing things in a specific way. Linux is not Windows, but it's close enough that I still have to think about things if they don't quite work the way that I expected. People with relatively little computer experience have a much easier time learning ubuntu than the windows old-hands.

I started with ubuntu about a year ago. I wasn't really having a lot of trouble with Windows Vista, but Office 2007 was a nightmare! I was a power user of Office 2003/XP/98/95 ..., but I could never get used to the new interface on Office 2007. A friend of mine suggested ubuntu and open office, and I gave it a try. I'm still here after a year.

The only thing that I haven't found a replacement for is Visio. It hasn't been reverse-engineered, and there is no suitable replacement program. I made the conscious decision to abandon my Visio files (there were relatively few of them).

I still have a Windows computer in the house, since my wife refuses to switch, but I don't use it.

Good to see that we old folks can still learn new tricks!

Enjoyed the chat, and glad you got your question answered.

Regards,

---

### Post by ByteJuggler on 2009-07-14
> **fballem said:**
> The only thing that I haven't found a replacement for is Visio. It hasn't been reverse-engineered, and there is no suitable replacement program. I made the conscious decision to abandon my Visio files (there were relatively few of them).

Well, there is Kivio, and Open Office Draw, and Dia (but I suppose you know of these...?)

---

