---
title: "terminal command - what does this mean"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by capnthommo on 2009-04-03
hi everybody.
i just came across the command 
```
sudo apt-get install -f
```
i don't think i know this one, not really being that familiar with the cli yet, so before i paste it into my 'handy-dandy reference guide to terminal commands' that i am gradually collecting, and then go using it can somebody just clarify for me, what does it do.  i have tried searches but i can't find the answer i seek.
from the context in which it was used, i would assume it restored or re-installed a deleted or broken package or app.  "am i right sir? am i right?"
(there will be a small prize for the first poster to correctly identify that closing quote above).
thanks everyone
cheers
nigel

---

### Post by CatKiller on 2009-04-03
From **man apt-get**:

>        -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. Any Package that are
           specified must completely correct the problem. The option is
           sometimes necessary when running APT for the first time; APT itself
           does not allow broken package dependencies to exist on a system. It
           is possible that a system´s dependency structure can be so corrupt
           as to require manual intervention (which usually means using
           dselect(8) or dpkg --remove to eliminate some of the offending
           packages). Use of this option together with -m may produce an error
           in some situations.

---

### Post by ajgreeny on 2009-04-03
"am i right sir? am i right?"

From "The Fast Show"?

I do like wasting time occasionally.

---

### Post by hyper_ch on 2009-04-03
if you don't know what any command means, you can find out:

```

man COMMAND

```

e.g.

```

man apt-get

```

---

### Post by capnthommo on 2009-04-03
hi again and thanks all.  as i thought, i was using a poor search term.  i shall make a big poster to remind me - use the man pages - sorry, i could have worked this out for myself couldn't i?  anyway, question answered.
and 'the fast show'?  no. i'm afraid not - try about, ooh, i should guess about 40 to 50 years earlier.  here's a hint - movies, not t.v.
care to try again sir?
thanks again everybody
nigel

---

### Post by CatKiller on 2009-04-03
It's The 39 Steps, isn't it?

---

### Post by Malalo on 2009-04-03
> **CatKiller said:**
> It's The 39 Steps, isn't it?

Awww beat by 10 minutes... I would've said "39 steps by Hitchcock"...

---

### Post by capnthommo on 2009-04-03
ladies and gentlemen we have a winner!
well done CatKiller, and the small prize is the kudos that goes with spotting this little bit of obscurity.
and malalo,  credit for the slightly more full answer.  it was, indeed, the original (i think) version.  it was the catch phrase and, incidentally, the last words of the memory man.
brilliant work, people.
sorry for the flippance, but it's a sunny friday here and i feel light of heart.
shears
nigel
=D>

---

### Post by kenb12 on 2009-04-04
Picked up this post with a search.
As a total novice/beginner I am trying to make sense of Ubuntu.
The posts in this Forum contain various instructions in the use of Commands.
If we take the a simple example in the above post/answer it states:
to use the following: man command
At the Terminal I typed in the above, and received the notification 'No 
Manual entry for Command'.
I must be doing something terribly wrong, and just cannot find out what I am doing or not doing correctly.
Have tried various other commands from this Forum and apart from Whoami and Date all have failed.
Very frustrated and puzzled.
Would someone kindly show/tell what the problem is.
Thanks.

---

### Post by Elfy on 2009-04-04
@kenB12 replace COMMAND with the command you are trying to get the man page for :)

man man

man apt-get

man sudo

etc ...

---

### Post by SteveNorman on 2009-04-04
try this one,

man woman

heehee

---

### Post by kenb12 on 2009-04-04
Thanks Forestpixie.
That explanation did the trick.
Now I can carry on 'trying' to learn Ubuntu.
Help much appreciated.Thanks.
By the way, have not used Windows for three days now, when does the 'withdrawal' symptoms courtesy of Mr gates STRIKE!!!!!!!

---

### Post by hyper_ch on 2009-04-04
well, if you're not comfortable with the cli yet then I suggest you get the Linux and Ubuntu cheat sheets on fosswire. You can download the pdfs here:

[http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/)
[http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/)

Also if you want to dig into shell scripting have a look at [http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by longtom on 2009-04-04
> **hyper_ch said:**
> well, if you're not comfortable with the cli yet then I suggest you get the Linux and Ubuntu cheat sheets on fosswire. You can download the pdfs here:

[http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/)
[http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/)

Also if you want to dig into shell scripting have a look at [http://www.linuxcommand.org](http://www.linuxcommand.org)

Oh hyper_ch - you are full of the fluids of wisdom...!

Thank you for those links - however, this one:

> 
[http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/)


appears to be offline - hopefully only temporarily.

---

### Post by hyper_ch on 2009-04-04
they all work for me :)

---

### Post by longtom on 2009-04-04
> **hyper_ch said:**
> they all work for me :)

Yep - they do now.  Probably just a short blackout....

---

### Post by CatKiller on 2009-04-04
> **kenb12 said:**
> By the way, have not used Windows for three days now, when does the 'withdrawal' symptoms courtesy of Mr gates STRIKE!!!!!!!

When you want to play a game that doesn't work in Wine. That appears to be the main reason people give for keeping a Windows install around.

As a point of interest, it's not like you need to use the command line all the time. It's simply that it's significantly easier to give assistance by giving a poster a simple command that they can copy/paste than attempt to explain how to do the same thing by point and click. Plus the terminal gives feedback on why a command didn't work, which the graphical methods sometimes don't.

---

### Post by kenb12 on 2009-04-05
Will be following the leads given.
Have bought 'Ubuntu Linux for Dummies', and have also ordered 'Ubuntu Pocket Guide and Reference'. This is coming from the States to the UK, will take several weeks (so say Amazon) to arrive.In the meantime enjoying exploring Ubuntu and 'learning'.
Many thanks for all your help.
Much obliged.
kb

---

### Post by Armor Nick on 2009-04-05
> **CatKiller said:**
> As a point of interest, it's not like you need to use the command line all the time. It's simply that it's significantly easier to give assistance by giving a poster a simple command that they can copy/paste than attempt to explain how to do the same thing by point and click. Plus the terminal gives feedback on why a command didn't work, which the graphical methods sometimes don't.
That, and you don't need to give steps to make something work in fluxbox, kde, gnome, openbox, lxde, xfce, awesome, ratpoison, etc.

---

### Post by longtom on 2009-04-05
> **kenb12 said:**
> Will be following the leads given.
Have bought 'Ubuntu Linux for Dummies', and have also ordered 'Ubuntu Pocket Guide and Reference'. This is coming from the States to the UK, will take several weeks (so say Amazon) to arrive.In the meantime enjoying exploring Ubuntu and 'learning'.
Many thanks for all your help.
Much obliged.
kb

Have a look here:  [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

You can download the pdf Version of 'Ubuntu Pocket Guide and Reference' so long and get started until your book arrives.  THat's what I did - and it does take weeks...

---

