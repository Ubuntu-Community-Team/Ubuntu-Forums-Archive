---
title: "I'm stuck at the terminal. Yes i know that the password doesnt show when you enter it"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by SnugNuts on 2010-04-30
I'm just stuck at the terminal, I try typing it, and i can't even hit  enter. I've even changed my password and I still can't get it. I've been  looking around but can't find it, figure i would make a new thread.

Thanks

---

### Post by SnugNuts on 2010-04-30
...

---

### Post by slvr42 on 2010-04-30
Can you boot into single user mode or safe mode?

---

### Post by SnugNuts on 2010-04-30
Yes, I can. I got passed the command prompt part already, i just can't enter my password

---

### Post by slvr42 on 2010-04-30
So you can boot into single user mode and you get a root prompt.  But at that point it will not let you enter a password?

---

### Post by SnugNuts on 2010-05-01
[IMG]http://i.imgur.com/nG83v.png[/IMG]

yes, at this screen, i cannot type anything.

---

### Post by philodice on 2010-05-01
Have you made sure your mouse and keyboard and snugly plugged in?

---

### Post by slvr42 on 2010-05-01
If you hit the numlock key on your keyboard does the light come on and off?  I was thinking maybe your keyboard is not responding at all.  Another thing to try would be to interrupt the boot process and see if you can type anything.

---

### Post by SnugNuts on 2010-05-01
yea, everything is plugged in, im typing on here. I dont have a num lock light, its wireless, but the usb receiver is blinking. And i know its reading it because when i type the insertion point stops blinking, i type the password and hit enter, and i can't, so i click log in and i get authentication failure

---

### Post by slvr42 on 2010-05-01
any particular error message that goes along with the authentication error.

---

### Post by SnugNuts on 2010-05-01
Nope, nothing else pops up

---

### Post by SnugNuts on 2010-05-01
ive even tried installing it on a separate vm.  I also have fedora and it works fine.

---

### Post by ugm6hr on 2010-05-01
Have you got a wired keyboard to use? PS2 if possible.

It sounds like you can use the keyboard in recovery mode, but not in the Desktop Environment.

Trying a different keyboard would at least help to isolate where the problem is.

---

### Post by SnugNuts on 2010-05-01
> **ugm6hr said:**
> Have you got a wired keyboard to use? PS2 if possible.

It sounds like you can use the keyboard in recovery mode, but not in the Desktop Environment.

Trying a different keyboard would at least help to isolate where the problem is.
no wired keyboards here

but i can see that ubuntu is noticing that i am typing something because the insertion point stops blinking when i type.

---

### Post by Peter09 on 2010-05-01
Can you move the cursor, if so can you select a recovery terminal at the bottom of the screen?

---

### Post by SnugNuts on 2010-05-01
> **Peter09 said:**
> Can you move the cursor, if so can you select a recovery terminal at the bottom of the screen?
yes, the cursor works. and i dont see a recovery terminal.

---

### Post by KMThompson on 2010-05-01
> **SnugNuts said:**
> [IMG]http://i.imgur.com/nG83v.png[/IMG]

yes, at this screen, i cannot type anything.


I am having a similar problem.  I updated from 9.10 to 10.04 and cannot login at this GUI or press Enter either.  I also tried a fresh install on a separate vm and am having the same problem there (I run both on VMs).  The workaround I found to log in is to boot into recovery mode, then drop to a root shell prompt & reset my password.  Then I 'exit' and resume normal boot.  I have to log in still in text console mode and 'startx' my way to the GUI, but it gets me there.  Have you tried this?

---

