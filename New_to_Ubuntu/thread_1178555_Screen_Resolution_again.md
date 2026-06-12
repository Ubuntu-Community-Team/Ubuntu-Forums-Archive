---
title: "Screen Resolution again"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by blur xc on 2009-06-04
Please don't post links to other screen resolution threads and think you are helping me out- I've already searched them, printed out about 100pages of them, and I'm still having trouble.

First foremost- the biggest problem I'm having is that almost every thread I read goes something like this- "Oh, that's not a big problem, just 'sudo apt get unitall reconfigure xorg.conf etc. etc...  add modelines config etc...  etc.."

Jibberish...I'm an ubuntu idiot. 

Ok- I'm building a new pc (I've that mentioned in some other posts), and I plan to go ubnunto on it.  I understand and accept there'll be learning curve, I'm like in kindergarten, so it doesn't do any good to give me college level inormation.  To get my feet wet, so I'm not completely out in the cold when I turn it on (maybe tonight!), I installed in on my work pc via wubi.  So far, the screen resolution is stuck at 800x600 61hz settings.  I'd like it to run 1920 x 1200 @ 60hz (what it is under windows).

Here's the specs- 
Dell Precision M6300 (laptop w/ external 24" monitor, but I run the laptop monitor at the same rez)
MS XP Pro SP3
Intel Core 2 Extreme CPU X7900 @ 2.80ghz
4gig ram
Nvidia Quadro FX 3600M 512mb Ram

I need my hands held, at least for a little bit, I've got like 2hrs of Ubuntu under my belt.

Thanks in advance..
BM

---

### Post by marshall.robert on 2009-06-04
All the threads that give you the command line to reconfigure XOrg (the graphical server for Ubuntu) are null and void. That functionality has been removed in promotion of the "automatic" approach.

I have to ask now, the typical question; have you downloaded installed the nVidia drivers, supplied by nVidia, via the Restricted Drivers Manager?

---

### Post by blur xc on 2009-06-04
I don't know.  how do I go about doing that?  Are those the ones that will cost some $$?

BM

---

### Post by marshall.robert on 2009-06-04
They are free. The Restricted Drivers Manager is in System -> Administration. They should be listed there, if they exist for your card. Just select one and click Activate and then wait a bit. A box with a progress bar will pop up, although it may look like its doing nothing its downloading.

---

### Post by blur xc on 2009-06-04
> **marshall.robert said:**
> They are free. The Restricted Drivers Manager is in System -> Administration. They should be listed there, if they exist for your card. Just select one and click Activate and then wait a bit. A box with a progress bar will pop up, although it may look like its doing nothing its downloading.

So, did like you said and I was amazed at how easy that was- but after the reboot I get a black screen.  The ubuntu loading screen shows up like normal w/ the cool status bar, but after that, I get a cursor at the top of the screen followed by "entering power save mode" as if the dvi cable was disconnected.  Only spastic striking of the ctrl-alt-del gets me to a reboot- then I booted up in recovery mode.  Ran xfix, which reverts the nvidia driver back to un-enabled.  Back to square 1.1.02  (I figure, that's a bit better than square 1 since I now know about the restricted drivers).

BM

---

### Post by marshall.robert on 2009-06-04
lol. Well, do you have a VGA/D-Sub connection on the graphics card too? 
I have a feeling it could be using that. 
That basically requires you to get a converter, or VGA monitor, and connect that to the VGA output on the card and see if that gives you anything. 
If it does then run the nVidia Settings program from System -> Administration and then attempt to get it to output from the DVI.
This may involve forcing it to output to the DVI through a mirroring option (I havn't had to use it in a while) and then plugging in to DVI then disabling it from the VGA. Bit of a faff but thats all that i can come up with.

---

### Post by blur xc on 2009-06-05
> **marshall.robert said:**
> lol. Well, do you have a VGA/D-Sub connection on the graphics card too? 
I have a feeling it could be using that. 
That basically requires you to get a converter, or VGA monitor, and connect that to the VGA output on the card and see if that gives you anything. 
If it does then run the nVidia Settings program from System -> Administration and then attempt to get it to output from the DVI.
This may involve forcing it to output to the DVI through a mirroring option (I havn't had to use it in a while) and then plugging in to DVI then disabling it from the VGA. Bit of a faff but thats all that i can come up with.

I think you are right.  I've got both vga and dvi outs on my laptop, and the desktop display is plugged into the dvi port.  Doesn't matter- trial period is over.  I've got my new home computer assmebled (not w/o problems, but that's in another thread :() and I removed ubuntu from my work computer.

Thanks for again for your help...  

BM

---

