---
title: "puzzled to say the least"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by orangeworx on 2010-09-07
Hello everyone!
I'm posting here because I suspect this to be a n00b question, so here goes.
I've just spent pretty much my whole day installing 10.04 and waited hours to download all the updates the update manager listed (yeah I'm on a craptastic connection!) and just when I thought everything was going fine and dandy, I hit the restart button!
NOOO! it's not the least bit fine... Now I can't even see the bootloader screen. What I get is this:
GNU GRUB version 1.98-1ubuntu7
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub > and a blinking cursor here

I hit tab to see what I could possibly get and true enough I get a huge list of commands (of which most I've never heard of)
I did try the boot command, in the form boot /boot/initrd.img-2.6.32-2x-generic... my options are 21 and 24 (replacing the x)
both return error: no loaded kernel

The installation of 10.04 + update was done to 2 systems, a laptop - HP NC6000 - and an older desktop with a celeron CPU.
the above steps were done on the NC6000
the desktop on the other hand seems to be dealing with the updates much differently... on boot I get a scary 1 line message
[   2.229563] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
WHAT THE !!!!

I honestly have no idea whatsoever as to what to do and I need more than just insight :S I need a working solution...
anyone ?

thanks in advance!

---

### Post by orangeworx on 2010-09-07
wow I feel special! Am I really the only one who's had this happen to me? I'm stuck with 2 non-working computers and data that I'd rather recover :S
Does anyone know what are my possible options if any (other than a format!)
I did save the *.deb update files... at least it isn't a total crap chute if I'm going to have to format... but then again, if I'm going to format to have the same problem happen again, what's the point?

---

### Post by ShakeyJake on 2010-09-07
It sounds like you've really crapped up your kernel. Before this menu (or lack therof) is there a GRUB menu? It'll be black with white writing and it'll give you a countdown to chose different kernels. Pick another one other than the default.

---

### Post by silverglade00 on 2010-09-07
It sounds like the laptop did not get grub installed correctly. You should be able to boot the LiveCD on the laptop and follow the instructions [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") to get it going again.

The desktop is having trouble finding your Ubuntu partition. You might try those instructions from above on that one as well.

---

### Post by orangeworx on 2010-09-07
Hey Jake
thanks for responding... I get the grub "screen" almost as soon as the laptop boots up. I do not get the grub entries, just straight to grub> with the text just before it...
I can't think of what I might have done wrong, in fact, I just let the update manager download the updates (yeah I watched as the updates painfully downloaded, all 270 of them!) and install them... I also stared at the terminal as the updates were being installed until the process was over and I got the window telling me to restart the computer.
I'm not 100% sure but for some reason I suspect GRUB downgraded, is that even possible?

---

### Post by orangeworx on 2010-09-07
I'm going to check these out and I'll be back as soon as it either blows in my face or works out :P
thanks for the links

---

### Post by orangeworx on 2010-09-07
wow I must say that was pretty intense! I just went through the whole page and the methods... Method 3 did finally work out!!!
Now it's time to do this on the desktop. I'll be back with results
thanks a whole bunch SilverGlade

---

### Post by silverglade00 on 2010-09-07
No problem. I'm glad you found one to work for you!

---

### Post by SERVed6 on 2010-10-04
i know this thread is 3 weeks old but i was so excited that it worked, i was having the same problem where on start up every time it would take me to "Minimal BASH-like line editing is  supported. For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device or file completions." I've been messing with ubuntu for about 3 days and am a first time user or noob lol. but method 3 on silverglades post fixed my problem :) i thought it deserved recognition after the hours i have put online trying to fix my problem

---

### Post by cap10Ibraim on 2010-10-04
> **SERVed6 said:**
> i know this thread is 3 weeks old but i was so excited that it worked, i was having the same problem where on start up every time it would take me to "Minimal BASH-like line editing is  supported. For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device or file completions." I've been messing with ubuntu for about 3 days and am a first time user or noob lol. but method 3 on silverglades post fixed my problem :) i thought it deserved recognition after the hours i have put online trying to fix my problem

so mark it as solved up in the right corner THREAD TOOLS

---

### Post by bbqsandwich on 2010-10-04
> **cap10Ibraim said:**
> so mark it as solved up in the right corner THREAD TOOLS

It isn't SERVed6's thread.

---

