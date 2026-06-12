---
title: "Log in...hang up"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Keez on 2009-03-07
I am trying to install 8.10 on an old machine that I have.  It loads terribly slowly and then after you log in the system hangs up.  It is a 6 year old Dell running a 2.2 gig Celeron with 1 gig ram and a brand new 500 gig HD (cause the old one died).  I have run older versions of red hat in the past without problems, but reverted to windows because it didn't support my network card.  It would not run off the live CD for Ubuntu, Kubuntu, or Fedora 10.  Knoppix seems to work fine, but that's not what I want to run full time.  I can't find this anywhere in the guides and threads and I've been looking since yesterday afternoon.

Please...this is driving me nuts!

---

### Post by DGortze380 on 2009-03-07
> **Keez said:**
> I am trying to install 8.10 on an old machine that I have.  It loads terribly slowly and then after you log in the system hangs up.  It is a 6 year old Dell running a 2.2 gig Celeron with 1 gig ram and a brand new 500 gig HD (cause the old one died).  I have run older versions of red hat in the past without problems, but reverted to windows because it didn't support my network card.  It would not run off the live CD for Ubuntu, Kubuntu, or Fedora 10.  Knoppix seems to work fine, but that's not what I want to run full time.  I can't find this anywhere in the guides and threads and I've been looking since yesterday afternoon.

Please...this is driving me nuts!

Does the system actually freeze? or does X freeze?

Try again. When it 'hangs up', hit ctrl+alt+f1
It should drop to a log-in shell.
Log-in (you will not see ANYTHING when you type your password. Type anyways, hit enter)
To shutdown type: sudo shutdown -h now

---

### Post by Keez on 2009-03-07
Not sure, maybe it's just X.  Actually, I think it is because the cursor is still on the screen and moves, the screen is just black and nothing else happens.  I'll give it a try and let you know.  Thank you

---

### Post by Keez on 2009-03-07
Well, that did nothing.  Maybe it is the whole thing because it wouldn't let me do anything. couldn't Ctrl+Alt+Del either.  All I can do is to shut off the power with the switch and start over.  CD won't even eject.

---

