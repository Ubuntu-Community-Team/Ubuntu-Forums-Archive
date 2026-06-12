---
title: "boot into terminal mode"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by spiky001 on 2010-02-19
Hi is it possible to boot into terminal, so that you can still run programs but have to type i.e Firefox or Gimp etc & will the pc still work as with the gui . Ctr+Alt+F1 gives you text mode but cant run programs, I thought this might help with using the terminal, or is there away to switch to terminal hope, I made this clear enough as to what i want

---

### Post by tom.swartz07 on 2010-02-19
> **spiky001 said:**
> Hi is it possible to boot into terminal, so that you can still run programs but have to type i.e Firefox or Gimp etc & will the pc still work as with the gui . Ctr+Alt+F1 gives you text mode but cant run programs, I thought this might help with using the terminal, or is there away to switch to terminal hope, I made this clear enough as to what i want

Your explanation is a bit confusing, albeit a bit run-on-y. 
I think youre trying to say that you want to use the terminal, but still would like to have a GUI. 

You could open a terminal from the applications bar- applications>accessories>terminal

That should take care of your business

---

### Post by argos3016 on 2010-02-19
What do you want to say? Disable GDM?
sudo update-rc.d -f gdm remove

if you dont like the idea later you can do:
sudo update-rc.d -f gdm defaults

---

### Post by spiky001 on 2010-02-19
I thought it would be confusing, I would like to just use terminal to do every day things but the temptation to click with mouse is to easy I have tried opening a terminal as big as screen to hide it but temptation is there, I'd like to run everyday programs

---

