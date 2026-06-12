---
title: "Thousands of Instances of Firefox"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by mistypotato on 2010-05-15
If an object happens to fall on the keyboard while I'm NOT at the computer, Ubuntu willingly opens an indefinite number of instances of Firefox (for example).

This puts the computer into overdrive as Ubuntu labors to open the infinite number of windows (rather than intelligently sense the same window is being opened too many times in too short a time and cease the action).

So, is re-booting while Ubuntu is choking on all these windows it is trying to open the only way out of the mess?  As Im sitting here watching, the 9.10 Ubuntu computer (besides the one Im on now) is popping open new windows like rain falling on a windshield.

I tried Ctrl_Q but it keeps on opening windows.

thx

---

### Post by Paddy Landau on 2010-05-15
> **mistypotato said:**
> So, is re-booting while Ubuntu is choking on all these windows it is trying to open the only way out of the mess?
Log out if you can.
Otherwise, reboot if you can.
Otherwise, you'll have to hit the reset button.

Avoid dropping things on your keyboard ;)

---

### Post by BandD on 2010-05-15
you can try ctrl+alt+F1 and login to the command line there.  Then try the command:
```
sudo killall firefox
```

It might take a while for tty1 to come up, if at all.  If you are successful there, to get back to the gui press ctrl+alt+F7.

Hope that helps!

PS my cats get on the keyboard every now and then and decide to sit on the "print screen" button.  Not very fun.  Only once did it actually freeze the system though...

---

### Post by mistypotato on 2010-05-15
> **Paddy Landau said:**
> 
Avoid dropping things on your keyboard ;)

Good Advice.  A few other things to avoid....

auto accidents
falling down
cuts and bruises
bad food
bad investments
mean people
snakes
long lists.....

Wow.  If ONLY we really could always avoid all bad things <sigh>.

:P

Thanks BandD :KS:KS:KS

---

### Post by Paddy Landau on 2010-05-15
> **mistypotato said:**
> good advice.  A few other things to avoid....
lol

---

### Post by samg34 on 2010-05-15
try System>Administration>System Moniter
go to the processes tab
'kill' the firefox process

also try alt+f4

---

### Post by Sealbhach on 2010-05-15
> **mistypotato said:**
> If an object happens to fall on the keyboard while I'm NOT at the computer....



I'm just wondering what sort of environment you do your Ubuntu in.... I don't know if Canonical tested in these conditions.

---

### Post by crjackson on 2010-05-15
> **Sealbhach said:**
> I'm just wondering what sort of environment you do your Ubuntu in.... I don't know if Canonical tested in these conditions.

It happens here all the time.  If you a cat in the house it's not hard to figure out.

---

### Post by Paddy Landau on 2010-05-15
> **crjackson said:**
> If you a cat in the house it's not hard to figure out.
I don't allow my cats on the table, ever. They know that now and won't jump on. It saves me lots of problems -- and cleaning!

---

### Post by Sealbhach on 2010-05-15
[SIZE=3]Ubuntu* from Canonical.[/SIZE]


[SIZE=1]* not tested on cats.[/SIZE]

.

---

### Post by tgalati4 on 2010-05-15
Training your cat not to jump on the table will not prevent the same cat from peeing on your keyboard.

I know that Ubuntu is not pee-rated.

---

### Post by samg34 on 2010-05-16
Do they make Ubuntu for the CAT chip set?
I have been trying to find a good operating system for my pet. I think it would be a lot more stable if i did... If anyone finds it, try installing it on your cat and tell me if it will still jump on the table. My old cat that was running windows 7 died of a virus. I hope the Linux for cats has less viruses. I also noticed that it had a lot of ticks, flees, and other bugs. My friends say that Ubuntu has almost no bugs...:)

---

### Post by Sealbhach on 2010-05-16
Well, I've looked up the man pages for cat:

```
SEE ALSO
       The  full  documentation for cat is maintained as a Texinfo manual.  If
       the info and cat programs are properly installed at your site, the com&#8208;
       mand

              info coreutils 'cat invocation'

should give you access to the complete manual.


```

---

### Post by HotShotDJ on 2010-05-16
A simple and effective cure for the problem... get an inexpensive sliding keyboard tray.  Once you've mounted it underneath the desk or table, you just slide your keyboard safely away when you are not using it, out of the reach of curious paws and random falling objects.

For example: [http://www.ergonomicssimplified.com/products/images/keyboard-trays/budget-keyboard-tray1.jpg](http://www.ergonomicssimplified.com/products/images/keyboard-trays/budget-keyboard-tray1.jpg)

---

### Post by tgalati4 on 2010-05-16
Those keyboard trays do nothing to protect the mouse from being grabbed by the cat.  It's an instinctive thing.

---

